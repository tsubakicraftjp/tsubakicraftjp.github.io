---
layout: post
title:  "Guitar Calculator"
date:   2017-09-10 11:25:00 +0900
author: Kazuo Tsubaki
categories: ギター
---

### 概要


fret-calulatorという名前のプロジェクトで[GitHub](https://github.com/kazz12211/fret-calculator) で公開したものですが、プログラムにコメントが入っていないのでその解説のつもりでこの文章を書きました。以前はiOS用のアプリケーションとしてソースコードを配布していましたが、ビルド環境のない方が多くいらっしゃいましたのでWebアプリケーションにしました。

アプリケーションにアクセスするとこんな画面が表示されます。
タブが４つありますが「多様なフレッティング」は未実装です。ここには標準律以外の音階のフレット計算機能を実装する予定ですが、まだ自分が使用しないこともあって実装をサボっています。


![](/assets/post-images/guitarcalc.png)


指板にフレット溝を切るときにスマートフォンやタブレットを使ってアプリケーションにアクセスして計算します。

![](/assets/post-images/fretting1.jpg)

フレット溝を切った様子。

![](/assets/post-images/fretting2.jpg)


### 開発に使用した環境

#### サーバーサイド
Spring BootとJava 1.8

#### クライアントサイド
AngularJS 1.6.2、Angular Translate 2.13.1、Angular Translate Loader Static Files 2.13.1、HTML、CSS、JavaScript

#### IDE
EclipseにSprint Tool SuiteプラグインをインストールしたものとJava 1.8

herokuにアプリケーションをデプロイしてあるので動きを見たい方は[https://guitar-calc.herokuapp.com/](https://guitar-calc.herokuapp.com/)で見られます。


### 計算コンポーネント

GuitarCalculator.javaがプログラムの本体部分です。サービスコンポーネントとして作られています。


	package net.artesware.service;

	import java.util.Map;

	import org.springframework.stereotype.Component;

	import java.util.ArrayList;
	import java.util.HashMap;
	import java.util.List;

	@Component
	public class GuitarCalculator {

		// [1]
		public List<Map<String, Object>> calcFretPositions(
			float scale,
			int numFrets)
		{
			float f = scale;
			float lastPos = 0.0f;
			List <Map<String, Object>>result = new ArrayList<Map<String, Object>>();
			Map<String, Object> pos;
			for(int i = 0; i < numFrets + 1; i++) {
				float fretPos = f / 17.817f;
				f -= fretPos;
				pos = new HashMap<String, Object>();
				pos.put("fret", i+1);
				pos.put("positionFromNut", lastPos + fretPos);
				pos.put("positionFromFret", fretPos);
				result.add(pos);
				lastPos += fretPos;
			}
			return result;
		}

		// [2]
		public Map<String, Object> calcBridgePosition(
			float scale,
			float jointPos,
			float neckAngle,
			float stringHeight,
			float fretHeight,
			float thickness)
		{
			float base = (float) ((scale - jointPos) * Math.cos((double)neckAngle * Math.PI / 180.0f));
			float height = (float) ((scale - jointPos) * Math.sin((double)neckAngle * Math.PI / 180.0f));
			float strHeight = (stringHeight - 0.1f) * 2.0f + fretHeight;
			Map<String, Object> result = new HashMap<String, Object>();
			result.put("saddlePosition", base);
			result.put("saddleHeight", (height + strHeight + thickness));
			return result;
		}

		// [3]
		public Map<String, Object> calcFingerboardSize(
			float scale,
			int numStrings,
			int numFrets,
			float nutPitch,
			float saddlePitch,
			float nutSpacing)
		{
			float fretboardLength = (float) (scale - scale / Math.pow(2.0f, ((numFrets+1.0f)/12.0f)));
			float nutWidth = nutPitch * (numStrings - 1) + nutSpacing * 2;
			float bw = saddlePitch * (numStrings - 1) + nutSpacing * 2;
			float endWidth = nutWidth + (bw-nutWidth) * (fretboardLength/scale);
			Map<String, Object> result = new HashMap<String, Object>();
			result.put("length", fretboardLength);
			result.put("nutWidth", nutWidth);
			result.put("endWidth", endWidth);
			return result;
		}


	}

#### フレット位置の計算

[1]は標準律音階のフレット位置を求めるメソッドです。弦長とフレット数を引数にして呼び出すと各フレットの位置を計算します。結果はナット（０フレット）から距離と直前のフレットからの距離のリストが返ってきます。
例えばGibson Les Paulの場合は弦長が628mmで22フレットですから、scale=628、numFrets=22として呼び出します。


#### ブリッジ位置と高さの計算

[2]はブリッジ位置と高さを計算するメソッドです。弦長、ネックのボディ接合位置、ネック仕込み角、１２フレットでの弦高、フレット高、指板厚を引数にして呼び出すとネックとボディの接合点からのブリッジの位置と高さを計算します。

#### 指板寸法の計算

[3]は指板の寸法を計算するメソッドです。弦長、弦の数、フレット数、ナット位置での弦間隔、サドル位置での弦間隔、指板の側面から最高音弦と最低音弦までの距離を引数にして呼び出すと指板の寸法を計算します。



### RESTコントローラー

GuitarCalcController.javaはRESTコントローラークラスです。
HTTPリクエストを受け取ったらGuitarCalculatorコンポーネントのメソッドを呼び出して結果を返すだけの単純なものです。

	package net.artesware.controller;

	import java.util.List;
	import java.util.Map;

	import org.springframework.beans.factory.annotation.Autowired;
	import org.springframework.web.bind.annotation.GetMapping;
	import org.springframework.web.bind.annotation.RequestParam;
	import org.springframework.web.bind.annotation.ResponseBody;
	import org.springframework.web.bind.annotation.RestController;

	import net.artesware.service.GuitarCalculator;

	@RestController
	public class GuitarCalcController {

		@Autowired
		private GuitarCalculator calculator;

		// [1]
		@GetMapping("/calcFretPositions")
		@ResponseBody
		public List<Map<String, Object>> calcFretPositions(
			@RequestParam float scale,
			int numFrets) {
			return calculator.calcFretPositions(scale, numFrets);
		}

		// [2]
		@GetMapping("/calcBridgePosition")
		@ResponseBody
		public Map<String, Object> calcBridgePosition(
			@RequestParam float scale,
			float jointPos,
			float neckAngle,
			float stringHeight,
			float fretHeight,
			float thickness) {
			return calculator.calcBridgePosition(scale, jointPos, neckAngle, stringHeight, fretHeight, thickness);
		}

		// [3]
		@GetMapping("/calcFingerboardSize")
		@ResponseBody
		public Map<String, Object> calcFingerboardSize(
			@RequestParam float scale,
			int numStrings,
			int numFrets,
			float nutPitch,
			float saddlePitch,
			float nutSpacing) {
			return calculator.calcFingerboardSize(scale, numStrings, numFrets, nutPitch, saddlePitch, nutSpacing);
		}
	}


### おわりに

これを作ったときはSpring Bootを使ってみたかっただけでした。この程度のプログラムですとSpringを使わずにAngularJSを使ってクライアントサイドだけで実装した方がお手軽で良かったかもしれません。
ソースコードの改変やデプロイは自由に行っていただいて構いませんしクレジットも不要です。

*追記（平成29年9月14日）　[Electron版](https://github.com/kazz12211/guitarcalc)をGitHubに載せました。*

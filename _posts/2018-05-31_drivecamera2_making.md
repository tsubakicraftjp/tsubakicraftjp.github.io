---
layout: post
title:  "ドラカメ２の作成記録まとめ"
date:   2018-05-31 12:00:00 +0900
author: Kazuo Tsubaki
categories: IT
---
[メインブログ](https://tsubakicraft.wordpress.com)にドラカメの第２版の記事を書いていますが、ブログから記事を拾うのが記事一覧を作成しました。

[ドラカメ（ドライブレコーダー）を作り直す](https://wp.me/p7Mkw3-1Nk)

![](https://tsubakicraft.files.wordpress.com/2018/05/start_develop_dr.png?w=616)

記録映像に時刻、速度、位置情報を合成したかったのでAVCaptureVideoDataOutputを使った録画アプリとして作り直しを決意しました。別途ナビアプリを作ってBluetooth速度警告灯を点灯させることにしたので、第１版で実装した速度警告灯との通信機能は削除して、ドライブレコーダー機能だけに特化したものにすることにしました。

[ドラカメの作り直し２日目](https://wp.me/p7Mkw3-1Np)

![](https://tsubakicraft.files.wordpress.com/2018/05/img_0257.png?w=616)

なんとなく動くようになった日の記事です。

[ドラカメ２をダイソーのBluetoothリモートシャッターで操作する](https://wp.me/p7Mkw3-1NG)

![](https://tsubakicraft.files.wordpress.com/2018/05/img_0188.jpg?w=616)

ダイソーのBluetoothリモートシャッターを使って走行中に写真撮影ができるようにしました。

[だいぶそれらしくなってきたドラカメ２](https://wp.me/p7Mkw3-1NJ)

![](https://tsubakicraft.files.wordpress.com/2018/05/dr_video.png?w=616)
記録映像に時刻、速度、位置情報を合成できるようになった日の記事です。

[ドラカメ２の夜の車載テスト](https://wp.me/p7Mkw3-1NR)

自動車で夜間の写りを試したときの記事です。

[ドラカメの車載ホルダー〜隼](https://wp.me/p7Mkw3-1O2)

![](https://tsubakicraft.files.wordpress.com/2018/05/img_0214.jpg?w=616)

バイク用の車載ホルダーを作ったという記事です。

[ドラカメ２の車載テスト〜NMAX](https://wp.me/p7Mkw3-1O6)

![](https://tsubakicraft.files.wordpress.com/2018/05/img_0218.png?w=616)

製作した車載ホルダーが使い物にならなくてガッカリしたという記事です。

[ドラカメの核心部分のまとめ〜AVCaptureVideoDataOutputを使ってフレーム画像に文字を合成する](https://wp.me/p7Mkw3-1O9)

![](https://tsubakicraft.files.wordpress.com/2018/05/compose_video.png?w=616)

ドラカメ２で使われているビデオとテキストを合成して録画する部分のコードスニペットを公開しました。


[ドラカメ２の車載テスト〜NMAXで](https://wp.me/p7Mkw3-1Oz)

![](https://tsubakicraft.files.wordpress.com/2018/05/img_0235.jpg?w=616)

マウントを変更してテスト走行しました。

[ドラカメ２の車載テスト〜隼で](https://wp.me/p7Mkw3-1OI)

![](https://tsubakicraft.files.wordpress.com/2018/05/img_0252.jpg?w=616)

隼に搭載してテスト走行しました。

[今日もドラカメ２のテスト〜NMAX](https://wp.me/p7Mkw3-1Pn)

![](https://tsubakicraft.files.wordpress.com/2018/05/img_ea72aaf5f06c-1.jpg?w=616)

淡々とテストを繰り返す。

[ドラカメ２のテストで予想外の結果〜隼](https://wp.me/p7Mkw3-1Pr)

![](https://tsubakicraft.files.wordpress.com/2018/05/img_0471.jpg?w=616)

隼に載せてテスト走行しましたが、原因不明の問題が発生。

[ドラカメ２のテストを兼ねてNMAXでショートツーリング〜道志みちを通って山中湖まで](https://wp.me/p7Mkw3-1PR)

![](https://tsubakicraft.files.wordpress.com/2018/05/img_0335.jpg?w=616)

長時間の連続使用で問題点を見つけるためにツーリングに行きました。この日の気温は２０〜２５度、天気は晴れ。給電しながらの使用なので加熱が心配でしたが、このくらいの気温・天気なら問題はありませんでした。

[長距離ツーリングに備えて隼でドラカメとナビアプリの最終テスト](https://wp.me/p7Mkw3-1PV)

![](https://tsubakicraft.files.wordpress.com/2018/05/img_0501.jpg?w=616)

長距離ツーリングに備えて、ナビアプリとともにドラカメ２のテスト走行をしました。

これを書いている時点では、オーディオが正しく録音されない問題やいくつかの積み残しの機能がありますが、一旦、ここでプロジェクトは終了とします。今後は気が向いたときに少しずつ改良をしていくことにします。

ドラカメ２のソースコードは[GitHub](https://github.com/kazz12211/dr)で公開しています。

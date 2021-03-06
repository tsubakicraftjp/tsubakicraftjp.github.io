---
layout: post
title:  "新たに開発しようと思っているギター　〜　木以外の素材・極端なスキャロップド加工指板・デジタル信号処理"
date:   2017-08-20 15:40:47 +0900
author: Kazuo Tsubaki
categories: ギター
tags: ギター
---
椿工藝舎は小さな工房ですので、多くの分野の仕事ができるわけではありませんが、木工の技術、革工芸の技術、ITの技術をうまく組み合わせて新しい製品を作ろうという考えがあります。

これまで普通のギターを作ってきました。普通というのは、ほとんどが木で出来ていて、弦が張られていて、指板のフレットの間で指で弦を押さえて弦を弾く。弾いた弦の振動を磁石とコイルでできたピックアップで拾い、可変抵抗器で音の特性と大きさを変えてアンプに出力するというアナログの仕組みのギターです。

最近ではギターの製作に適した木材（ほとんどが輸入木材）の貿易が制限されたり、木材の供給が少なかったりして、材料が手に入らない、あるいは手に入っても高価であるという問題があります。世界中で多くの人がこの問題に取り組んでおり、木材を無駄なく使おうとする人、木材以外の材料を利用しようという人がいます。
ギターの材料になる木材は高価ですから、これまでも無駄なく使う努力はしてきましたが、材料費の高騰は製品の価格に跳ね返ります。大きなギターメーカーでは多くの材料を在庫できる経済力がありますが、小さな工房にはとてもそんな力はありません。できれば良質な製品を手頃な価格で提供したいと思っていますが、材料費が高くてはそれもできません。
そこでこれまで作ってきた普通のギターとは違う考え方でギターを作ることで、この問題を解決するか、別の問題に転換できるかもしれないと思いました。

弦を弾いて音を出すギターという根本的な部分を変えてしまうのも可能ですが、それはギター奏者にとって喜ばしいことではないかもしれません。ギターの形をした別のモノ、ギターの音が出る別のモノになってしまいそうです。
ですから、この部分は変えずに、それ以外の部分はガラっと変えてしまおうと思います。

#### 材料を変える
加工と入手がしやすい材料ということではカーボンやFRPなどの繊維素材、アルミや鉄などの金属素材が挙げられます。木材とは振動特性や音の伝達速度が違うので、事前の実験が必要かもしれませんが、すでに行われいることもでありますので問題はないと思われます。

#### 指板をなくす
日本の楽器である琵琶は指板がありません。フレットの間で弦を軽く押さえれば、フレットとサドル間の弦長で音の高さが一定に決まり、強く押さえればピッチベンドがかかります。スキャロップド加工された指板の極端なものと言えるかもしれません。直進性が安定したネックであれば、弦高を低く設定して、弦を軽く押さえるだけで弾けるギターになりますし、琵琶のような演奏スタイルも可能になります。

#### デジタル信号処理
マイクロコントローラーやDSPは高性能化・低価格かが進んでいます。ハイレゾオーディオほどの性能は必要なく、48KHz/16ビット程度のサンプリングが行えれば十分に実用的ですし入手しやすいマイクロコントローラーで信号処理が行えます。
デバイデッドピックアップ（弦ごとに振動を拾うピックアップ）のシステムなども売られていて、MIDIやギターシンセサイザー用の入力に使われることもあります。
磁石とコイルを使ったピックアップから出力される信号はハイインピーダンスですので、通常はプリアンプを取り付けてインピーダンスを下げます。デバイデッドピックアップでも通常のピックアップでもこの点は同じです。

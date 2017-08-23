---
layout: post
title:  "Nu Series Modular Pickup"
date:   2017-08-22 11:28:47 +0900
categories: ギター
---
最近見つけたCYCFI Research社が製造販売するデバイデッドピックアップの[Nu Series Modular Active Pickup](http://www.cycfi.com/projects/nu-series/)。
低インピーダンスで低ノイズ、各コイルにプリアンプを内蔵していて、弦ごとにマイコンやDSPでデジタル信号処理がしやすい設計になっています。20Hzから20KHzまでの周波数帯域でほぼフラットな特性なので、ギター以外の楽器にも適用できます。
ハードウェアの構造や電子回路がオープンソースとして公開されているので同じ機能のものを作ることもできます。

![](http://www.cycfi.com/wp-content/uploads/2016/02/Nu-Multi-3D.jpg)


[『新たに開発しようと思っているギター』の投稿](http://blog.tsubakicraft.jp/%E3%82%AE%E3%82%BF%E3%83%BC/2017/08/20/new-guitar.html)にも書きましたが、ギターをデジタル化するには、

- ピックアップからの信号のインピーダンスを下げるためにプリアンプを取り付ける
- 高速なADコンバーターを使う
- DSPを使う

ということが必要になりますが、このピックアップを使うならプリアンプはいらないことになります。
高速なADコンバーターは[『高速なADコンバーター』の投稿](http://blog.tsubakicraft.jp/%E9%9B%BB%E5%AD%90%E5%B7%A5%E4%BD%9C/2017/08/21/fast_adc.html)で書いたようなものが使えますが、これだと入力がステレオなので折角のデバイデッドピックアップの機能を活かせません。

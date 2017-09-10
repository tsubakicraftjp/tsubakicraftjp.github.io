---
layout: post
title:  "STM32CubeMXのC++プロジェクトでEclipseのエディタがシンボルが見つけられない問題"
date:   2017-09-08 09:47:00 +0900
author: Kazuo Tsubaki
categories: IT
---
STM32CubeMXで生成したプロジェクトをSystem Workbench for STM32 (AC6)でC++プロジェクトに変換してソースコードを開いたときに、AC6 (Eclipse)のエディターがSTM32のペリフェラルライブラリやHALライブラリのシンボルが見つからないという問題があります。これは標準のインデクサーの設定が適切ではないためです。
この問題を解消するには、プロジェクトの「Properties」を開き設定パネルを表示し、「C/C++ General」の「Preprocessor include Paths, MAcros etc.」の設定を変更します。

- ProvidersタブでCDT Cross GCC Built-in Compiler Settingsにチェックを入れる
- Use global provider shared between projectsのチェックを外す
- Command to get compiler specsに -std=c++11 を追加する

この設定をしてApplyをクリックして設定パネルを閉じます。(またはOKをクリックする)

![](/assets/post-images/resolve_symbol_cubemx_project.png)

次に「Project」メニューの「C/C++ Index」から「Rebuild」を選択するか、Project Explorerでプロジェクトを選択した状態で右クリックしてコンテクストメニューを開き「Index」から「Rebuild」を選んで、インデックスを再構成します。

これでAC6のエディタで快適にプログラミングができます。

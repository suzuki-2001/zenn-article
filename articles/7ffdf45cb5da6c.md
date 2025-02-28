---
title: "Beamer (Metropolis) でスライドを作る"
emoji: "🍁"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [Latex, Beamer, Metropolis]
published: true
---

大学/大学院生であればLatexで論文を書いたり、ミーティング資料を作成される方も多いと思います。
そこでLatexのプレゼンテーションパッケージであるBeamerを紹介します。

## Beamer
Beamerは、LaTeXで作成されたプレゼンテーション用のパッケージです。Latexの書式で作成でき、数式を美しくスライドに反映することができます。また、多くの方がBeamerのスライドテンプレートを公開しており、それらを利用することでモダンなスライドを作成することができます。

Beamerは、PDF形式で出力されるため、Adobe Readerやその他のPDFリーダーで表示することができます。また、Beamerは、動画ファイルなどの外部リソースをプレゼンテーションに追加することができるため、豊富なコンテンツを含むプレゼンテーションを作成することができます。

## Metropolis
Beamerの有名なテーマの一つに[Metropolis](https://github.com/matze/mtheme)があります。

![Metropolis theme](/images/beamer/metropolis_theme.png)
*Metropolis theme*

> Metropolis is a simple, modern Beamer theme suitable for anyone to use. It tries to minimize noise and maximize space for content; the only visual flourish it offers is an (optional) progress bar added to each slide.

テーマを適用することでスライドの見た目を整えることができます。Metropolisはmodern Beamer themeと謳っている通り、かなり整ったスライドを作成することができます。

GitHubからのインストール方法は以下手順です。

1. Metropolisリポジトリーのクローン
```
git clone https://github.com/matze/mtheme.git
```

2. `*.sty`ファイルを作成します。
```
% source/metropolistheme.ins
latex metropolistheme.ins
```

3. `*.sty`ファイルをフォルダーに移動します。複数のプレゼンテーションでMetropolisを使用する場合は、`make install`を実行するか、`*.sty`ファイルをTeXパス内のフォルダに移動することができます。ただし、TeXパス内のフォルダに移動する場合は、sudo権限が必要になる場合があります。

4. latex内で`\usetheme{metropolis}`と記述することでテーマを適用できます。


## テーマカラー設定

Metropolisはテーマカラーを自分でカスタマイズすることができます。
HTMLカラーコードで指定できるので、かなり見た目に変化をつけることができます。

```latex:
% ユーザーカラーを定義する
\definecolor{turquoise}{HTML}{40e0d0}
\definecolor{tomato}{HTML}{ff6347}

% カラーの適用
\setbeamercolor{alerted text}{fg=tomato}
\setbeamercolor{frametitle}{bg=turquoise}
```
***

:::message
より細かい設定に関しては[こちらのissue](https://github.com/matze/mtheme/issues/193)を参考にしてください。
:::

![background color](/images/beamer/background.jpeg)
*change background color*

```latex:
% ユーザーカラーを定義する
\definecolor{BlueTOL}{HTML}{222255}
\definecolor{BrownTOL}{HTML}{666633}
\definecolor{GreenTOL}{HTML}{225522}
\setbeamercolor{normal text}{fg=BlueTOL,bg=white}
\setbeamercolor{alerted text}{fg=BrownTOL}
\setbeamercolor{example text}{fg=GreenTOL}

% カラーの適用
\setbeamercolor{block title alerted}{use=alerted text,
    fg=alerted text.fg,
    bg=}
\setbeamercolor{block body alerted}{use={block title alerted, alerted text},
    fg=alerted text.fg,
    bg=}
\setbeamercolor{block title example}{use=example text,
    fg=example text.fg,
    bg=}
\setbeamercolor{block body example}{use={block title example, example text},
    fg=example text.fg,
    bg=}
```

`fg=`で文字の色を、`bg=`でブロック背景を設定できます。

`normal text`の`fg=`は単純に文章の色を指定できますが、`bg=`ではスライドの背景色が変わります。デフォルトだと薄いグレーですが、ここで色を指定するとその色に変わります。`bg=white`とすれば、画像を挿入した際に境界線が消えるので良いかもしれません。


## その他のテーマ

GitHubでBeamer-themeなどのタグを検索すると様々ななテーマが見つかります。いくつかおすすめを紹介しておきます。

- [sthlmNord BeamerTheme](https://github.com/mholson/sthlmNordBeamerTheme)
かなりモダンなスライドです。DarkとLightの二つのモードが用意されているので、目的に応じてスライドの雰囲気を変えることができます。

- [SimplePlus Beamer Theme](https://github.com/PM25/SimplePlus-BeamerTheme)
名前の通り白背景のとてもシンプルなスライドです。[SimpleDarkBlue Beamer Theme](https://github.com/PM25/SimpleDarkBlue-BeamerTheme)の色違いですね。

- [Focus v3.3.0](https://github.com/pcafrica/focus-beamertheme)
Metropolisをかっこよくした感じのスライドです。`# beamer-theme`で検索するとスター数がトップで一番上に出てきます。

## 最後に

BeamerはLatex記法で簡単にスライドを作成することができます。

Metropolisをはじめとして多くのモダンなテーマがユーザーによって公開されているので、Latexで文章を書いてるだけで美しいスライドができるのはBeamerの強みです。

Latexユーザーはぜひ一度お試しください。

## 参考資料
- [VSCode で最高の LaTeX 環境を作る](https://qiita.com/rainbartown/items/d7718f12d71e688f3573) :contentReference[oaicite:0]{index=0}
- [Latexmkから学ぶPDF化までの処理の流れ](https://qiita.com/Rumisbern/items/d9de41823aa46d5f05a8) :contentReference[oaicite:1]{index=1}
- [TEX Wiki (LaTeX入門)](https://texwiki.texjp.org/?LaTeX入門) :contentReference[oaicite:2]{index=2}
- [Metropolis GitHubリポジトリ](https://github.com/matze/mtheme) :contentReference[oaicite:3]{index=3}

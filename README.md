# 部誌作成テンプレート
これはLaTeXで複数記事を集めた部誌的なものを作成するためのテンプレートです。

[サンプルpdf](out/main.pdf)

## 準備
このテンプレートを使うには
- 完全なTeX Live環境


が必要です。macについてはHomebrewを使ってmactexをインストールしてもらえれば大丈夫です。
私はWinユーザーではないので全く保証はできませんが，Windowsについては[WSL](https://learn.microsoft.com/ja-jp/windows/wsl/install)を使ってUbuntuをインストールするのが便利らしいです。
Ubuntuならば，以下のコマンドでインストールできるらしいです。
```
#アップデートと更新
sudo apt update
sudo apt upgrade

# TeX Liveのインストール
sudo apt install texlive-full
```

こだわりがない限りはVSCodeを使って書くのが便利そうです。
私は[VSCode で最高の LaTeX 環境を作る](https://qiita.com/rainbartown/items/d7718f12d71e688f3573)という記事を参考にVSCodeでLaTeXできるようにしました。
テンプレートの中にある.latexmkrcファイルもこのサイトのものを丸パクリしています。

## 使い方
GitHubで「Use this template」をクリックして、リポジトリを作成するのが便利です。
詳しくは，[テンプレートからリポジトリを作成する](https://docs.github.com/ja/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template)等を参照してみてください。

### 表紙
Titleフォルダの中にあるtitle.texをmain.texで読み込むことで表紙を表示します。
表紙は別で作成して，画像（比率はA4と同じ）として出力することを想定しています。
title.texの中の\includegraphics{}に読み込む画像のパスを書くことでその画像が表紙として表示されます。
画像は画面いっぱいいっぱいに出力されるようにしています。
[TeXでjsbookの表紙いっぱいに画像を設定する](https://qiita.com/gatosyocora/items/396d11b94d9201c61094)を参考にしました。

### 序文
Hajimeniフォルダの中にあるhajimeni.texをmain.texで読み込むことで序文を表示します。
hajimeni.texの中身はchapter*扱いなので，章題を変更することで「はじめに」の部分を変更できます。
frontmatter.texではじめにと目次の体裁を制御しています。
デフォルトではmcfamilyで中央に表示するようにしています。
また，この部分はヘッダーがページ番号になるようにしています。

### 目次(TOC)
Table Of Contents (略してTOC) はいつも通り\tableofcontentsコマンドで出力するのですが，その体裁を整えるためにTOCフォルダの中にあるTOC_style.texを読み込んでいます。
このファイルでは「目次」の字の間のスペースと，\partのTOCが中央に表示されるように制御しています。

### 記事
一人分の記事のtexファイルとその記事で使われている画像等が入ったフォルダをArticlesフォルダに入れてください。
Articleフォルダ内のcombineフォルダに，記事と全体を繋ぐtexファイルをcombine_sample.texのように記述して，そのcombine_hogehoge.texファイルをmain.texで読み込んでください。
本来，記事は少なくともsectionの構造をもつものとして体裁を整えていますが，**万が一sectionの構造すら持たない文章だけの記事の場合**はcombineフォルダ内のcombine_sanple.texのようにはじめに\input{Header/only_pages.tex}, 終わりに\input{Header/section_subsection.tex}を読み込むことを推奨します。

また，参考文献はArticles/sankoubunken_template/sankoubunken_template.tex　のように記述してください。いつものthebibliographyの上下をこのテンプレのように挟んでください。

また，Articleフォルダ内のarticles_style.texで記事の体裁について記述しています。
sectionの番号を記事ごとにリセットするためのコードを元に定義しています。
また，デフォルトではchapterは終わるごとに奇数ページ始まりになるのですが，それをやめてchapter終わり直後のページから次のchapterが始まるようにしています。

また，白紙ページを挿入したくなった場合は（例えばPartを奇数ページ始まりにしたい場合）手動で\afterpage{\blankpage}と記述してください。
このコードはpreambleフォルダのarticle.texで定義しています。

### 奥付
奥付もかけます。OkudsukeフォルダのOkudsuke.texに倣って必要事項を記入してください。










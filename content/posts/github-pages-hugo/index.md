+++
title = 'GitHub PagesにHugoで作ったサイトを公開する方法'
date = 2024-07-31T11:04:43+09:00
draft = false
+++

GitHub Pagesを長らく使用していませんでしたが、  
今回このブログを作成するにあたり、GitHub Pagesの仕様も色々と変わっていたようなので改めて調査しました。

<!--more-->

### 前提条件
* 2024年7月現在
* 作業PC：Windows 11 Home (x64)
* git version 2.45.2.windows.1
* hugo v0.129.0

&nbsp;  

### 1. GitHubにて新しいリポジトリを作成する

#### リポジトリの作成
* リポジトリ名： `username.github.io` とする
* 可視性：Public を選択
* READMEファイルを追加しておく

#### リポジトリの設定
* 作成したリポジトリの Settings → Pages を開く
* Source： `GitHub Actions` を選択
    ||
    |-|
    |![](/posts/github-pages-hugo/ss1.png)|
    * browse all workflows をクリック
    * Search workflows に `hugo` と入力し、出てきた Hugo workflow の Configure をクリック
        ||
        |-|
        |![](/posts/github-pages-hugo/ss2.png)|
    * 右上の Commit changes... をクリック
    * Commit message 等はそのままで、Commit changes をクリック
        ||
        |-|
        |![](/posts/github-pages-hugo/ss3.png)|
* Enforce HTTPS：有効であることを確認

&nbsp;  

### 2. Hugo サイトの作成
#### サイトの作成
* Windows のコマンドプロンプトにて以下を実行：
    ```bash
    # リポジトリのクローン
    > cd [作業ディレクトリ]
    > git clone https://github.com/username/username.github.io.git
    > cd username.github.io

    # 必要に応じてリポジトリ用のユーザー設定を登録
    > git config user.name "username"
    > git config user.email "username@example.com"
    > git config --list --local

    # hugo サイトの作成
    > hugo new site . --force  # 空でないフォルダに新規作成の場合 --force が必要
    # 任意のテーマを追加
    > git submodule add https://github.com/nodejh/hugo-theme-mini.git themes/mini
    ```
* テキストエディタで `hugo.toml` を開き、次を追加：
    ```toml
    theme = 'テーマ名'
    # 今回の場合
    theme = 'mini'
    ```

#### 記事の作成

* Windowsの場合、`/archetypes/default.md` をテキストエディタで開き、改行コードを LF から CRLF に変更しておくとよい。
* 最初のポストを作成
    ```bash
    # ポストを作成する
    > hugo new content content/posts/first-post/index.md
    ```
    content/posts/first-post.md ではなく上記のようにする。  
    first-postというフォルダが作成され、その中に表示させる画像等を格納するため。
* `/first-post/index.md` をテキストエディタで編集する

&nbsp;  

### 3. 変更内容の送信
#### リポジトリへのプッシュ
* コミットおよびプッシュの実行
    ```bash
    > git add .
    > git commit -m "Initial Commit"
    > git push
    ```
* push後、GitHub Actions によりサイトのビルドが行なわれる。
* ビルド完了後、https://username.github.io にてサイトが公開される。

&nbsp;  

***

#### その他注意点
* リポジトリ作成時に作成した README.md は、不要な場合は変更をコミットする前のタイミングで削除しても問題ありません。
* `hugo.toml` に baseURL を設定するところがありますが、baseURL の値は GitHub Actions でのビルド時に Hugo workflow によって上書きされるので、これについては特に指定しなくてもよさそうです。
    ```yaml
    # hugo.yml 抜粋
    run: |
        hugo \
        --minify \
        --baseURL "${{ steps.pages.outputs.base_url }}/"
    ```
* ここで、base_url にはリポジトリ名（username.github.io）が入ります。  
    カスタムドメインが設定されている場合は、そのドメインが入ると思われます。  
    リポジトリの Pages の設定で、Enforce HTTPS を有効にしていると `https://` が、無効だと `http://` がURLスキーム名となります。
    Enforce HTTPS が無効になっている場合に、トップページは HTTPS で表示されるのに HTML の構成ファイル（テーマで指定されている CSS ファイル等）が HTTP で読み込まれようとすると混在コンテンツ (mixed content) エラーとなり正しく読み込まれませんので、ご注意ください。

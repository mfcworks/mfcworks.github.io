+++
title = 'Markdown Example'
date = 2024-07-30T13:40:08+09:00
draft = false
+++

以下はHugoで使用できるMarkdown記法の例です。

<!--more-->

&nbsp;  

## ◆ 改行・空行の入れ方
```markdown
これは１行目です。
２行目を改行しただけで書くと実際には改行されません。
```
これは１行目です。
２行目を改行しただけで書くと実際には改行されません。

&nbsp;  

```markdown
これは１行目です。  ←(ここに半角スペースが２つある)
１行目の行末に半角スペースを2つおくと２行目は改行されます。
```
これは１行目です。  
１行目の行末に半角スペースを2つおくと２行目は改行されます。

&nbsp;  

```markdown
これは１行目です。

１行目と２行目の間に空行を入れると段落分けされます。
```
これは１行目です。

１行目と２行目の間に空行を入れると段落分けされます。

&nbsp;  

```markdown
文章と文章の間隔を空けるには、

&nbsp;  ←(ここに半角スペースが２つある)

必要な分だけ "&nbsp;  "＋改行を入れます。
```
文章と文章の間隔を空けるには、

&nbsp;  

必要な分だけ "\&nbsp;&ensp;&ensp;"＋改行を入れます。


&nbsp;  
&nbsp;  
&nbsp;  

## ◆ 見出し

``` markdown
# 見出し H1

## 見出し H2

### 見出し H3

#### 見出し H4

##### 見出し H5

###### 見出し H6
```

# 見出し H1

## 見出し H2

### 見出し H3

#### 見出し H4

##### 見出し H5

###### 見出し H6

&nbsp;  
&nbsp;  
&nbsp;  

## ◆ 文字の強調

```markdown
*これは斜体の文です。*  
**これは太字の文です。**  
***これは斜体かつ太字の文です。***  
~この文は取り消し線が引かれています。~
```

*これは斜体の文です。*  
**これは太字の文です。**  
***これは斜体かつ太字の文です。***  
~この文は取り消し線が引かれています。~

&nbsp;  
&nbsp;  
&nbsp;  

# ◆ 水平線
```markdown
↓ この下に水平線を挿入します。
***
```
↓ この下に水平線を挿入します。
***

&nbsp;  
&nbsp;  
&nbsp;  

# ◆ 箇条書き
```markdown
- 番号無しの項目
    - 番号無しの子項目
    - 番号無しの子項目
- 番号無しの項目
    - 番号無しの子項目
    - 番号無しの子項目
```
- 番号無しの項目
    - 番号無しの子項目
    - 番号無しの子項目
- 番号無しの項目
    - 番号無しの子項目
    - 番号無しの子項目

&nbsp;  

```markdown
1. 番号付きの項目
    1. 番号無しの子項目
    2. 番号無しの子項目
2. 番号付きの項目
    1. 番号無しの子項目
    2. 番号無しの子項目
```
1. 番号付きの項目
    1. 番号無しの子項目
    2. 番号無しの子項目
2. 番号付きの項目
    1. 番号無しの子項目
    2. 番号無しの子項目

&nbsp;  
&nbsp;  
&nbsp;  

# ◆ チェックリスト
```markdown
- [x] 完了した項目
- [ ] 未完了の項目
    - [x] 完了した子項目
    - [ ] 未完了の子項目
```
- [x] 完了した項目
- [ ] 未完了の項目
    - [x] 完了した子項目
    - [ ] 未完了の子項目

&nbsp;  
&nbsp;  
&nbsp;  

# ◆ 引用
```markdown
> この文章は引用されています。  
> 引用とは、他人の書いた文章を  
> 自分の文章の中に取り込む方法です。
```
> この文章は引用されています。  
> 引用とは、他人の書いた文章を  
> 自分の文章の中に取り込む方法です。

&nbsp;  
&nbsp;  
&nbsp;  

# ◆ ソースコード
```markdown
以下は`JavaScript`コードのサンプルです。(※注：このコード例はインデントされています)
    ```JavaScript
    function hello(name) {
        console.log(`Hello, ${name}!`);
        return;
    }
    ```
```
以下は`JavaScript`コードのサンプルです。
```JavaScript
function hello(name) {
    console.log(`Hello, ${name}!`);
    return;
}
```

&nbsp;  
&nbsp;  
&nbsp;  

# ◆ リンク
```markdown
www.example.com にアクセスするには[ここ](https://www.example.com)をクリックしてください。

ポップアップするタイトル付きの[リンク](https://www.example.com "Example Domain")を作成することもできます。

https://はじめよう.みんな のように、自動的にURLと認識されないアドレスは、  
<https://はじめよう.みんな> とするとリンクになります。
```
www.example.com にアクセスするには[ここ](https://www.example.com)をクリックしてください。

ポップアップするタイトル付きの[リンク](https://www.example.com "Example Domain")を作成することもできます。

https://はじめよう.みんな のように、自動的にURLと認識されないアドレスは、  
<https://はじめよう.みんな> とするとリンクになります。

&nbsp;  
&nbsp;  
&nbsp;  

# ◆ 脚注
```markdown
これは脚注付きの文です[^1]。脚注は本文末に表示されます。

[^1]: これは脚注です。
```
これは脚注付きの文です[^1]。脚注は本文末に表示されます。

[^1]: これは脚注です。

&nbsp;  
&nbsp;  
&nbsp;  

# ◆ 画像の挿入
ポストに画像を挿入するには、以下のようなフォルダ構成にします。  
ここでは、picture.jpg を挿入するものとします。
```
content/
└── posts/
    └── post-title/
        ├── index.md
        └── picture.jpg
```
`index.md` で、以下のように記述します。
```markdown
![altテキスト](/posts/post-title/picture.jpg)
```
![altテキスト](/posts/markdown-example/picture.jpg)


画像をリンクにするには、以下のようにします。
```markdown
[![altテキスト](/posts/post-title/picture.jpg)](/posts/post-title/picture.jpg)
```
[![altテキスト](/posts/markdown-example/picture.jpg)](/posts/markdown-example/picture.jpg)


&nbsp;  
&nbsp;  
&nbsp;  

# ◆ 表
* １列目：左寄せ（既定）
* ２列目：左寄せ（明示）
* ３列目：中央揃え
* ４列目：右寄せ

にしています。

```markdown
| Header 1 | Header 2 | Header 3 | Header 4 |
|----------|:---------|:--------:|---------:|
| Data 1   | Data 2   | Data 3   | Data 4   |
| Data 5   | Data 6   | Data 7   | Data 8   |
| Data 9   | Data 10  | Data 11  | Data 12  |
| Data 13  | Data 14  | Data 15  | Data 16  |
```
| Header 1 | Header 2 | Header 3 | Header 4 |
|----------|:---------|:--------:|---------:|
| Data 1   | Data 2   | Data 3   | Data 4   |
| Data 5   | Data 6   | Data 7   | Data 8   |
| Data 9   | Data 10  | Data 11  | Data 12  |
| Data 13  | Data 14  | Data 15  | Data 16  |

&nbsp;  
&nbsp;  
&nbsp;  

# ◆ 数式
```markdown
例１：
$$ \sigma = \sqrt{\frac{1}{N} \sum_{i=1}^{N}(x_i-\mu)^2} $$
例２：
$$ i \hbar \frac{\partial}{\partial t} \psi(\mathbf{r}, t) = \left( -\frac{\hbar^2}{2m} \nabla^2 + V(\mathbf{r}, t) \right) \psi(\mathbf{r}, t) $$
```
例１：
$$ \sigma = \sqrt{\frac{1}{N} \sum_{i=1}^{N}(x_i-\mu)^2} $$
例２：
$$ i \hbar \frac{\partial}{\partial t} \psi(\mathbf{r}, t) = \left( -\frac{\hbar^2}{2m} \nabla^2 + V(\mathbf{r}, t) \right) \psi(\mathbf{r}, t) $$

&nbsp;  
&nbsp;  
&nbsp;  

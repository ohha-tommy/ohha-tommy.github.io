
#### はじめてのマークダウン方式

### 文章の書き方

HTMLと比べながら覚える。  

文章は p タグで囲うところはなにもいらない。  
途中改行したい場合は、br タグを突っ込むところに半角スペースを２ついれて改行。n\  
n\は正規表現  

### jQuery Sample

    jQuery(function(){
      alert('HELLO');
    });

### 見出しの書き方（h1～h5）

htmlでh1～h5タグを使うところを# ## ###と付ける。  


### リストの書き方（ul+li、ol+li）

リストは ul と li タグを使うところを*であらわす

* HTML
* CSS
* JavaScript

ul の代わりに ol を使うと箇条書きの頭に連番がつきやす

1. HTML
2. CSS
3. JavaScript

### リンクの書き方（a）

リンクは a タグを使いやす。たとえば google にリンクを貼るにはこう書きます。

[天気予報](http://www.jma.go.jp/jp/yoho/320.html)

リンク先を別ウィンドウに表示したい場合は target属性を書きます。

<a href="http://www.google.com" target="_blank">Goolge</a>

### 画像読み込みの書き方（img）

img タグを使います。src 属性に画像ファイルの所在を書きます。

![おいしそうなガレットという説明](http://img04.ti-da.net/usr/soraumiblue/%E7%94%9F%E3%83%8F%E3%83%A0%E3%81%A8%E3%83%AB%E3%83%83%E3%82%B3%E3%83%A9%E3%81%AE%E3%82%AC%E3%83%AC%E3%83%83%E3%83%882.jpg)



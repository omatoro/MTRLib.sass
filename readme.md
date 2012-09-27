ライブラリの制作の方法については、以前のエントリである<a href="http://testcording.com/?p=355" title="Sassで未対応ブラウザへのCSS3使用は警告＆自動修正！">「Sassで未対応ブラウザへのCSS3使用は警告＆自動修正！」</a>を参考にしてください。今回は、紹介しているトピックスをまとめたものをライブラリとして公開する旨のエントリーとなります。こんな感じでライブラリ作ってますよ！と言いたいだけなので、まだまだ完成とは言えるものではありません。

　<br />
<a href="http://testcording.com/wp-content/uploads/2012/09/MTRLib.png"><img src="http://testcording.com/wp-content/uploads/2012/09/MTRLib.png" alt="" title="MTRLib" width="750" height="340" class="aligncenter size-full wp-image-557" /></a>
　<br />　<br />

<!--more-->

<h1 class="headline_2">何ができるのか</h1>
予め対応予定のブラウザを設定してください。すると勝手に CSS3 に対応していない場合は警告を出します。中には自動で IE に対応するものもあります。なので CSS3 のブラウザ対応表とにらめっこする必要がありません。



<h1 class="headline_2">導入方法</h1>
<a href='http://testcording.com/wp-content/uploads/2012/09/MTRLib.zip'>こちら</a>でダウンロード後、普段使用している <a title="Sass" href="http://sass-lang.com/">Sass</a> のファイルがあるフォルダ内にコピー後、「 _mtrlib.scss 」をインポートしてください。それだけです。

　<br />

まだ <a title="Sass" href="http://sass-lang.com/">Sass</a> 自体をインストールしていない場合は、<a href="http://testcording.com/?p=497" title="Sass導入 – Windows7 + Sass">「Sass導入 – Windows7 + Sass」</a>を参考にしてみてください。

　<br />
<a href="http://testcording.com/wp-content/uploads/2012/09/MTRLib.zip"><img src="http://testcording.com/wp-content/uploads/2012/09/2012-09-23_23h21_071.png" alt="" title="2012-09-23_23h21_07" width="259" height="145" class="aligncenter size-full wp-image-575" /></a>
　<br />　<br />


<h1 class="headline_2">使い方</h1>

CSS3 を直に書いている場合は、以下のようなソースになっているかと思います。

 
<pre class="lang:default decode:true " >
body {
    -webkit-border-radius: 5px;
    -moz-border-radius: 5px;
    -ms-border-radius: 5px;
}</pre> 

これを以下に書き換えてください。

 
<pre class="lang:default decode:true " >
body {
    @include border-radius(5px);
}</pre> 


このように CSS3 のプロパティを書き換えます。これだけで勝手にベンダープレフィックスを出力する上、未対応ブラウザに対しては警告を出します。

　<br />　<br />
<h1 class="headline_2">パラメータの設定</h1>

<h1 class="headline_3">対応ブラウザ</h1>

対応予定のブラウザを設定します。「 _exparam.scss 」ファイルを開いてください。以下の変数が定義されていると思います。

 
<pre class="lang:default decode:true " >$SUPPORT_WIN_IE8:        false;</pre> 

これを以下に書き換えてください。

 
<pre class="lang:default decode:true " >$SUPPORT_WIN_IE8:        true;    // IE8に対応する必要がある</pre> 


すると、当ライブラリを使用している CSS3 のプロパティで、 IE8 に対応していないものがあればコンパイル時に警告を出します。中には自動で IE 用に変換されるものもあります。その場合も変換したことを警告で知らせてくれます。

　<br />
<a href="http://testcording.com/wp-content/uploads/2012/09/2012-09-23_23h15_18.png"><img src="http://testcording.com/wp-content/uploads/2012/09/2012-09-23_23h15_18.png" alt="" title="2012-09-23_23h15_18" width="707" height="522" class="aligncenter size-full wp-image-556" /></a>
　<br />


<h1 class="headline_3">使用するベンダープレフィックス</h1>


「 _exparam.scss 」ファイルを開いてください。以下の変数を定義します。

 
<pre class="lang:default decode:true " >$USE_WEBKIT: false;</pre> 

すると、「 -webkit- 」を使用しません。対応不要なベンダープレフィックスの出力を行わないよう設定することができます。

　<br />

他にもいくつかパラメータがありますが、もう少しライブラリの完成が近づいたらドキュメントでも作ろうかと思ってます。(使う方がいればの話ですが)

　<br />　<br />
<h1 class="headline_2">現在作成しているプロパティ</h1>

作っているプロパティの一覧です。もし、こんなのを作って欲しいなどありましたら是非 <a href="https://twitter.com/omatoro">Twitter</a> にて連絡を頂ければと思います。

<h1 class="headline_3">RGBA</h1>

 
<pre class="lang:default decode:true " >body {
    color: rgba(255,255,255,0.5);
}</pre> 


<h1 class="headline_3">HSLA</h1>

 
<pre class="lang:default decode:true " >body {
    color: hsla(255,255,255,0.5);
}</pre> 


<h1 class="headline_3">border-radius</h1>

 
<pre class="lang:default decode:true " >body {
    @include border-radius(3px);
}</pre> 


<h1 class="headline_3">box-shadow</h1>

 
<pre class="lang:default decode:true " >body {
    @include box-shadow(5px 5px 5px 5px #111111);
}</pre> 


<h1 class="headline_3">opacity</h1>

 
<pre class="lang:default decode:true " >body {
    @include opacity(0.5);
}</pre> 


<h1 class="headline_3">transition</h1>

 
<pre class="lang:default decode:true " >body {
    @include transition(border, 0.1s, linear);
}</pre> 


　<br />　<br />

<h1 class="headline_2">ライセンス</h1>
<a href="http://ja.wikipedia.org/wiki/MIT_License">MIT License</a>
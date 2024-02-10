# CSSエディタ

[CSSエディタモジュール](https://omeka.org/s/modules/CSSEditor){target=_blank}は、Omeka Sの管理インターフェースからCSSを記述することを可能にします。

管理ダッシュボードの[モジュール](https://omeka.org/s/docs/user-manual/modules/){target=_blank}セクションで有効化された後、CSSエディタはサイトごとに使用されます。

CSSの使い方が初めての場合、以下の無料リソースが学習を開始するのにお勧めです：

* [Mozillaの「CSSを学ぶ」](https://developer.mozilla.org/en-US/docs/Web/CSS){target=_blank}
* [Codecademyの「CSSを学ぶ」コース](https://www.codecademy.com/learn/learn-css){target=_blank}
* [Marksheetの「CSSの基礎」](https://marksheet.io/css-basics.html){target=_blank}

CSS編集のためのOmeka Sページコンポーネントを学ぶ最も簡単な方法は、選んだテーマを見ているときにブラウザの「検証」ツールを使用することです。

## CSSエディタインターフェースの使用方法

CSSエディタがアクティブであれば、各サイトのコンテキストメニューにCSSエディタへのリンクが表示されます。

![CSSエディタナビゲーションアイテムが強調表示されたOmeka Sサイトのコンテキストメニューのスクリーンショット。](modulesfiles/csseditor_contextmenu.jpg)

最初の大きなテキストエリアは、個々のスタイルを記述する場所です。これはスタイルシートファイルと同様に使用します。これにより、選択したOmeka Sサイトのすべてのパブリックページのhead内に以下のような行を読み込みます：

`<link href="/yoursiteslug/css-editor" media="screen" rel="stylesheet" type="text/css">`

この行は、Omekaのデフォルトや選択したテーマから来るスタイルシートの後に表示されます。したがって、ここにあるエントリは、`!important`としてマークされていない限り、それらのファイルに設定された他のスタイルを上書きするべきです。また、メインアクセントカラーやバナーの高さといったテーマ設定からのカスタムCSSなど、この行の下にヘッダーでロードされる他のカスタムCSSがあるかもしれません。これらは、あなたのカスタムCSSに優先して適用される可能性があります。

![CSSエディタモジュールインターフェースのスクリーンショット。](modulesfiles/csseditor_interface.jpg)

CSSエディタを使用すると、URLを入力することで外部スタイルシートを含むことも可能です。外部スタイルシートURLを入力する数に制限はありません。各テキスト入力は単一のURLを受け取り、追加の入力は「別のスタイルシートを追加」ボタンをクリックすることで作成できます。

外部スタイルシートを削除するには、テキスト入力をクリアするか、複数のスタイルシートフィールドがある場合はゴミ箱アイコンをクリックします。

![外部スタイルシートフィールドにフォーカスし、削除ボタン（ゴミ箱アイコン）が強調表示されたCSSエディタモジュールインターフェースのスクリーンショット。](modulesfiles/csseditor_remove.jpg)

## チュートリアル：Googleウェブフォントを使用する

カスタムフォントを使用することで、Omeka Sサイトをより特徴的にすることができます。[Googleは無料のウェブフォントライブラリを提供しています](https://fonts.google.com/){target=_blank}。このチュートリアルでは、「デフォルト」テーマを使用しているOmeka Sサイトに、CSSエディタインターフェースを通じてウェブフォントを適用する方法を示します。

参考までに、"Default"テーマは、「Open Sans」フォントを使用して以下のように見え始めます。

![「デフォルト」テーマのOmeka Sサイトのスクリーンショット。全てのテキストが「Open Sans」を使用しています。](modulesfiles/csseditor_before.jpg)

このチュートリアルでは、「Open Sans」を「Lato」フォントファミリーに上書きします。

1. [Googleフォント](https://fonts.google.com/){target=_blank}にアクセスし、「Lato」フォントファミリーを探して、それを選択するためにオレンジ色の「+」ボタンをクリックしてください。
   ![「Lato」フォントファミリーが強調表示されたGoogleフォントのメインページ](modulesfiles/csseditor_tutorial1.jpg)<br>
2. 右下に「1ファミリーが選択されました」とラベル付けされたバーが表示されます。このバーをクリックしてください。
   ![選択したフォントファミリーバーが強調表示されたGoogleフォントページのトリミングビュー](modulesfiles/csseditor_tutorial2.jpg)<br>
3. バーを開くと、サイトでLatoを使用するために必要な情報が記載されたパネルが表示されます。「このフォントを埋め込む」という最初のセクションには、必要な外部スタイルシートURLがあります。`href`属性にあるURLを選択してください、下の画像のように。
   ![「このフォントを埋め込む」セクションのスクリーンショット、外部スタイルシートのURL（"https://fonts.googleapis.com/css?family=Lato&display=swap"）が強調表示。](modulesfiles/csseditor_tutorial3.jpg)<br>
4. このURLをCSSエディタの「外部スタイルシート」入力の1つにコピーしてください。
   ![外部スタイルシートフィールドに貼り付けられたスタイルシートURLに焦点を合わせたCSSエディタモジュールインターフェースのスクリーンショット。](modulesfiles/csseditor_tutorial4.jpg)<br>
5. Googleフォントパネルに戻ると、2番目のセクションである「CSSで指定する」があります。`font-family`のルールをコピーしてください。
   ![「CSSで指定する」セクションのスクリーンショット、「font-family: 'Lato', sans-serif;」のフォントファミリールールが強調表示](modulesfiles/csseditor_tutorial5.jpg)<br>
6. このチュートリアルでは、Latoをサイトのデフォルトフォントとして設定しています。これを実現するために、CSSエディタの大きな「CSS」テキストエリアで、コピーしたルールを使って`body`要素のフォントファミリーを設定してください。
   ![「body {font-family: "Lato", sans-serif;}」のボディフォントファミリールールが貼り付けられたCSSエディタモジュールインターフェースのCSSテキストエリアに焦点を合わせたスクリーンショット。](modulesfiles/csseditor_tutorial6.jpg)<br>
7. 右上隅にある「保存」ボタンをクリックしてください。「デフォルト」テーマの見た目はこれになります。
![「デフォルト」テーマのOmeka Sサイトのスクリーンショットで、全てのテキストが「Lato」フォントで表示されている](modulesfiles/csseditor_after.jpg)
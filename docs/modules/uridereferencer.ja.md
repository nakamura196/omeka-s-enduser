# URI デリファレンサ

[URI Dereferencer モジュール](https://omeka.org/s/modules/UriDereferencer/){target=_blank} は、Omekaのアイテム、メディア、アイテムセットのページで多くのURIのソースから動的にデータを表示させることができます。

このモジュールには設定項目がなく、管理ダッシュボードに機能を追加することもありません。内蔵された[リンクデータサービス](#リンクデータサービス)から認識できるURIに関しては、リソースビューにメタデータ値としてURIが入力されているすべての場所でフロントエンドに表示されます。

![Creator フィールド内の2つのURIに [+] トグルリンクが横にある様子。](modulesfiles/uri-display.png)

このモジュールは、ページ上のURIを検索し、ページから離れることなくリンクされたデータのスナップショットをユーザーに提供します。登録されたサービスに一致する「URI」データ型の値は自動的に参照外しされます。認識されたURIは横に "[+]" リンクが表示され、クリックするとソースで見つかった情報が展開されます。展開すると、リンクは "[-]" に変わります。外部メタデータのスナップショットはURIの下に読み込まれます。

![アイテム編集ページのURIエントリ。](modulesfiles/uri-entry.png)

これらのトグルボタンは `uri-dereferencer-toggle` クラスと共に読み込まれ、[CSSエディターモジュール](../modules/csseditor.md)または外部のスタイルシートを使用してスタイルを設定することができます。展開されたとき、外部メタデータは `uri-dereferencer-markup` クラスのある `div` 内で読み込まれ、そこから `dl` 説明リストに読み込まれます。プロパティは `dt` として、値は `dd` として表示されます。

![アイテムビューページに表示された同じURIエントリで、1つのURIからの情報が展開されて表示されている様子。](modulesfiles/uri-expanded.png)

参照されるメタデータの値の数とそれらがどれであるかは、サービスとそのデータ型によって決まり、Omekaで設定することはできません。これらのURIを使用してユーザーに参照されたメタデータを表示させたいかどうかを決める前に、サービスとデータ特性をテストしてください。このモジュールでは、参照される特定のプロパティを含めたり除外したりすることはできません。

サービスが複数の言語で情報を提供している場合、プロパティ値を編集しているときに言語フィールド（地球のアイコン）で2文字の言語タグを提供することで、表示されるべき言語のフィールドを指定することができます。

![言語コードが指定されたアイテム編集ページのURIエントリ。](modulesfiles/uri-language-item-editing.png)

公開ページでアイテムがアクセスされると、指定された言語で情報を表示するためにURIを拡張することができます。希望する言語が利用できない場合、URIは英語にフォールバックします。どの言語が提供されているかを確認するには、特定のサービスに問い合わせてください。現在、翻訳を提供するサービスは以下の4つだけです：[Wikidata](https://www.wikidata.org/wiki/Wikidata:Main_Page){target=_blank}、[DBpedia](https://wiki.dbpedia.org/){target=_blank}、[RDA Value Vocabularies](http://www.rdaregistry.info/termList/){target=_blank}、[Getty Vocabularies](https://www.getty.edu/research/tools/vocabularies/){target=_blank} (ULANを除く)。

![アイテムビューページに表示された同じURIエントリで、複数の言語からの情報が展開して表示されている様子。](modulesfiles/uri-language-item-view.png)

[カスタムデータタイプ値](../modules/customvocab.md)をお持ちで、それをリファレンス可能にしたい場合は、URIを含むアンカータグに `uri-value-link` クラスを追加する必要があります。

## リンクデータサービス

リンクデータサービスは、URIを参照し、リソースに関する情報を返す責任を持つJavaScriptオブジェクトです。このモジュールには幾つかのサービスが内蔵されています：

- [DBpedia](https://wiki.dbpedia.org/){target=_blank}
- [Geonames](https://www.geonames.org/){target=_blank}
- [Getty Vocabularies](https://www.getty.edu/research/tools/vocabularies/){target=_blank}
- [LC Linked Data Service](http://id.loc.gov/){target=_blank}
- [OCLC VIAF](https://www.oclc.org/en/viaf.html){target=_blank}
- [OCLC FAST](http://fast.oclc.org/){target=_blank}
- [RDA Value Vocabularies](http://www.rdaregistry.info/termList/){target=_blank}
- [Wikidata](https://www.wikidata.org/wiki/Wikidata:Main_Page){target=_blank}
- [Gemeentegeschiedenis](https://www.gemeentegeschiedenis.nl/){target=_blank}。

他のサービスを追加する方法については、[Readme](https://omeka.org/s/modules/UriDereferencer/){target=_blank}をご覧ください。
# リソースメタ

[リソースメタモジュール](https://omeka.org/s/modules/ResourceMeta/){target=_blank}は、インストールユーザーがサイトのページHTMLにおいてリソースメタデータ（アイテム、アイテムセット、メディア）を[`<meta>`要素](https://www.w3schools.com/tags/tag_meta.asp){target=_blank}として出力できるようにすることができます。メタ値は[リソーステンプレート](../content/resource-template.md)を介して適用されます。テンプレート内のメタデータプロパティ（例: `dcterms:creator`）は、公開ページの`<head>`タグ内で`<meta name="dcterms.creator" content="Shakespeare, William">`のようなメタタグとして出力されます。

リソースメタの設定は全てのレベルのユーザーが閲覧でき、エディター、スーパーバイザー、グローバル管理者レベルのユーザーが変更できます。

![ページ上のメタデータ値やHTML内の様子を示した公開アイテムページのスクリーンショット](modulesfiles/resourcemeta.png)

メタ要素は、ページコンテンツの最も関連性の高い部分の検索エンジン最適化とインデキシングのために使用されます。このモジュールは、BE Press, Highwire Press, EPrints, PRISMなどの学術リソースのインデキシングと発見可能性のための一般的に使用されるメタ要素を提供し、他のリソースタイプのためにダブリンコアエレメントとダブリンコアタームも提供します。

## メタデータのメタタグマッピング

左側のナビゲーションのモジュールタブからリソースメタを選択します。すべてのリソーステンプレートがページにリストされ、それぞれのテンプレートのプロパティにどれだけのメタタグが既に適用されているか（「メタ名の数」）が示されます。

![インストールのリソーステンプレートとその現在のメタ設定を表示する設定ページ](modulesfiles/resourcemeta_homepage.png)

各テンプレートに表示されている鉛筆アイコンをクリックして、そのメタ設定を変更します。リソーステンプレートのプロパティの表示が開かれ、使用可能なメタ要素を選択するためのドロップダウンメニューが表示されます。

![BE Press要素が表示されたドロップダウンを示す、リソーステンプレートのメタ設定の編集画面](modulesfiles/resourcemeta_edit1.png)

リソーステンプレートの各フィールドは、一つ以上のメタ要素にマッピング可能です。選択肢は以下の通りです：

- BE Press
- Dublin Core Elements
- Dublin Core Terms
- Highwire Press
- EPrints
- PRISM。

画面上部の「Map dcterms」ボタンを使って、リソーステンプレート内のダブリンコアタームプロパティを自動的にダブリンコアタームメタタグにマッピングすることができます。それ以外の場合は、利用可能なドロップダウンから手動でメタタグを選択する必要があります。ダブリンコアタームを自動的にマッピングした後、さらに手動でタグを追加することもできます。たとえば、`dcterms:title`フィールドを`bepress_citation_title`やHighwire Pressの`citation_title`を含む他のタイトルフィールドに提供することが可能です。ただし、「Map dcterms」ボタンを押すと、既存のマッピングが消去されてしまいます。

現在のマッピングをすべて消去するには「Clear」を、その消去を元に戻すには「Reset」を押します。編集内容を保存することを忘れないでください。

![複数のプロパティに複数のマッピングを表示している、リソーステンプレートのメタ設定の編集画面](modulesfiles/resourcemeta_edit2.png)

モジュールが意図した通りに機能しているかを確認するには、マッピングがされているリソーステンプレートを使用しているアイテムの公開ページにアクセスします。ページのソースを表示し、`<head>`タグ内にあなたの設定に対応する`<meta>`要素が含まれているか確かめてください。

![上の画像のメタマッピングが設定されたアイテムのページソース](modulesfiles/resourcemeta_public.png)

## 用途

例えば、[Google Scholarにアイテムがインデックスされることを目的として](https://scholar.google.com/intl/en/scholar/inclusion.html#indexing){target=_blank}学術リソースをOmekaを使って利用可能にしている場合、4つの出版オプションのうちの1つを選ぶことが望ましいかもしれません。これらすべてのオプションに対応しています。[これら4つのオプションと学術リソースの発見可能性に関する詳細はこちらで確認できます](http://div.div1.com.au/div-thoughts/div-commentaries/66-div-commentary-metadata){target=_blank}。

別の例として、Omekaアイテムを[Zoteroにインデックスされ、インポートされるようにしたい場合](https://zotero-manual.github.io/adding-items/#generic-translators){target=_blank}、Highwire Press、Dublin Core、PRISMを使用することが望ましいかもしれません。

ソーシャルメディアウェブサイト上でOmekaリソースを動的に表示させるためのメタ要素については、[共有モジュール](sharing.md)をインストールしてください。
```

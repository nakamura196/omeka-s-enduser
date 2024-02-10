# IIIFプレゼンテーション

[IIIF Presentationモジュール](https://omeka.org/s/modules/IiifPresentation/){target=_blank} を利用することで、Omeka Sのアイテムやアイテムセットに対して、[IIIF Presentation APIエンドポイントおよびビューア](https://iiif.io/api/presentation/3.0/){target=_blank} を提供することができます。このモジュールがインストールされ有効になると、すべてのアイテムとアイテムセットに自動的にAPIエンドポイントが利用可能になります。

Omeka Sは、[Mirador IIIFビューア](https://projectmirador.org/){target=_blank} をコアコードに組み込んでおり、これがOmekaがWeb上のIIIFメディアを[入力および表示](../content/media.md#add-media)することを可能にしています。これは、デジタルコレクションを別の場所でホストしている機関がOmekaの仮想展示でそれらの素材を使用したい場合や、教育者が教育に公開されている素材を使用したい場合に役立ちます。

このモジュールは、Omeka Sのアイテムやアイテムセットを他のIIIFビューアで表示したり、インストール上でIIIFビューアをプレビューおよび設定するために読み込む機能を追加します。これは、Omekaリソースを自分のサイトで表示したい他のユーザーによって使用されます。

任意のアイテム、複数のアイテムセット、任意のアイテムセット、または複数のアイテムセットを表示するIIIFビューアは、希望するURLを作成することによって設定することができます。このモジュールには設定や追加の管理インターフェースオプションはありません。

## モジュールの使用方法

インストール後、マニフェストとビューアのURLは、インストールの特定のサイトではなく、ベースのOmeka SインストールURLを使用して生成されます。従って、ユーザーは各アイテムのIIIFビューアURLを次のように見つけることができます。

`
https://example.com/omeka-s/iiif-presentation/3/item/123/
`

そしてマニフェストURLは

`
https://example.com/omeka-s/iiif-presentation/3/item/123/manifest
`

以下のようになります。

- `https://example.com/omeka-s/` はベースのインストールURLです（特定のサイトへのURLや、サイトの前にある `/s/` を含めないでください）
- `iiif-presentation/3/` はあなたがバージョン3.0タイプのIIIFマニフェストを提供していることを示しています
- `item` は対象がOmeka Sのアイテムであることを示しています
- `123` は特定のアイテムIDです。

同様に、各アイテムセットのURLは

`
https://example.com/omeka-s/iiif-presentation/3/item-set/45
`

となります。`45` はアイテムセットIDです。

カンマで区切られた値を含めれば、複数のアイテムIDやアイテムセットIDを同じ場所で提供することができます。例えば：

`
https://example.com/omeka-s/iiif-presentation/3/item/6,7,8,9
`

値は任意の順序で良く、与えられた順序でビューアに表示されます。

ブラウザで直接ビューアまたはマニフェストURLにアクセスすることによって、モジュールが正しく動作しているかをテストできます。

ビューアについては、アイテムのメディアがサイドバーと共にビューアにロードされるのが見えるはずです。URLは次のようなフォームにリダイレクトされます。

`
https://example.com/omeka-s/iiif-viewer?url=https://example.com/omeka-s/iiif-presentation/3/item/1082/manifest
`

![複数ページの本を示すIIIF Miradorビューアのビュー](modulesfiles/iiifpresentation_viewer.png)

マニフェストについては、「Manifest」が早い段階でタイプとして現れる、JSONがロードされるページを見るはずです。

![IIIFマニフェストJSON出力のビュー](modulesfiles/iiifpresentation_json.png)

また、[https://presentation-validator.iiif.io/](https://presentation-validator.iiif.io/){target=_blank} のようなバリデーターツールも利用可能です。

## エンドポイント

### IIIF Presentation v3

これらのエンドポイントは、IIIF Presentation APIのバージョン3で利用できます。

- `/iiif-presentation/3/item/:item-id/manifest`
    OmekaアイテムのIIIFマニフェストリソースを取得します。JSON-LDを出力します。
    - `:item-id`: OmekaアイテムID
- `/iiif-presentation/3/item/:item-id`
    OmekaアイテムのIIIFマニフェストリソースを表示します。Omeka S IIIFビューア（Mirador）へリダイレクトします。
    - `:item-id`: OmekaアイテムID
- `/iiif-presentation/3/item/:item-ids/collection`
    2つ以上のOmekaアイテムのIIIFコレクションリソースを取得します。JSON-LDを出力します。
    - `:item-ids`: カンマで区切られたOmekaアイテムID
- `/iiif-presentation/3/item/:item-ids`
    2つ以上のOmekaアイテムのIIIFコレクションリソースを表示します。Omeka IIIFビューア（Mirador）へリダイレクトします。
    - `:item-ids`: カンマで区切られたOmekaアイテムID
- `/iiif-presentation/3/item-set/:item-set-id/collection`
    OmekaアイテムセットのIIIFコレクションリソースを取得します。JSON-LDを出力します。
    - `:item-set-id`: OmekaアイテムセットID
- `/iiif-presentation/3/item-set/:item-set-id`
    OmekaアイテムセットのIIIFコレクションリソースを表示します。Omeka S IIIFビューア（Mirador）へリダイレクトします。
    - `:item-set-id`: OmekaアイテムセットID
- `/iiif-presentation/3/item-set/:item-set-ids/collection`
    2つ以上のOmekaアイテムセットのIIIFコレクションリソースを取得します。JSON-LDを出力します。
    - `:item-set-ids`: カンマで区切られたOmekaアイテムセットID
- `/iiif-presentation/3/item-set/:item-set-ids`
    2つ以上のOmekaアイテムセットのIIIFコレクションリソースを表示します。Omeka IIIFビューア（Mirador）へリダイレクトします。
    - `:item-set-ids`: カンマで区切られたOmekaアイテムセットID。

### IIIF Presentation v2

これらのエンドポイントは、IIIF Presentation APIのバージョン2で利用できます。

- `/iiif-presentation/2/item/:item-id/manifest`
    OmekaアイテムのIIIFマニフェストリソースを取得します。JSON-LDを出力します。
    - `:item-id`: OmekaアイテムID
- `/iiif-presentation/2/item/:item-id`
    OmekaアイテムのIIIFマニフェストリソースを表示します。Omeka S IIIFビューア（Mirador）へリダイレクトします。
    - `:item-id`: OmekaアイテムID
- `/iiif-presentation/2/item/:item-ids/collection`
    2つ以上のOmekaアイテムのIIIFコレクションリソースを取得します。JSON-LDを出力します。
    - `:item-ids`: カンマで区切られたOmekaアイテムID
- `/iiif-presentation/2/item/:item-ids`
    2つ以上のOmekaアイテムのIIIFコレクションリソースを表示します。Omeka IIIFビューア（Mirador）へリダイレクトします。
    - `:item-ids`: カンマで区切られたOmekaアイテムID
- `/iiif-presentation/2/item-set/:item-set-id/collection`
    OmekaアイテムセットのIIIFコレクションリソースを取得します。JSON-LDを出力します。
    - `:item-set-id`: OmekaアイテムセットID
- `/iiif-presentation/2/item-set/:item-set-id`
    OmekaアイテムセットのIIIFコレクションリソースを表示します。Omeka S IIIFビューア（Mirador）へリダイレクトします。
    - `:item-set-id`: OmekaアイテムセットID
- `/iiif-presentation/2/item-set/:item-set-ids/collection`
    2つ以上のOmekaアイテムセットのIIIFコレクションリソースを取得します。JSON-LDを出力します。
    - `:item-set-ids`: カンマで区切られたOmekaアイテムセットID
- `/iiif-presentation/2/item-set/:item-set-ids`
    2つ以上のOmekaアイテムセットのIIIFコレクションリソースを表示します。Omeka IIIFビューア（Mirador）へリダイレクトします。
    - `:item-set-ids`: カンマで区切られたOmekaアイテムセットID。

## イベント

このモジュールは、特定のIIIF Presentationリソース（マニフェスト、キャンバス、コレクションなど）を構成する際にこれらのイベントをトリガーします。イベントの `getTarget()` メソッドを使用して、現在のコントローラを取得できます。

### IIIF Presentation v3

これらのイベントは、IIIF Presentation APIのバージョン3で利用できます。

- `iiif_presentation.3.media.canvas`
    メディアキャンバス配列を構成した後にトリガーされます。キャンバスを変更するには、イベントに設定されている `canvas` パラメータを変更し、イベントに戻して設定することができます。
    - `canvas`: キャンバス配列
    - `canvas_type`: キャンバスタイプサービスオブジェクト
    - `media_id`: メディアID
- `iiif_presentation.3.item.manifest`
    アイテムマニフェスト配列を構成した後にトリガーされます。マニフェストを変更するには、イベントに設定されている `manifest` パラメータを変更し、イベントに戻して設定することができます。
    - `manifest`: マニフェスト配列
    - `item_id`: アイテムID
- `iiif_presentation.3.item.collection`
    アイテムコレクション配列を構成した後にトリガーされます。コレクションを変更するには、イベントに設定されている `collection` パラメータを変更し、イベントに戻して設定することができます。
    - `collection`: コレクション配列
    - `item_ids`: コレクション内のアイテムID
- `iiif_presentation.3.item_set.collection`
    アイテムセットコレクション配列を構成した後にトリガーされます。コレクションを変更するには、イベントに設定されている `collection` パラメータを変更し、イベントに戻して設定することができます。
    - `collection`: コレクション配列
    - `item_set_id`: アイテムセットID
- `iiif_presentation.3.item_set.collections`
    アイテムセットコレクション配列を構成した後にトリガーされます。コレクションを変更するには、イベントに設定されている `collection` パラメータを変更し、イベントに戻して設定することができます。
    - `collection`: コレクション配列
    - `item_set_ids`: コレクション内のアイテムセットID。

### IIIF Presentation v2

これらのイベントは、IIIF Presentation APIのバージョン2で利用できます。

- `iiif_presentation.2.media.canvas`
    メディアキャンバス配列を構成した後にトリガーされます。キャンバスを変更するには、イベントに設定されている `canvas` パラメータを変更し、イベントに戻して設定することができます。
    - `canvas`: キャンバス配列
    - `canvas_type`: キャンバスタイプサービスオブジェクト
    - `media_id`: メディアID
- `iiif_presentation.2.item.manifest`
    アイテムマニフェスト配列を構成した後にトリガーされます。マニフェストを変更するには、イベントに設定されている `manifest` パラメータを変更し、イベントに戻して設定することができます。
    - `manifest`: マニフェスト配列
    - `item_id`: アイテムID
- `iiif_presentation.2.item.collection`
    アイテムコレクション配列を構成した後にトリガーされます。コレクションを変更するには、イベントに設定されている `collection` パラメータを変更し、イベントに戻して設定することができます。
    - `collection`: コレクション配列
    - `item_ids`: コレクション内のアイテムID
- `iiif_presentation.2.item_set.collection`
    アイテムセットコレクション配列を構成した後にトリガーされます。コレクションを変更するには、イベントに設定されている `collection` パラメータを変更し、イ
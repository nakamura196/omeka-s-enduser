# 共有

[共有モジュール](https://omeka.org/s/modules/Sharing){target=_blank} は、訪問者がソーシャルメディアやメールを介してサイトのコンテンツを共有または埋め込むために使用するボタンをサイトページに追加することを可能にします。共有には、ソーシャルメディアで共有された際にプレビューカードが表示されるように、各アイテムページの `<head>` に [Open Graph](https://ogp.me/){target=_blank} と [oEmbed](https://oembed.com/){target=_blank} のメタ要素も含まれています。

現在、共有は以下のオプションをサポートしています：

- Facebook
- Twitter
- Tumblr
- Pinterest
- メール
- 埋め込みコード。

共有がOmeka Sにインストールされ有効化された後は、インストールの全てのサイトで利用できるようになります。

## 設定

![サイトの左側のナビゲーションオプション：設定は最下部にあります](../modules/modulesfiles/sharing2.png)

共有設定はサイトごとに構成されます。サイトに行き、サイト設定に進んでください。「共有」と表示されたセクションがあり、2つのオプションがあります：

**これらの方法で共有モジュールを有効にする**: 各サービスやオプション（Facebook、Twitterなど）ごとに、チェックボックスが一連になっています。

**ページ上の共有ボタンの配置**: 共有ボタンの配置を、コンテンツの上部（ナビゲーションとページヘッダーの下）または下部（フッターの直上）に設定します。

![上記の共有オプションのチェックボックスが2列で表示されています](../modules/modulesfiles/sharing_options.png)

サイトに適切なボックスがチェックされていることを確認してください。すべてのボックスのチェックを外して、あなたのサイトの共有をオフにすることができます。変更を保存することを忘れないでください。

### 埋め込み要素

モジュールは、サイトの設定に関係なくOpen GraphとoEmbedメタタグを送信します。

Open Graphについては、次のような感じになります：

```
<meta property="og:site_name" content="My Omeka S Site">
```

タグは次を含む可能性があります：

- `og:description`、適用可能であればリソースの `dcterms:description` の内容、または [リソース説明用に使用されるフィールド](../content/resource-template.md#other-options) を反映します。
- `og:title`、`dcterms:title` またはリソースタイトル用に使用されるフィールドを反映します。
- `og:image`、プライマリメディアまたはメディアタイプに基づいたデフォルトサムネイルです。
- `og:type`、この時点では常に `content="website"` です。
- `og:url`、現在のページのURLです。

これらのフィールドはアイテムセットまたはメディアページには送信されません。マルチメディア（オーディオおよびビデオ）は送信されず、サムネイル画像のみが送信されます。

oEmbedは、アイテム、メディア、検索およびブラウズページを含む、すべてのOmeka S公開ページの `<head>` に単一のタグとして表示されます：

```
<link rel="alternate" type="application/json+oembed" title="[Your page's title here]"> 
```

この要素には、`yourInstallationURLhere/oembed` に見つかるサイトのoEmbed APIを反映する `href` 値と、`yourInstallationURLhere/s/site-one/item/item1` のような特定のサイトページのURLが含まれます。

## パブリック側

有効なサービスとオプションの共有アイコンは、作成したページやサイトの個々のアイテム/表示ページに表示されます。

![アイテムのタイトルの上、ページヘッダーの直下に表示されているFacebook、Twitter、メール用の共有ボタン](../modules/modulesfiles/sharing_buttons.png)

デフォルトで、モジュールはページのタイトル、サイト名、インストール名を共有します。

![ページのタイトル、その後にドット、続いてサイトのタイトル、更にドット、インストールタイトルが続き、サイトのダミーURLで終わるツイートの例](../modules/modulesfiles/sharing_display1.png)
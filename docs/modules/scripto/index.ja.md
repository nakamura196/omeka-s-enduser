# Scriptoのセットアップ

[Scriptoモジュール](https://omeka.org/s/modules/Scripto/){target=_blank}を使用すると、Omeka Sのインストールに添付されたアイテムのメディアを一般の人々に書き起こし、翻訳、または記述してもらうためのプロジェクトを作成することができます。

アイテムとメディアはアイテムセットに整理され、その後Scripto内のプロジェクトと同期されます。Scripto内で作成されたコンテンツは定期的にアイテムおよびメディアのメタデータとしてOmeka Sにインポートすることができます。

コンテンツの作成（書き起こし、翻訳、または記述）はすべてあなたのScripto [プロジェクト](scriptoproject/)の[公開面](scriptoPublicView/)で行われます。

## 概念と用語

Scriptoの**プロジェクト**を使用すると、取り組みたい資料を整理し、それらをどのように扱うかを設定することができます。プロジェクトは書き起こし、翻訳、記述のいずれか一つを行うことができますが、複数の作業を同時に行うことはできません。

しかし、Omeka SのScriptoモジュールでは、単一のScriptoインストール上で複数のプロジェクトを作成することができます。Omeka S内のサイトと同様に、Scriptoプロジェクトは互いに独立して存在することができます。これは、同じOmeka Sインストールを介して、原稿の書き起こしプロジェクトと文書の翻訳プロジェクトをサポートすることができることを意味します。

Scripto内の**アイテム**はOmeka Sのアイテムに対応します。プロジェクトを閲覧する際、コミュニティメンバーはアイテムをページングします。アイテムにはオーディオ、ブック、文書、ジャーナル、原稿、紙、ビデオといったラベルを付けることもできます。

アイテムに関連付けられた**メディア**はコミュニティメンバーが書き起こし、翻訳、または記述するレベルです。メディアは全てアイテムに関連付けられています。メディアはまた、エントリー、フォリオ、画像、ページ、セグメント、セクション、またはシートと呼ぶこともできます。

## インストールと設定
Scriptoをインストールするためには、次の条件を満たしている必要があります：

- Omeka S v2.0.0またはそれ以上を実行していること
- Omeka Sインストールと同じサーバー上で動作する[MediaWiki](https://www.mediawiki.org/wiki/MediaWiki)のインストールがあること。必要なMediaWikiの最低バージョンは1.30.0です。

サーバー上で[その指示](https://www.mediawiki.org/wiki/Manual:FAQ#Installation_and_configuration)に従ってMediaWikiインストールを作成します。[モジュールのインストールに関するドキュメント](../../modules/#installing-modules)を使用してScriptoモジュールをインストールしてください。

モジュールをインストールし、MediaWikiインストールを作成したら、Omeka Sインストールのモジュールタブに移動してScriptoモジュールをアクティブにします。

モジュールタブにとどまり、ScriptoモジュールのConfigureボタンをクリックします。MediaWiki APIのURLを入力するための1つの必須フィールドがあります。

![Scriptoモジュールの設定ページ、空のフィールドが赤でハイライトされている](../modulesfiles/scripto-configure.png)

そのフィールドに[MediaWiki APIエンドポイント](https://www.mediawiki.org/wiki/API:Main_page#Endpoint)のURLを入力します。これは`<your mediawiki url>/api.php`のようになっているはずです。変更を保存するには「Submit」をクリックしてください。

### Scripto語彙
Scriptoがインストールされアクティブになると、Omeka SインストールにScripto[語彙](../../content/vocabularies/)が追加されます。この語彙には以下のプロパティが含まれています：

- コンテンツ：リソースのコンテンツのプレーンテキスト表現。
- 書き起こし：リソースの書き起こし。
- 翻訳：リソースの翻訳。

この語彙は編集しないでください。

## アイテムセットの作成
Scriptoモジュールは[アイテムセット](../../content/item-sets)を使用して、Omekaインストールからのコンテンツの管理を行います。

各Scriptoプロジェクトは、同期できる独自のアイテムセットを必要とします。プロジェクトに含めたいOmeka Sインストールのアイテムを使用してアイテムセットを作成します。必要に応じて、後でこのアイテムセットにアイテムを追加することができます。

## Scripto管理ダッシュボード
Omeka Sインストールの管理側の左側のナビゲーションのモジュールセクションの下にあるScriptoタブは、Scriptoダッシュボードに移動します。

ダッシュボードから、上部のバーを使用してScriptoにログインできます：

![Scriptoダッシュボードのヘッダーとログインフィールド](../../modules/modulesfiles/scripto-dash-login.png)

ログインすると、ダッシュボードには以下が含まれます：

- ユーザー名とダッシュボード、投稿、ウォッチリストへのリンク、そしてScriptoからログアウトするためのボタンが含まれた上部のバー。
- あなたが所有するすべての[プロジェクト](../../modules/scripto/scriptoproject/)のビュー。
- あなたがレビューするすべての[プロジェクト](../../modules/scripto/scriptoproject/)のビュー。
- 最近の投稿のビュー。
- ウォッチリストのビュー。

![3つのプロジェクトがあり、そのうち2つがユーザーによってレビューされているScriptoダッシュボードと、一連の最近の投稿。](../../modules/modulesfiles/scripto_dash.png)

右上のドロップダウンから、Omeka Sのグローバルとサイト管理者は：すべての[プロジェクト](../../modules/scripto/scriptoproject/)を閲覧することができます。新しい[プロジェクト](../../modules/scripto/scriptoproject/)を追加することができます。またすべてのScriptoユーザーを閲覧することができます。

![プロジェクトを閲覧する、プロジェクトを追加する、ユーザーを閲覧するオプションを示すドロップダウン](../../modules/modulesfiles/scripto-dash-actions.png)

## ユーザー
Omeka Sのユーザーアカウントに加えて、Scriptoで作業する個人はMediaWikiのユーザーアカウントも必要です。彼らはScriptoインターフェースの公開側からこのアカウントにサインアップすることができます：`<your omeka S url>/scripto/create-account`。

書き起こしのステータスを変更し、プロジェクトをOmeka Sへ同期するためには、ユーザーはMediaWikiインストール上で[官僚レベルの権限](https://www.mediawiki.org/wiki/Manual:User_rights)を持っている必要があります。これは*MediaWiki上で行われなければならず*、Omeka S上のScriptoダッシュボードを通じて管理することはできません。

通常、何が行われているかを追跡するために、両方のインストールで同じまたは類似のユーザー名を使用することが最も簡単です。

### ユーザーの閲覧
Scriptoダッシュボードの右上にある「アクション」ドロップダウンから「ユーザーの閲覧」を選択できます。

これにより、このインストールにあるすべてのScriptoユーザー（MediaWikiから）を表示するユーザー閲覧ページに移動します。

![2人のユーザー、1人は通常ユーザー、もう1人は管理者であるユーザー閲覧テーブル](../../modules/modulesfiles/scripto-browseUsers.png)

ユーザーは彼らの次のリストを含むテーブルに表示されます：

- 名前
- MediaWikiグループ、これは彼らの役割を示します
- 編集回数（編集したメディアの数）
- アカウントが作成された日付。

### ユーザーの投稿
ユーザー名をクリックすると、そのユーザーの投稿の要約が記載されたページに移動します。

![DemoUserのユーザー投稿 - 2019年10月15日付の編集1件](../../modules/modulesfiles/scripto-user-contributions.png)

各ユーザーに対して、彼らがメディアに対して行った編集ごとに表内に行があります。列は以下です：

- 改訂、その改訂へのリンクを含むタイムスタンプ
- メディア番号、メディアへのリンク付き
- タイプ
- Scripto内のアイテムへのリンクを含むアイテム
- 関連するプロジェクト
- 編集のサイズ
- コメント（あれば）。

## 公開ビューと管理ビュー
プロジェクトの公開ビューと管理ビューを切り替えるには、ScriptoサイトのURLから`/admin`を削除するか、またはOmeka Sインストール名の直後に直接入力してください。

管理側は`youromekaurl.net/admin/scripto`で、公開側は`youromekaurl.net/scripto`です。

書き起こし作業は**公開側**のScriptoプロジェクトで行われます。管理ダッシュボードから書き起こしを編集することはできません。

## Scriptoのアンインストール

Scriptoを正常にアンインストールするには、モジュールがまだアクティブである必要があります。アンインストールする前にScriptoを非アクティブにしないでください。
```

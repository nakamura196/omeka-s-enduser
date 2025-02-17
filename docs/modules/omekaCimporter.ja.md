# Omeka Classic インポーター

[Omeka Classicインポーターモジュール](https://omeka.org/s/modules/Omeka2Importer){target=_blank}（通称Omeka 2インポーター）を使用すると、Omeka Classic 2.xサイトからアイテムやコレクションをOmeka Sインスタレーションにインポートすることができます。ソースサイトは、このモジュールが使用するAPIエンドポイントを提供するために、Classicバージョン2以上である必要があります。

インストールされると、Omeka Classicインポーターモジュールは、メインの管理ダッシュボードの左ナビゲーションメニューの下部に表示されるはずです。選択すると、**インポート**と**過去のインポート**のサブメニュー項目があります。

![Omeka Classicインポーターメニューのオプション、インポート、および過去のインポート](../modules/modulesfiles/oCi_menu.png)

このモジュールは、アイテムとそのメタデータ（タグを含む）、添付ファイル、コレクション（アイテムセットとして）のみをインポートします。シンプルページのコンテンツやエキシビットビルダーのコンテンツは*インポートされません*。

ソースサイトとターゲットサイトの両方にプラグイン/モジュールがインストールされている場合、Omeka Classicインポーターはモジュール固有のメタデータをインポートすることができます。例えば、SのMappingモジュールとClassicのGeolocationプラグインによって容易にされるジオロケーションデータは自動的にインポートされます。PDF Text要素は、Extract Textフィールドにマッピングしてインポートすることができます。データが自動的に適切にマッピングされない可能性があるため、マッピングを手動で確認してください。

!!!注意
	Omeka SでのリソースプロパティにはHTMLフォーマットがないため、インポートプロセス中にOmeka Classicのアイテムプロパティ内のHTML（リンク、テキストフォーマットなど）が削除されます。代わりに、メディアタイプとして「HTML」を持つ任意の要素をメディアとして保持することができます。

## インポート

インポートタブから新規インポートを開始できます。

インポーターを機能させるには、ソースのOmeka ClassicインスタレーションでAPIを有効にする必要があります。これを行うには、元のOmeka Classicインスタレーションの所有者が、管理ダッシュボードの上部ナビゲーションバーを介してアクセスできる設定のAPIタブに移動します。"APIを有効にする"ボックスがチェックされていることを確認してください。

元のOmeka ClassicインスタレーションのAPIエンドポイントを見つけるには、そのインスタレーションのホームページに移動します。URLの末尾に`/api`を追加します。すると、「これは[name of origin site]のエンドポイントURLです」というメッセージと、サイト情報と利用可能なAPIリソースへのリンクが表示されるページが表示されます。APIが有効になっていることを確認するには、利用可能なAPIリソースへのリンクをクリックします。`{"message":"API is disabled"}`と表示された場合、このサイトからはインポートできません。

### APIを入力
インポーターの最初のページで、**Omeka Classic APIエンドポイント**、つまりアクセスしたいAPIのサイトURLを入力します（URLは"api"で終わる必要があります）。完全なURLを"http"から始めて入力してください。そうしないとインポーターはそのサイトのアイテムにアクセスできません。"次へ"をクリックします。

![APIインポートフィールド](../modules/modulesfiles/oCi_enterapi.png)

有効なAPIエンドポイントを入力すると、次のページが問題なく読み込まれます。無効なエンドポイントを入力した場合、モジュールは"Warning: Invalid argument"というエラーメッセージを表示します。

### インポート設定とメタデータのマッピング
インポーターの2ページ目には、**基本インポート設定**、**Omeka Sプロパティへのマッピング**、**Omeka Sクラスへのマッピング**、および**Omeka Sテンプレートへのマッピング**の3つのタブがあります。

"最初からやり直す"ボタンをクリックすると、最初のページに戻り、異なるAPIエンドポイントを入力することができます。

このモジュールはバージョン1.3からClassicからSへのアイテムの可視性（公開または非公開）を保存します。

#### 基本インポート設定
* **Omeka Classic APIキー**: このフィールドは、データをインポートしようとしているサイトのAPIキーがあるかどうかに応じて、空白または入力済みのどちらかです。
* **コメント**: 「Jane DoeのAPI、キーなし」のようなコメントを追加して、過去のインポートを表示する際に特定のインポートを識別できるようにします。
* **インポート先**: ここでは、アイテムをインポートするアイテムセットを選択できます。このページから新しいアイテムセットを作成することはできません。コレクションを代わりに、またはここでのアイテムセットへのインポートに追加してインポートすることを希望する場合があります。
* **ページあたり**: リクエストごとに取得するレコード数を制限するための数字を入力します。アイテム数が多いサイトに役立ちます。
* **以前のインポートを更新**: 同じソースからの以前のインポートを更新して上書きします。
* **コレクションをインポート**: Omeka ClassicサイトからOmeka Sサイトへのコレクションを、アイテムセットとしてインポートします。
* **タグをインポートするとして**: Omeka Classicのタグをインポートするには、それらをマッピングするプロパティを選択します。

![インポートの基本オプション](../modules/modulesfiles/oCi_basic.png)

#### Omeka Sプロパティへのマッピング
このタブには、Omeka Classicの要素とOmeka Sプロパティの間のマッピングのためのテーブルが表示されています。

インポートモジュールは多くのプロパティを自動的にマッピングしますが、追加のマッピングが必要か、自動マッピングを編集する必要がないかを確認するために、マッピングを確認する必要があります。カスタムアイテムタイプの要素は、手動でマッピングする必要がある場合があります。

デフォルトマッピングをクリアするには、「デフォルトをクリアする」ボタンをクリックします。

テーブルの列には、**Omeka Classic要素**、**マップされたプロパティ**、および**HTMLをメディアとして保持する**のチェックボックスオプションがあります。説明フィールドの改行やテキストスタイリングなど、Omeka Sインストールで保持したいHTMLを含む任意のフィールドは、アイテムに添付されたHTMLファイルとしてインポートできます。フィールドはメタデータへのプレーンテキストとして、およびメディアとしてそのフォーマットでインポートされます。

![Omekaプロパティのマッピング](../modules/modulesfiles/oCi_mapprop.png)

テーブルの最初のセットはダブリンコアで、その後にアイテムタイプメタデータが続きます。インポートはまた、レガシーや追加のエレメントセット（例えばOmeka Legacy File）、Classicプラグインによって作成されたエレメント（例えば抽出されたテキスト用のPDFテキストセクション）も取り込みます。これらのプラグインベースのエレメントは、同等のOmeka Sモジュールがインストールされている場合（この場合はExtract Text）に自動的にマッピングされる場合があります。

マッピングするには：

1. テーブルで要素またはアイテムタイプをクリックし、その行またはラベルを選択します。

1. 右側のドロワーで、Classic要素にマッピングしたいSプロパティをクリックするか、検索します。

1. ドロワーでプロパティをクリックしてマッピングします。

![誕生日の要素をFOAFプロパティの"birthday"にマッピングし、マッピングされた関係を示しています。](../modules/modulesfiles/oCi_mapping.png)

マッピングを削除するには、要素/プロパティの行にあるゴミ箱アイコンをクリックします。

#### Omeka Sクラスへのマッピング
このタブでは、Omeka ClassicアイテムタイプをOmeka Sリソースクラスにマッピングすることができます。インストールされているすべてのボキャブラリーからクラスを選択できます。

マッピングするには：

1. テーブルでアイテムタイプをクリックし、その行またはラベルを選択します。

1. 右側のドロワーで、要素にマッピングしたいリソースクラスをクリックするか、検索します。

1. ドロワーでリソースクラスをクリックしてマッピングします。

元のClassicアイテムタイプを持つアイテムは、新しいSクラスでインポートされます。

![リソースクラスマッピングタブ](../modules/modulesfiles/oCi_mapclass.png)

#### Omeka Sテンプレートへのマッピング

このタブでは、インポートするアイテムをOmeka Sインストール内の特定のリソーステンプレートにマッピングできます。Sでの既存のすべてのリソーステンプレートが右側のドロワーに表示されます。

マッピングするには：

1. テーブルでアイテムタイプをクリックし、その行またはラベルを選択します。

1. 右側のドロワーで、要素にマッピングしたいリソーステンプレートをクリックするか、検索します。

1. ドロワーでリソーステンプレートをクリックしてマッピングします。

元のClassicアイテムタイプを持つアイテムは、新しいSリソーステンプレートでインポートされます。

![リソースクラスマッピングタブ](../modules/modulesfiles/oCi_mapresource.png)

### インポートの完了
マッピングのカスタマイズが完了したら、ウィンドウの右上にある「インポート」ボタンをクリックします。

!!! 注意
	ジョブが開始されても完了しないですか？システムがアイテムを実行するバックグラウンドプロセスを実行できるように、[PHPのパスを設定する](../configuration.md#php-path)必要があるかもしれません。

## 過去のインポート

モジュールの過去のインポートセクションでは、以前のAPIインポートを表示できます。

各インポートは行です。テーブルには以下の列があります：

* **元に戻す**: インポートを元に戻したい場合は、このボックスをチェックします。Submitをクリックすると、その特定のインポートのステータスが「undone」に変わります。
* **ジョブID**: 各APIインポートに割り当てられる数値です。[管理ダッシュボードのジョブタブ](../admin/jobs.md)でジョブを表示することもできます。
* **コメント**: インポートの設定時にコメントを入力した場合、そのコメントがここに表示されます。
* **アイテム**: 各インポートで追加または更新されたアイテムの数をリストします。
* **日付**: インポートが行われた日付。
* **ステータス**: 「in_progress」、「completed」、または「undone」になります。
* **所有者**: インポートを要求したユーザー。

![過去のインポートのヘッダーロウと過去のインポートの1行を示すテーブル。](../modules/modulesfiles/oCi_past.png)
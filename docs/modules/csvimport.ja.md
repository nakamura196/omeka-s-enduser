# CSV インポート

[CSV インポートモジュール](https://omeka.org/s/modules/CSVImport){target=_blank} を使用すると、CSV（コンマ区切り値）、TSV（タブ区切り値）、ODS（OpenDocument スプレッドシート）ファイルからアイテム、アイテムセット、メディア、ユーザーを Omeka S インストールにインポートできます。このモジュールは [Global Administrator と Supervisor ユーザー](../admin/users.md) のみが利用可能です。

CSV インポートには、バックグラウンドのインポートジョブを実行するために Omeka S インストールで PHP が動作することが必要です ([PHP パスをテストおよび設定する](../install.md#test-and-set-the-php-path))。CSV インポートを使用する前に、[システム情報ページ](../admin-dashboard.md#system-information)から PHP が認識されているかを確認してください。

## CSV ファイルの準備

Microsoft Excel、Google Sheets、Apple Numbers を含むほとんどのスプレッドシートエディターは、CSV、TSV、または ODS 形式にエクスポートできます。

!!! note
	インポート用の CSV ファイルは **UTF-8 でエンコードする必要があります**。新しいドキュメントをエクスポートまたは保存する際に、エンコーディングが UTF-8 であることを確認してください。

ほとんどの CSV インポートオプションは、一種類のデータのみをインポートすることを前提としています: アイテムのリスト、アイテムセットのリスト、メディアのリストなどです。各行のタイプを識別する列を必要とする[混在リソースインポート](#mixed-resource-import)オプションもあります。

スプレッドシートがすでに作成されている場合、どの列をどの[語彙のプロパティ](../content/vocabularies.md)にマッチさせたいかを考慮してください。モジュールが正しく処理できるように、CSV ファイルには **ヘッダー行が必要です**。したがって、列名が含まれる行を最上部に追加する必要がある場合があります。

単一のプロパティに対して複数の入力を持つ場合、**複数値区切り文字**を使用してそれらを区切ることができます。例えば、著者が複数いる作品（E.B. White と William Strunk Jr.）で、Creator 列に「E.B. White;William Strunk Jr」という値がある場合、セミコロン `;` が複数値区切り文字となります。Omeka S にインポートされたとき、それぞれがプロパティ内で個別のエントリとして表示されます（Creator: 「E.B. White」と Creator: 「William Strunk Jr.」）。区切り文字の後にスペースを入れるかどうかにかかわらず、インポートされる内容は同じです（「E.B. White; William Strunk Jr」としても変わりません）。

### 列名

それぞれの列を対応するプロパティに手動でマッピングすることができますが、メタデータでない列（アップロード用のファイル URL など）は手動でマッピングする必要です。ヘッダー行に記載された名前がインストールされた [語彙](../content/vocabularies.md) のプロパティ用語と一致する場合、モジュールはメタデータ列を自動的にマッピングします。この形式は `prefix:property` となります。例えば、列のヘッダーが「dcterms:title」となっている CSV ファイルは、CSV をマッピング用にロードした際に Dublin Core の Title プロパティに自動マッピングされます。インポート前に、これらの自動マッピングされた列を変更することができます。

使用する列のヘッダーの用語を見つけるには、管理ダッシュボードから語彙のタブに移動します。使用したい語彙のプロパティ数をクリックします（以下のイメージでは Dublin Core です）。

語彙プロパティのテーブルには、**用語**の列があります。CSV インポートで自動マップするプロパティの列ヘッダーとして用語を使用します。例えば、「dcterms:abstract」は Dublin Core の「Abstract」プロパティに、「foaf:firstName」は Friend of a Friend の「firstName」プロパティに自動マップされます。

![Dublin Core のプロパティに対する用語列を指す矢印。](../modules/modulesfiles/csvimport_automap2.png)

最初のインポート設定には簡単なラベルで自動マッピングする設定があります。この設定を使用すると、「title」や「abstract」など、語彙ラベルと一致する列名を自動的にマッピングできます。このオプションは、他のインストールされた語彙を通過する前に Dublin Core (`dcterms:title` および `dcterms:abstract`) にデフォルトで設定されます。

自動マッピング機能が認識しない、ピッタリ一致しない列名がある場合でも、インポート中に手動でマッピングするのに役立つような何かしらのラベルを付けるべきです。

既存のモジュール（Mapping モジュールからの緯度と経度など）またはモジュールからの構造化された語彙（Value Suggest モジュールからのデータタイプなど）でメタデータやプロパティを一括してインポートする予定がある場合は、これらのフィールドがサイトのデータモデルに存在することを確実にするため、これらのモジュールを最初にインストールして構成してください。その後で情報を入力するようにしてください。これらのモジュールを後でアンインストールすると、データが失われる可能性があります。

## 初期インポート設定

左側のナビゲーションから CSV インポートタブをクリックすると、初期の「インポート設定」ページが開きます。ソフトウェアプログラムから直接正しい形式でエクスポートされたほとんどのスプレッドシートについては、これらの設定はデフォルトのままで問題ありません。

- 「ファイルを選択」ボタンを使用して、コンピューターからスプレッドシートを選択します。
- **CSV 列区切り文字**ドロップダウンから、次のオプションを選びます（これはあなたのファイルの形式に合っている必要があります）。これは行内の異なる値を区切る文字です:
	- カンマ（デフォルト）
	- セミコロン
	- コロン
	- タブ
	- キャリッジリターン
	- スペース
	- パイプ (`|`).

- **CSV 列エンクロージャ**ドロップダウンから、該当する場合にファイル内の長いテキストを囲むオプションを選択します:
	- ダブルクォート（デフォルト）
	- クォート
	- ハッシュ (`#`).

- **インポートタイプ** ドロップダウンから、インポートする内容を選択します:
	- アイテム
	- アイテムセット
	- メディア（既存のアイテムにメディアをマッチさせる列が必要です）
	- 混在リソース（スプレッドシートにアイテムセット、アイテム、メディアが含まれる場合；各行のタイプを識別する列が必要です）
	- ユーザー.

- **簡単なラベルで自動マッピングする** チェックボックスを選択します。CSV インポートは、特別にフォーマットされた列の見出し (`prefix:property` 形式) を自動的にマッピングしますが、このボックスをチェックすると、既存の語彙プロパティラベル（「Title」など）と一致する任意の列見出しも自動的にマッピングされます。

- **コメント**は「過去のインポート」ページに表示されます。これは、インポート内容やこのページで選択した設定に関するメモを残すことができるため、バッチ処理で作業を行う場合や、後でインポートを元に戻したい場合に便利です。

![説明されているようなインポート設定、未入力](../modules/modulesfiles/csvimport_settings.png)

「次へ」ボタンをクリックして、インポートプロセスを続行します。

## アイテムのインポート
アイテムをインポートするには、最初のページで「インポートタイプ」の下にある「アイテム」を選択します。

「次へ」をクリックすると、次のタブが読み込まれたページが表示されます:

### Omeka S データにマッピング
このタブには、スプレッドシートの列が行として表示されるテーブルがあります。各行には次のものが表示されます:

- チェックボックス
- スプレッドシートの列のヘッダー
- マッピングの追加または変更のためのプラス記号ボタン
- スプレッドシート列のオプションのためのレンチ記号ボタン
- 自動的にまたは手動でマップされたプロパティを表示する列
- 既存のマッピングを削除するゴミ箱
- 選択された特定のオプションを表示する列。

![10列のスプレッドシートのマッピング。Description や Title と名付けられた列のいくつかは、Dublin Core プロパティに自動的にマップされています。](../modules/modulesfiles/csvimport_itemsMap1.png)

#### マッピングオプション

列のヘッダーを語彙プロパティにマップするには、プラス記号ボタンをクリックします。これにより、画面の右側に引き出し（サイドバー）が開きます。

引き出しには複数のマッピングオプションがあります:

**プロパティ**では、インストールされている語彙のいずれかから、列データにマップするプロパティを選択できます。特定のプロパティを検索するために「フィルタ」フィールドを使用します。

![プロパティオプションが開いており、Omeka S インストール用にインストールされているすべての語彙が表示されています: Dublin Core、Bibliographic Ontology、Friend of a Friend、Scripto、OWL-Time Ontology](../modules/modulesfiles/csvimport_itemsMapProp.png)

**アイテム固有データ**には、選択したプロパティによってアイテムセットを設定するドロップダウンがあります。各アイテムにアイテムセットを追加したい場合（「基本設定」タブですべてのインポートアイテムを同じアイテムセットに入れるのではなく）、このドロップダウンでマッピングを設定できます。アイテムセットの内部IDまたはそのプロパティ（タイトルなど）を使用できます。

![説明されているドロップダウン](../modules/modulesfiles/csvimport_itemsMapISD.png)

**汎用データ**にもドロップダウンがあり、次の4つのオプションを設定できます:

- **リソーステンプレート（ラベル別）**: スプレッドシートに入力されたテンプレートの名前と Omeka S 内のテンプレートの名前が厳密に一致する場合に、アイテムのテンプレートを設定します。
- **リソースクラス（用語別）**: アイテムのリソースクラスを設定します。スプレッドシート内のクラスの用語と Omeka S インストール内の用語が厳密に一致している必要があります。インストール内の Vocabularies タブを参照してください。例えば、「dctype:Dataset」、「dcterms:Location」、「bibo:Interview」、「foaf:Person」と入力します。語彙のプレフィックスと用語をコロンで区切り、スペースは入れません。
- **所有者（メールアドレスによる）**: メールアドレスでアイテムの所有者を設定します。これは Omeka S インストールにおけるユーザーアカウントに関連付けられたメールアドレスでなければなりません。
- **可視性公開/非公開**: アイテムの可視性を設定します。スプレッドシートで「private」または「public」と使用します。

![説明されているようなドロップダウン](../modules/modulesfiles/csvimport_itemsMapgeneric.png)

**メディアソース**では、アイテムに一緒にインポートする[メディア](../content/media.md#add-media-to-an-item)をドロップダウンから選択して、ソーシング方法を指定できます:

- HTML
- IIIF image (リンク)
- IIIF presentation (リンク)
- oEmbed (リンク)
- URL
- YouTube
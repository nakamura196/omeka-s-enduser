# インストール

## システム要件
Omeka Sをインストールするには、以下を実行するサーバーが必要です：

- Linux
- Apache（[AllowOverride](https://httpd.apache.org/docs/2.4/mod/core.html#allowoverride)を"All"に設定し、[mod_rewrite](http://httpd.apache.org/docs/current/mod/mod_rewrite.html)が有効）
- MySQL、最低バージョン5.6.4（または、MariaDB、最低バージョン10.0.5）
- PHP、最低バージョン7.4、[PDO](http://php.net/manual/en/intro.pdo.php)、[pdo_mysql](http://php.net/manual/en/ref.pdo-mysql.php)、[xml](http://php.net/manual/en/intro.xml.php)拡張機能がインストールされている
- オプション、サムネイル作成用：ImageMagickバージョン6.7.5以上、PHPの`imagick`拡張機能、またはPHPの`gd`拡張機能。

[GD](https://secure.php.net/manual/en/intro.image.php)はPHPにデフォルトでインストールされている基本的なグラフィックライブラリです。jpeg、gif、pngなどの一般的なイメージフォーマットのサムネイルを作成することができます。[ImagickおよびImageMagick](https://www.imagemagick.org)は同じライブラリで、200種類以上のフォーマットのサムネイルを作成することができます。詳細については、[設定ページ](configuration.md#thumbnails)を参照してください。

## インストール方法

### ダウンロードからのインストール

!!! note
	Omeka Sをインストールする前に、MySQLデータベースとユーザーを作成する必要があります。Omeka Sは専用のデータベースを使用する必要があります。他のシステムやOmeka SまたはClassicのインストールに使用するデータベースにプレフィックスを使用することはできません。データベースとユーザーを作成する方法の詳細については、ホスティングのサポートドキュメントを参照するか、システム管理者にお問い合わせください。

1. [最新リリースをリリースページからダウンロード](https://omeka.org/s/download/)します。
1. ダウンロードしたzipファイルをコンピューターに解凍します。
1. ディレクトリの中にある`config/database.ini`ファイルを開き、MySQLのユーザー名、パスワード、データベース名、ホスト名を追加します。この手順より前にユーザーとデータベースを作成しておく必要があります。
1. このディレクトリ全体を、選んだフォルダにサーバーにアップロードします。たとえば、サーバーが`https://yourwebsite.org/`であれば、`https://yourwebsite.org/myomekas/`にOmeka Sをインストールするフォルダを作成することになります。更新された`database.ini`ファイルが含まれていることを確認してください（ダウンロードした元のzipファイルはアップロードしないでください）。
1. サーバー上の`files/`ディレクトリがApacheによって書き込み可能であることを確認してください。
1. Webブラウザで、Omeka Sのインストールが完了した`admin`ページにアクセスします。たとえば、ディレクトリの内容を`https://yourwebsite.org/myomekas/`にアップロードした場合は、`https://yourwebsite.org/myomekas/admin`にアクセスします。

### GitHubからのインストール

GitHubからインストールおよび更新する基本的な手順は、Omeka S GitHubリポジトリの[ReadMe](https://github.com/omeka/omeka-s/blob/develop/README.md)にあります。

その後、WebブラウザでOmeka Sのインストールの管理ページ(`https://yourwebsite.org/myomekas/admin`)にアクセスし、インストールを完了します。

### ワンクリックインストール

[Softaculous](https://softaculous.com/)を使用するホスティング会社では、[Omeka Classic](https://www.softaculous.com/softaculous/apps/educational/Omeka)と[Omeka S](https://www.softaculous.com/softaculous/apps/others/Omeka_S) のワンクリックインストールを提供しているはずです。Softaculousを介したワンクリックインストールプロセスでは、データベースとユーザーを同時に作成でき、「config/database.ini」ファイルを編集してくれます。

ユーザーからの提案には：

- [Reclaim Hosting](https://reclaimhosting.com/) - いくつかのステップ（PHPパスを[手動で設定する](#test-and-set-the-php-path)など）を含む[シンプルなOmeka Sインストール](https://support.reclaimhosting.com/hc/en-us/sections/204007617-Omeka)を提供し、他のオープンソースソフトウェアプラットフォームのサポート
- [Dotblock](http://www.dotblock.com) - Softaculousを使用
- [HostGator](http://hostgator.com) - Softaculousを使用
- [TMD Hosting](https://www.tmdhosting.com) - Softaculousを使用
- [Webuzo](http://webuzo.com) - Softaculousを使用。

## 初期設定

Omeka Sのインストールに成功し、`database.ini`ファイルを設定したら、Omeka Sのインストールの管理URLにアクセスする必要があります（`https://yourwebsite.org/myomekas/admin`のようなもの）。

新しくインストールされたサイトにブラウザを向けた最初の時、最初のユーザーの情報を入力し、インストールの基本情報を入力する必要があります。このページには2つのセクションがあります：**最初のユーザーを作成**と**設定**。

**最初のユーザーを作成**セクションで：

- **メールアドレス**を入力し、確認のため再入力します
- **パスワード**を確認し、次の入力欄で確認のため再入力します
- ユーザーの**表示名**を入力します。

これらはいずれもインストールの[ユーザー](admin/users.md)管理セクションで後で変更することができます。

![最初のユーザーセクションの説明にあるフィールドとともに](files/installOmekaS1.png)

**設定**セクションで、次の項目を入力します：

- 管理サイトに表示される**インストールのタイトル**
- インストールの**タイムゾーン**（ドロップダウンから選択）
- インストールの管理側の言語になる**ロケール**を選択します。

![説明されているフィールドがある設定セクション](files/installOmekaS2.png)

これらはいつでもインストールの[設定](admin/settings.md)セクションか[管理ダッシュボード](admin-dashboard.md)で変更が可能です。

### PHPパスをテストして設定する

Omeka Sは、多くのアイテムに作用する長時間実行されるタスクや、単に長い時間がかかるかもしれないタスクのためのバックグラウンドジョブを使用します。Omeka Sはこれらのジョブを実行するためにPHP CLI（コマンドラインインターフェイス）、`php`コマンドを使用します。無効なPHPパスは、Omeka Classicインストールの多くの問題を引き起こす可能性があります。

Omeka Sはデフォルトではサーバー上のPHP CLIへのパスを自動的に検出しようとしますが、検出が機能しないサーバーや複数の異なる`php`コマンドから選択する必要があるサーバーもあります。

[Reclaim Hostingを使用している場合](#one-click-installation)は、インストール時にPHPパスを手動で設定する必要があります。[ここでの彼らの指示を参照してください](https://support.reclaimhosting.com/hc/en-us/articles/1500005620481#omeka-s)。

[システム情報ページ](admin-dashboard.md#system-information)を使用して、インストールが正しいPHPパスを識別しているかを確認します。ボタンをクリックしたときにエラーが発生する場合、それは手動で設定を行う必要があるかもしれないことを示しています。

![PHPパスとImageMagickバージョンを取得するためのシステム情報ボタン。](files/systeminfo_buttons.png)

サムネイル生成の変更、手動でPHPパスを設定する方法などについては、[構成オプション](configuration.md)で詳しく学んでください。

### インストール作業の開始

Omeka Sインストールのすべての技術的なコンポーネントが正しく設定されたら、他のユーザーの追加、リソーステンプレート、語彙、アイテムセットの作成、1つ以上のサイトの作成、アイテムの追加、およびこれらのリソースのサイトへの割り当てから始めることになります。Omeka Sのこれらの部分についてもっと学ぶため、ユーザーマニュアルを続けてください。

!!! note
	既存のOmeka ClassicまたはSインストールを持っている場合は、[Omeka Classic Importer](modules/omekaCimporter.md)、[Omeka S Item Importer](modules/ositemimporter.md)、または[CSV Importモジュール](modules/csvimport.md)のようなモジュールを見て、他のタイプのデータをコピーするのに役立つかもしれません。

## アップデート

### 手動でアップデートする

1. リリースページから最新リリースをダウンロードします。
1. `/config`ディレクトリのコピーを作成します。`local.config.php`および`database.ini`ファイルをそのコピーから復元する必要があります。
1. `/modules`および`/themes`ディレクトリのコピーを作成します。
1. `/files`ディレクトリのコピーを作成します。
1. すべてのOmeka Sファイルを削除し、更新されたzipファイルのファイルで置き換えます。
1. 元の`/config/local.config.php`ファイル、`/config/database.ini`ファイル、およびコピーした`/modules`、`/themes`、`/files`ディレクトリを置き換えます。
    - 大きなバージョンアップデートの場合は、モジュールとテーマの更新バージョンをインストールする必要もあるかもしれません。バージョンのリリースノートで、それらの更新が必要かどうかが示されるでしょう。さらに、ブラウザを使用して移行が完了すると、新しいバージョンが必要なモジュールとテーマがそれぞれのページで明確にマークされます。
1. Webブラウザで、サイトの管理ページ(`/myomekas/admin`)にアクセスし、必要な移行を実行します。

### GitHubからのアップデート

GitHubからのインストールおよびアップデートの基本的な手順は、Omeka S GitHubリポジトリの[ReadMe](https://github.com/omeka/omeka-s/blob/develop/README.md)にあります。

## WindowsまたはMac OSでのインストール（開発のみ）
Omeka Sは、独占的またはクローズドソースのオペレーティングシステムをサポートしていません。しかし、**基本的な開発目的**や迅速なトレーニングのために、Omekaは[WAMP](http://www.wampserver.com)、[MAMP](https://www.mamp.info)、またはそれに類似したツールを使って実行することができます。

標準のインストール手順に従ってください。`config/local.config.php`のファイルに以下の[設定](configuration.md)変更を行う必要があります。

まず、Omeka Sがあなたのローカルサーバー上のPHPユーティリティの場所を自動的に検出できない場合、PHPパスを設定する必要があります。`local.config.php`ファイルを開き、12行目を探します：
```
    'cli' => [
        'phpcli_path' => null,
    ],
```

`phpcli_path`の値に、オペレーティングシステムに適したパスを記入します。たとえば、MAMP環境を使用している場合は、MAMPのインストールフォルダ内の`MAMP\bin\php\php74`でPHPユーティリティを見つけるかもしれません。

次に、ローカルサーバーで利用可能なサムネイル生成ユーティリティを使用するようにOmeka Sを設定する必要があります。`local.config.php`ファイルを開き、次のセクションを探します：
```
    'service_manager' => [
        'aliases' => [
            'Omeka\File\Store' => 'Omeka\File\Store\Local',
            'Omeka\File\Thumbnailer' => 'Omeka\File\Thumbnailer\ImageMagick',
        ],
    ],
```
システムに利用可能なものに基づいて`Omeka\File\Thumbnailer`の値を以下に置き換えます：

- デフォルトのサムネイラーを`Omeka\File\Thumbnailer\Gd`に置き換えます。
- デフォルトのサムネイラーを`Omeka\File\Thumbnailer\Imagick`に置き換え、サーバーの`php.ini`ファイルでImagickを有効にします。
- デフォルトのサムネイラー`Omeka
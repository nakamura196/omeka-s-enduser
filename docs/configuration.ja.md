# 設定オプション

以下は、`local.config.php`ファイルで設定可能な、よく求められるオプションです。このファイルは`/config`ディレクトリにあります。

利用可能なすべての設定キーの完全なリストについては、[開発者ドキュメントページの設定設定](https://omeka.org/s/docs/developer/configuration/){target=_blank}をご覧ください。

## パスワード設定
ユーザーパスワードの要件を変更することができます。オプションには最小長、大文字と小文字の数、許可される記号の設定が含まれます。

```
    'password' => [
        'min_length' => 6,
        'min_lowercase' => null,
        'min_uppercase' => null,
        'min_number' => null,
        'min_symbol' => null,
        'symbol_list' => '`~!@#$%^&*()-=_+[]\{}|;:",./<>?\'',
    ],
```
要件は[ユーザー作成と編集ページに表示されます](admin/users.md#password)。

## サムネイル

`thumbnails`設定キーには、サムネイル設定のほとんどが含まれています：

```
    'thumbnails' => [
        'types' => [
            'large' => ['constraint' => 800],
            'medium' => ['constraint' => 200],
            'square' => ['constraint' => 200],
        ],
        'thumbnailer_options' => [
            'imagemagick_dir' => null,
        ],
    ],
```

`types`の下には、メディアファイルの派生画像の最大ピクセル寸法を設定します。大、中、正方形にはそれぞれ800、200、200ピクセルのデフォルトがあります。

`thumbnailer_options`は使用中の特定のサムネイルプログラムに渡されるオプションの配列です。例えば、`imagemagick_dir` サムネイルオプションは、サーバー上でImageMagickの `convert` コマンドが見つかるフォルダへのパスを設定します。これは、Omeka SがImageMagickの正しいパスを自動検出できない場合に役立ちます。

[システム情報ページ](admin-dashboard.md#system-information)を使用して、インストールのImageMagickバージョンを確認してください。ボタンをクリックしたときにエラーが発生すると、手動で設定が必要かどうかを示すことがあります。

![PHPパスとImageMagickバージョンを取得するためのシステム情報ボタン。](files/systeminfo_buttons.png)

使用するサムネイルプログラムは `service_manager` キーの下で設定され、`Omeka\File\Thumbnailer`のエイリアスを設定します：

```
    'service_manager' => [
        'aliases' => [
            'Omeka\File\Thumbnailer' => 'Omeka\File\Thumbnailer\ImageMagick',
        ],
    ],
```

デフォルトのサムネイルプログラムは `Omeka\File\Thumbnailer\ImageMagick` です。利用可能なのは `Omeka\File\Thumbnailer\Imagick` (PHPの `imagick` 拡張機能を使用) と `Omeka\File\Thumbnailer\Gd` (`gd` PHP拡張機能を使用) もあります。

`Omeka\File\Thumbnailer\NoThumbnail`にサムネイルプログラムを設定することもできます。これはOmeka Sのインストールがサムネイルを生成しないようにします。

[GD](https://secure.php.net/manual/en/intro.image.php){target=_blank}はPHPと共にデフォルトでインストールされる基本的なグラフィックライブラリで、jpeg、gif、pngなどの一般的な画像フォーマットのサムネイルを作成することができます。

[ImagickとImageMagick](https://www.imagemagick.org){target=_blank}は同じライブラリで、200以上のフォーマットのサムネイルを作成することができます。ImagickはPHPに統合されており、ImageMagickはコマンドラインバージョンです。

ImageMagickでは `imagemagick_dir`で手動でパスを設定する必要がある場合がありますが、ImagickとGDではパスを必要としません。

管理インタフェースの最下部にある["システム情報"ページ](admin-dashboard.md#system-information)を使用して、GDとImagickがサーバー上のPHP拡張機能として有効になっているかダブルチェックすることができます。

!!! 注記
	一部のサーバーは、アプリケーションがPHP経由でコマンドラインプログラムを実行することを許可しません。次のようなエラーメッセージが表示される場合があります。

	`Laminas\ServiceManager\Exception\ServiceNotCreatedException`

	`サービス名 “Omeka\Cli” を作成できませんでした。理由: “proc_open()”も“exec()”も利用できません。`

	この場合、ImageMagickは機能しませんが、ImagickとGDは機能します。

## PHPパス

Omeka Sは、多くの項目を操作するか、それ以外に長時間かかる可能性のあるいくつかの長時間実行タスク
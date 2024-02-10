# トラブルシューティング

以下は、Omeka S用Scriptoのための上級者向けオプションおよびトラブルシューティングのヒントです。

## 匿名編集の無効化
デフォルトでは、Omeka S用Scriptoは匿名ユーザーがプロジェクトのコンテンツを編集できるようにしています。

これを防ぐためには、MediaWikiインストールがあるディレクトリ内のファイルを編集する必要があります。以下の行を

```
$wgGroupPermissions['*']['edit'] = false;
```

`LocalSettings.php` ファイルに追加してください。

さらに情報が必要な場合は、[アクセスを防ぐためのMediaWikiマニュアル](https://www.mediawiki.org/wiki/Manual:Preventing_access){target=_blank}をご覧ください。

## トラブルシューティング
### プロジェクト同期が停止している
プロジェクト同期が開始されない、または処理中のままである場合は、[Omeka SインストールのためのPHP-CLIパスが正しく設定されているかを確認してください](../../configuration.md#php-path)。
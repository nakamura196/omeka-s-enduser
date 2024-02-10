# Scriptoプロジェクト

Scriptoはプロジェクトで構成されています。あなたが開始するすべての転写、翻訳、または説明の努力は、プロジェクトとして作成することができ、また作成するべきです。

## プロジェクトを作成する
この[スクリーンキャスト](https://vimeo.com/422818763){target=_blank}は、Omeka S内でScriptoプロジェクトを作成するプロセスを説明しています。

<div style="padding:56.64% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/422818763?h=1a3fc18046" style="position:absolute;top:0;left=0;width:100%;height:100%;" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>
<p><a href="https://vimeo.com/422818763">Scriptoプロジェクトの作成</a> by <a href="https://vimeo.com/omeka">Omeka</a> on <a href="https://vimeo.com">Vimeo</a>.</p>

新しいScriptoプロジェクトを作成するには、Scriptoダッシュボードに移動し（左側のナビゲーションバーのScriptoタブ）、画面右上の「Actions」ドロップダウンメニューから「Add new project」を選択します。

![Actions dropdown open with a red arrow pointing to the Add New Project option](../modulesfiles/scripto-projectAdd.png)

これによって「New project」ページが開きます。このページには「Configuration」と「Reviewers」という2つのタブがあります。

「Add」ボタンの右上にある目のシンボルはプロジェクトの可視性を設定します。ボタンが非公開（目に斜線）の場合、Omekaサイトのユーザーのみがプロジェクトを閲覧できます。

![New projectページの上部のみを表示し、2つのタブと目のシンボルを表示している](../modulesfiles/scripto-projectAdd2.png)

これらの設定は後でいつでも、「プロジェクトのレビュー」でプロジェクトを編集してActionsドロップダウンメニューを使用することで変更できます。

### 設定オプション
これらの設定オプションのいくつかは、Scriptoプロジェクトを作成するために必要です。すべてのオプションは後から「Edit project」オプションを使用して変更できます。

![「Configuration」タブが開いている「Add New Project」ウィンドウ。すべてのフィールドは空白です](../../modules/modulesfiles/scripto-projectNewConfig.png)

**Title:** (必須) Scriptoプロジェクトの名前です。これは一般公開と管理側の両方で表示されます。

**Item set:** (必須) Scriptoプロジェクトと同期すべきアイテムセットを選択します。このアイテムセットには、プロジェクトに含めたいすべてのアイテムやメディアが含まれているべきです。

**Property:** (必須) Scriptoを介して作成されたコンテンツがOmeka Sメタデータにインポートされる際、どのプロパティに保存するかをドロップダウンから選択します。インストール済みの[Vocabularies](https://omeka.org/s/docs/user-manual/content/vocabularies/)に加えて、Scriptoにはコンテンツ、転写、翻訳の独自の語彙オプションがあります。これらはプロパティに適しています。

**Description:** プロジェクトの説明です。これは一般公開と管理側の両方で表示されます。

**Guidelines:** 転写のガイドラインです。このフィールドに入力すると表示されるテキストフォーマットエディターを使用してフォーマットできます。

![ガイドラインエディターが動作中で、エディターを表示しています](../modulesfiles/scripto-projectGuideEdit.png)

**Create account text:** これは、利用者が転写するためにサインアップする公開ページに表示されるテキストを入力します。たとえば、プロジェクトの目的や活動の簡単な要約などがあります。文字を入力しない場合、ページは名前、メール、パスワードのフィールドのみを表示します。

**Language tag:** 上で選択したプロパティにインポートされるコンテンツの言語タグです。

**Import target:** ScriptoプロジェクトからOmeka Sメタデータにデータをプッシュする際にデータを保存するリソースレベルを選択します。オプションは「Item and Media」、「Item」、または「Media」です。

「Item」を選択した場合、Scriptoで作成されたコンテンツは、あらかじめ選択したプロパティのアイテムメタデータに表示されます。

「Media」を選択した場合、Scriptoで作成されたコンテンツはメディアメタデータに表示されますが、アイテムレベルでは表示されません。

**Browse layout:** プロジェクトのデフォルトのブラウズレイアウトを「Grid」または「List」から選択します。

**Filter approved:** このオプションをチェックすると、承認済みのアイテムは一般公開のブラウズビューで表示されません。

**Item Type:** このプロジェクトで使用するアイテムのタイプを指定したい場合があります。ここで選択したものはユーザーのインターフェース言語を変更します。たとえば、「manuscript」と選択すると、プロジェクトのブラウズリンクは"browse items"ではなく"browse manuscripts"と表示されます。選択肢には以下があります：

- Generic Item (デフォルト)
- Audio
- Book
- Document
- Journal 
- Manuscript
- Paper
- Video

**Media Type:** このドロップダウンを使用して、プロジェクトで使用するメディアのタイプを指定し、このプロジェクトにおけるScriptoでのメディアの言及方法を変更します。選択肢には以下があります：

- Generic Media
- Entry
- Folio
- Image
- Page
- Section
- Segment
- Sheet

**Content Type:** プロジェクトの作業内容を指定するために使用します。選択肢には以下があります：

- Generic Content
- Description
- Transcription
- Translation

### レビュアー
あなたのScriptoプロジェクトにレビュアーとして[Omeka Sユーザー](../../../admin/users/)を追加します。レビュアーは非公開プロジェクトにアクセスし、メディアを承認および非承認としてマークできます。プロジェクト追加後、ユーザーを管理することができます（下記参照）。

オメカユーザーでは、**サイト管理者（site administrator）** と **グローバル管理者（global administrator）** の役割を持つユーザーのみが、プロジェクトの同期とインポートが可能です。その行動の破壊的な可能性のためです。

レビュアーはScriptoプロジェクトをレビューするためにMediaWikiアカウントを持っている必要はありませんが、アカウントを作成することを推奨します。

![レビュアーを追加するウィンドウが開いています。ページの大部分は空白で、一方の側にはアルファベットメニューがあります。](../modulesfiles/scripto_newrev.png)

ウィンドウの右側には、ユーザー名でアルファベット順にソートされたOmeka Sユーザーの閲覧可能なリストがあります。Omeka SユーザーをScriptoプロジェクトのレビュアーとして追加するには、単にその名前をクリックします。これにより、彼らはページの主要部分のレビュアーのテーブルに追加されます。

このプロジェクトで作業する予定がある場合は、自分自身をレビュアーとして追加してください。

レビュアーとしてユーザーを削除するには、レビュアーのテーブルの彼らのメールアドレスの右側にあるゴミ箱のアイコンをクリックします。

### プロジェクトを追加する
必要なフィールドに入力を行い、「Add」をクリックして新しいプロジェクトを作成します。

### 初期同期
プロジェクトを作成した直後に、「No Scripto items found. Do you need to sync the project? If you have recently synced, the sync job has likely not finished.」というメッセージが表示されます。

![新しいプロジェクトの同期メッセージ](../modulesfiles/scripto-newproject.png)

プロジェクトを同期するには、ウィンドウの右上にあるActionsドロップダウンボタンに移動します。オプションから「Sync project」を選択すると、アイテムセットに含まれているすべてのアイテムがプロジェクトに更新されます。

![](../modulesfiles/scripto-projectactions.png)

初めて同期を実行すると、時間がかかる可能性があり、引き続き「No Scripto items found」メッセージが表示されることがあります。同期が進行中であること、および同期のジョブへのリンクを示す緑色のメッセージがページの上部に表示されるはずです。

## 管理者のプロジェクトビュー
Scriptoダッシュボードからは、自分が所有するプロジェクトと、レビュアー権限を持つプロジェクトにアクセスできます。プロジェクトのステータスにかかわらず、プロジェクトのタイトルをクリックすると、そのレビューページに移動します。

![scripto review page, user not logged in to Scripto](../../modules/modulesfiles/scripto-admin-project1.png)

ページの上部には、「Review」と表示されるプロジェクトタイトルがあります。プロジェクトタイトルの下には、ログインするか、ダッシュボード、自分の貢献、ウォッチリストに移動するためのScriptoアカウントバーがあります。

※ 以下は、字数の制限により省略させていただきますが、もし続きをご希望の場合は、さらに区切って再度リクエストしていただければ幸いです。

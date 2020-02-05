---
id: version-18.0-architecture
title: 4D プロジェクトのアーキテクチャー
original_id: architecture
---

4D プロジェクトは、一つの親プロジェクトフォルダーに格納された、複数のフォルダーやファイルから構成されています。 たとえば:

![](assets/en/Project/project1.png)

> バイナリデータベースから変換されたプロジェクトの場合には、追加のフォルダーが存在している場合があります  (doc.4d.com にて "[データベースをプロジェクトモードに変換する](https://doc.4d.com/4Dv18/4D/18/Converting-databases-to-projects.300-4606146.ja.html)" 参照)。


## Project フォルダー

典型的な Project フォルダーの構造です:

- *databaseName*.4DProject file
- Sources
    + DatabaseMethods
    + Methods
    + Forms
    + TableForms
    + Triggers
- DerivedData
- Trash (あれば)


### *databaseName*.4DProject file

プロジェクトを定義し、起動するためのプロジェクト開発ファイルです。 このファイルを開くには次のいずれかが必要です:

- 4D Developer
- 4D Server (デザインモードは読み取り専用；[プロジェクトの開発](developing.md) 参照)

**Note:** In 4D projects, development is done with 4D Developer and multi-user development is managed through source control tools. 4D Server は .4DProject ファイルを開くことができますが、クライアントからの開発はおこなえません。


### Sources フォルダー

| 内容                      | 説明                                                                                                                                                                                    | 形式   |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---- |
| catalog.4DCatalog       | テーブルおよびフィールド定義                                                                                                                                                                        | XML  |
| folders.json            | 　エクスプローラーフォルダー定義                                                                                                                                                                      | JSON |
| menus.json              | メニュー定義                                                                                                                                                                                | JSON |
| settings.4DSettings     | *Structure* database settings. If *user settings* are defined, they take priority over these settings. If *user settings for data* are defined, they take priority over user settings | XML  |
| tips.json               | 定義されたヘルプTips                                                                                                                                                                          | JSON |
| lists.json              | 定義されたリスト                                                                                                                                                                              | JSON |
| filters.json            | 定義されたフィルター                                                                                                                                                                            | JSON |
| styleSheets.css         | CSS スタイルシート                                                                                                                                                                           | CSS  |
| styleSheets_mac.css     | Mac用 CSS スタイルシート (変換されたバイナリデータベースより)                                                                                                                                                  | CSS  |
| styleSheets_windows.css | Windows用 CSS スタイルシート (変換されたバイナリデータベースより)                                                                                                                                              | CSS  |


#### DatabaseMethods フォルダー

| 内容                       | 説明                                                  | 形式   |
| ------------------------ | --------------------------------------------------- | ---- |
| *databaseMethodName*.4dm | データベース内で定義されているデータベースメソッド  (1つのデータベースメソッドにつき1ファイル)。 | テキスト |

#### Methods フォルダー

| 内容               | 説明                                            | 形式   |
| ---------------- | --------------------------------------------- | ---- |
| *methodName*.4dm | データベース内で定義されているプロジェクトメソッド  (1つのメソッドにつき1ファイル)。 | テキスト |

#### Forms フォルダー

| 内容                                        | 説明                                  | 形式      |
| ----------------------------------------- | ----------------------------------- | ------- |
| *formName*/form.4DForm                    | プロジェクトフォームの定義                       | JSON    |
| *formName*/method.4dm                     | プロジェクトフォームメソッド                      | テキスト    |
| *formName*/Images/*pictureName*           | プロジェクトフォームのスタティックピクチャー              | picture |
| *formName*/ObjectMethods/*objectName*.4dm | オブジェクトメソッド  (1つのオブジェクトメソッドにつき1ファイル) | テキスト    |

#### TableForms フォルダー

| 内容                                                   | 説明                                             | 形式      |
| ---------------------------------------------------- | ---------------------------------------------- | ------- |
| *n*/Input/*formName*/form.4DForm                     | 入力テーブルフォームの定義 (n: テーブル番号)                      | JSON    |
| *n*/Input/*formName*/Images/*pictureName*            | 入力テーブルフォームのスタティックピクチャー                         | picture |
| *n*/Input/*formName*/method.4dm                      | 入力テーブルフォームのフォームメソッド                            | テキスト    |
| *n*/Input/*formName*/ObjectMethods/*objectName*.4dm  | 入力テーブルフォームのオブジェクトメソッド  (1つのオブジェクトメソッドにつき1ファイル) | テキスト    |
| *n*/Output/*formName*/form.4DForm                    | 出力テーブルフォーム (n: テーブル番号)                         | JSON    |
| *n*/Output/*formName*/Images/*pictureName*           | 出力テーブルフォームのスタティックピクチャー                         | picture |
| *n*/Output/*formName*/method.4dm                     | 出力テーブルフォームのフォームメソッド                            | テキスト    |
| *n*/Output/*formName*/ObjectMethods/*objectName*.4dm | 出力テーブルフォームのオブジェクトメソッド  (1つのオブジェクトメソッドにつき1ファイル) | テキスト    |

#### Triggers フォルダー

| 内容            | 説明                                                    | 形式   |
| ------------- | ----------------------------------------------------- | ---- |
| table_*n*.4dm | データベース内で定義されているトリガーメソッド  ( 1つのテーブルにつき1ファイル；n: テーブル番号) | テキスト |

**Note:** The .4dm file extension is a text-based file format, containing the code of a 4D method. ソース管理ツールに対応しています。


### Trash フォルダー

プロジェクトから削除されたメソッドやフォームがあれば、Trash フォルダーにはそれらが格納されます。 たとえば、つぎのフォルダーが格納されている場合があります:

- Methods
- Forms
- TableForms

削除された要素はファイル名に括弧が付いた形でフォルダー内に置かれます (例: "(myMethod).4dm")。 フォルダーの構成は [Sources](#sources) フォルダーと同じです。


### DerivedData フォルダー

DerivedData フォルダーには、処理を最適化するため 4D が内部的に使用するキャッシュデーターが格納されます。 これらは必要に応じて自動的に生成・再生成されます。 このフォルダーは無視してかまいません。


## Resources フォルダー

Resources フォルダーには、追加のカスタムデータベースリソースファイルやフォルダーが格納されます。 アプリケーションインターフェースの翻訳やカスタマイズに必要なファイルはすべてここに格納します (ピクチャー、テキスト、XLIFF ファイルなど)。 4D は自動のメカニズムによってフォルダー内のファイル (とくに XLIFF ファイルおよびスタティックピクチャー) を扱います。 リモートモードにおいては、サーバーとすべてのクライアントマシン間でファイルを共有することが Resources フォルダーによって可能です See the *4D Server Reference Manual*.

| 内容                    | 説明                                                                        | 形式      |
| --------------------- | ------------------------------------------------------------------------- | ------- |
| *item*                | データベースリソースファイルとフォルダー                                                      | 様々      |
| Images/Library/*item* | ピクチャーライブラリの個別ピクチャーファイル(*)。 各アイテムの名称がファイル名となります。 名称が重複する場合には、名称に番号が追加されます。 | picture |

(*) .4db バイナリデータベースから変換されたプロジェクトの場合のみ


## Data フォルダー

Data フォルダーには、データファイルのほか、データに関わるするファイルやフォルダーがすべて格納されています。

| 内容           | 説明                                                                                                                                                                                                                                                                                                                                                     | 形式   |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---- |
| data.4dd(*)  | レコードとして入力されたデータと、レコードに属するデータが格納されたデータファイルです。 4D プロジェクトを開くと、アプリケーションはカレントデータファイルをデフォルトで開きます。 If you change the name or location of this file, the *Open data file* dialog box will then appear so that you can select the data file to use or create a new one                                                                                          | バイナリ |
| data.journal | データベースがログファイルを使用する場合のみ作成されます。 ログファイルは2つのバックアップ間のデータ保護を確実なものにするために使用されます。 データに対して実行されたすべての処理が、このファイルに順番に記録されます。 つまりデータに対して操作がおこなわれるたびに、データ上の処理 (操作の実行) とログファイル上の処理 (操作の記録) という 2つの処理が同時に発生します。 ログファイルはユーザーの処理を妨げたり遅くしたりすることなく、独立して構築されます。 データベースは 1つのログファイルしか同時に使用できません。 ログファイルにはレコードの追加・更新・削除やトランザクションなどの処理が記録されます。 ログファイルはデータベースが作成される際にデフォルトで生成されます。 | バイナリ |
| data.match   | (内部用) テーブル番号に対応する UUID                                                                                                                                                                                                                                                                                                                                 | XML  |

(*) .4db バイナリデータベースからプロジェクトに変換した場合、データファイルは変換による影響を受けません。 このデータファイルの名称を変更して移動させることができます。

### Settings フォルダー

This folder contains **user settings files for data** used for database administration.

> These settings take priority over **[user settings files](#settings-folder-1)** and **structure settings** files.

| 内容                  | 説明                                                                                                                                                                                 | 形式   |
| ------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---- |
| Backup.4DSettings   | このデータファイルを使ってデータベースが実行されている場合に使用する [バックアップオプション](Backup/settings.md) を定義したデータベースバックアップ設定です。 Keys concerning backup configuration are described in the *4D XML Keys Backup* manual. | XML  |
| settings.4DSettings | データファイル用のカスタムデータベース設定                                                                                                                                                              | XML  |
| directory.json      | このデータファイルを使ってデータベースが実行されている場合に使用する 4D グループとユーザー、およびアクセス権の定義                                                                                                                        | JSON |



### Logs フォルダー

Logs フォルダーには、プロジェクトが使用するすべてのログファイルが格納されます。 以下のログファイルが格納されます:

- データベース変換
- Webサーバーリクエスト
- backup/restore activities journal (*Backup Journal\[xxx].txt*, see [Backup journal](Backup/backup.md#backup-journal))
- コマンドデバッグ
- 4D Serverリクエスト (クライアントマシンおよびサーバー上で生成)

> データフォルダーが読み取り専用モードの場合やメンテナンスログファイルの保存には、システムのユーザー設定フォルダー (Active 4D Folder のこと、詳しくは [Get 4D folder](https://doc.4d.com/4Dv18/4D/18/Get-4D-folder.301-4505365.ja.html) コマンド参照) 内にある Logs フォルダーが利用されます。

## Settings フォルダー

This folder contains **user settings files** used for database administration. 必要に応じてこのフォルダーにファイルが追加されます。

> [Data フォルダー](#settings-folder)の Setting フォルダー内にデータファイル用のユーザー設定ファイルがある場合には、そちらが優先されます。

| 内容                  | 説明                                                                                                                                                                                                                                                                                            | 形式   |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---- |
| directory.json      | 4D グループとユーザー、およびアクセス権の定義                                                                                                                                                                                                                                                                      | JSON |
| BuildApp.4DSettings | アプリケーションビルダーのダイアログボックス、または `BUILD APPLICATION` コマンドを使ったときに自動的に作成されるビルド設定ファイル                                                                                                                                                                                                                  | XML  |
| Backup.4DSettings   | バックアップ開始時に [バックアップオプション](Backup/settings.md) を指定するためのデータベースバックアップ設定です。 This file can also be used to read or set additional options, such as the amount of information stored in the *backup journal*. Keys concerning backup configuration are described in the *4D XML Keys Backup* manual. | XML  |


## userPreferences.*userName* folder

ブレークポイントの位置など、ユーザーの環境設定を定義するファイルを格納するフォルダーです。 このフォルダーは無視してかまいません。 格納されるファイルの例です:

| 内容                           | 説明                                 | 形式   |
| ---------------------------- | ---------------------------------- | ---- |
| methodPreferences.json       | カレントユーザーのメソッドエディター環境設定             | JSON |
| methodWindowPositions.json   | カレントユーザーのメソッドのウィンドウポジション           | JSON |
| formWindowPositions.json     | カレントユーザーのフォームのウィンドウポジション           | JSON |
| workspace.json               | 開かれているウィンドウのリスト；macOS ではタブウィンドウの順序 | JSON |
| debuggerCatches.json         | キャッチコマンドリスト                        | JSON |
| recentTables.json            | 最近開かれたテーブルのリスト                     | JSON |
| preferencesv15.4DPreferences | ユーザー環境設定                           | JSON |


## Components フォルダー

プロジェクトデータベースが利用するコンポーネントを格納するフォルダーです。 このフォルダーは、Project フォルダーと同じ階層に置きます。

> プロジェクトデータベースはコンポーネントとして利用することができます:<br /> - 開発においては、ホストデーターベースの Components フォルダーに .4dproject ファイルのエイリアスを置きます。 - 運用時においては、コンポーネントをビルドし ([プロジェクトパッケージのビルド](building.md))、生成された .4dz ファイルを .4dbase フォルダーに格納し、それをホストデータベースの Components フォルダーに置きます。


## Plugins フォルダー

プロジェクトデータベースが利用するプラグインを格納するフォルダーです。 このフォルダーは、Project フォルダーと同じ階層に置きます。
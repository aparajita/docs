---
id: fileClass
title: File
---

`File` objects are created with the [`File`](#file) command. They contain references to disk files that may or may not actually exist on disk. For example, when you execute the `File` command to create a new file, a valid `File` object is created but nothing is actually stored on disk until you call the [`file.create( )`](#create) function.

### 例題

The following example creates a preferences file in the project folder:

```code4d
var $created : Boolean
$created:=File("/PACKAGE/SpecialPrefs/"+Current user+".myPrefs").create()
```

### File オブジェクト

|                                                                                                                                                                                                  |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [<!-- INCLUDE #document.copyTo().Syntax -->](#copyto)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #document.copyTo().Summary -->|
| [<!-- INCLUDE #fileClass.create().Syntax -->](#create)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #fileClass.create().Summary -->|
| [<!-- INCLUDE #fileClass.createAlias().Syntax -->](#createalias)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #fileClass.createAlias().Summary -->|
| [<!-- INCLUDE #document.creationDate.Syntax -->](#creationdate)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #document.creationDate.Summary -->|
| [<!-- INCLUDE #document.creationTime.Syntax -->](#creationtime)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #document.creationTime.Summary -->|
| [<!-- INCLUDE #fileClass.delete().Syntax -->](#delete)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #fileClass.delete().Summary -->|
| [<!-- INCLUDE #document.exists.Syntax -->](#exists)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #document.exists.Summary -->|
| [<!-- INCLUDE #document.extension.Syntax -->](#extension)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #document.extension.Summary -->|
| [<!-- INCLUDE #document.fullName.Syntax -->](#fullname)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #document.fullName.Summary -->|
| [<!-- INCLUDE #document.getContent().Syntax -->](#getcontent)<p><!-- INCLUDE #document.getContent().Summary -->|
| [<!-- INCLUDE #document.getIcon().Syntax -->](#geticon)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #document.getIcon().Summary -->|
| [<!-- INCLUDE #document.getText().Syntax -->](#gettext)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #document.getText().Summary -->|
| [<!-- INCLUDE #document.hidden.Syntax -->](#hidden)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #document.hidden.Summary -->|
| [<!-- INCLUDE #document.isAlias.Syntax -->](#isalias)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #document.isAlias.Summary -->
|
| [<!-- INCLUDE #document.isFile.Syntax -->](#isfile)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #document.isFile.Summary -->|
| [<!-- INCLUDE #document.isFolder.Syntax -->](#isFolder)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #document.isFolder.Summary -->|
| [<!-- INCLUDE #document.isWritable.Syntax -->](#iswritable)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #document.isWritable.Summary -->|
| [<!-- INCLUDE #document.modificationDate.Syntax -->](#modificationdate)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #document.modificationDate.Summary -->|
| [<!-- INCLUDE #document.modificationTime.Syntax -->](#modificationtime)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #document.modificationTime.Summary -->|
| [<!-- INCLUDE #fileClass.moveTo().Syntax -->](#moveto)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #fileClass.moveTo().Summary -->|
| [<!-- INCLUDE #document.name.Syntax -->](#name)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #document.name.Summary -->|
| [<!-- INCLUDE #document.original.Syntax -->](#original)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #document.original.Summary -->|
| [<!-- INCLUDE #document.parent.Syntax -->](#parent)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #document.parent.Summary -->|
| [<!-- INCLUDE #document.path.Syntax -->](#path)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #document.path.Summary -->|
| [<!-- INCLUDE #document.platformPath.Syntax -->](#platformpath)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #document.platformPath.Summary -->|
| [<!-- INCLUDE #fileClass.rename().Syntax -->](#rename)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #fileClass.rename().Summary -->|
| [<!-- INCLUDE #fileClass.setContent().Syntax -->](#setcontent)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #fileClass.setContent().Summary -->|
| [<!-- INCLUDE #fileClass.setText().Syntax -->](#settext)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #fileClass.setText().Summary -->|
| [<!-- INCLUDE #document.size.Syntax -->](#size)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #document.size.Summary -->|



## File

<details><summary>履歴</summary>
| バージョン  | 内容 |
| ------ | -- |
| v17 R5 | 追加 |
</details>

<!-- REF #_command_.File.Syntax -->
**File** ( *path* : Text { ; *pathType* : Integer }{ ; *\** } ) : 4D.File<br>**File** ( *fileConstant* : Integer { ; *\** } ) : 4D.File<!-- END REF -->


<!-- REF #_command_.File.Params -->
| 参照           | タイプ     |    | 説明                                             |
| ------------ | ------- |:--:| ---------------------------------------------- |
| path         | テキスト    | -> | ファイルパス                                         |
| fileConstant | 整数      | -> | 4Dファイル定数                                       |
| pathType     | 整数      | -> | `fk posix path` (デフォルト) または `fk platform path` |
| *            |         | -> | ホストデータベースのファイルを返すには * を渡します                    |
| 戻り値          | 4D.File | <- | 新規ファイルオブジェクト                                   |
<!-- END REF -->


#### 説明

`File` コマンドは、 <!-- REF #_command_.File.Summary -->`4D.File` 型の新しいオブジェクトを作成して返します<!-- END REF -->。 The command accepts two syntaxes:

**File ( path { ; pathType } { ; \* })**

In the *path* parameter, pass a file path string. You can use a custom string or a filesystem (e.g., "/DATA/myfile.txt").

> Only absolute pathnames are supported with the `File` command.

By default, 4D expects a path expressed with the POSIX syntax. If you work with platform pathnames (Windows or macOS), you must declare it using the *pathType* parameter. The following constants are available:

| 定数               | 結果 | 説明                                                                                      |
| ---------------- | -- | --------------------------------------------------------------------------------------- |
| fk platform path | 1  | Path expressed with a platform-specific syntax (mandatory in case of platform pathname) |
| fk posix path    | 0  | Path expressed with POSIX syntax (default)                                              |

**File ( fileConstant { ; \* } )**

In the *fileConstant* parameter, pass a 4D built-in or system file, using one of the following constants:

| 定数                                | 結果 | 説明                                                                                                                                                                                                                                                                                                                                                                                                       |
| --------------------------------- | -- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Backup history file               | 19 | Backup history file (see Configuration and trace files). Stored in the backup destination folder.                                                                                                                                                                                                                                                                                                        |
| Backup log file                   | 13 | Current backup journal file. Stored in the application Logs folder.                                                                                                                                                                                                                                                                                                                                      |
| Backup settings file              | 1  | Default backup.4DSettings file (xml format), stored in the Settings folder of the project                                                                                                                                                                                                                                                                                                                |
| Backup settings file for data     | 17 | backup.4DSettings file (xml format) for the data file, stored in the Settings folder of the data folder                                                                                                                                                                                                                                                                                                  |
| Build application log file        | 14 | Current log file in xml format of the application builder. Stored in the Logs folder.                                                                                                                                                                                                                                                                                                                    |
| Build application settings file   | 20 | Default settings file of the application builder ("buildApp.4DSettings"). Stored in the Settings folder of the project.                                                                                                                                                                                                                                                                                  |
| Compacting log file               | 6  | Log file of the most recent compacting done with the Compact data file command or the Maintenance and security center. Stored in the Logs folder.                                                                                                                                                                                                                                                        |
| Current backup settings file      | 18 | backup.4DSettings file currently used by the application. It can be the backup settings file (default) or a custom user backup settings file defined for the data file                                                                                                                                                                                                                                   |
| Debug log file                    | 12 | Log file created by the `SET DATABASE PARAMETER(Debug log recording)` command. Stored in the Logs folder.                                                                                                                                                                                                                                                                                                |
| Diagnostic log file               | 11 | Log file created by the `SET DATABASE PARAMETER(Diagnostic log recording)` command. Stored in the Logs folder.                                                                                                                                                                                                                                                                                           |
| Directory file                    | 16 | directory.json file, containing the description of users and groups (if any) for the project application. It can be located either in the user settings folder (default, global to the project), or in the data settings folder (specific to a data file).                                                                                                                                               |
| HTTP debug log file               | 9  | Log file created by the `WEB SET OPTION(Web debug log)` command. Stored in the Logs folder.                                                                                                                                                                                                                                                                                                              |
| HTTP log file                     | 8  | Log file created by the `WEB SET OPTION(Web log recording)` command. Stored in Logs folder.                                                                                                                                                                                                                                                                                                              |
| Last backup file                  | 2  | 任意の場所に格納されている、最終バックアップファイル (名称は: \<applicationName>[bkpNum].4BK)                                                                                                                                                                                                                                                                                                                                        |
| Last journal integration log file | 22 | Full pathname of the last journal integration log file (stored in the Logs folder of the restored application), if any. This file is created, in auto-repair mode, as soon as a log file integration occurred                                                                                                                                                                                            |
| Repair log file                   | 7  | Log file of database repairs made on the database in the Maintenance and Security Center (MSC). Stored in the Logs folder.                                                                                                                                                                                                                                                                               |
| Request log file                  | 10 | Standard client/server request log file (excluding Web requests) created by the `SET DATABASE PARAMETER(4D Server log recording)` or `SET DATABASE PARAMETER(Client log recording)` commands. If executed on the server, the server log file is returned (stored in the Logs folder on the server). If executed on the client, the client log file is returned (stored in the client local Logs folder). |
| SMTP log file                     | 15 | Log file created by the `SET DATABASE PARAMETER(SMTP Log)` command. Stored in the Logs folder.                                                                                                                                                                                                                                                                                                           |
| User settings file                | 3  | settings.4DSettings file for all data files, stored in Preferences folder next to structure file if enabled.                                                                                                                                                                                                                                                                                             |
| User settings file for data       | 4  | settings.4DSettings file for current data file, stored in Preferences folder next to the data file.                                                                                                                                                                                                                                                                                                      |
| Verification log file             | 5  | Log files created by the `VERIFY CURRENT DATA FILE` and `VERIFY DATA FILE` commands or the Maintenance and Security Center (MSC). Stored in the Logs folder.                                                                                                                                                                                                                                             |

If the target *fileConstant* does not exist, a null object is returned. No errors are raised.

If the command is called from a component, pass the optional * parameter to get the path of the host database. Otherwise, if you omit the * parameter, a null object is always returned.


## 4D.File.new()

<details><summary>履歴</summary>
| バージョン  | 内容 |
| ------ | -- |
| v18 R6 | 追加 |
</details>

<!-- REF #4D.File.new().Syntax -->**4D.File.new** ( *path* : Text { ; *pathType* : Integer }{ ; *\** } ) : 4D.File<br>**4D.File.new** ( *fileConstant* : Integer { ; *\** } ) : 4D.File<!-- END REF -->


#### 説明

`4D.File.new()` 関数は、 <!-- REF #4D.File.new().Summary -->`4D.File` 型の新しいオブジェクトを作成して返します<!-- END REF -->。 It is identical to the [`File`](#file) command (shortcut).

> It is recommended to use the [`File`](#file) shortcut command instead of `4D.File.new()`. 


<!-- INCLUDE document.copyTo().Desc -->



<!-- REF file.create().Desc -->
## .create()

<details><summary>履歴</summary>
| バージョン  | 内容 |
| ------ | -- |
| v17 R5 | 追加 |
</details>

<!--REF file.create().Note -->
**Not available for ZIP archives**<!-- END REF -->


<!--REF #fileClass.create().Syntax -->
**.create()** : Boolean <!-- END REF -->

<!--REF #fileClass.create().Params -->
| 参照  | タイプ |    | 説明                                   |
| --- | --- | -- | ------------------------------------ |
| 戻り値 | ブール | <- | ファイルが正常に作成された場合に true、それ以外の場合は false |
<!-- END REF -->

#### 説明

`.create()` 関数は、 <!-- REF #fileClass.create().Summary -->`File` オブジェクトのプロパティに基づいてディスク上にファイルを作成します<!-- END REF -->。

If necessary, the function creates the folder hierachy as described in the [platformPath](#platformpath) or [path](#path) properties. If the file already exists on disk, the function does nothing (no error is thrown) and returns false.

**戻り値**

*   **True** if the file is created successfully;
*   **False** if a file with the same name already exists or if an error occured.

#### 例題

Creation of a preferences file in the database folder:

```4d
 var $created : Boolean
 $created:=File("/PACKAGE/SpecialPrefs/"+Current user+".myPrefs").create()
```
<!-- END REF -->





<!-- REF file.createAlias().Desc -->
## .createAlias()

<details><summary>履歴</summary>
| バージョン  | 内容 |
| ------ | -- |
| v17 R5 | 追加 |
</details>

<!--REF #fileClass.createAlias().Syntax -->
**.createAlias**( *destinationFolder* : 4D.Folder ; *aliasName* : Text { ; *aliasType* : Integer } ) : 4D.File<!-- END REF -->

<!--REF #fileClass.createAlias().Params -->
| 参照                | タイプ       |    | 説明                       |
| ----------------- | --------- | -- | ------------------------ |
| destinationFolder | 4D.Folder | -> | エイリアスまたはショートカットの作成先フォルダー |
| aliasName         | テキスト      | -> | エイリアスまたはショートカットの名称       |
| aliasType         | 整数        | -> | エイリアスリンクのタイプ             |
| 戻り値               | 4D.File   | <- | エイリアスまたはショートカットのファイル参照   |
<!-- END REF -->


#### 説明

`.createAlias()` 関数は、*destinationFolder* オブジェクトで指定されたフォルダー内に、*aliasName* が指定する名称で、対象ファイルへの <!-- REF #fileClass.createAlias().Summary -->エイリアス (macOS) またはショートカット (Windows) を作成します<!-- END REF --> 。

Pass the name of the alias or shortcut to create in the *aliasName* parameter.

By default on macOS, the function creates a standard alias. You can also create a symbolic link by using the *aliasType* parameter. The following constants are available:

| 定数                 | 結果 | 説明                         |
| ------------------ | -- | -------------------------- |
| `fk alias link`    | 0  | Alias link (default)       |
| `fk symbolic link` | 1  | Symbolic link (macOS only) |

On Windows, a shortcut (.lnk file) is always created (the *aliasType* parameter is ignored).


**返されるオブジェクト**

A `4D.File` object with the `isAlias` property set to **true**.

#### 例題

You want to create an alias to a file in your database folder:

```4d
 $myFile:=Folder(fk documents folder).file("Archives/ReadMe.txt")
 $aliasFile:=$myFile.createAlias(File("/PACKAGE");"ReadMe")
```
<!-- END REF -->




<!-- INCLUDE document.creationDate.Desc -->




<!-- INCLUDE document.creationTime.Desc -->



<!-- REF file.delete().Desc -->
## .delete()

<details><summary>履歴</summary>
| バージョン  | 内容 |
| ------ | -- |
| v17 R5 | 追加 |
</details>


<!--REF #fileClass.delete().Syntax -->
**.delete( )**<!-- END REF -->


<!-- REF #fileClass.delete().Params -->
| 参照 | タイプ |  | 説明                |
| -- | --- |  | ----------------- |
|    |     |  | このコマンドは引数を必要としません |
<!-- END REF -->


#### 説明

`.delete()` 関数は、 <!-- REF #fileClass.delete().Summary -->ファイルを削除します<!-- END REF -->。

If the file is currently open, an error is generated.

If the file does not exist on disk, the function does nothing (no error is generated).
> **WARNING**: `.delete( )` can delete any file on a disk. This includes documents created with other applications, as well as the applications themselves. `.delete( )` should be used with extreme caution. Deleting a file is a permanent operation and cannot be undone.

#### 例題

You want to delete a specific file in the database folder:

```4d
 $tempo:=File("/PACKAGE/SpecialPrefs/"+Current user+".prefs")
 If($tempo.exists)
    $tempo.delete()
    ALERT("User preference file deleted.")
 End if
``` 
<!-- END REF -->




<!-- INCLUDE document.exists.Desc -->




<!-- INCLUDE document.extension.Desc -->




<!-- INCLUDE document.fullName.Desc -->




<!-- INCLUDE document.getContent().Desc -->




<!-- INCLUDE document.getIcon().Desc -->


<!-- INCLUDE document.getText().Desc -->




<!-- INCLUDE document.hidden.Desc -->



<!-- INCLUDE document.isAlias.Desc -->



<!-- INCLUDE document.isFile.Desc -->




<!-- INCLUDE document.isFolder.Desc -->




<!-- INCLUDE document.isWritable.Desc -->




<!-- INCLUDE document.modificationDate.Desc -->




<!-- INCLUDE document.modificationTime.Desc -->




<!-- REF file.moveTo().Desc -->
## .moveTo()

<details><summary>履歴</summary>
| バージョン  | 内容 |
| ------ | -- |
| v17 R5 | 追加 |
</details>


<!--REF #fileClass.moveTo().Syntax -->
**.moveTo**( *destinationFolder* : 4D.Folder { ; *newName* : Text } ) : 4D.File<!-- END REF -->

<!--REF #fileClass.moveTo().Params -->
| 参照                | タイプ       |    | 説明              |
| ----------------- | --------- | -- | --------------- |
| destinationFolder | 4D.Folder | -> | 宛先フォルダー         |
| newName           | テキスト      | -> | 移動先でのファイルの完全な名称 |
| 戻り値               | 4D.File   | <- | 移動したファイル        |
<!-- END REF -->


#### 説明

`.moveTo()` 関数は、 <!-- REF #fileClass.moveTo().Summary -->`File` オブジェクトを *destinationFolder* が指定する移行先へと移動すると同時に、*newName* を指定した場合は名称も変更します<!-- END REF -->。

The *destinationFolder* must exist on disk, otherwise an error is generated.

By default, the file retains its name when moved. If you want to rename the moved file, pass the new full name in the *newName* parameter. The new name must comply with naming rules (e.g., it must not contain characters such as ":", "/", etc.), otherwise an error is returned.


**返されるオブジェクト**

移動後の `File` オブジェクト。

#### 例題


```4d
$DocFolder:=Folder(fk documents folder)
$myFile:=$DocFolder.file("Current/Infos.txt")
$myFile.moveTo($DocFolder.folder("Archives");"Infos_old.txt")
```
<!-- END REF -->




<!-- INCLUDE document.name.Desc -->



<!-- INCLUDE document.original.Desc -->



<!-- INCLUDE document.parent.Desc -->



<!-- INCLUDE document.path.Desc -->



<!-- INCLUDE document.platformPath.Desc -->



<!-- REF file.rename().Desc --> 
## .rename()

<details><summary>履歴</summary>
| バージョン  | 内容 |
| ------ | -- |
| v17 R5 | 追加 |
</details>


<!--REF #fileClass.rename().Syntax -->
**.rename**( *newName* : Text ) : 4D.File<!-- END REF -->

<!--REF #fileClass.rename().Params -->
| 参照      | タイプ     |    | 説明            |
| ------- | ------- | -- | ------------- |
| newName | テキスト    | -> | ファイルの新しい完全な名称 |
| 戻り値     | 4D.File | <- | 名称変更されたファイル   |
<!-- END REF -->

#### 説明

`.rename()` 関数は、 <!-- REF #fileClass.rename().Summary -->ファイル名を *newName* に指定した名称に変更し、名称変更後の `File` オブジェクトを返します<!-- END REF -->。

The *newName* parameter must comply with naming rules (e.g., it must not contain characters such as ":", "/", etc.), otherwise an error is returned. If a file with the same name already exists, an error is returned.

Note that the function modifies the full name of the file, i.e. if you do not pass an extension in *newName*, the file will have a name without an extension.


**返されるオブジェクト**

名称変更された `File` オブジェクト。

#### 例題

You want to rename "ReadMe.txt" in "ReadMe_new.txt":

```4d
 $toRename:=File("C:\\Documents\\Archives\\ReadMe.txt";fk platform path)
 $newName:=$toRename.rename($toRename.name+"_new"+$toRename.extension)
```
<!-- END REF -->



<!-- REF file.setContent().Desc --> 
## .setContent()

<details><summary>履歴</summary>
| バージョン  | 内容 |
| ------ | -- |
| v17 R5 | 追加 |
</details>


<!--REF #fileClass.setContent().Syntax -->
**.setContent** ( *content* : Blob ) <!-- END REF -->

<!--REF #fileClass.setContent().Params -->
| 参照      | タイプ  |    | 説明            |
| ------- | ---- | -- | ------------- |
| content | BLOB | -> | ファイルの新しいコンテンツ |
<!-- END REF -->


#### 説明

`.setContent( )` 関数は、 <!-- REF #fileClass.setContent().Summary -->*content* 引数の BLOB に保存されているデータを使用して、ファイルの全コンテンツを上書きします<!-- END REF -->。 BLOB についての詳細は、[BLOB](Concepts/dt_blob.md) の章を参照してください。


#### 例題

```4d
 $myFile:=Folder(fk documents folder).file("Archives/data.txt")
 $myFile.setContent([aTable]aBlobField)
```
<!-- END REF -->





<!-- REF file.setText().Desc --> 
## .setText()


<details><summary>履歴</summary>
| バージョン  | 内容 |
| ------ | -- |
| v17 R5 | 追加 |
</details>


<!--REF #fileClass.setText().Syntax -->
**.setText** ( *text* : Text {; *charSetName* : Text { ; *breakMode* : Integer } } )<br>**.setText** ( *text* : Text {; *charSetNum* : Integer { ; *breakMode* : Integer } } ) <!-- END REF -->


<!--REF #fileClass.setText().Params -->
| 参照          | タイプ  |    | 説明                                 |
| ----------- | ---- | -- | ---------------------------------- |
| text        | テキスト | -> | ファイルに保存するテキスト                      |
| charSetName | テキスト | -> | Name of character set              |
| charSetNum  | 整数   | -> | Number of character set            |
| breakMode   | 整数   | -> | 改行の処理モード<!-- END REF -->

|

#### 説明

`.setText()` 関数は、 <!-- REF #fileClass.setText().Summary -->*text* に渡されたテキストをファイルの新しいコンテンツとして書き込みます<!-- END REF -->。

If the file referenced in the `File` object does not exist on the disk, it is created by the function. When the file already exists on the disk, its prior contents are erased, except if it is already open, in which case, its contents are locked and an error is generated.

In *text*, pass the text to write to the file. It can be a literal ("my text"), or a 4D text field or variable.

Optionally, you can designate the character set to be used for writing the contents. You can pass either:

- in *charSetName*, a string containing the standard set name (for example "ISO-8859-1" or ""UTF-8"),
- or in *charSetNum*, the MIBEnum ID (number) of the standard set name.

> For the list of character sets supported by 4D, refer to the description of the `CONVERT FROM TEXT` command.

If a Byte Order Mark (BOM) exists for the character set, 4D inserts it into the file. If you do not specify a character set, by default 4D uses the "UTF-8" character set and a BOM.

In *breakMode*, you can pass a number indicating the processing to apply to end-of-line characters before saving them in the file. The following constants, found in the **System Documents** theme are available:

| 定数                            | 結果 | 説明                                                                                                        |
| ----------------------------- | -- | --------------------------------------------------------------------------------------------------------- |
| `Document unchanged`          | 0  | No processing                                                                                             |
| `Document with native format` | 1  | (デフォルト) 改行は OS のネイティブフォーマットに変換されます。macOS では CR (キャリッジリターン) に、Windows では CRLF (キャリッジリターン＋ラインフィード) に変換されます。 |
| `Document with CRLF`          | 2  | Line breaks are converted to Windows format: CRLF (carriage return + line feed)                           |
| `Document with CR`            | 3  | Line breaks are converted to OS X format: CR (carriage return)                                            |
| `Document with LF`            | 4  | Line breaks are converted to Unix format: LF (line feed)                                                  |

By default, when you omit the *breakMode* parameter, line breaks are processed in native mode (1).



#### 例題

```4d
$myFile:=File("C:\\Documents\\Hello.txt";fk platform path)
$myFile.setText("Hello world")
```
<!-- END REF -->





<!-- INCLUDE document.size.Desc -->



<style> h2 { background: #d9ebff;}</style>
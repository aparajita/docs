---
id: imapTransporterClass
title: IMAPTransporter
---

`IMAPTransporter` クラスを使って、IMAP メールサーバーからメッセージを取得することができます。


### IMAP Transporter オブジェクト

IMAP Transporter オブジェクトは [IMP New transporter](#imap-new-transporter) コマンドによってインスタンス化されます。 これらは、次のプロパティや関数を持ちます:

|                                                                                                                                                                                                                                       |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [<!-- INCLUDE #transporter.acceptUnsecureConnection.Syntax -->](#acceptunsecureconnection)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #transporter.acceptUnsecureConnection.Summary -->|
| [<!-- INCLUDE #imapTransporterClass.addFlags().Syntax -->](#addflags)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #imapTransporterClass.addFlags().Summary -->|
| [<!-- INCLUDE #imapTransporterClass.append().Syntax -->](#append)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #imapTransporterClass.append().Summary -->|
| [<!-- INCLUDE #transporter.authenticationMode.Syntax -->](#authenticationmode)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #transporter.authenticationMode.Summary -->|
| [<!-- INCLUDE #transporter.checkConnection().Syntax -->](#checkconnection)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #transporter.checkConnection().Summary -->|
| [<!-- INCLUDE #imapTransporterClass.checkConnectionDelay.Syntax -->](#checkconnectiondelay)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #imapTransporterClass.checkConnectionDelay.Summary -->|
| [<!-- INCLUDE #transporter.connectionTimeOut.Syntax -->](#connectiontimeout)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #transporter.connectionTimeOut.Summary -->|
| [<!-- INCLUDE #imapTransporterClass.copy().Syntax -->](#copy)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #imapTransporterClass.copy().Summary -->|
| [<!-- INCLUDE #imapTransporterClass.delete().Syntax -->](#delete)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #imapTransporterClass.expunge().Summary -->|
| [<!-- INCLUDE #imapTransporterClass.expunge().Syntax -->](#expunge)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #imapTransporterClass.expunge().Summary -->|
| [<!-- INCLUDE #imapTransporterClass.getBoxInfo().Syntax -->](#getboxinfo)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #imapTransporterClass.getBoxInfo().Summary -->|
| [<!-- INCLUDE #imapTransporterClass.getBoxList().Syntax -->](#getboxlist)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #imapTransporterClass.getBoxList().Summary -->|
| [<!-- INCLUDE #imapTransporterClass.getDelimiter().Syntax -->](#getdelimiter)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #imapTransporterClass.getDelimiter().Summary -->|
| [<!-- INCLUDE #imapTransporterClass.getMail().Syntax -->](#getmail)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #imapTransporterClass.getMail().Summary -->|
| [<!-- INCLUDE #imapTransporterClass.getMails().Syntax -->](#getmails)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #imapTransporterClass.getMails().Summary -->|
| [<!-- INCLUDE #imapTransporterClass.getMIMEAsBlob().Syntax -->](#getmimeasblob)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #imapTransporterClass.getMIMEAsBlob().Summary -->|
| [<!-- INCLUDE #transporter.host.Syntax -->](#host)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #transporter.host.Summary -->|
| [<!-- INCLUDE #transporter.logFile.Syntax -->](#logfile)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #transporter.logFile.Summary -->|
| [<!-- INCLUDE #imapTransporterClass.move().Syntax -->](#move)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #imapTransporterClass.move().Summary -->|
| [<!-- INCLUDE #imapTransporterClass.numToID().Syntax -->](#numToID)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #imapTransporterClass.numToID().Summary -->|
| [<!-- INCLUDE #imapTransporterClass.removeFlags().Syntax -->](#removeflags)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #imapTransporterClass.removeFlags().Summary -->|
| [<!-- INCLUDE #transporter.port.Syntax -->](#port)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #transporter.port.Summary -->|
| [<!-- INCLUDE #imapTransporterClass.searchMails().Syntax -->](#selectbox)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #imapTransporterClass.searchMails().Summary -->|
| [<!-- INCLUDE #imapTransporterClass.selectBox().Syntax -->](#selectbox)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #imapTransporterClass.selectBox().Summary -->|
| [<!-- INCLUDE #transporter.user.Syntax -->](#user)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #transporter.user.Summary -->|



## IMAP New transporter

<details><summary>履歴</summary>
| バージョン  | 内容 |
| ------ | -- |
| v18 R4 | 追加 |
</details>

<!-- REF #_command_.IMAP New transporter.Syntax -->
**IMAP New transporter**( *server* : Object ) : 4D.IMAPTransporter<!-- END REF -->

<!-- REF imapTransporterClass.IMAP New transporter.Params -->
| 参照     | タイプ                |    | 説明                                                  |
| ------ | ------------------ |:--:| --------------------------------------------------- |
| server | オブジェクト             | -> | メールサーバー情報                                           |
| 戻り値    | 4D.IMAPTransporter | <- | [IMAP transporter オブジェクト](#imap-transporter-オブジェクト) |
<!-- END REF -->


#### 説明

`IMAP New transporter` コマンドは、*server* 引数の指定に応じて <!-- REF #_command_.IMAP New transporter.Summary -->新規の IMAP接続を設定します<!-- END REF --> 。戻り値は、新しい *IMAP transporter* オブジェクトです。 返された transporter オブジェクトは、通常メールの受信に使用されます。

*server* 引数として、以下のプロパティを持つオブジェクトを渡します:

| *server*                                                                                                                                                                                                                                                                                       | デフォルト値 (省略時)                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------- |
| [<!-- INCLUDE #transporter.acceptUnsecureConnection.Syntax -->](#acceptunsecureconnection)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #transporter.acceptUnsecureConnection.Summary -->| False                            |
| .**accessTokenOAuth2**: Text<p>OAuth 2 認証の資格情報を表すテキスト文字列。 `authenticationMode` が OAUTH2 の場合のみ使用されます。 `accessTokenOAuth2` が使用されているが `authenticationMode` が省略されていた場合、OAuth2 プロトコルが使用されます (サーバーで許可されていれば)。 *[IMAP transporter](#imap-transporter-オブジェクト)* オブジェクトには返されません。 | なし                               |
| [<!-- INCLUDE #transporter.authenticationMode.Syntax -->](#authenticationmode)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #transporter.authenticationMode.Summary -->| サーバーがサポートするもっともセキュアな認証モードが使用されます |
| [<!-- INCLUDE #imapTransporterClass.checkConnectionDelay.Syntax -->](#checkconnectiondelay)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #imapTransporterClass.checkConnectionDelay.Summary -->| 300                              |
| [<!-- INCLUDE #transporter.connectionTimeOut.Syntax -->](#connectiontimeout)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #transporter.connectionTimeOut.Summary -->| 30                               |
| [<!-- INCLUDE #transporter.host.Syntax -->](#host)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #transporter.host.Summary -->| *必須*                             |
| [<!-- INCLUDE #transporter.logFile.Syntax -->](#logfile)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #transporter.logFile.Summary -->| なし                               |
| .**password** : Text<p>サーバーとの認証のためのユーザーパスワード *[IMAP transporter](#imap-transporter-オブジェクト)* オブジェクトには返されません。                                                                                                                                                            | なし                               |
| [<!-- INCLUDE #transporter.port.Syntax -->](#port)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #transporter.port.Summary -->| 993                              |
| [<!-- INCLUDE #transporter.user.Syntax -->](#user)<p>&nbsp;&nbsp;&nbsp;&nbsp;<!-- INCLUDE #transporter.user.Summary -->| なし                               |
> **警告**: 定義されたタイムアウトが、サーバータイムアウトより短いようにしてください。そうでない場合、クライアントタイムアウトは無意味になります。


#### 戻り値

この関数は、[**IMAP transporter オブジェクト**](#imap-transporter-オブジェクト) を返します。 返されるプロパティはすべて **読み取り専用** です。
> IMAP接続は、transporter オブジェクトが消去された時点で自動的に閉じられます。

#### 例題

```4d
 $server:=New object
 $server.host:="imap.gmail.com" // 必須
 $server.port:=993
 $server.user:="4d@gmail.com"
 $server.password:="XXXXXXXX"
 $server.logFile:="LogTest.txt" // Logsフォルダーに保存するログファイル

 var $transporter : 4D.IMAPTransporter
 $transporter:=IMAP New transporter($server)

 $status:=$transporter.checkConnection()
 If(Not($status.success))
    ALERT("エラーが発生しました: "+$status.statusText)
 End if
```


## 4D.IMAPTransporter.new()


<!-- REF #4D.IMAPTransporter.new().Syntax -->
**4D.IMAPTransporter.new**( *server* : Object ) : 4D.IMAPTransporter<!-- END REF -->

<!-- REF #4D.IMAPTransporter.new().Params -->
| 参照     | タイプ                |    | 説明                                                  |
| ------ | ------------------ |:--:| --------------------------------------------------- |
| server | オブジェクト             | -> | メールサーバー情報                                           |
| 戻り値    | 4D.IMAPTransporter | <- | [IMAP transporter オブジェクト](#imap-transporter-オブジェクト) |
<!-- END REF -->

#### 説明

`4D.IMAPTransporter.new()` 関数は、 <!-- REF #4D.IMAPTransporter.new().Summary -->新規の `4D.IMAPTransporter`型オブジェクトを作成して返します<!-- END REF -->。 この関数の機能は、[`IMAP New transporter`](#imap-new-transporter) コマンドと同一です。
 
<!-- INCLUDE transporter.acceptUnsecureConnection.Desc -->


<!-- REF imapTransporterClass.addFlags().Desc -->
## .addFlags()

<details><summary>履歴</summary>
| バージョン  | 内容 |
| ------ | -- |
| v18 R6 | 追加 |
</details>

<!-- REF #imapTransporterClass.addFlags().Syntax -->
**.addFlags**( *msgIDs* : Collection ; *keywords* :  Object ) : Object<br>**.addFlags**( *msgIDs* : Text ; *keywords* :  Object ) : Object<br>**.addFlags**( *msgIDs* : Longint  ; *keywords* :  Object ) : Object<!-- END REF -->

<!-- REF #imapTransporterClass.addFlags().Params -->
| 参照       | タイプ    |    | 説明                                                                                                        |
| -------- | ------ |:--:| --------------------------------------------------------------------------------------------------------- |
| msgIDs   | コレクション | -> | 文字列のコレクション: メッセージの固有ID (テキスト型)<br> テキスト: メッセージの固有ID<br> 倍長整数 (IMAP all): 選択されたメールボックス内の全メッセージ |
| keywords | オブジェクト | -> | 追加するキーワードフラグ                                                                                              |
| 戻り値      | オブジェクト | <- | addFlags処理のステータス                                                                                          |
<!-- END REF -->


#### 説明

`.addFlags()` 関数は、 <!-- REF #imapTransporterClass.addFlags().Summary -->`msgIDs` のメッセージに対して、`keywords` で指定したフラグを追加します<!-- END REF -->。

`msgIDs` には、以下のいずれかを渡すことができます:

*   指定するメッセージの固有ID を格納した *コレクション*
*   単一のメッセージの固有ID (*テキスト*)
*   以下の定数 (*longint*) を使用することで、選択されているメールボックスの全メッセージを指定することができます:

    | 定数       | 結果 | 説明                        |
    | -------- | -- | ------------------------- |
    | IMAP all | 1  | 選択されたメールボックスの全メッセージを選択します |

`keywords` には、`msgIDs` 引数で指定したメッセージに対して追加するフラグのキーワード値を格納したオブジェクトを渡します。 次のキーワードを渡すことができます:

| 参照        | タイプ | 説明                                |
| --------- | --- | --------------------------------- |
| $draft    | ブール | メッセージに "draft" フラグを追加するには true    |
| $seen     | ブール | メッセージに "seen" フラグを追加するには true     |
| $flagged  | ブール | メッセージに "flagged" フラグを追加するには true  |
| $answered | ブール | メッセージに "answered" フラグを追加するには true |
| $deleted  | ブール | メッセージに "deleted" フラグを追加するには true  |
> * false値は無視されます。
> * キーワードフラグの解釈は、メールクライアントごとに異なる可能性があります。


**返されるオブジェクト**

この関数は、IMAP ステータスを表すオブジェクトを返します:

| プロパティ      |                         | タイプ    | 説明                                                 |
| ---------- | ----------------------- | ------ | -------------------------------------------------- |
| success    |                         | ブール    | 処理が正常に終わった場合には true、それ以外は false                    |
| statusText |                         | テキスト   | IMAPサーバーから返されたステータスメッセージ、または 4Dエラースタック内に返された最後のエラー |
| errors     |                         | コレクション | 4Dエラースタック (IMAPサーバーレスポンスが受信できた場合には返されません)          |
|            | \[].errcode            | 数値     | 4Dエラーコード                                           |
|            | \[].message            | テキスト   | 4Dエラーの詳細                                           |
|            | \[].componentSignature | テキスト   | エラーを返した内部コンポーネントの署名                                |


#### 例題

```4d
var $options;$transporter;$boxInfo;$status : Object

$options:=New object
$options.host:="imap.gmail.com"
$options.port:=993
$options.user:="4d@gmail.com"
$options.password:="xxxxx"

// transporter を作成します
$transporter:=IMAP New transporter($options)

// メールボックスを選択します
$boxInfo:=$transporter.selectBox("INBOX")

// INBOXの全メッセージを既読に設定します
$flags:=New object
$flags["$seen"]:=True
$status:=$transporter.addFlags(IMAP all;$flags)
```

<!-- END REF -->


<!-- REF imapTransporterClass.append().Desc -->
## .append()

<details><summary>履歴</summary>
| バージョン  | 内容 |
| ------ | -- |
| v18 R6 | 追加 |
</details>

<!-- REF #imapTransporterClass.append().Syntax -->
**.append**( *mailObj* : Object ; *destinationBox* : Text ; *options* : Object ) : Object<!-- END REF -->

<!-- REF #imapTransporterClass.append().Params -->
| 参照             | タイプ    |    | 説明                      |
| -------------- | ------ |:--:| ----------------------- |
| mailObj        | オブジェクト | -> | Email オブジェクト            |
| destinationBox | テキスト   | -> | Emailオブジェクトを受信するメールボックス |
| options        | オブジェクト | -> | 文字セット情報を格納したオブジェクト      |
| 戻り値            | オブジェクト | <- | delete処理のステータス          |
<!-- END REF -->


#### 説明

`.append()` 関数は、 <!-- REF #imapTransporterClass.append().Summary -->`destinationBox` に指定したメールボックスに、`mailObj` のメールを追加します<!-- END REF -->。

`mailObj` には、Email オブジェクトを渡します。 メールプロパティに関する包括的な詳細については、[Email オブジェクト](emails.html#email-オブジェクト) を参照ください。  `.append()` 関数は Email オブジェクトの `keywords` 属性内のキーワードタグをサポートします。

任意の `destinationBox` には、`mailObj` が追加されるメールボックスの名前を指定することができます。 省略した場合は、カレントメールボックスが使用されます。

任意の `options` には、メールの特定部分の文字セットやエンコーディングを定義するオブジェクトを渡すことができます。 次のプロパティを含みます:

| プロパティ         | タイプ  | 説明                                                                                |
| ------------- | ---- | --------------------------------------------------------------------------------- |
| headerCharset | テキスト | メールの以下の部分で使用される文字セットとエンコーディング: 件名、添付ファイル名、メール名の属性。 取り得る値: 以下の可能な文字セットテーブルを参照ください。 |
| bodyCharset   | テキスト | メールの HTML およびテキスト本文コンテンツで使用される文字セットとエンコーディング。 取り得る値: 以下の可能な文字セットテーブルを参照ください。      |

使用可能な文字セット:

| 定数                       | 結果                             | 説明                                                                                       |
| ------------------------ | ------------------------------ | ---------------------------------------------------------------------------------------- |
| mail mode ISO2022JP      | US-ASCII_ISO-2022-JP_UTF8_QP | <ul><li>headerCharset: 可能なら US-ASCII 、次に可能なら Japanese (ISO-2022-JP) &amp; Quoted-printable 、それも不可なら UTF-8 &amp; Quoted-printable</li><li>bodyCharset: 可能なら US-ASCII、次に可能なら Japanese (ISO-2022-JP) &amp; 7-bit、それも不可なら UTF-8 &amp; Quoted-printable</li></ul>                                                                |
| mail mode ISO88591       | ISO-8859-1                     | <ul><li>headerCharset: ISO-8859-1 &amp; Quoted-printable</li><li>bodyCharset: ISO-8859-1 &amp; 8-bit</li></ul>                                                                |
| mail mode UTF8           | US-ASCII_UTF8_QP             | headerCharset & bodyCharset: 可能なら US-ASCII、それが不可なら UTF-8 & Quoted-printable (**デフォルト値**) |
| mail mode UTF8 in base64 | US-ASCII_UTF8_B64            | headerCharset & bodyCharset: 可能な場合は US-ASCII、それ以外は UTF-8 & base64                        |


**返されるオブジェクト**

この関数は、IMAP ステータスを表すオブジェクトを返します:

| プロパティ      |                         | タイプ    | 説明                                                 |
| ---------- | ----------------------- | ------ | -------------------------------------------------- |
| success    |                         | ブール    | 処理が正常に終わった場合には true、それ以外は false                    |
| statusText |                         | テキスト   | IMAPサーバーから返されたステータスメッセージ、または 4Dエラースタック内に返された最後のエラー |
| errors     |                         | コレクション | 4Dエラースタック (IMAPサーバーレスポンスが受信できた場合には返されません)          |
|            | \[].errcode            | 数値     | 4Dエラーコード                                           |
|            | \[].message            | テキスト   | 4Dエラーの詳細                                           |
|            | \[].componentSignature | テキスト   | エラーを返した内部コンポーネントの署名                                |


#### 例題

Drafts メールボックスにメールを保存します:

```4d
var $settings; $status; $msg; $imap: Object

$settings:=New object("host"; "domain.com"; "user"; "xxxx"; "password"; "xxxx"; "port"; 993)

$imap:=IMAP New transporter($settings)

$msg:=New object
$msg.from:="xxxx@domain.com"
$msg.subject:="Lorem Ipsum"
$msg.textBody:="Lorem ipsum dolor sit amet, consectetur adipiscing elit."
$msg.keywords:=New object
$msg.keywords["$seen"]:=True // メッセージに既読フラグをつけます
$msg.keywords["$draft"]:=True // // メッセージに下書きフラグをつけます

$status:=$imap.append($msg; "Drafts")
```

<!-- END REF -->









<!-- INCLUDE transporter.authenticationModeIMAP.Desc -->





<!-- INCLUDE transporter.checkConnection().Desc -->



## .checkConnectionDelay

<details><summary>履歴</summary>
| バージョン  | 内容 |
| ------ | -- |
| v18 R4 | 追加 |
</details>

<!-- REF #imapTransporterClass.checkConnectionDelay.Syntax -->
**.checkConnectionDelay** : Integer<!-- END REF -->


#### 説明

`.checkConnectionDelay` 関数は、 <!-- REF #imapTransporterClass.checkConnectionDelay.Summary -->サーバー接続をチェックするまでの最長時間 (秒単位)<!-- END REF -->を格納します。  関数呼び出しの間隔がこの時間を超過する場合、サーバー接続が確認されます。 プロパティが *server* オブジェクトによって設定されていない場合は、デフォルトで 300 という値が使用されます。
> **警告**: 定義されたタイムアウトが、サーバータイムアウトより短いようにしてください。そうでない場合、クライアントタイムアウトは無意味になります。 



<!-- INCLUDE transporter.connectionTimeOut.Desc -->



<!-- REF imapTransporterClass.copy().Desc -->
## .copy()

<details><summary>履歴</summary>
| バージョン  | 内容 |
| ------ | -- |
| v18 R5 | 追加 |
</details>

<!-- REF #imapTransporterClass.copy().Syntax -->
**.copy**( *msgsIDs* : Collection ; *destinationBox* : Text ) : Object<br>**.copy**( *allMsgs* : Integer ; *destinationBox* : Text ) : Object<!-- END REF -->

<!-- REF #imapTransporterClass.copy().Params -->
| 参照             | タイプ    |    | 説明                              |
| -------------- | ------ |:--:| ------------------------------- |
| msgsIDs        | コレクション | -> | メッセージの固有ID のコレクション (テキスト)       |
| allMsgs        | 整数     | -> | `IMAP all`: 選択されたメールボックスの全メッセージ |
| destinationBox | テキスト   | -> | メッセージのコピー先のメールボックス              |
| 戻り値            | オブジェクト | <- | copy処理のステータス                    |
<!-- END REF -->


#### 説明

`.copy()` 関数は、 <!-- REF #imapTransporterClass.copy().Summary -->*msgsIDs* または *allMsgs* で定義されたメッセージを IMAP サーバーの *destinationBox* へとコピーします<!-- END REF -->。

以下のものを渡すことができます:

- *msgsIDs* には、コピーするメッセージの固有ID を格納したコレクション
- *allMsgs* には、選択されているメールボックスの全メッセージをコピーするための定数 (倍長整数型):

*destinationBox* には、メッセージのコピー先メールボックスの名称をテキスト値で渡すことができます。


**返されるオブジェクト**

この関数は、IMAP ステータスを表すオブジェクトを返します:

| プロパティ      |                         | タイプ    | 説明                                                 |
| ---------- | ----------------------- | ------ | -------------------------------------------------- |
| success    |                         | ブール    | 処理が正常に終わった場合には true、それ以外は false                    |
| statusText |                         | テキスト   | IMAPサーバーから返されたステータスメッセージ、または 4Dエラースタック内に返された最後のエラー |
| errors     |                         | コレクション | 4Dエラースタック (IMAPサーバーレスポンスが受信できた場合には返されません)          |
|            | \[].errcode            | 数値     | 4Dエラーコード                                           |
|            | \[].message            | テキスト   | 4Dエラーの詳細                                           |
|            | \[].componentSignature | テキスト   | エラーを返した内部コンポーネントの署名                                |




#### 例題 1

選択されたメッセージをコピーします:


```4d
 var $server;$boxInfo;$status : Object
 var $mailIds : Collection
 var $transporter : 4D.IMAPTransporter

 $server:=New object
 $server.host:="imap.gmail.com" // 必須
 $server.port:=993
 $server.user:="4d@gmail.com"
 $server.password:="XXXXXXXX"

 $transporter:=IMAP New transporter($server)

  // メールボックスを選択します
 $boxInfo:=$transporter.selectBox("inbox")

  //  メッセージの固有ID のコレクションを取得します
 $mailIds:=$transporter.searchMails("subject \"4D new feature:\"")

  // 見つかったメッセージを "documents" メールボックスへコピーします
 $status:=$transporter.copy($mailIds;"documents")
```

#### 例題 2

カレントメールボックスの全メッセージをコピーします:


```4d
 var $server;$boxInfo;$status : Object
 var $transporter : 4D.IMAPTransporter

 $server:=New object
 $server.host:="imap.gmail.com" // 必須
 $server.port:=993
 $server.user:="4d@gmail.com"
 $server.password:="XXXXXXXX"

 $transporter:=IMAP New transporter($server)

  // メールボックスを選択します
 $boxInfo:=$transporter.selectBox("inbox")

  // 全メッセージを "documents" メールボックスへコピーします
 $status:=$transporter.copy(IMAP all;"documents")
```

<!-- END REF -->



<!-- REF imapTransporterClass.delete().Desc -->
## .delete()

<details><summary>履歴</summary>
| バージョン  | 内容 |
| ------ | -- |
| v18 R5 | 追加 |
</details>

<!-- REF #imapTransporterClass.delete().Syntax -->
**.delete**( *msgsIDs* : Collection ) : Object<br>**.delete**( *allMsgs* : Integer ) : Object<!-- END REF -->

<!-- REF #imapTransporterClass.delete().Params -->
| 参照      | タイプ    |    | 説明                              |
| ------- | ------ |:--:| ------------------------------- |
| msgsIDs | コレクション | -> | メッセージの固有ID のコレクション (テキスト)       |
| allMsgs | 整数     | -> | `IMAP all`: 選択されたメールボックスの全メッセージ |
| 戻り値     | オブジェクト | <- | delete処理のステータス                  |
<!-- END REF -->


#### 説明

`.delete()` 関数は、 <!-- REF #imapTransporterClass.delete().Summary -->`msgsIDs` または `allMsgs` が指定するメッセージに対して "削除済み" フラグを設定します<!-- END REF -->。

以下のものを渡すことができます:

- `msgsIDs` には、削除するメッセージの固有ID を格納したコレクション
- `allMsgs` には、選択されているメールボックスの全メッセージを削除するための定数 (倍長整数型):

この関数を実行しても、メールが実際に削除される訳ではありません。 "削除済み" フラグがつけられたメッセージも引き続き [.searchMails()](#searchmails) 関数によって検索可能です。 フラグがつけられたメッセージは、[`.expunge()`](#expunge) を実行したときか、別のメールボックスを選択したとき、あるいは([IMAP New transporter](#imap-new-transporter) で作成された) [transporter オブジェクト](#imap-transporter-オブジェクト) が消去されたときにのみ、IMAPサーバーから削除されます。


**返されるオブジェクト**

この関数は、IMAP ステータスを表すオブジェクトを返します:

| プロパティ      |                         | タイプ    | 説明                                                 |
| ---------- | ----------------------- | ------ | -------------------------------------------------- |
| success    |                         | ブール    | 処理が正常に終わった場合には true、それ以外は false                    |
| statusText |                         | テキスト   | IMAPサーバーから返されたステータスメッセージ、または 4Dエラースタック内に返された最後のエラー |
| errors     |                         | コレクション | 4Dエラースタック (IMAPサーバーレスポンスが受信できた場合には返されません)          |
|            | \[].errcode            | 数値     | 4Dエラーコード                                           |
|            | \[].message            | テキスト   | 4Dエラーの詳細                                           |
|            | \[].componentSignature | テキスト   | エラーを返した内部コンポーネントの署名                                |




#### 例題 1

選択されたメッセージを削除します:


```4d
 var $server;$boxInfo;$status : Object
 var $mailIds : Collection
 var $transporter : 4D.IMAPTransporter

 $server:=New object
 $server.host:="imap.gmail.com" // 必須
 $server.port:=993
 $server.user:="4d@gmail.com"
 $server.password:="XXXXXXXX"

 $transporter:=IMAP New transporter($server)

  // メールボックスを選択します
 $boxInfo:=$transporter.selectBox("Inbox")

  // メッセージの固有ID のコレクションを取得します
 $mailIds:=$transporter.searchMails("subject \"Reports\"")

  // 選択されたメッセージを削除します
 $status:=$transporter.delete($mailIds)
```

#### 例題 2

カレントメールボックスの全メッセージを削除します:


```4d
 var $server;$boxInfo;$status : Object
 var $transporter : 4D.IMAPTransporter

 $server:=New object
 $server.host:="imap.gmail.com" // 必須
 $server.port:=993
 $server.user:="4d@gmail.com"
 $server.password:="XXXXXXXX"

 $transporter:=IMAP New transporter($server)

  //メールボックスを選択します
 $boxInfo:=$transporter.selectBox("Junk Email")

  // カレントメールボックスの全メッセージを削除します
 $status:=$transporter.delete(IMAP all)
```

<!-- END REF -->


<!-- REF imapTransporterClass.expunge().Desc -->
## .expunge()

<details><summary>履歴</summary>
| バージョン  | 内容 |
| ------ | -- |
| v18 R6 | 追加 |
</details>

<!-- REF #imapTransporterClass.expunge().Syntax -->
**.expunge()** : Object<!-- END REF -->

<!-- REF imapTransporterClass.expunge().Params -->
| 参照  | タイプ    |    | 説明              |
| --- | ------ |:--:| --------------- |
| 戻り値 | オブジェクト | <- | expunge処理のステータス |
<!-- END REF -->

#### 説明

`.expunge()` 関数は、 <!-- REF #imapTransporterClass.expunge().Summary -->"deleted" フラグがつけられたメッセージをすべてIMAP メールサーバーから削除します<!-- END REF --> 。"deleted" フラグは [`.delete()`](#delete) または [`.addFlags()`](#addflags) 関数によって設定可能です。

**返されるオブジェクト**

この関数は、IMAP ステータスを表すオブジェクトを返します:

| プロパティ      |                         | タイプ    | 説明                                                 |
| ---------- | ----------------------- | ------ | -------------------------------------------------- |
| success    |                         | ブール    | 処理が正常に終わった場合には true、それ以外は false                    |
| statusText |                         | テキスト   | IMAPサーバーから返されたステータスメッセージ、または 4Dエラースタック内に返された最後のエラー |
| errors     |                         | コレクション | 4Dエラースタック (IMAPサーバーレスポンスが受信できた場合には返されません)          |
|            | \[].errcode            | 数値     | 4Dエラーコード                                           |
|            | \[].message            | テキスト   | 4Dエラーの詳細                                           |
|            | \[].componentSignature | テキスト   | エラーを返した内部コンポーネントの署名                                |


#### 例題

```4d
var $options;$transporter;$boxInfo;$status : Object
var $ids : Collection

$options:=New object
$options.host:="imap.gmail.com"
$options.port:=993
$options.user:="4d@gmail.com"
$options.password:="xxxxx"

// transporter を作成します
$transporter:=IMAP New transporter($options)

// メールボックスを選択します
$boxInfo:=$transporter.selectBox("INBOX")

// INBOX の既読メッセージに削除フラグを立てます
$ids:=$transporter.searchMails("SEEN")
$status:=$transporter.delete($ids)

// "deleted" フラグがついたメッセージをすべて消去します
$status:=$transporter.expunge()
```

<!-- END REF -->


<!-- REF imapTransporterClass.getBoxInfo().Desc -->
## .getBoxInfo()

<details><summary>履歴</summary>
| バージョン  | 内容        |
| ------ | --------- |
| v18 R5 | name が任意に |
| v18 R4 | 追加        |
</details>

<!-- REF #imapTransporterClass.getBoxInfo().Syntax -->
**.getBoxInfo**( { *name* : Text }) : Object<!-- END REF -->

<!-- REF #imapTransporterClass.getBoxInfo().Params -->
| 参照   | タイプ    |    | 説明             |
| ---- | ------ |:--:| -------------- |
| name | テキスト   | -> | メールボックスの名称     |
| 戻り値  | オブジェクト | <- | boxInfo オブジェクト |
<!-- END REF -->


#### 説明

`.getBoxInfo()` 関数は、 <!-- REF #imapTransporterClass.getBoxInfo().Summary -->*name* が指定するメールボックスに対応する `boxInfo` オブジェクトを返します<!-- END REF -->。 この関数は、[`.selectBox()`](#selectbox) と同じ情報を返しますが、カレントメールボックスは変えません。

任意の *name* パラメーターには、アクセスするメールボックスの名称を渡します。 この名称は明確な左から右への階層を表し、特定の区切り文字でレベルを区分けします。 この区切り文字は [`.getDelimiter()`](#getdelimiter) 関数で調べることができます。


**返されるオブジェクト**

返される `boxInfo` オブジェクトには、以下のプロパティが格納されています:

| プロパティ      | タイプ    | 説明                                         |
| ---------- | ------ | ------------------------------------------ |
| name       | text   | メールボックスの名称                                 |
| mailCount  | number | メールボックス内のメッセージの数                           |
| mailRecent | number | (新しいメッセージであることを表す) "recent" フラグがついたメッセージの数 |



#### 例題

```4d
 var $transporter : 4D.IMAPTransporter
 $transporter:=IMAP New transporter($server)

 $info:=$transporter.getBoxInfo("INBOX")
 ALERT("INBOX には "+String($info.mailRecent)+" 件の最近のメールがあります。")
```

<!-- END REF -->




<!-- REF imapTransporterClass.getBoxList().Desc -->
## .getBoxList()

<details><summary>履歴</summary>
| バージョン  | 内容 |
| ------ | -- |
| v18 R4 | 追加 |
</details>

<!-- REF #imapTransporterClass.getBoxList().Syntax -->
**.getBoxList()** : Collection<!-- END REF -->

<!-- REF #imapTransporterClass.getBoxList().Params -->
| 参照  | タイプ    |    | 説明                    |
| --- | ------ |:--:| --------------------- |
| 戻り値 | コレクション | <- | mailbox オブジェクトのコレクション |
<!-- END REF -->


#### 説明

`.getBoxList()` 関数は、 <!-- REF #imapTransporterClass.getBoxList().Summary -->利用可能なメールボックスの情報を mailbox オブジェクトのコレクションとしてを返します<!-- END REF -->。 この関数を使用すると、IMAPメールサーバー上にあるメッセージの一覧をローカルで管理することができるようになります。

#### 戻り値

返されるコレクションの各オブジェクトには、以下のプロパティが格納されています:

| プロパティ            | タイプ     | 説明                                                                          |
| ---------------- | ------- | --------------------------------------------------------------------------- |
| \[].name        | text    | メールボックスの名称                                                                  |
| \[].selectable  | boolean | アクセス権でメールボックスを選択できるかどうかを表します: <ul><li>true - メールボックスは選択可能</li><li>false - メールボックスは選択不可能</li></ul>                     |
| \[].inferior    | boolean | アクセス権でメールボックス内に下の階層レベルを作成できるかどうかを表します: <ul><li>true - 下の階層レベルは作成可能</li><li>false - 下の階層レベルは作成不可能</li></ul>            |
| \[].interesting | boolean | サーバーがメールボックスに “interesting” のマーク付けをしているかどうかを表します: <ul><li>true - メールボックスはサーバーから "interesting" のマーク付けをされています。 たとえば、メールボックスには新着メッセージが入っている場合が考えられます。</li><li>false - メールボックスはサーバーから "interesting" のマーク付けをされていません。</li></ul> |


アカウントにメールボックスが一つもない場合、空のコレクションが返されます。
> * 開いている接続がない場合、`.getBoxList()` は接続を開きます。
> * 接続が指定された時間 (`IMAP New transporter` 参照) 以上に使用されなかった場合には、`.checkConnection( )` 関数が自動的に呼び出されます。


#### 例題


```4d
 var $transporter : 4D.IMAPTransporter
 $transporter:=IMAP New transporter($server)

 $boxList:=$transporter.getBoxList()

 For each($box;$boxList)
    If($box.interesting)
       $split:=Split string($box.name;$transporter.getDelimiter())
       ALERT("新規メールが届いています: "+$split[$split.length-1])
    End if
 End for each
```

<!-- END REF -->



<!-- REF imapTransporterClass.getDelimiter().Desc -->
## .getDelimiter()

<details><summary>履歴</summary>
| バージョン  | 内容 |
| ------ | -- |
| v18 R4 | 追加 |
</details>

<!-- REF #imapTransporterClass.getDelimiter().Syntax -->
**.getDelimiter()** : Text<!-- END REF -->

<!-- REF #imapTransporterClass.getDelimiter().Params -->
| 参照  | タイプ  |    | 説明      |
| --- | ---- |:--:| ------- |
| 戻り値 | テキスト | <- | 階層区切り文字 |
<!-- END REF -->


#### 説明

`.getDelimiter()` 関数は、 <!-- REF #imapTransporterClass.getDelimiter().Summary -->メールボックス名で階層レベルを区切るのに使用される文字を返します<!-- END REF -->。

この区切り文字は以下のように使用することができます:

*   下層レベルのメールボックスを作成する
*   メールボックスの階層内での上層・下層レベルを検索する


#### 戻り値

メールボックス名の区切り文字
> * 開いている接続がない場合、`.getDelimiter()` は接続を開きます。
> * 接続が指定された時間 ([IMAP New transporter](#checkconnectiondelay) 参照) 以上に使用されなかった場合には、[`.checkConnection()`](#checkconnection) 関数が自動的に呼び出されます。



#### 例題


```4d
 var $transporter : 4D.IMAPTransporter
 $transporter:=IMAP New transporter($server)

 $boxList:=$transporter.getBoxList()

 For each($box;$boxList)
    If($box.interesting)
       $split:=Split string($box.name;$transporter.getDelimiter())
       ALERT("新規メールが届いています: "+$split[$split.length-1])
    End if
 End for each
```

<!-- END REF -->



<!-- REF imapTransporterClass.getMail().Desc -->
## .getMail()

<details><summary>履歴</summary>
| バージョン  | 内容 |
| ------ | -- |
| v18 R4 | 追加 |
</details>

<!-- REF #imapTransporterClass.getMail().Syntax -->
**.getMail**( *msgNumber*: Integer { ; *options* : Object } ) : Object<br>**.getMail**( *msgID*: Text { ; *options* : Object } ) : Object<!-- END REF -->

<!-- REF #imapTransporterClass.getMail().Params -->
| 参照        | タイプ    |    | 説明                                               |
| --------- | ------ |:--:| ------------------------------------------------ |
| msgNumber | 整数     | -> | メッセージのシーケンス番号                                    |
| msgID     | テキスト   | -> | メッセージの固有ID                                       |
| options   | オブジェクト | -> | メッセージ管理オプション                                     |
| 戻り値       | オブジェクト | <- | [Email オブジェクト](emailObjectClass.md#email-オブジェクト) |
<!-- END REF -->


#### 説明

`.getMail()` 関数は、 <!-- REF #imapTransporterClass.getMail().Summary -->`IMAP_transporter` が指定するメールボックス内の、*msgNumber* または *msgID* に対応するメールを `Email` オブジェクトとして返します<!-- END REF -->。 この関すを使用すると、メールのコンテンツをローカルで管理できるようになります。

最初の引数として、次のいずれかを渡すことができます:

*   *msgNumber* に、取得するメッセージのシーケンス番号 (*倍長整数*) を渡します。
*   *msgID*に、取得するメッセージの固有ID (*テキスト*) を渡します。

任意の *options* 引数として、メッセージの扱い方を定義する追加のオブジェクトを渡すことができます。 次のプロパティを利用することができます:

| プロパティ      | タイプ     | 説明                                                                         |
| ---------- | ------- | -------------------------------------------------------------------------- |
| updateSeen | boolean | true 時には、メールボックス内でメッセージを "既読" にします。 false 時にはメッセージの状態は変化しません。 デフォルト値: true |
| withBody   | boolean | true を渡すとメッセージ本文を返します。 false 時には、メッセージヘッダーのみが返されます。 デフォルト値: true           |
> * *msgID* 引数が存在しないメッセージを指定した場合、関数はエラーを生成し **Null** を返します。
> * [`.selectBox()`](#selectbox) によって選択されたメールボックスがない場合、エラーが生成されます。
> * 開いている接続がない場合、`.getMail()` は [`.selectBox()`](#selectbox) で最後に指定されたメールボックスへの接続を開きます。


#### 戻り値

`.getMail()` は、以下の IMAP特有のプロパティを持つ [`Email` オブジェクト](emailObjectClass.md#email-オブジェクト)を返します: *id*、*receivedAt*、および *size*。

#### 例題

ID = 1のメッセージを取得します:

```4d
 var $server : Object
 var $info; $mail; $boxInfo : Variant
 var $transporter : 4D.IMAPTransporter

 $server:=New object
 $server.host:="imap.gmail.com" // 必須
 $server.port:=993
 $server.user:="4d@gmail.com"
 $server.password:="XXXXXXXX"

  // transporter を作成します
 $transporter:=IMAP New transporter($server)

  //メールボックスを選択します
 $boxInfo:=$transporter.selectBox("Inbox")

  // ID = 1 の Emailオブジェクトを取得します
 $mail:=$transporter.getMail(1)
```

<!-- END REF -->



<!-- REF imapTransporterClass.getMails().Desc -->
## .getMails()

<details><summary>履歴</summary>
| バージョン  | 内容 |
| ------ | -- |
| v18 R5 | 追加 |
</details>

<!-- REF #imapTransporterClass.getMails().Syntax -->
**.getMails**( *ids* : Collection { ; *options* : Object } ) : Object<br>**.getMails**( *startMsg* : Integer ; *endMsg* : Integer { ; *options* : Object } ) : Object<!-- END REF -->

<!-- REF #imapTransporterClass.getMails().Params -->
| 参照       | タイプ    |    | 説明                                                       |
| -------- | ------ |:--:| -------------------------------------------------------- |
| ids      | コレクション | -> | メッセージID のコレクション                                          |
| startMsg | 整数     | -> | 先頭メッセージのシーケンス番号                                          |
| endMsg   | 整数     | -> | 最後のメッセージのシーケンス番号                                         |
| options  | オブジェクト | -> | メッセージ管理オプション                                             |
| 戻り値      | オブジェクト | <- | 次のコレクションを格納したオブジェクト:<br><ul><li>[Email オブジェクト](emailObjectClass.md#email-オブジェクト) のコレクション</li><li>見つからなかったメッセージの ID または番号のコレクション</li></ul> |
<!-- END REF -->


#### 説明

`.getMails()` 関数は、 <!-- REF #imapTransporterClass.getMails().Summary -->`Email` オブジェクトのコレクションを格納したオブジェクトを返します<!-- END REF -->。

**第一シンタックス:**

***.getMails( ids { ; options } ) -> result***

第一シンタックスを使用すると、メッセージID に基づいてメッセージを取得することができます。

*ids* 引数として、取得するメッセージID のコレクションを渡します。 これらの ID は [`.getMail()`](#getmail) で取得することができます。

任意の *options* 引数を渡すと、返されるメッセージのパートを定義することができます。 利用可能なプロパティについては、以下の **オプション** の表を参照ください。

**第二シンタックス:**

 ***.getMails( startMsg ; endMsg { ; options } ) -> result***

第二シンタックスを使用すると、連続したレンジに基づいてメッセージを取得することができます。 渡される値はメールボックス内でのメッセージの位置を表します。

*startMsg* には、連続したレンジの最初のメッセージの番号に対応する *倍長整数* の値を渡します。 負の値 (*startMsg* <= 0) を渡した場合、メールボックスの最初のメッセージが連続レンジの先頭メッセージとして扱われます。

*endMsg* には、連続レンジに含める最後のメッセージの番号に対応する *倍長整数* の値を渡します。 負の値 (*startMsg* <= 0) を渡した場合、メールボックスの最後のメッセージが連続レンジの最終メッセージとして扱われます。

任意の *options* 引数を渡すと、返されるメッセージのパートを定義することができます。

**オプション**

| プロパティ      | タイプ | 説明                                                                     |
| ---------- | --- | ---------------------------------------------------------------------- |
| updateSeen | ブール | true 時には、指定されたメッセージを "既読" にします。 false 時にはメッセージの状態は変化しません。 デフォルト値: true |
| withBody   | ブール | true を渡すと指定されたメッセージの本文を返します。 false 時には、メッセージヘッダーのみが返されます。 デフォルト値: true |
> * [`.selectBox()`](#selectbox) によって選択されたメールボックスがない場合、エラーが生成されます。
> * 開いている接続がない場合、`.getMails()` は [`.selectBox()`](#selectbox) で最後に指定されたメールボックスへの接続を開きます。


#### 戻り値

`.getMails()` は、以下のコレクションを格納したオブジェクトを返します。


| プロパティ    | タイプ    | 説明                                                                                                 |
| -------- | ------ | -------------------------------------------------------------------------------------------------- |
| list     | コレクション | [`Email`](emailObjectClass.md#email-オブジェクト) オブジェクトのコレクション。 Email オブジェクトが見つからない場合、空のコレクションが返されます。   |
| notFound | コレクション | 使用したシンタックスによって返されるものが異なります:<br><ul><li>第一シンタックス - 指定した ID のうち、存在しなかったメッセージの ID</li><li>第二シンタックス - startMsg と endMsg の間の番号のうち、存在しなかったメッセージの番号</li></ul>すべてのメッセージが見つかった場合には、空のコレクションが返されます。 |


#### 例題

直近の 20件のメールを、"既読" ステータスを変更せずに取得します:

```4d
 var $server,$boxInfo,$result : Object
 var $transporter : 4D.IMAPTransporter 

 $server:=New object
 $server.host:="imap.gmail.com" // 必須
 $server.port:=993
 $server.user:="4d@gmail.com"
 $server.password:="XXXXXXXX"

  //create transporter
 $transporter:=IMAP New transporter($server)

  // メールボックスを選択します
 $boxInfo:=$transporter.selectBox("INBOX")

  If($boxInfo.mailCount>0)
        // 直近20件のメッセージのヘッダーを、"既読" にせずに取得します
    $result:=$transporter.getMails($boxInfo.mailCount-20;$boxInfo.mailCount;\
        New object("withBody";False;"updateSeen";False))
    For each($mail;$result.list)
        // ...
    End for each
 End if
```

<!-- END REF -->



<!-- REF imapTransporterClass.getMIMEAsBlob().Desc -->
## .getMIMEAsBlob()

<details><summary>履歴</summary>
| バージョン  | 内容 |
| ------ | -- |
| v18 R4 | 追加 |
</details>

<!-- REF #imapTransporterClass.getMIMEAsBlob().Syntax -->
**.getMIMEAsBlob**( *msgNumber* : Integer { ; *updateSeen* : Boolean } ) : Blob<br>**.getMIMEAsBlob**( *msgID* : Text { ; *updateSeen* : Boolean } ) : Blob<!-- END REF -->


<!-- REF #imapTransporterClass.getMIMEAsBlob().Params -->
| 参照         | タイプ  |    | 説明                                                            |
| ---------- | ---- |:--:| ------------------------------------------------------------- |
| msgNumber  | 整数   | -> | メッセージのシーケンス番号                                                 |
| msgID      | テキスト | -> | メッセージの固有ID                                                    |
| updateSeen | ブール  | -> | true 時には、メールボックス内でメッセージを "既読" にします。 false 時にはメッセージの状態は変化しません。 |
| 戻り値        | BLOB | <- | メールサーバーから返された MIME文字列の BLOB                                   |
<!-- END REF -->



#### 説明

`.getMIMEAsBlob()` 関数は、 <!-- REF #imapTransporterClass.getMIMEAsBlob().Summary -->`IMAP_transporter` が指定するメールボックス内の、*msgNumber* または *msgID* に対応するメッセージの MIMEコンテンツを格納した BLOB を返します<!-- END REF -->。

最初の引数として、次のいずれかを渡すことができます:

*   *msgNumber* に、取得するメッセージのシーケンス番号 (*倍長整数*) を渡します。
*   *msgID*に、取得するメッセージの固有ID (*テキスト*) を渡します。

任意の *updateSeen* 引数を渡すと、メールボックス内でメッセージが "既読" とマークされるかどうかを指定します。 以下のものを渡すことができます:

*   **True** - メッセージは "既読" とマークされます (このメッセージが読まれたことを表します)
*   **False** - メッセージの "既読" ステータスは変化しません。
> * *msgNumber* または *msgID* 引数が存在しないメッセージを指定した場合、関数は空の BLOB を返します。
> * [`.selectBox()`](#selectbox) によって選択されたメールボックスがない場合、エラーが生成されます。
> * 開いている接続がない場合、`.getMIMEAsBlob()` は `.selectBox()` で最後に指定されたメールボックスへの接続を開きます。


#### 戻り値

`.getMIMEAsBlob()` は `BLOB` を返します。この BLOB はデータベースにアーカイブしたり、`MAIL Convert from MIME` コマンドを使用して [`Email` オブジェクト](emailObjectClass.md#email-object) へと変換したりすることができます。


#### 例題


```4d
 var $server : Object
 var $boxInfo : Variant
 var $blob : Blob
 var $transporter : 4D.IMAPTransporter

 $server:=New object
 $server.host:="imap.gmail.com"
 $server.port:=993
 $server.user:="4d@gmail.com"
 $server.password:="XXXXXXXX"

  // transporter を作成します
 $transporter:=IMAP New transporter($server)

  // メールボックスを選択します
 $boxInfo:=$transporter.selectBox("Inbox")

  // BLOB を取得します
 $blob:=$transporter.getMIMEAsBlob(1)
```

<!-- END REF -->



<!-- INCLUDE transporter.host.Desc -->




<!-- INCLUDE transporter.logFile.Desc -->



<!-- REF imapTransporterClass.move().Desc -->
## .move()

<details><summary>履歴</summary>
| バージョン  | 内容 |
| ------ | -- |
| v18 R5 | 追加 |
</details>

<!-- REF #imapTransporterClass.move().Syntax -->
**.move**( *msgsIDs* : Collection ; *destinationBox* : Text ) : Object<br>**.move**( *allMsgs* : Integer ; *destinationBox* : Text ) : Object<!-- END REF -->

<!-- REF #imapTransporterClass.move().Params -->
| 参照             | タイプ    |    | 説明                              |
| -------------- | ------ |:--:| ------------------------------- |
| msgsIDs        | コレクション | -> | メッセージの固有ID のコレクション (テキスト)       |
| allMsgs        | 整数     | -> | `IMAP all`: 選択されたメールボックスの全メッセージ |
| destinationBox | テキスト   | -> | メッセージの移動先のメールボックス               |
| 戻り値            | オブジェクト | <- | move処理のステータス                    |
<!-- END REF -->


#### 説明

`.move()` 関数は、 <!-- REF #imapTransporterClass.move().Summary -->*msgsIDs* または *allMsgs* で定義されたメッセージを IMAP サーバーの *destinationBox* へと移動します<!-- END REF -->。

以下のものを渡すことができます:

- *msgsIDs* には、移動するメッセージの固有ID を格納したコレクション
- *allMsgs* には、選択されているメールボックスの全メッセージを移動するための定数 (倍長整数型):

*destinationBox* には、メッセージの移動先メールボックスの名称をテキスト値で渡すことができます。

> RFC [8474](https://tools.ietf.org/html/rfc8474) に準拠している IMAPサーバーでのみ、この関数はサポートされます。


**返されるオブジェクト**

この関数は、IMAP ステータスを表すオブジェクトを返します:

| プロパティ      |                         | タイプ    | 説明                                                 |
| ---------- | ----------------------- | ------ | -------------------------------------------------- |
| success    |                         | ブール    | 処理が正常に終わった場合には true、それ以外は false                    |
| statusText |                         | テキスト   | IMAPサーバーから返されたステータスメッセージ、または 4Dエラースタック内に返された最後のエラー |
| errors     |                         | コレクション | 4Dエラースタック (IMAPサーバーレスポンスが受信できた場合には返されません)          |
|            | \[].errcode            | 数値     | 4Dエラーコード                                           |
|            | \[].message            | テキスト   | 4Dエラーの詳細                                           |
|            | \[].componentSignature | テキスト   | エラーを返した内部コンポーネントの署名                                |




#### 例題 1

選択されたメッセージを移動します:

```4d
 var $server;$boxInfo;$status : Object
 var $mailIds : Collection
 var $transporter : 4D.IMAPTransporter

 $server:=New object
 $server.host:="imap.gmail.com" // 必須
 $server.port:=993
 $server.user:="4d@gmail.com"
 $server.password:="XXXXXXXX"

 $transporter:=IMAP New transporter($server)

  // メールボックスを選択します
 $boxInfo:=$transporter.selectBox("inbox")

  // メッセージの固有IDのコレクションを取得します
 $mailIds:=$transporter.searchMails("subject \"4D new feature:\"")

  // カレントメールボックス内で見つかったメッセージを "documents" メールボックスに移動します
 $status:=$transporter.move($mailIds;"documents")
```

#### 例題 2

カレントメールボックスの全メッセージを移動します:


```4d
 var $server;$boxInfo;$status : Object
 var $transporter : 4D.IMAPTransporter

 $server:=New object
 $server.host:="imap.gmail.com" // 必須
 $server.port:=993
 $server.user:="4d@gmail.com"
 $server.password:="XXXXXXXX"

 $transporter:=IMAP New transporter($server)

  // メールボックスを選択します
 $boxInfo:=$transporter.selectBox("inbox")

  // カレントメールボックスの全メッセージを "documents" メールボックスに移動します
 $status:=$transporter.move(IMAP all;"documents")
```

<!-- END REF -->



<!-- REF imapTransporterClass.numToID().Desc -->
## .numToID()

<details><summary>履歴</summary>
| バージョン  | 内容 |
| ------ | -- |
| v18 R5 | 追加 |
</details>

<!-- REF #imapTransporterClass.numToID().Syntax -->
**.numToID**( *startMsg* : Integer ; *endMsg* : Integer ) : Collection<!-- END REF -->

<!-- REF #imapTransporterClass.numToID().Params -->
| 参照       | タイプ    |    | 説明               |
| -------- | ------ |:--:| ---------------- |
| startMsg | 整数     | -> | 先頭メッセージのシーケンス番号  |
| endMsg   | 整数     | -> | 最後のメッセージのシーケンス番号 |
| 戻り値      | コレクション | <- | 固有ID のコレクション     |
<!-- END REF -->


#### 説明

`.numToID()` 関数は、現在選択されているメールボックスにおいて、 <!-- REF #imapTransporterClass.numToID().Summary -->*startMsg* および *endMsg* で指定された連続した範囲のメッセージのシーケンス番号を IMAP固有IDへと変換します<!-- END REF --> 。

*startMsg* には、連続したレンジの最初のメッセージの番号に対応する *倍長整数* の値を渡します。 負の値 (*startMsg* <= 0) を渡した場合、メールボックスの最初のメッセージが連続レンジの先頭メッセージとして扱われます。

*endMsg* には、連続レンジに含める最後のメッセージの番号に対応する *倍長整数* の値を渡します。 負の値 (*startMsg* <= 0) を渡した場合、メールボックスの最後のメッセージが連続レンジの最終メッセージとして扱われます。


#### 戻り値

メソッドは文字列 (固有ID) のコレクションを返します。

#### 例題


```4d
 var $transporter : 4D.IMAPTransporter
 var $server;$boxInfo;$status : Object
 var $mailIds : Collection

 $server:=New object
 $server.host:="imap.gmail.com" // 必須
 $server.port:=993
 $server.user:="4d@gmail.com"
 $server.password:="XXXXXXXX"

 $transporter:=IMAP New transporter($server)

  // メールボックスを選択します
 $boxInfo:=$transporter.selectBox("inbox")

  // 最も古い 5通のメッセージID を取得します
 $mailIds:=$transporter.numToID(($boxInfo.mailCount-5);$boxInfo.mailCount)

  // カレントメールボックスからメッセージを削除します
 $status:=$transporter.delete($mailIds)
```

<!-- END REF -->


<!-- REF imapTransporterClass.removeFlags().Desc -->
## .removeFlags()

<details><summary>履歴</summary>
| バージョン  | 内容 |
| ------ | -- |
| v18 R6 | 追加 |
</details>

<!-- REF #imapTransporterClass.removeFlags().Syntax -->
**.removeFlags**( *msgIDs* : Collection ; *keywords* :  Object ) : Object<br>**.removeFlags**( *msgIDs* : Text ; *keywords* :  Object ) : Object<br>**.removeFlags**( *msgIDs* : Longint ; *keywords* :  Object ) : Object<!-- END REF -->

<!-- REF #imapTransporterClass.removeFlags().Params -->
| 参照       | タイプ    |    | 説明                                                                                                        |
| -------- | ------ |:--:| --------------------------------------------------------------------------------------------------------- |
| msgIDs   | コレクション | -> | 文字列のコレクション: メッセージの固有ID (テキスト型)<br> テキスト: メッセージの固有ID<br> 倍長整数 (IMAP all): 選択されたメールボックス内の全メッセージ |
| keywords | オブジェクト | -> | 削除するキーワードフラグ                                                                                              |
| 戻り値      | オブジェクト | <- | removeFlags処理のステータス                                                                                       |
<!-- END REF -->


#### 説明

`.removeFlags()` 関数は、 <!-- REF #imapTransporterClass.removeFlags().Summary -->`msgIDs` のメッセージに対して、`keywords` で指定したフラグを削除します<!-- END REF -->。

`msgIDs` には、以下のいずれかを渡すことができます:

*   指定するメッセージの固有ID を格納した *コレクション*
*   単一のメッセージの固有ID (*テキスト*)
*   以下の定数 (*longint*) を使用することで、選択されているメールボックスの全メッセージを指定することができます:

    | 定数       | 結果 | 説明                        |
    | -------- | -- | ------------------------- |
    | IMAP all | 1  | 選択されたメールボックスの全メッセージを選択します |

`keywords` には、`msgIDs` 引数で指定したメッセージから削除するフラグのキーワード値を格納したオブジェクトを渡します。 次のキーワードを渡すことができます:

| 参照        | タイプ | 説明                                |
| --------- | --- | --------------------------------- |
| $draft    | ブール | メッセージの "draft" フラグを削除するには true    |
| $seen     | ブール | メッセージの "seen" フラグを削除するには true     |
| $flagged  | ブール | メッセージの "flagged" フラグを削除するには true  |
| $answered | ブール | メッセージの "answered" フラグを削除するには true |
| $deleted  | ブール | メッセージの "deleted" フラグを削除するには true  |

false値は無視されます。


**返されるオブジェクト**

この関数は、IMAP ステータスを表すオブジェクトを返します:

| プロパティ      |                         | タイプ    | 説明                                                 |
| ---------- | ----------------------- | ------ | -------------------------------------------------- |
| success    |                         | ブール    | 処理が正常に終わった場合には true、それ以外は false                    |
| statusText |                         | テキスト   | IMAPサーバーから返されたステータスメッセージ、または 4Dエラースタック内に返された最後のエラー |
| errors     |                         | コレクション | 4Dエラースタック (IMAPサーバーレスポンスが受信できた場合には返されません)          |
|            | \[].errcode            | 数値     | 4Dエラーコード                                           |
|            | \[].message            | テキスト   | 4Dエラーの詳細                                           |
|            | \[].componentSignature | テキスト   | エラーを返した内部コンポーネントの署名                                |


#### 例題

```4d
var $options;$transporter;$boxInfo;$status : Object

$options:=New object
$options.host:="imap.gmail.com"
$options.port:=993
$options.user:="4d@gmail.com"
$options.password:="xxxxx"

// transporter を作成します
$transporter:=IMAP New transporter($options)

// メールボックスを選択します
$boxInfo:=$transporter.selectBox("INBOX")

// INBOX の全メッセージを未読にします
$flags:=New object
$flags["$seen"]:=True
$status:=$transporter.removeFlags(IMAP all;$flags)
```

<!-- END REF -->



<!-- INCLUDE transporter.port.Desc -->


<!-- REF imapTransporterClass.searchMails().Desc -->
## .searchMails()

<details><summary>履歴</summary>
| バージョン  | 内容 |
| ------ | -- |
| v18 R5 | 追加 |
</details>

<!-- REF #imapTransporterClass.searchMails().Syntax -->
**.searchMails**( *searchCriteria* : Text ) : Collection<!-- END REF -->

<!-- REF #imapTransporterClass.searchMails().Params -->
| 参照             | タイプ    |    | 説明             |
| -------------- | ------ |:--:| -------------- |
| searchCriteria | テキスト   | -> | 検索条件           |
| 戻り値            | コレクション | <- | メッセージ番号のコレクション |
<!-- END REF -->


#### 説明

> この関数は、[IMAP プロトコル](https://en.wikipedia.org/wiki/Internet_Message_Access_Protocol) の仕様に基づいています。

`.searchMails()` 関数は、 <!-- REF #imapTransporterClass.searchMails().Summary -->カレントメールボックスにおいて *searchCriteria* の検索条件に合致するメッセージを検索します<!-- END REF -->。 *searchCriteria* 引数には、一つ以上の検索キーを格納します。

*searchCriteria* はテキスト型の引数で、一つ以上の検索キー (詳細は後述の [利用可能な検索キー](#利用可能な検索キー) 参照) を格納し、検索する値を渡します (渡さない場合もあります)。 検索キーは単一または複数の項目からなります。 たとえば:

```
SearchKey1 = FLAGGED
SearchKey2 = NOT FLAGGED
SearchKey3 = FLAGGED DRAFT
```

> 文字の大小は通常区別されません。

- *searchCriteria* 引数が null 文字列の場合、検索は "すべてを選択" と同等です。
- 引数が複数の検索キーを格納している場合、それらすべてに合致する和集合 (AND) が検索結果になります。

```
searchCriteria = FLAGGED FROM "SMITH"
```
... この検索結果は \Flagged フラグが設定されていて、かつ Smith から送られたメッセージをすべて返します。
- **OR** および **NOT** 演算子を、以下のように使用することができます:

```
searchCriteria = OR SEEN FLAGGED
```
... \Seen フラグが設定されている、あるいは \Flagged フラグが設定されているメッセージをすべて返します。

```
searchCriteria = NOT SEEN
```
... \Seen フラグが設定されていないメッセージをすべて返します。

```
searchCriteria = HEADER CONTENT-TYPE "MIXED" NOT HEADER CONTENT-TYPE "TEXT"...
```
... content-type ヘッダーが "Mixed" を格納しているもののうち、"Text" は格納していないメッセージを返します。

```
searchCriteria = HEADER CONTENT-TYPE "E" NOT SUBJECT "o" NOT HEADER CONTENT-TYPE "MIXED"
```
... content-type ヘッダーが "e" を格納しているもののうち、Subject ヘッダーが "o"を格納していないもの、かつ content-type ヘッダーが"Mixed" でないメッセージを返します。

最後の 2例については、最初の検索キーリストのカッコを取り除いてしまうと検索結果が異なることに注意してください。

- *searchCriteria* 引数には任意の \[CHARSET] 指定を含めることができます。 これは "CHARSET" という単語の後に実際の文字コード \[CHARSET] (US ASCII, ISO-8859 など) が続きます。 これは *searchCriteria* 文字列の文字コードを指定します。 そのため、\[CHARSET] 指定を使用する場合には *searchCriteria* 文字列を指定された文字コードへと変換する必要があります (詳細については `CONVERT FROM TEXT` または `Convert to text` コマンドを参照ください)。 デフォルトでは、searchCriteria 引数に拡張された文字列が含まれていた場合には4D はそれを Quotable Printable へとエンコードします。

```
searchCriteria = CHARSET "ISO-8859" BODY "Help"
```
... これは、検索条件に iso-8859 文字コードを使用し、必要に応じてサーバーは検索前に検索条件をこの文字コードに変換しなければならない、ということを意味します。


#### 検索する値の型について

検索キーによっては、次の型の検索値が必要となる場合があります:

- **日付値の検索キー**: date は日付を指定する文字列で、以下のようにフォーマットされている必要があります: *date-day+"-"+date-month+"-"+date-year*。ここでの date-day は日付の数値 (最大2桁) を意味し、date-month は月の名前 (Jan/Feb/Mar/Apr/May/Jun/Jul/Aug/Sep/Oct/Dec) を意味し、date-year は年 (4桁) を意味します。 例: `searchCriteria = SENTBEFORE 1-Feb-2000` (日付は特殊文字を含まないため、通常は引用符でくくる必要はありません)

- **文字列値の検索キー**: string はあらゆる文字列を含みうるため、引用符でくくらなければなりません。 文字列が特殊文字 (スペース文字など) をまったく含まない場合には、引用符で括る必要はありません。 このような文字列を引用符でくくることは、渡した文字列値が正確に解釈されることを保証します。 例: `searchCriteria = FROM "SMITH"`<br /> 文字列を使用するすべての検索キーに対し、フィールドの文字列に検索キーが含まれる場合には検索に合致したとみなされます。 合致は文字の大小を区別しません。

- **field-name 値の検索キー**: field-name はヘッダーフィールドの名称です。 例: `searchCriteria = HEADER CONTENT-TYPE "MIXED"`

- **フラグ値の検索キー**: flag は一つ以上のキーワードを (標準のフラグを含めて) 受け入れます。複数指定する場合にはスペースで区切ります。 例: `searchCriteria = KEYWORD \Flagged \Draft`

- **メッセージセット値の検索キー**: 複数のメッセージを識別します。 メッセージシーケンス番号は、1 から始まりメールボックスのメッセージの総数までの連続した番号です。 個別の番号はカンマで区切ります。コロンは、その前後の番号を含めた連続した番号を指定します。 例:<br /> `2,4:7,9,12:*` は、15通あるメールボックスの場合に `2,4,5,6,7,9,12,13,14,15` を指定します。 `searchCriteria = 1:5 ANSWERED` は、メッセージシーケンス番号 1 から 5番のメッセージのうち、\Answered フラグが設定されているメッセージを検索します。 `searchCriteria= 2,4 ANSWERED` は、メッセージセレクション (メッセージ番号 2番と4番) のうち、\Answered フラグが設定されているメッセージを検索します。


#### 利用可能な検索キー

**ALL**: メールボックスの全メッセージ  
**ANSWERED**: \Answered フラグが設定されたメッセージ  
**UNANSWERED**: \Answered フラグが設定されていないメッセージ  
**DELETED**: \Deleted フラグが設定されたメッセージ  
**UNDELETED**: \Deleted フラグが設定されていないメッセージ  
**DRAFT**: \Draft フラグが設定されているメッセージ  
**UNDRAFT**: \Draft フラグが設定されていないメッセージ  
**FLAGGED**: \Flagged フラグが設定されているメッセージ  
**UNFLAGGED**: \Flagged フラグが設定されていないメッセージ  
**RECENT**: \Recent フラグが設定されているメッセージ  
**OLD**: \Recent フラグが設定されていないメッセージ  
**SEEN**: \Seen フラグが設定されているメッセージ  
**UNSEEN**: \Seen フラグが設定されていないメッセージ  
**NEW**: \Recent フラグが設定されているが \Seen フラグが設定されていないメッセージ。 これは機能的には “(RECENT UNSEEN)” と同じです。  
**KEYWORD** <flag>: 指定されたキーワードが設定されているメッセージ  
**UNKEYWORD** <flag>: 指定されたキーワードが設定されていないメッセージ  
**BEFORE** <date>: 内部の日付が指定日より前のメッセージ  
**ON** <date>: 内部の日付が指定日に合致するメッセージ  
**SINCE** <date>: 内部の日付が指定日より後のメッセージ  
**SENTBEFORE** <date>: 日付ヘッダーが指定日より前のメッセージ  
**SENTON** <date>: 日付ヘッダーが指定日に合致するメッセージ  
**SENTSINCE** <date>: 日付ヘッダーが指定日以降のメッセージ  
**TO** <string>: TO ヘッダーに指定文字列が含まれているメッセージ  
**FROM** <string>: FROM ヘッダーに指定文字列が含まれているメッセージ  
**CC** <string>: CC ヘッダーに指定文字列が含まれているメッセージ  
**BCC** <string>: BCC ヘッダーに指定文字列が含まれているメッセージ  
**SUBJECT** <string>: 件名ヘッダーに指定文字列が含まれているメッセージ  
**BODY** <string>: メッセージ本文に指定文字列が含まれているメッセージ  
**TEXT** <string>: ヘッダーまたはメッセージ本文に指定文字列が含まれているメッセージ  
**HEADER** <field-name> <string>: 指定フィールド名のヘッダーを持ち、そのフィールド内に指定文字列が含まれているメッセージ  
**UID** <message UID>: 指定された固有識別子に対応する固有識別子を持つメッセージ  
**LARGER** <n>: 指定バイト数以上のサイズを持つメッセージ  
**SMALLER** <n>: 指定バイト数以下のサイズを持つメッセージ  
**NOT** <search-key>: 指定検索キーに合致しないメッセージ  
**OR** <search-key1> <search-key2>: いずれかの検索キーに合致するメッセージ  


<!-- END REF -->


<!-- REF imapTransporterClass.selectBox().Desc -->
## .selectBox()

<details><summary>履歴</summary>
| バージョン  | 内容 |
| ------ | -- |
| v18 R4 | 追加 |
</details>

<!-- REF #imapTransporterClass.selectBox().Syntax -->
**.selectBox**( *name* : Text { ; *state* : Integer } ) : Object<!-- END REF -->

<!-- REF #imapTransporterClass.selectBox().Params -->
| 参照    | タイプ    |    | 説明             |
| ----- | ------ |:--:| -------------- |
| name  | テキスト   | -> | メールボックスの名称     |
| state | 整数     | -> | メールボックスのアクセス状態 |
| 戻り値   | オブジェクト | <- | boxInfo オブジェクト |
<!-- END REF -->


#### 説明

`.selectBox()` 関数は、 <!-- REF #imapTransporterClass.selectBox().Summary -->*name* に指定したメールボックスをカレントメールボックスとして選択します<!-- END REF -->。 この関数を使用するとメールボックスに関する情報を取得することができます。
> カレントメールボックスを変更せずに、メールボックスから情報を取得するには、[`.getBoxInfo()`](#getboxinfo) を使用します。

*name* には、アクセスするメールボックスの名前を渡します。 この名称は明確な左から右への階層を表し、特定の区切り文字でレベルを区分けします。 この区切り文字は [`.getDelimiter()`](#getdelimiter) 関数で調べることができます。

任意の *state* 引数を渡すと、メールボックスへのアクセスタイプを定義できます。 取りうる値は以下の通りです:

| 定数                    | 結果 | 説明                                                                         |
| --------------------- | -- | -------------------------------------------------------------------------- |
| IMAP read only state  | 1  | 選択されたメールボックスは読み取り専用権限でアクセスされます。 新しいメッセージを表す "新着" フラグはそのまま変化しません。           |
| IMAP read write state | 0  | 選択されたメールボックスは読み書き可能権限でアクセスされます。 メッセージは "既読" と判断され、"新着" フラグは失われます。 (デフォルト値) |
> * name 引数が存在しないメールボックスを指定した場合、関数はエラーを生成し **Null** を返します。
> * 開いている接続がない場合、`.selectBox()` は接続を開きます。
> * 接続が指定された時間 (`IMAP New transporter` 参照) 以上に使用されなかった場合には、[`.checkConnection()`](#checkconnection) 関数が自動的に呼び出されます。

**返されるオブジェクト**

返される `boxInfo` オブジェクトには、以下のプロパティが格納されています:

| プロパティ      | タイプ    | 説明                      |
| ---------- | ------ | ----------------------- |
| name       | テキスト   | メールボックスの名称              |
| mailCount  | number | メールボックス内のメッセージの数        |
| mailRecent | number | "recent" フラグがついたメッセージの数 |


#### 例題


```4d
 var $server; $boxinfo : Object
 $server:=New object
 $server.host:="imap.gmail.com" // 必須
 $server.user:="4d@gmail.com"
 $server.password:="XXXXXXXX"

 var $transporter : 4D.IMAPTransporter
 $transporter:=IMAP New transporter($server)
 $boxInfo:=$transporter.selectBox("INBOX")
```

<!-- END REF -->




<!-- INCLUDE transporter.user.Desc -->




<style> h2 { background: #d9ebff;}</style>








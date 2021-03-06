---
id: preemptiveWeb
title: プリエンプティブWebプロセスの使用
---


4D Webサーバーを使って、コンパイル済みアプリケーションでプリエンプティブWebプロセスを使用することによって、マルチコアコンピューターの利点を最大限引き出すことができます。 4D変換タグや Webデータベースメソッドを含めた Web関連コードを、可能な限り多くのコアで同時に実行するよう設定することが可能です。

4D のプリエンプティブプロセスについての詳細は、*ランゲージリファレンス* の *プリエンプティブ4Dプロセス* の章を参照ください。

## Webプロセスにおけるプリエンプティブモードの使用可能状況

Webプロセスに対してプリエンプティブモードの使用が可能なのは、以下のコンテキストの場合に限られます:

*   4D Server あるいはローカルモードの 4D を使用している (リモートモードでの 4D はプリエンプティブモードをサポートしていません)

*   コンパイル済みデータベースを使用している

*   データベースの **プリエンプティブプロセスを使用** 設定がチェックされている(以下参照)

*   Web関連のデータベースメソッドとプロジェクトメソッドは、すべてスレッドセーフであると 4Dコンパイラから確認済みである

上記の要項がどれか一つでも欠けていた場合、Webサーバーはコオペラティブプロセスを使用します。

## Webサーバーにおいてプリエンプティブモードを有効化する

アプリケーションの Webサーバーコードにおいてプリエンプティブモードを有効化するには、データベース設定ダイアログボックスの "Web / オプション (I)" ページの、**プリエンプティブプロセスを使用** にチェックをつける必要があります:

![](assets/en/WebServer/preemptive.png)

このオプションがチェックされているとき、4Dコンパイラは Web関連のコードそれぞれのスレッドセーフプロパティを自動的に評価し (以下参照)、違反があった場合にはエラーを返します。
> このオプションは Webサービスプロセス (サーバーあるいはクライアント) には適用されません。 Webサービスプロセスのプリエンプティブモードは、メソッドレベルでサポートされています。公開済みの SOAPサーバーメソッド (*4Dで Web サービスを公開する* 参照) あるいはプロキシクライアントメソッド (*4Dから Web サービスへサブスクライブする* 参照) の "プリエンプティブプロセスで実行可能" プロパティをチェックし、メソッドがコンパイラーによってスレッドセーフと確認されるようにします。

## スレッドセーフなWebサーバーコードの書き方

Webプロセスをプリエンプティモードで実行するには、Webサーバーで実行されるすべての 4Dコードがスレッドセーフでなければなりません。 ストラクチャー設定ダイアログボックスにおいて **プリエンプティブプロセスを使用** オプションがチェックされている場合、アプリケーションの以下の部分が 4Dコンパイラーによって自動的に評価されます:

*   すべての Web関連データベースメソッド:
    *   [`On Web Authentication`](authentication.md#on-web-authentication)
    *   [`On Web Connection`](httpRequests.md#on-web-connection)
    *   [`On REST Authentication`](REST/configuration.md#on-rest-authentication-データベースメソッドを使用する)
    *   [`On Mobile App Authentication`](https://doc.4d.com/4Dv18/4D/18.4/On-Mobile-App-Authentication-database-method.301-5233127.en.html)

*   `compiler_web` プロジェクトメソッド (実際の "実行モード" プロパティに関わらず評価されます)

*   Webコンテキストにおいて `PROCESS 4D TAGS` コマンドによって処理される基本的にすべてのコード (.shtmlページを通して実行されるものなど)

*   "公開オプション: 4DタグとURL (`4DACTION`)..." 属性が有効なプロジェクトメソッド。

*   "RESTリソースとして公開" 属性が有効なテーブルのトリガー

*   REST経由で利用可能なプロジェクトメソッド ("公開オプション: RESTサーバー" プロパティがチェックされているメソッド)

これらそれぞれのメソッドとコードの部分について、スレッドセーフのルールが遵守されているかをコンパイラーがチェックし、問題があった場合にはエラーを返します。 スレッドセーフルールについての詳細は、*プロセス* の章の *スレッドセーフなメソッドの書き方* の段落を参照ください。

## 4D Webコードのスレッドセーフティ

Web関連のほとんどの 4Dコマンドや関数、データベースメソッド、そして URL がスレッドセーフとなり、プリエンプティモードで使用できます。

### 4Dコマンドとデータベースメソッド

すべての Web関連コマンドはスレッドセーフです:

*   *Webサーバー* テーマの全コマンド
*   *HTTPクライアント* テーマの全コマンド

Web関連のデータベースメソッドもスレッドセーフであり、プリエンプティモードで使用することが可能です: `On Web Authentication`, `On Web Connection`, `On REST Authentication`...)。

もちろん、これらのメソッドによって実行されるコードもまたスレッドセーフである必要があります。


### WebサーバーURL

以下の 4D WebサーバーURLはスレッドセーフであり、プリエンプティモードで使用可能です:

*   *4daction/* (呼び出されるプロジェクトメソッドもまたスレッドセーフでなければいけません)
*   *4dcgi/* (呼び出されるデータベースメソッドもまたスレッドセーフでなければいけません)
*   *4dwebtest/*
*   *4dblank/*
*   *4dstats/*
*   *4dhtmlstats/*
*   *4dcacheclear/*
*   *rest/*
*   *4dimgfield/* (ピクチャーフィールドの Webリクエストに対し `PROCESS 4D TAGS` によって生成されます)
*   *4dimg/* (ピクチャー変数の Webリクエストに対し `PROCESS 4D TAGS` によって生成されます)

### プリエンプティブWebプロセスアイコン

ランタイムエクスプローラーと 4D Server管理ウィンドウの両方において、プリエンプティブな Webプロセスに対し専用アイコンが表示されるようになりました:

| プロセスタイプ         | アイコン                                     |
| --------------- | ---------------------------------------- |
| プリエンプティブWebメソッド | ![](assets/en/WebServer/processIcon.png) |



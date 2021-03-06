---
title: C++ 用の visual Studio data tools
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CPP
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
- cplusplus
ms.openlocfilehash: d2e74fca7109a19c789215424526eef6190b568c
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34752399"
---
# <a name="visual-studio-data-tools-for-c"></a>C++ 用の visual Studio data tools

多くの場合、ネイティブ C++ は、データ ソースにアクセスするときに、最も高速なパフォーマンスを提供します。 ただし、Visual Studio での C++ アプリケーション用のツールをデータは、高度で .NET アプリケーションの場合とではありません。 たとえば、ドラッグ アンド ドロップを C++ のデザイン画面にデータ ソースにデータ ソース ウィンドウを使用できません。 オブジェクト リレーショナル レイヤーを必要がある場合は、独自の作成、またはサード パーティ製品を使用する必要があります。  Microsoft Foundation Class ライブラリを使用するアプリケーションでは、ドキュメントとビュー、と共に、一部のデータベース クラスを使用してをメモリにデータを保存し、ユーザーに表示することも、データ バインディング機能について同様です。 詳細については、次を参照してください。 [Visual c でのデータ アクセス](/cpp/data/data-access-in-cpp)です。

SQL データベースに接続するには、ネイティブ C++ アプリケーションは、ODBC および OLE DB ドライバーおよび Windows に含まれている、ADO プロバイダーを使用できます。 これらは、これらのインターフェイスをサポートする任意のデータベースに接続できます。 ODBC ドライバーは、標準です。 OLE DB は旧バージョンとの互換性のために提供されます。 このようなデータ テクノロジの詳細については、次を参照してください。 [Windows Data Access Components](https://msdn.microsoft.com/library/windows/desktop/aa968814.aspx)です。

SQL Server 2005 でのカスタム機能を利用し、後で、使用して、 [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client)です。 ネイティブ クライアントには、SQL Server ODBC ドライバーと 1 つのネイティブ ダイナミック リンク ライブラリ (DLL) で SQL Server の OLE DB プロバイダーも含まれています。 Microsoft SQL Server へのネイティブ コード Api (ODBC、OLE DB と ADO) を使用してアプリケーションをサポートします。  SQL Server Native Client は、SQL Server Data Tools と共にインストールされます。 ここでは、プログラミング ガイド: [SQL Server Native Client プログラミング](/sql/relational-databases/native-client/sql-server-native-client-programming)です。

## <a name="to-connect-to-localdb-through-odbc-and-sql-native-client-from-a-c-application"></a>C++ アプリケーションから ODBC および SQL Native Client で localDB に接続するには

1.  SQL Server Data Tools をインストールします。

2.  サンプル SQL データベースに接続する場合は、Northwind データベースをダウンロードして、新しい場所に解凍します。

3.  LocalDB に解凍 Northwind.mdf ファイルをアタッチするのにには、SQL Server Management Studio を使用します。 SQL Server Management Studio が起動したら、(localdb) \MSSQLLocalDB に接続します。

     ![SSMS の接続 ダイアログ](../data-tools/media/raddata-ssms-connect-dialog.png)

     左側のウィンドウで localdb ノードを右クリックしを選択し、**アタッチ**です。

     ![データベースの SSMS のアタッチ](../data-tools/media/raddata-ssms-attach-database.png)

4.  ODBC の Windows SDK サンプルをダウンロードして、新しい場所に解凍します。 このサンプルでは、データベースと問題のクエリとコマンドへの接続に使用される ODBC の基本的なコマンドを示します。 これらの関数について詳しく知ることができます、 [Microsoft オープン データベース コネクティビティ)](/sql/odbc/microsoft-open-database-connectivity-odbc)です。 (C++ フォルダーには) ソリューションを最初に読み込むときに、ソリューションを Visual Studio の現在のバージョンにアップグレードする Visual Studio が提供されます。 **[はい]** をクリックします。

5.  ネイティブのクライアントを使用して、そのヘッダー ファイルとライブラリ ファイルが必要です。 これらのファイルには、関数および sql.h で定義された ODBC 関数を超える SQL Server に固有の定義が含まれます。 **プロジェクト** > **プロパティ** > **vc++ ディレクトリ**、インクルード ディレクトリを次を追加します。

**%ProgramFiles%\Microsoft SQL Server\110\SDK\Include**

このライブラリ ディレクトリ:

**%ProgramFiles%\Microsoft SQL Server\110\SDK\Lib**

6.  Odbcsql.cpp でこれらの行を追加します。 #Define コンパイルされない無関係な OLE DB 定義を防止します。

    ```cpp
    #define _SQLNCLI_ODBC_
    #include <sqlncli.h>
    ```

    サンプルは実際に使用されない、ネイティブのクライアントの機能のいずれか、上記の手順は、コンパイルして実行するのには、不要なので注意してください。 この機能を使用するためのプロジェクトが構成されているようになりました。 詳細については、次を参照してください。 [SQL Server Native Client プログラミング](/sql/relational-databases/native-client/sql-server-native-client)です。

7.  ODBC サブシステムで使用するドライバーを指定します。 サンプルは、コマンドラインの引数としてのドライバー接続文字列の属性を渡します。 **プロジェクト** > **プロパティ** > **デバッグ**、このコマンドの引数を追加します。

    ```cpp
    DRIVER="SQL Server Native Client 11.0"
    ```

8.  F5 キーを押してアプリケーションをビルドし、実行します。 データベースを入力するように要求する、ドライバーからダイアログ ボックスを表示する必要があります。 入力`(localdb)\MSSQLLocalDB`、し確認**信頼された接続を使用する**です。 **[OK]** を押します。 コンソールを接続に成功を示すメッセージが表示されます。 表示されます、コマンド プロンプトの SQL ステートメントで入力することができます。 次の画面は、クエリの例と、結果を示しています。

     ![ODBC のサンプル クエリの出力](../data-tools/media/raddata-odbc-sample-query-output.png)

## <a name="see-also"></a>関連項目

- [Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)
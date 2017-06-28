---
title: "Office プロジェクトのイベント"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Sheet1_Startup"
  - "ThisDocument_Shutdown"
  - "ThisDocument_Startup"
  - "アプリケーション レベルのアドイン [Visual Studio での Office 開発]、イベント"
  - "イベント ハンドラー [Visual Studio での Office 開発]"
  - "ThisWorkbook_Startup"
  - "Sheet2_Startup"
  - "ThisWorkbook_Shutdown"
  - "ドキュメント レベルのカスタマイズ [Visual Studio での Office 開発]、イベント"
  - "Sheet2_Shutdown"
  - "Startup イベント"
  - "Sheet3_Shutdown"
  - "アドイン [Visual Studio での Office 開発]、イベント"
  - "Shutdown イベント"
  - "ThisAddIn_Startup"
  - "Sheet3_Startup"
  - "Startup メソッド [Visual Studio での Office 開発]"
  - "Shutdown メソッド [Visual Studio での Office 開発]"
  - "Sheet1_Shutdown"
  - "イベント [Visual Studio での Office 開発]"
  - "ThisAddIn_Shutdown"
ms.assetid: 666d7f23-ef85-4f2e-9cd3-258df5bdc6fd
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# Office プロジェクトのイベント
  各 Office プロジェクト テンプレートは、自動的に複数のイベント ハンドラーを生成します。 ドキュメント レベルのカスタマイズに使用するイベント ハンドラーは、VSTO アドイン用のイベント ハンドラーとは若干異なります。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## ドキュメント レベルのプロジェクト  
 Visual Studio では、ドキュメント レベルのカスタマイズ内の新規または既存のドキュメントまたはワークシートの背後に生成されたコードを提供します。 このコードは 2 つの異なるイベントを発生させます。**Startup** と **Shutdown** です。  
  
### スタートアップ イベント  
 **Startup** イベントは、ドキュメントが実行中になり、アセンブリ内の初期化コードがすべて実行された後で、ホスト項目 \(ドキュメント、ブックまたはワークシート\) ごとに発生します。 これは、コードが実行されているクラスのコンストラクターで最後に実行されるイベントです。 ホスト項目の詳細については、「[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)」を参照してください。  
  
 ドキュメント レベルのプロジェクトを作成する場合、Visual Studio は生成されたコード ファイル内の **Startup** イベント用に次のイベント ハンドラーを作成します。  
  
-   Microsoft Office Word プロジェクトの場合、イベント ハンドラーの名前は `ThisDocument_Startup` です。  
  
-   Microsoft Office Excel プロジェクトの場合、イベント ハンドラーの名前は次のようになります。  
  
    -   `Sheet1_Startup`  
  
    -   `Sheet2_Startup`  
  
    -   `Sheet3_Startup`  
  
    -   `ThisWorkbook_Startup`  
  
### シャットダウン イベント  
 **Shutdown**  イベントは、コードが読み込まれるアプリケーション ドメインがアンロードされるときに、ホスト項目 \(ドキュメントまたはワークシート\) ごとに発生します。 これは、アンロード時にクラス内で呼び出される最後のイベントです。  
  
 ドキュメント レベルのプロジェクトを作成する場合、Visual Studio は生成されたコード ファイル内の  **Shutdown**  イベント用に次のイベント ハンドラーを作成します。  
  
-   Microsoft Office Word プロジェクトの場合、イベント ハンドラーの名前は `ThisDocument_Shutdown` です。  
  
-   Microsoft Office Excel プロジェクトの場合、イベント ハンドラーの名前は次のようになります。  
  
    -   `Sheet1_Shutdown`  
  
    -   `Sheet2_Shutdown`  
  
    -   `Sheet3_Shutdown`  
  
    -   `ThisWorkbook_Shutdown`  
  
> [!NOTE]  
>  ドキュメントの **Shutdown** イベント ハンドラー中にプログラムによってコントロールを削除しないでください。**Shutdown** イベントが発生すると、ドキュメントの UI 要素は利用できなくなります。 アプリケーションが終了する前にコントロールを削除する場合は、**BeforeClose** や **BeforeSave** などの別のイベント ハンドラーにコードを追加します。  
  
### イベント ハンドラー メソッドの宣言  
 イベント ハンドラー メソッドの宣言にはすべて次の同じ引数が渡されます。*sender* と *e* です。 Excel では、*sender* 引数は `Sheet1` や `Sheet2` などのシートを参照します。Word では、*sender* 引数はドキュメントを参照します。*e* 引数は、ここでは使用されませんが、イベントの標準の引数を参照します。  
  
 次のコード例は、Word のドキュメント レベルのプロジェクト内にある既定のイベント ハンドラーを示します。  
  
 [!code-csharp[Trin_VstcoreWordAutomation#121](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#121)]
 [!code-vb[Trin_VstcoreWordAutomation#121](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#121)]  
  
 次のコード例は、Excel のドキュメント レベルのプロジェクト内にある既定のイベント ハンドラーを示します。  
  
> [!NOTE]  
>  次のコード例は、`Sheet1` クラスのイベント ハンドラーを示します。 その他のホスト項目クラス内のイベント ハンドラーの名前は、クラス名に対応しています。 たとえば、`Sheet2` クラスでは、**Startup** イベント ハンドラーの名前は `Sheet2_Startup` です。`ThisWorkbook` クラスでは、**Startup** イベント ハンドラーの名前は `ThisWorkbook_Startup` です。  
  
 [!code-csharp[Trin_VstcoreExcelAutomation#83](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#83)]
 [!code-vb[Trin_VstcoreExcelAutomation#83](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#83)]  
  
### ドキュメント レベルの Excel プロジェクト内のイベントの順序  
 Excel プロジェクト内の **Startup** イベント ハンドラーは、次の順序で呼び出されます。  
  
1.  `ThisWorkbook_Startup`。  
  
2.  `Sheet1_Startup`。  
  
3.  `Sheet2_Startup`。  
  
4.  `Sheet3_Startup`。  
  
5.  順にその他のシート。  
  
 ブック ソリューション内の  **Shutdown** イベント ハンドラーは、次の順序で呼び出されます。  
  
1.  `ThisWorkbook_Shutdown`。  
  
2.  `Sheet1_Shutdown`。  
  
3.  `Sheet2_Shutdown`。  
  
4.  `Sheet3_Shutdown`。  
  
5.  順にその他のシート。  
  
 順序は、プロジェクトがコンパイルされるときに決定されます。 ユーザーが実行時にシートを再配置した場合、次にブックが開くまたは閉じるときにイベントが発生する順序は変更されません。  
  
## VSTO アドイン プロジェクト  
 Visual Studio は、VSTO アドインで生成されたコードを提供します。 このコードは 2 つの異なるイベントを発生させます。<xref:Microsoft.Office.Tools.AddInBase.Startup> と <xref:Microsoft.Office.Tools.AddInBase.Shutdown> です。  
  
### スタートアップ イベント  
 <xref:Microsoft.Office.Tools.AddIn.Startup> イベントは、VSTO アドインが読み込まれ、アセンブリ内のすべての初期化コードが実行された後に発生します。 このイベントは、生成されたコード ファイル内の `ThisAddIn_Startup` メソッドによって処理されます。  
  
 `ThisAddIn_Startup` イベント ハンドラー内のコードは、VSTO アドインが <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> メソッドをオーバーライドしない限り、最初に実行されるユーザー コードです。 この場合、`ThisAddIn_Startup` イベント ハンドラーが、<xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> の後に呼び出されます。  
  
 コードでドキュメントを開く必要がある場合、`ThisAdd-In_Startup` イベント ハンドラーでコードを追加しないでください。 代わりに、ユーザーがドキュメントを作成するとき、または開くときに Office アプリケーションが発生させるイベントにそのコードを追加します。 詳細については、「[Office アプリケーションの起動時にドキュメントにアクセスする](../vsto/programming-vsto-add-ins.md#AccessingDocuments)」を参照してください。  
  
 VSTO アドインの起動処理の詳細については、「[VSTO アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)」を参照してください。  
  
### シャットダウン イベント  
 <xref:Microsoft.Office.Tools.AddInBase.Shutdown> イベントは、コードが読み込まれるアプリケーション ドメインがアンロードされるときに発生します。 このイベントは、生成されたコード ファイル内の `ThisAddIn_Shutdown` メソッドによって処理されます。 このイベント ハンドラーは、VSTO アドインがアンロードされるときに最後に実行されるユーザー コードです。  
  
#### Outlook VSTO アドインのシャットダウン イベント  
 <xref:Microsoft.Office.Tools.AddInBase.Shutdown> イベントは、ユーザーが Outlook の COM アドイン ダイアログ ボックスを使用して、VSTO アドインを無効にした場合にのみ発生します。 Outlook の終了時には発生しません。 Outlook の終了時に実行する必要のあるコードがある場合は、次のいずれかのイベントを処理します。  
  
-   <xref:Microsoft.Office.Interop.Outlook.Application> オブジェクトの <xref:Microsoft.Office.Interop.Outlook.ApplicationEvents_11_Event.Quit> イベント。  
  
-   <xref:Microsoft.Office.Interop.Outlook.Explorer> オブジェクトの <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> イベント。  
  
> [!NOTE]  
>  レジストリを変更して終了する場合、Outlook が <xref:Microsoft.Office.Tools.AddInBase.Shutdown> イベントを発生させるように強制することができます。 ただし、管理者がこの設定を元に戻す場合、`ThisAddIn_Shutdown` メソッドに追加したコードは Outlook の終了時に実行されなくなります。 詳細については、[\[Outlook 2010 でのシャットダウンの変更\]](http://go.microsoft.com/fwlink/?LinkID=184614) を参照してください。  
  
## 参照  
 [Office ソリューションの開発](../vsto/developing-office-solutions.md)   
 [方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [ドキュメント レベルのカスタマイズのプログラミング](../vsto/programming-document-level-customizations.md)   
 [VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)   
 [Office プロジェクト テンプレートの概要](../vsto/office-project-templates-overview.md)  
  
  
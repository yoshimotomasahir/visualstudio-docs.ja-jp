---
title: "Office ソリューションのエラーのトラブルシューティング"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.Project.DesignerDisabled"
  - "VST.Designer.CannotActivate"
  - "VST.Project.ExcelBusy"
  - "VST.SelectDocWizard.AlreadyCustomized"
  - "VST.SelectDocWizard.DocPath"
  - "VST.Project.CannotOpen"
  - "VST.Designer.ErrorsOccurred"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "トラブルシューティング [Visual Studio での Office 開発]"
ms.assetid: 8bbf5433-1992-4ecf-ae1b-19117b8ebe43
caps.latest.revision: 69
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 68
---
# Office ソリューションのエラーのトラブルシューティング
  Visual Studio で Office ソリューションを開発する際、次のタスクを実行するときに問題が発生する場合があります。  
  
-   [プロジェクトを作成する、アップグレードする、開く](#creating)  
  
-   [デザイナーを使用する](#designers)  
  
-   [コードを作成する](#code)  
  
-   [プロジェクトをビルドする](#building)  
  
-   [プロジェクトをデバッグする](#debugging)  
  
##  <a name="creating"></a> プロジェクトを作成する、アップグレードする、開く  
 Office プロジェクトを作成、または開くときに、次のエラーが発生する場合があります。  
  
### プロジェクトを作成できない  
 Office プロジェクトを作成または開こうとするときにエラーが発生しましたが、Visual Studio では、原因を特定するのに十分な情報がありませんでした。  プロジェクトを閉じ、Visual Studio を終了してから、再起動してみてください。  
  
 ドキュメント レベルのプロジェクトを作成しようとしている場合、新しいプロジェクトのドキュメントと同じ名前を持つ別のドキュメントが Excel または Word で開いている可能性があります。  Excel または Word の他のすべてのインスタンスが閉じられていることを確認します。  
  
### 既存のプロジェクトのドキュメントに基づいて新しいプロジェクトを作成するときに、コントロールのプロパティが失われる  
 既存のプロジェクトのドキュメントに基づいて新しい Office プロジェクトを作成する場合、ドキュメント上にあるすべてのコントロールのプロパティは、新しいプロジェクトにコピーされません。  すべての既存のコントロールのプロパティを手動でリセットする必要があります。  または、新しいプロジェクトを作成する代わりに既存のプロジェクトのコピーを作成するか、\(デザイナーで\) 新しいソリューションに既存のプロジェクトの読み込み既存のドキュメントから新しいドキュメントにコントロールをコピーおよび貼り付けして、コントロールのプロパティを保持できます。  
  
### 既存のブックに基づいて Excel ブック プロジェクトを作成するときにエラーが発生する  
 既存のブックに基づいて新しい Excel ブック プロジェクトを作成する場合は、次のエラーの組み合わせが発生する場合があります。  
  
 Excel から: "プライバシーに関する注意: このドキュメントには、マクロ、ActiveX コントロール、XML 拡張パック情報、または Web コンポーネントが含まれています。  これらには、ドキュメント検査で削除できない個人情報が含まれている場合があります。"  
  
 Visual Studio から: "デザイナーの読み込みが正しくできませんでした。"  
  
 これらのエラーは、ドキュメント検査を使用して削除された個人情報があったブックに基づいてプロジェクトを作成しようとしたときに、発生する可能性があります。  このエラーを回避するには、プロジェクトを作成する前に次の手順を実行します。  
  
1.  Excel でブックを開きます。  
  
2.  Excel でセキュリティ センターを開きます。  
  
3.  **\[プライバシー オプション\]** タブで、**\[ファイルを保存するときにファイルのプロパティから個人情報を削除する\]**チェック ボックスをオフにします。  
  
4.  ブックを保存し、Excel を終了します。  
  
### 移行後に、プロジェクトを開くことができない  
 Office のソリューションを Microsoft Office 2010 に移行後は、2007 Microsoft Office システムのみがインストールされている開発用コンピューターでは、プロジェクトを開くことができません。  次のエラー メッセージが表示される可能性があります。  
  
 "ソリューション内の 1 つ以上のプロジェクトが正しく読み込まれていません。  詳細については、出力ウィンドウを確認してください。"  
  
 "このプロジェクト タイプに関連付けられてるアプリケーションがこのコンピューターにインストールされていないため、プロジェクトを作成できません。  このプロジェクト タイプに関連付けられている Microsoft Office アプリケーションをインストールする必要があります。"  
  
 この問題を解決するには、.vbproj ファイル、または .csproj ファイルを編集します。  Word プロジェクトの場合は、HostPackage\="{763FDC83\-64E5\-4651\-AC9B\-28C4FEB985A1}" を、HostPackage\="{6CE98B71\-D55A\-4305\-87A8\-0D6E368D9600}" に置き換えます。  Excel プロジェクトの場合は、HostPackage\="{B284B16A\-C42C\-4438\-BDCD\-B72F4AC43CFB}" を、HostPackage\="{825100CF\-0BA7\-47EA\-A084\-DCF3308DAF74}" に置き換えます。  Outlook プロジェクトの場合は、HostPackage\="{D2B20FF5\-A6E5\-47E1\-90E8\-463C6860CB05}" を HostPackage\="{20A848B8\-E01F\-4801\-962E\-25DB0FF57389}" に置き換えます。  
  
 または、Microsoft Office 2010 が既にインストールされている開発用コンピューターでのみ、移行プロジェクトを開くようにします。  
  
### Windows フォーム コントロールを含むアップグレード済みの Office 2003 のドキュメント レベルのプロジェクトでのエラー  
 Microsoft Office 2003 のドキュメント レベルのプロジェクトをアップグレードする場合で、ドキュメントに Windows フォーム コントロールが含まれていると、アップグレードされたプロジェクトにコンパイル エラーまたは実行時エラーが発生することがあります。  この問題を回避するには、プロジェクトをアップグレードする前に、Visual Studio 2005 Tools for Office Second Edition Runtime を開発コンピューターにインストールします。  このバージョンのランタイムは、Microsoft ダウンロード センターの「[Microsoft Visual Studio 2005 Tools for Office Second Edition Runtime \(VSTO 2005 SE\) \(x86\)](http://go.microsoft.com/fwlink/?linkid=49612)」から再頒布可能パッケージとしてダウンロードできます。  
  
 Visual Studio 2005 Tools for Office Second Edition Runtime は、他の Office ソリューションで使用されていない場合、プロジェクトのアップグレードが完了した後に開発用コンピューターからアンインストールできます。  
  
##  <a name="designers"></a> デザイナーを使用する  
 ドキュメント レベルのプロジェクトでドキュメント、ブック、またはワークシート デザイナーを使用する場合に、次のエラーが発生する可能性があります。  
  
### デザイナーの読み込みが正しくできない  
 Visual Studio は次の場合、デザイナーを開くことができません。  
  
-   Excel または Word が既に開いており、モーダル ダイアログ ボックスを表示している。  デザイナーを開くには、Excel または Word でモーダル ダイアログ ボックスが開いていないかを確認し、開いているモーダル ダイアログ ボックスがあればそれを閉じます。  開いているモーダル ダイアログ ボックスがない場合は、Excel または Word が応答する前に、何か別のアクションが必要な可能性があります。  
  
-   プロジェクトは現在デバッグ中である。  デザイナーを開くには、デバッグを停止または終了します。  
  
-   開発用コンピューターにインストールされている Excel の VSTO アドインにより、Excel の開始時にダイアログ ボックスが表示される。  ドキュメント レベルの Excel プロジェクトを作成するには、まず、VSTO アドインを無効にする必要があります。  
  
### ドキュメントやワークシートでコントロールが黒い長方形として表示される  
 ドキュメントやワークシートでコントロールをグループ化すると、Visual Studio はもうコントロールを認識しなくなります。  グループ化されたコントロールは **\[プロパティ\]** ウィンドウでアクセスできず、ドキュメントやワークシート上で黒い長方形として表示されます。  コントロールの機能を復元するには、グループ化を解除する必要があります。  
  
### Word テンプレート上のコントロールが Visual Studio に表示されない  
 Visual Studio デザイナーで Word テンプレートを開くと、テンプレート上のテキストの範囲内にないコントロールが表示されない場合があります。  これは、Visual Studio が Word テンプレートを**標準**ビューで開くためです。  コントロールを表示するには、**\[ビュー\]** メニューをクリックし、**\[Microsoft Office Word View\]** をポイントしてから **\[印刷レイアウト\]** をクリックします。  
  
### 「クリップ アートの挿入」コマンドを実行しても、Visual Studio デザイナーで何も起こらない。  
 Excel または Word が、Visual Studio デザイナーで開いているとき、リボンの **\[イラスト\]** タブで **\[クリップ アート\]** ボタンをクリックしても、**\[クリップ アート\]** 作業ウィンドウは開きません。  クリップ アートを追加するには、Visual Studio の外部のメイン プロジェクト フォルダー \(\\bin フォルダーにあるコピーではないフォルダー\) にあるブックまたはドキュメントのコピーを開き、クリップ アートを追加してから、ブックまたはドキュメントを保存します。  
  
##  <a name="code"></a> コードの作成  
 Office プロジェクトでコードを作成するときに、次のエラーが発生する場合があります。  
  
### C\# を使用するときに、Office オブジェクトの一部のイベントにアクセスできない  
 場合によっては、Visual C\# プロジェクトで Office プライマリ相互運用機能アセンブリ \(PIA\) 型のインスタンスの特定のイベントにアクセスしようとすると、次のようなコンパイラ エラーが表示される場合があります。  
  
 "'Microsoft.Office.Interop.Excel.\_Application.NewWorkbook' と 'Microsoft.Office.Interop.Excel.AppEvents\_Event.NewWorkbook' の間にあいまいさがあります"  
  
 このエラーは、オブジェクトの別のプロパティやメソッドと同じ名前を持つイベントにアクセスしようとしていることを意味します。  イベントにアクセスするには、オブジェクトをその*イベント インターフェイス*にキャストする必要があります。  
  
 イベントを持つ Office PIA の型は、すべてのプロパティとメソッドを持つコア インターフェイスと、オブジェクトによって公開されるイベントを含むイベント インターフェイスの、2 つのインターフェイスを実装します。  これらのイベント インターフェイスでは、*objectname*Events*n*\_Event の名前付け規約が使用されます \(<xref:Microsoft.Office.Interop.Excel.AppEvents_Event> や <xref:Microsoft.Office.Interop.Word.ApplicationEvents2_Event> など\)。  オブジェクト上で検出できることが予想されるイベントにアクセスできない場合は、オブジェクトをそのイベント インターフェイスにキャストします。  
  
 たとえば、<xref:Microsoft.Office.Interop.Excel.Application> オブジェクトが、<xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook> イベントおよび <xref:Microsoft.Office.Interop.Excel._Application.NewWorkbook%2A> プロパティを持つとします。  <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook> イベントを処理するには、<xref:Microsoft.Office.Interop.Excel.Application> を <xref:Microsoft.Office.Interop.Excel.AppEvents_Event> インターフェイスにキャストします。  Excel のドキュメント レベルのプロジェクトでこれを実行する方法を、次のコード例に示します。  
  
 [!code-csharp[Trin_VstcoreTroubleshootingExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreTroubleshootingExcel/CS/ThisWorkbook.cs#1)]  
  
 Office PIA のイベント インターフェイスの詳細については、「[Office プライマリ相互運用機能アセンブリのクラスとインターフェイスの概要](http://msdn.microsoft.com/ja-jp/da92dc3c-8209-44de-8095-a843659368d5)」を参照してください。  
  
### [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] または [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] を対象とするプロジェクトで Office PIA のクラスを参照できない  
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] または [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] を対象とするプロジェクトでは、Office PIA で定義されているクラスを参照するコードは、既定ではコンパイルされません。  PIA のクラスは *objectname*Class の名前付け規約を使用します \(<xref:Microsoft.Office.Interop.Word.DocumentClass> や <xref:Microsoft.Office.Interop.Excel.WorkbookClass> など\)。  たとえば、Word の VSTO アドイン プロジェクトの次のコードはコンパイルされません。  
  
```vb  
Dim document As Word.DocumentClass = Globals.ThisAddIn.Application.ActiveDocument  
```  
  
```csharp  
Word.DocumentClass document = (Word.DocumentClass) Globals.ThisAddIn.Application.ActiveDocument;  
```  
  
 このコードを実行すると、次のようなコンパイル エラーが発生します。  
  
-   Visual Basic: "クラス ‘DocumentClass’ への参照は、そのアセンブリが No\-PIA モードを使用してリンクされている場合には許可されません。"  
  
-   Visual C\#: "相互運用機能型 'Microsoft.Office.Interop.Word.DocumentClass' を埋め込むことができません。  代わりに適用可能なインターフェイスを使用してください。"  
  
 このエラーを解決するには、対応するインターフェイスを代わりに参照するようにコードを変更します。  たとえば、<xref:Microsoft.Office.Interop.Word.DocumentClass> オブジェクトを参照するのではなく、代わりに <xref:Microsoft.Office.Interop.Word.Document> インターフェイスを参照します。  
  
```vb  
Dim document As Word.Document = Globals.ThisAddIn.Application.ActiveDocument  
```  
  
```csharp  
Word.Document document = Globals.ThisAddIn.Application.ActiveDocument;  
```  
  
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] または [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] を対象とするプロジェクトは、既定で自動的に Office PIA のすべての相互運用機能型を埋め込みます。  このコンパイル エラーは、埋め込まれた相互運用機能型の機能は、クラスでなくインターフェイスでのみ機能するために発生します。  Office PIA のインターフェイスとクラスの詳細については、「[Office プライマリ相互運用機能アセンブリのクラスとインターフェイスの概要](http://go.microsoft.com/fwlink/?LinkId=189592)」を参照してください。  Office プロジェクトの埋め込み相互運用機能型の機能の詳細については、「[Office ソリューションのデザインと作成](../vsto/designing-and-creating-office-solutions.md)」を参照してください。  
  
### Office クラスへの参照が認識されない  
 たとえば Application などの一部のクラス名は、<xref:Microsoft.Office.Interop.Word> と <xref:System.Windows.Forms> など、複数の名前空間にあります。  このため、プロジェクト テンプレートの上部にある **Imports**\/**using** ステートメントには、次のように短縮形の修飾定数が含まれます。  
  
 [!code-csharp[Trin_VstcoreTroubleshootingWord#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreTroubleshootingWord/CS/ThisDocument.cs#2)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreTroubleshootingWord/VB/ThisDocument.vb#2)]  
  
 こうした **Imports**\/**using** ステートメントの使用法では、次のように、Word または Excel の修飾子を持つ Office クラスへの参照を区別することが必要です。  
  
 [!code-csharp[Trin_VstcoreTroubleshootingWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreTroubleshootingWord/CS/ThisDocument.cs#3)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreTroubleshootingWord/VB/ThisDocument.vb#3)]  
  
 非修飾の宣言を使用した場合は、次のようにエラーが発生します。  
  
 [!code-csharp[Trin_VstcoreTroubleshootingWord#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreTroubleshootingWord/CS/ThisDocument.cs#4)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreTroubleshootingWord/VB/ThisDocument.vb#4)]  
  
 Word または Excel の名前空間をインポートし、名前空間内のすべてのクラスへのアクセスがある場合でも、名前空間のあいまいさを排除するには、すべての型を Word または Excel で完全に修飾する必要があります。  
  
##  <a name="building"></a> プロジェクトをビルドする  
 Office プロジェクトをビルドするときに、次のエラーが発生する場合があります。  
  
### 制限付きアクセス許可を持つドキュメントに基づくドキュメント レベルのプロジェクトをビルドできない  
 Visual Studio は、ドキュメントのアクセス許可が制限されている場合、ドキュメント レベルのプロジェクトをビルドできません。  プロジェクトにアクセス許可が制限されているドキュメントが含まれている場合には、プロジェクトがコンパイルされず、**\[エラー一覧\]** ウィンドウに次のメッセージが表示されます。  
  
 "カスタマイズを追加できませんでした。"  
  
 アクセス許可が制限されているドキュメントを含める場合は、ソリューションを開発およびビルドする間は、制限のないドキュメントを使用します。  次に、ソリューションを発行した後に、発行場所でアクセス許可の制限をドキュメントに適用します。  
  
### NamedRange コントロールを削除した後にコンパイラ エラーが発生する  
 デザイナーで作業中のワークシートではないワークシートから <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを削除した場合、自動生成されたコードがプロジェクトから削除されず、コンパイラ エラーが発生することがあります。  コードが確実に削除されるようにするには、必ず、<xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールを含むワークシートを選択し作業中のワークシートにしてからコントロールを削除します。  コントロールを削除するときに、自動生成されたコードが削除されない場合は、ワークシートをアクティブ化して、ワークシートが変更済みとしてマークされるように変更を加えれば、デザイナーによりコードが削除されます。  プロジェクトをリビルドするときに、コードが削除されます。  
  
##  <a name="debugging"></a> プロジェクトをデバッグする  
 Office プロジェクトをデバッグするときに、次のエラーが発生する場合があります。  
  
### 開発用コンピューターでソリューションを発行およびインストールするとアンインストールするよう求めるプロンプトが表示される  
 Office ソリューションをデバッグするときに、次のエラー メッセージが表示されることがあります。  
  
 "現在他のバージョンがインストールされており、この場所からアップグレードすることはできないため、このカスタマイズをインストールすることはできません。"  
  
 このエラーは、開発用コンピューターで以前に Office ソリューションを発行し、インストールしたことを示しています。  メッセージが表示されないようにには、ソリューションをデバッグする前に、コンピューターにインストールされているプログラムの一覧からソリューションをアンインストールします。  または、開発コンピューターに別のユーザー アカウントを作成し、発行済みソリューションのインストールをテストできます。  
  
### UNC ネットワークの場所で作成されたドキュメント レベルのプロジェクトを Visual Studio から実行できない  
 UNC ネットワークの場所で Excel または  Word のドキュメント レベルのプロジェクトを作成する場合は、Excel または Word の \[信頼できる場所\] リストに、そのドキュメントの場所を追加する必要があります。  そうしない場合、Visual Studio でプロジェクトの実行またはデバッグを試行するときに、カスタマイズが読み込まれません。  信頼できる場所の詳細については、「[ドキュメントへの信頼の付与](../vsto/granting-trust-to-documents.md)」を参照してください。  
  
### デバッグ後にスレッドが正しく停止されない  
 Visual Studio の Office プロジェクトはスレッドの名前付け規約に従っており、デバッガーはプログラムを正しく終了できます。  ソリューション内にスレッドを作成する場合、デバッグの停止時にこれらのスレッドが確実に正常に処理されるよう、各スレッドに VSTA \_  というプレフィックスを付ける必要があります。  たとえば、ネットワーク イベントを待機するスレッドの `Name` プロパティを VSTA\_NetworkListener と設定できます。  
  
### 開発用コンピューターで Office ソリューションを実行またはデバッグできない  
 開発用コンピューターで Office プロジェクトを実行または開発できない場合に、次のエラー メッセージが表示されることがあります。  
  
 "アプリケーション ドメインが作成されなかったため、カスタマイズは読み込まれませんでした。"  
  
 Visual Studio は、Office ソリューションを読み込む前に、.NET Framework アセンブリ ローダーである Fusion を使用してアセンブリをキャッシュします。  Visual Studio が Fusion キャッシュへ書き込めることを確認し、もう一度やり直してください。  詳細については、「[アセンブリのシャドウ コピー](../Topic/Shadow%20Copying%20Assemblies.md)」を参照してください。  
  
### エディット コンティニュを使用した後に、ドキュメント レベルのプロジェクトでデバッガーを停止するときにエラーが発生する  
 プロジェクトが中断モードの間に、エディット コンティニュを使用して、Excel または Word のドキュメント レベルのプロジェクトでコードを変更する場合、その後デバッガを停止すると、次のエラー メッセージのダイアログ ボックスが表示されることがあります。  
  
 "このプロセスを現在の状態で終了すると、データを消失したりシステムが不安定になったりするなど、予期しない結果になる場合があります。"  
  
 ダイアログ ボックスで **\[はい\]** をクリックしても **\[いいえ\]** をクリックしても、Visual Studio は Excel プロセスまたは Word プロセスを終了して、デバッガーを停止します。  このダイアログ ボックスを表示せずにプロジェクトのデバッグを停止するには、Visual Studio のデバッガを停止するのではなく、直接、Excel または Word を終了します。  
  
## 参照  
 [Office ソリューションのトラブルシューティング](../vsto/troubleshooting-office-solutions.md)   
 [Office ソリューションのセキュリティのトラブルシューティング](../vsto/troubleshooting-office-solution-security.md)   
 [Office ソリューション配置のトラブルシューティング](../vsto/troubleshooting-office-solution-deployment.md)  
  
  
---
title: "チュートリアル : サーバー上のブックへのデータの挿入"
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
  - "データ [Visual Studio での Office 開発], アクセス (サーバーで)"
  - "データセット [Visual Studio での Office 開発], アクセス (サーバーで)"
  - "ドキュメント [Visual Studio での Office 開発], サーバー側データ アクセス"
  - "サーバー側データ アクセス [Visual Studio での Office 開発]"
  - "ブック [Visual Studio での Office 開発], 挿入 (データを)"
ms.assetid: e6481902-781c-4666-bc18-4d69368c9bb3
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# チュートリアル : サーバー上のブックへのデータの挿入
  このチュートリアルでは、<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> クラスを使用して、Microsoft Office Excel ブックにキャッシュされたデータセットに、Excel を起動することなくデータを挿入する方法について説明します。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   AdventureWorksLT データベースのデータを格納するデータセットを定義する。  
  
-   Excel ブック プロジェクトおよびコンソール アプリケーション プロジェクトにデータセットのインスタンスを作成する。  
  
-   ブックのデータセットにバインドされた <xref:Microsoft.Office.Tools.Excel.ListObject> を作成する。  
  
-   ブックのデータセットをデータ キャッシュに追加する。  
  
-   コンソール アプリケーションでコードを実行して、Excel を起動することなく、キャッシュされたデータセットにデータを挿入する。  
  
 このチュートリアルでは開発用コンピューターでコードを実行することを想定していますが、このチュートリアルに掲載されているコードは、Excel がインストールされていないサーバー上でも実行できます。  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。  これらの要素は、使用する Visual Studio のエディションとその設定によって決まります。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] または [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
-   AdventureWorksLT サンプル データベースがアタッチされた、Microsoft SQL Server または Microsoft SQL Server Express の実行中のインスタンスへのアクセス。  AdventureWorksLT データベースは、[CodePlex の Web サイト](http://go.microsoft.com/fwlink/?linkid=87843)からダウンロードできます。  データベースを関連付ける方法の詳細については、以下のトピックを参照してください。  
  
    -   SQL Server Management Studio または SQL Server Management Studio Express を使用してデータベースを関連付ける方法については、「[データベースをアタッチする方法 \(SQL Server Management Studio\)](http://msdn.microsoft.com/ja-jp/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa)」を参照してください。  
  
    -   コマンド ラインを使用してデータベースを関連付ける方法については、「[データベース ファイルを SQL Server Express にアタッチする方法](http://msdn.microsoft.com/ja-jp/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68)」を参照してください。  
  
## データセットを定義するクラス ライブラリ プロジェクトの作成  
 Excel ブック プロジェクトとコンソール アプリケーションとで同じデータセットを使用するには、これらのプロジェクトの両方から参照される別個のアセンブリ内にデータセットを定義する必要があります。  このチュートリアルでは、データセットをクラス ライブラリ プロジェクトに定義します。  
  
#### クラス ライブラリ プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  **\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックします。  
  
3.  テンプレート ペインで、**\[Visual C\#\]** または **\[Visual Basic\]** を展開し、**\[Windows\]** をクリックします。  
  
4.  プロジェクト テンプレートの一覧で、**\[クラス ライブラリ\]** を選択します。  
  
5.  **\[プロジェクト名\]** ボックスに「**AdventureWorksDataSet**」と入力します。  
  
6.  **\[参照\]** をクリックします。%UserProfile%\\My Documents フォルダー \(Windows XP 以前のバージョンの場合\) または %UserProfile%\\Documents \(Windows Vista の場合\) フォルダーに移動し、**\[フォルダーの選択\]** をクリックします。  
  
7.  **\[新しいプロジェクト\]** ダイアログ ボックスで、**\[ソリューションのディレクトリを作成\]** チェック ボックスがオフになっていることを確認します。  
  
8.  **\[OK\]** をクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] によって **AdventureWorksDataSet** プロジェクトが**ソリューション エクスプローラー**に追加され、**Class1.cs** コード ファイルまたは **Class1.vb** コード ファイルが開かれます。  
  
9. **ソリューション エクスプローラー**で、**\[Class1.cs\]** または **\[Class1.vb\]** を右クリックし、**\[削除\]** をクリックします。  このファイルは、このチュートリアルには必要ありません。  
  
## クラス ライブラリ プロジェクトへのデータセットの定義  
 SQL Server 2005 用 AdventureWorksLT データベースのデータを格納する型指定されたデータセットを定義します。  このチュートリアルの後半で、Excel ブック プロジェクトおよびコンソール アプリケーション プロジェクトからこのデータセットを参照します。  
  
 このデータセットは、AdventureWorksLT データベースの Product テーブルのデータを表す*型指定されたデータセット*です。  型指定されたデータセットの詳細については、「[Visual Studio でのデータセットの操作](../data-tools/dataset-tools-in-visual-studio.md)」を参照してください。  
  
#### クラス ライブラリ プロジェクトに型指定されたデータセットを定義するには  
  
1.  **ソリューション エクスプローラー**で **\[AdventureWorksDataSet\]** プロジェクトをクリックします。  
  
2.  **\[データ ソース\]** のウィンドウが表示されない場合は、これを、**\[ビュー\]**、**\[その他のウィンドウ\]** を選択する、メニュー バーの **\[データ ソース\]** 表示されます。  
  
3.  **\[データ ソース構成ウィザード\]** を開始するには **\[新しいデータ ソースの追加\]** を選択します。  
  
4.  **\[データベース\]** をクリックし、**\[次へ\]** をクリックします。  
  
5.  AdventureWorksLT データベースへの接続が既に設定されている場合は、その接続を選択し、**\[次へ\]** をクリックします。  
  
     それ以外の場合は、**\[新しい接続\]** をクリックし、**\[接続の追加\]** ダイアログ ボックスを使用して新しい接続を作成します。  詳細については、「[How to: Connect to Data in a Database](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)」を参照してください。  
  
6.  \[アプリケーション構成ファイルに接続文字列を保存\] ページで、\[次へ\] をクリックします**Save the Connection String to the Application Configuration FileNext**。  
  
7.  **\[データベース オブジェクトの選択\]** ページで、**\[テーブル\]** を展開し、**\[Product \(SalesLT\)\]** を選択します。  
  
8.  \[完了\] をクリックします。  
  
     AdventureWorksLTDataSet.xsd ファイルが **AdventureWorksDataSet** プロジェクトに追加されます。  このファイルでは、次の項目を定義します。  
  
    -   `AdventureWorksLTDataSet` という名前の型指定されたデータセット。  このデータセットは、AdventureWorksLT データベースの Product テーブルの内容を表します。  
  
    -   `ProductTableAdapter` という名前の TableAdapter。  TableAdapter は、`AdventureWorksLTDataSet` のデータを読み書きするために使用します。  詳細については、「[TableAdapter の概要](/visual-studio/data-tools/tableadapter-overview)」を参照してください。  
  
     これらのオブジェクトはどちらもこのチュートリアルの後半で使用します。  
  
9. **ソリューション エクスプローラー**で、**\[AdventureWorksDataSet\]** を右クリックし、**\[ビルド\]** をクリックします。  
  
     プロジェクトがエラーを発生させずにビルドすることを確認します。  
  
## Excel ブック プロジェクトの作成  
 データとのインターフェイス用の Excel ブック プロジェクトを作成します。  このチュートリアルの後半では、データを表示する <xref:Microsoft.Office.Tools.Excel.ListObject> を作成し、データセットのインスタンスをブック内のデータ キャッシュに追加します。  
  
#### Excel ブック プロジェクトを作成するには  
  
1.  **ソリューション エクスプローラー**で、**\[AdventureWorksDataSet\]** ソリューションを右クリックします。**\[追加\]** をポイントし、**\[新しいプロジェクト\]** をクリックします。  
  
2.  テンプレート ペインで、または **\[Visual C\#\]** か  **\[Visual Basic\]**を展開し、**\[Office\/SharePoint\]** を展開します。  
  
3.  **\[Office\/SharePoint\]** の展開したノードの下で、**\[Office Add\-ins\]** のノードを選択します。  
  
4.  プロジェクト テンプレートの一覧で、**\[Excel 2010 ブック\]** または **\[Excel 2013 Workbook\]** のプロジェクトを選択します。  
  
5.  **\[プロジェクト名\]** ボックスに「**AdventureWorksReport**」と入力します。  場所は変更しないでください。  
  
6.  **\[OK\]** をクリックします。  
  
     **Visual Studio Tools for Office プロジェクト ウィザード**が開きます。  
  
7.  **\[新規ドキュメントの作成\]** が選択されていることを確認し、**\[OK\]** をクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] によって、デザイナーで **AdventureWorksReport** ブックが開かれ、**ソリューション エクスプローラー**に **AdventureWorksReport** プロジェクトが追加されます。  
  
## Excel ブック プロジェクトのデータ ソースへのデータセットの追加  
 Excel ブックにデータセットを表示するには、その前に Excel ブック プロジェクトのデータ ソースにデータセットを追加する必要があります。  
  
#### Excel ブック プロジェクトのデータ ソースにデータセットを追加するには  
  
1.  **ソリューション エクスプローラー**で、**\[AdventureWorksReport\]** プロジェクトの下の **\[Sheet1.cs\]** または **\[Sheet1.vb\]** をダブルクリックします。  
  
     ブックがデザイナーで開かれます。  
  
2.  **\[データ\]** メニューの **\[新しいデータ ソースの追加\]** をクリックします。  
  
     **データ ソース構成**ウィザードが開きます。  
  
3.  **\[オブジェクト\]** をクリックし、**\[次へ\]** をクリックします。  
  
4.  **\[バインド先のオブジェクトを選択します\]** ページで、**\[参照の追加\]** をクリックします。  
  
5.  **\[プロジェクト\]** タブで、**\[AdventureWorksDataSet\]** をクリックし、**\[OK\]** をクリックします。  
  
6.  **\[AdventureWorksDataSet\]** アセンブリの **\[AdventureWorksDataSet\]** 名前空間の下にある **\[AdventureWorksLTDataSet\]** をクリックし、**\[完了\]** をクリックします。  
  
     **\[データ ソース\]** ウィンドウが開き、**AdventureWorksLTDataSet** がデータ ソースの一覧に追加されます。  
  
## データセットのインスタンスにバインドされた ListObject の作成  
 データセットをブックに表示するには、データセットのインスタンスにバインドされた <xref:Microsoft.Office.Tools.Excel.ListObject> を作成します。  コントロールのデータへのバインドの詳細については、「[Office ソリューションでのコントロールへのデータのバインド](../vsto/binding-data-to-controls-in-office-solutions.md)」を参照してください。  
  
#### データセットのインスタンスにバインドされた ListObject を作成するには  
  
1.  **\[データ ソース\]** ウィンドウで、**\[AdventureWorksDataSet\]** の下にある **\[AdventureWorksLTDataSet\]** ノードを展開します。  
  
2.  **\[Product\]** ノードを選択し、表示されるドロップダウン矢印をクリックします。ドロップダウン リストで **\[ListObject\]** を選択します。  
  
     ドロップダウン矢印が表示されない場合は、デザイナーでブックが開かれていることを確認します。  
  
3.  **Product** テーブルをセル A1 にドラッグします。  
  
     `productListObject` という名前の <xref:Microsoft.Office.Tools.Excel.ListObject> コントロールが、セル A1 を始点にワークシートに作成されます。  同時に、`adventureWorksLTDataSet` という名前のデータセット オブジェクトと、`productBindingSource` という名前の <xref:System.Windows.Forms.BindingSource> がプロジェクトに追加されます。  <xref:Microsoft.Office.Tools.Excel.ListObject> が <xref:System.Windows.Forms.BindingSource> にバインドされ、さらにこれがデータセット オブジェクトにバインドされます。  
  
## データ キャッシュへのデータセットの追加  
 Excel ブック プロジェクトの外部のコードからブック内のデータセットにアクセスできるようにするには、データセットをデータ キャッシュに追加する必要があります。  データ キャッシュの詳細については、「[ドキュメント レベルのカスタマイズのキャッシュ データ](../vsto/cached-data-in-document-level-customizations.md)」および「[キャッシュされたデータ](../vsto/caching-data.md)」を参照してください。  
  
#### データ キャッシュにデータセットを追加するには  
  
1.  デザイナーで、**\[adventureWorksLTDataSet\]** をクリックします。  
  
2.  **\[プロパティ\]** ウィンドウで、**\[Modifiers\]** プロパティを **\[Public\]** に設定します。  
  
3.  **\[CacheInDocument\]** プロパティを **\[True\]** に設定します。  
  
## チェックポイント  
 Excel ブック プロジェクトをビルドして実行して、エラーが発生することなくコンパイルおよび実行されることを確認します。  
  
#### プロジェクトをビルドして実行するには  
  
1.  **ソリューション エクスプローラー**で、**\[AdventureWorksReport\]** プロジェクトを右クリックします。**\[デバッグ\]** を選択し、**\[新しいインスタンスを開始\]** をクリックします。  
  
     プロジェクトがビルドされ、ブックが Excel で開かれます。  データ キャッシュの `adventureWorksLTDataSet` オブジェクトにはまだデータがないため、Sheet1 の <xref:Microsoft.Office.Tools.Excel.ListObject> は空です。  次のセクションでは、コンソール アプリケーションを使用して、`adventureWorksLTDataSet` オブジェクトにデータを設定します。  
  
2.  Excel を終了します。  変更を保存しないでください。  
  
## コンソール アプリケーション プロジェクトの作成  
 ブックのキャッシュされたデータセットにデータを挿入するためのコンソール アプリケーション プロジェクトを作成します。  
  
#### コンソール アプリケーション プロジェクトを作成するには  
  
1.  **ソリューション エクスプローラー**で、**\[AdventureWorksDataSet\]** ソリューションを右クリックします。**\[追加\]** をポイントし、**\[新しいプロジェクト\]** をクリックします。  
  
2.  **\[プロジェクトの種類\]** ペインで、**\[Visual C\#\]** または **\[Visual Basic\]** を展開し、**\[Windows\]** をクリックします。  
  
3.  **\[テンプレート\]** ペインで **\[コンソール アプリケーション\]** を選択します。  
  
4.  **\[プロジェクト名\]** ボックスに「**DataWriter**」と入力します。  場所は変更しないでください。  
  
5.  **\[OK\]** をクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] によって **DataWriter** プロジェクトが**ソリューション エクスプローラー**に追加され、コード ファイルの **Program.cs** または **Module1.vb** が開かれます。  
  
## コンソール アプリケーションを使用したキャッシュされたデータセットへのデータの追加  
 ブックのキャッシュされたデータセットにデータを設定するには、コンソール アプリケーションで <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> クラスを使用します。  
  
#### キャッシュされたデータセットにデータを追加するには  
  
1.  **ソリューション エクスプローラー**で、**\[DataWriter\]** プロジェクトを右クリックし、**\[参照の追加\]** をクリックします。  
  
2.  **\[.NET\]** のタブで、\[ **\[Microsoft.VisualStudio.Tools.Applications.ServerDocument\]**。  
  
3.  **\[OK\]** をクリックします。  
  
4.  **ソリューション エクスプローラー**で、**\[DataWriter\]** プロジェクトを右クリックし、**\[参照の追加\]** をクリックします。  
  
5.  **\[プロジェクト\]** タブで、**\[AdventureWorksDataSet\]** を選択し、**\[OK\]** をクリックします。  
  
6.  コード エディターで Program.cs ファイルまたは Module1.vb ファイルを開きます。  
  
7.  コード ファイルの先頭に次の **using** ステートメント \(C\# の場合\) または **Imports** ステートメント \(Visual Basic の場合\) を追加します。  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/CS/DataWriter/Program.cs#1)]
     [!code-vb[Trin_CachedDataWalkthroughs#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/VB/DataWriter/Module1.vb#1)]  
  
8.  `Main` メソッドに次のコードを追加します。  このコードは、次のオブジェクトを宣言します。  
  
    -   **AdventureWorksDataSet** プロジェクトに定義されている `AdventureWorksLTDataSet` 型および `ProductTableAdapter` 型のインスタンス  
  
    -   **AdventureWorksReport** プロジェクトのビルド フォルダー内の AdventureWorksReport ブックへのパス  
  
    -   ブックのデータ キャッシュにアクセスするための <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> オブジェクト  
  
        > [!NOTE]  
        >  次のコードでは、ファイル拡張子として .xlsx を持つブックを使用していると想定しています。  プロジェクトのブックで異なるファイル拡張子を使用している場合は、必要に応じてパスを変更してください。  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/CS/DataWriter/Program.cs#3)]
     [!code-vb[Trin_CachedDataWalkthroughs#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/VB/DataWriter/Module1.vb#3)]  
  
9. 前の手順で追加したコードの後で、次のコードを `Main` メソッドに追加します。  このコードは次のタスクを実行します。  
  
    -   テーブル アダプターを使用して、型指定されたデータセット オブジェクトに値を設定します。  
  
    -   <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> クラスの <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> プロパティを使用して、ブックのキャッシュされたデータセットにアクセスします。  
  
    -   <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> メソッドを使用して、キャッシュされたデータセットにローカルの型指定されたデータセットのデータを設定します。  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/CS/DataWriter/Program.cs#4)]
     [!code-vb[Trin_CachedDataWalkthroughs#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/VB/DataWriter/Module1.vb#4)]  
  
10. **ソリューション エクスプローラー**で、**\[DataWriter\]** プロジェクトを右クリックします。**\[デバッグ\]** をポイントし、**\[新しいインスタンスを開始\]** をクリックします。  
  
     プロジェクトがビルドされ、ローカル データセットにデータを設定する処理、およびデータをブックのキャッシュされたデータセットに保存する処理が実行されている間、コンソール アプリケーションによっていくつかのステータス メッセージが表示されます。  Enter キーを押してアプリケーションを閉じます。  
  
## ブックのテスト  
 ブックを開くと、コンソール アプリケーションを使用してキャッシュされたデータセットに追加されたデータが <xref:Microsoft.Office.Tools.Excel.ListObject> に表示されます。  
  
#### ブックをテストするには  
  
1.  Visual Studio デザイナーに AdventureWorksReport ブックが開かれている場合はこれを閉じます。  
  
2.  ファイル エクスプローラーで、**AdventureWorksReport** のプロジェクトのビルド フォルダーにある AdventureWorksReport ブックを開きます。  ビルド フォルダーは、既定で次のどちらかの場所に設定されます。  
  
    -   %UserProfile%\\My Documents\\AdventureWorksReport\\bin\\Debug \(Windows XP 以前のバージョンの場合\)  
  
    -   %UserProfile%\\Documents\\AdventureWorksReport\\bin\\Debug \(Windows Vista の場合\)  
  
3.  ブックを開いた後、<xref:Microsoft.Office.Tools.Excel.ListObject> にデータが設定されていることを確認します。  
  
## 次の手順  
 キャッシュされたデータの操作については、以下のトピックを参照してください。  
  
-   キャッシュされたデータセット内のデータを Excel を起動することなく変更する。  詳細については、「[チュートリアル : サーバー上のブックにキャッシュされたデータの変更](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)」を参照してください。  
  
## 参照  
 [チュートリアル : サーバー上のブックにキャッシュされたデータの変更](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)   
 [Windows フォーム アプリケーションでのデータへの接続](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)  
  
  
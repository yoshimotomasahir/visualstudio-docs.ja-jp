---
title: "チュートリアル : VBA から Visual C# プロジェクトのコードを呼び出す"
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
  - "Excel [Visual Studio での Office 開発]、呼び出し (コードを VBA から)"
  - "Word [Visual Studio での Office 開発]、呼び出し (コードを VBA から)"
  - "Visual C# [Visual Studio での Office 開発]、呼び出し (コードを VBA から)"
  - "ブック [Visual Studio での Office 開発]、呼び出し (コードを VBA から)"
  - "VBA [Visual Studio での Office 開発]、呼び出し (ドキュメント レベルのカスタマイズのコードを)"
  - "Office ドキュメント [Visual Studio での Office 開発]、Visual Basic for Applications、および"
  - "呼び出し (コードを VBA から)"
  - "ドキュメント レベルのカスタマイズ [Visual Studio での Office 開発]、呼び出し (コードを)"
ms.assetid: 9a5741f1-8260-4964-afa1-c69b68d1cfdf
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# チュートリアル : VBA から Visual C# プロジェクトのコードを呼び出す
  このチュートリアルでは、ブック内の Visual Basic for Applications \(VBA\) コードから Microsoft Office Excel 用のドキュメント レベルのカスタマイズ内のメソッドを呼び出す方法を示します。 このプロシージャには次の 3 つの基本的な手順が含まれます。`Sheet1` ホスト項目クラスにメソッドを追加する、ブックの VBA コードにメソッドを公開する、および、ブック内の VBA コードからメソッドを呼び出す、の 3 つです。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 このチュートリアルでは具体的には Excel を使用していますが、チュートリアルで示されるコンセプトは Word のドキュメント レベルのプロジェクトにも適用できます。  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   VBA コードが含まれるブックを作成する。  
  
-   Excel のセキュリティ センターを使用して、ブックの場所を信頼する。  
  
-   `Sheet1` ホスト項目クラスにメソッドを追加する。  
  
-   `Sheet1` ホスト項目クラスのインターフェイスを抽出する。  
  
-   VBA コードにメソッドを公開する。  
  
-   VBA コードからメソッドを呼び出す。  
  
> [!NOTE]  
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。 これらの要素は、使用している Visual Studio のエディションや独自の設定によって決まります。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## VBA コードが含まれるブックを作成する  
 最初の手順では、単純な VBA マクロを含むマクロ対応のブックを作成します。 カスタマイズ内のコードを VBA に公開する前に、ブックに VBA コードを含めておく必要があります。 含めないと、Visual Studio は VBA プロジェクトを変更して、VBA コードがカスタマイズ アセンブリを呼び出せるようにすることができません。  
  
 使用する VBA コードを含むブックが既にある場合は、この手順を省略できます。  
  
#### VBA コードが含まれるブックを作成するには  
  
1.  Excel を起動します。  
  
2.  作業中のドキュメントを **WorkbookWithVBA** という名前で、**Excel マクロ有効ブック \(\*.xlsm\)** として保存します。 このブックは、デスクトップなどの便利な場所に保存します。  
  
3.  リボンの **\[開発\]** タブをクリックします。  
  
    > [!NOTE]  
    >  **\[開発\]** タブが表示されていない場合は、最初にこれを表示する必要があります。 詳細については、「[方法 :タブをリボンに表示する](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)」を参照してください。  
  
4.  **\[コード\]** グループの **\[Visual Basic\]** をクリックします。  
  
     Visual Basic エディターが開きます。  
  
5.  **\[プロジェクト\]** ウィンドウで、**\[ThisWorkbook\]** をダブルクリックします。  
  
     `ThisWorkbook` オブジェクトのコード ファイルが開きます。  
  
6.  コード ファイルに次の VBA コードを追加します。 このコードは何も実行しない単純な関数を定義します。 この関数の唯一の目的は、VBA プロジェクトがブック内に確実に存在するようにすることです。 これは、このチュートリアルの後の手順に必要です。  
  
    ```  
    Sub EmptySub() End Sub  
    ```  
  
7.  ドキュメントを保存して、Excel を終了します。  
  
## プロジェクトの作成  
 これで、先ほど作成したマクロ対応のブックを使用する、Excel のドキュメント レベルのプロジェクトを作成できます。  
  
#### 新しいプロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を起動します。  
  
2.  **\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックします。  
  
3.  テンプレート ウィンドウで、**\[Visual C\#\]** を展開してから、**\[Office\/SharePoint\]** を展開します。  
  
4.  **\[Office アドイン\]** ノードを選択します。  
  
5.  プロジェクト テンプレートのリストで、**\[Excel 2010 ブック\]** または **\[Excel 2013 ブック\]** プロジェクトを選択します。  
  
6.  **\[名前\]** ボックスに、「**CallingCodeFromVBA**」と入力します。  
  
7.  **\[OK\]** をクリックします。  
  
     **Visual Studio Tools for Office プロジェクト ウィザード**が開きます。  
  
8.  **\[既存のドキュメントをコピーする\]** を選択し、**\[既存のドキュメントの完全なパス\]** ボックスで、先ほど作成した  **WorkbookWithVBA** ブックの場所を指定します。 独自のマクロ対応ブックを使用している場合は、代わりにそのブックの場所を指定します。  
  
9. **\[完了\]** をクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] はデザイナーで **WorkbookWithVBA** ブックを開き、**ソリューション エクスプローラー**に **CallingCodeFromVBA** プロジェクトを追加します。  
  
## ブックの場所を信頼する  
 ソリューションのコードをブック内の VBA コードに公開する前に、実行するブック内の VBA を信頼する必要があります。 これにはいくつかの方法があります。 このチュートリアルでは、ブックの場所を Excel の**セキュリティ センター**で信頼することにより、この作業を実行します。  
  
#### ブックの場所を信頼するには  
  
1.  Excel を起動します。  
  
2.  **\[ファイル\]** タブをクリックします。  
  
3.  **\[Excel のオプション\]** ボタンをクリックします。  
  
4.  \[カテゴリ\] ウィンドウで **\[セキュリティ センター\]** をクリックします。  
  
5.  詳細ウィンドウで **\[セキュリティ センターの設定\]** をクリックします。  
  
6.  \[カテゴリ\] ウィンドウで **\[信頼できる場所\]** をクリックします。  
  
7.  詳細ウィンドウで **\[新しい場所の追加\]** をクリックします。  
  
8.  **\[Microsoft Office の信頼できる場所\]** ダイアログ ボックスで、**CallingCodeFromVBA** プロジェクトを含むフォルダーを参照します。  
  
9. **\[この場所のサブフォルダも信頼する\]** を選択します。  
  
10. **\[Microsoft Office の信頼できる場所\]** ダイアログ ボックスで、**\[OK\]** をクリックします。  
  
11. **\[セキュリティ センター\]** ダイアログ ボックスで **\[OK\]** をクリックします。  
  
12. **\[Excel のオプション\]** ダイアログ ボックスで **\[OK\]** をクリックします。  
  
13. **Excel** を終了します。  
  
## Sheet1 クラスにメソッドを追加する  
 VBA プロジェクトのセットアップができたので、今度は VBA コードから呼び出すことのできる `Sheet1` ホスト項目クラスにパブリック メソッドを追加します。  
  
#### Sheet1 クラスにメソッドを追加するには  
  
1.  **ソリューション エクスプローラー**で **Sheet1.cs** を右クリックし、**\[コードの表示\]** をクリックします。  
  
     コード エディターで **Sheet1.cs** ファイルが開きます。  
  
2.  `Sheet1` クラスに次のコードを追加します。`CreateVstoNamedRange` メソッドは指定された範囲に新しい <xref:Microsoft.Office.Tools.Excel.NamedRange> オブジェクトを作成します。 このメソッドにより、<xref:Microsoft.Office.Tools.Excel.NamedRange> の <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected> イベントのイベント ハンドラーも作成されます。 このチュートリアルの後半では、ドキュメント内の VBA コードからこの `CreateVstoNamedRange` メソッドを呼び出します。  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CallingCSCustomizationFromVBA/CS/Sheet1.cs#2)]  
  
3.  `Sheet1` クラスに次のメソッドを追加します。 このメソッドは <xref:Microsoft.Office.Tools.Excel.Worksheet.GetAutomationObject%2A> メソッドをオーバーライドして、`Sheet1` クラスの現在のインスタンスを返します。  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CallingCSCustomizationFromVBA/CS/Sheet1.cs#3)]  
  
4.  `Sheet1` クラスの宣言の最初の行の前で、次の属性を適用します。 これらの属性によってクラスが COM で表示されるようになりますが、クラスのインターフェイスは生成されません。  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CallingCSCustomizationFromVBA/CS/Sheet1.cs#1)]  
  
## Sheet1 クラスのインターフェイスを抽出する  
 `CreateVstoNamedRange` メソッドを VBA コードに公開する前に、このメソッドを定義するパブリック インターフェイスを作成し、そのインターフェイスを COM に公開する必要があります  
  
#### Sheet1 クラスのインターフェイスを抽出するには  
  
1.  **Sheet1.cs** コード ファイルで、`Sheet1` クラスの任意の場所をクリックします。  
  
2.  **\[リファクター\]** メニューの **\[インターフェイスの抽出\]** をクリックします。  
  
3.  **\[インターフェイスの抽出\]** ダイアログ ボックスの **\[インターフェイスを形成するパブリック メンバーを選択してください\]** ボックスで、`CreateVstoNamedRange` メソッドのエントリをクリックします。  
  
4.  **\[OK\]** をクリックします。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] により、`ISheet1` という名前の新しいインターフェイスが生成され、`ISheet1` インターフェイスを実装できるように `Sheet1` クラスの定義が変更されます。 また、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] によりコード エディターで **ISheet1.cs** ファイルが開きます。  
  
5.  **ISheet1.cs** ファイルで、`ISheet1` インターフェイス宣言を次のコードで置き換えます。 このコードにより、`ISheet1` インターフェイスはパブリック インターフェイスになり、<xref:System.Runtime.InteropServices.ComVisibleAttribute> 属性が適用されて、インターフェイスが COM で表示されるようになります。  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CallingCSCustomizationFromVBA/CS/ISheet1.cs#4)]  
  
6.  プロジェクトをビルドします。  
  
## VBA コードにメソッドを公開する  
 `CreateVstoNamedRange` メソッドをブック内の VBA コードに公開するには、`Sheet1`ホスト項目の **ReferenceAssemblyFromVbaProject** プロパティを **True** に設定します。  
  
#### メソッドを VBA コードに公開するには  
  
1.  **ソリューション エクスプローラー**で、**Sheet1.cs** をダブルクリックします。  
  
     デザイナーで **WorkbookWithVBA** ファイルが開き、Sheet1 が表示されます。  
  
2.  **\[プロパティ\]** ウィンドウで、**ReferenceAssemblyFromVbaProject** プロパティを選択し、値を **True** に変更します。  
  
3.  表示されるメッセージで **\[OK\]** をクリックします。  
  
4.  プロジェクトをビルドします。  
  
## VBA コードからメソッドを呼び出す  
 これで、ブック内の VBA コードから `CreateVstoNamedRange` メソッドを呼び出せます。  
  
> [!NOTE]  
>  このチュートリアルでは、プロジェクトのデバッグ中に VBA コードをブックに追加します。 Visual Studio はビルド出力フォルダー内のドキュメントをメイン プロジェクト フォルダーからのドキュメントのコピーで置き換えるので、このドキュメントに追加したすべての VBA コードは次にプロジェクトをビルドすると上書きされます。 VBA コードを保存したい場合は、プロジェクト フォルダー内のドキュメントにコピーします。 詳細については、「[VBA とドキュメント レベルのカスタマイズの結合](../vsto/combining-vba-and-document-level-customizations.md)」を参照してください。  
  
#### VBA コードからメソッドを呼び出すには  
  
1.  F5 キーを押してプロジェクトを実行します。  
  
2.  **\[開発者\]** タブで、**\[コード\]** グループの、**\[Visual Basic\]** をクリックします。  
  
     Visual Basic エディターが開きます。  
  
3.  **\[挿入\]** メニューで **\[モジュール\]** をクリックします。  
  
4.  次のコードを新しいモジュールに追加します。  
  
     このコードはカスタマイズ アセンブリの `CreateTable` メソッドを呼び出します。 マクロは VBA コードに公開する `Sheet1` ホスト項目クラスにアクセスするために、グローバル `GetManagedClass` メソッドを使用してこのメソッドにアクセスします。`GetManagedClass` メソッドは、このチュートリアルで先ほど **ReferenceAssemblyFromVbaProject** プロパティを設定したときに自動的に生成されたものです。  
  
    ```  
    Sub CallVSTOMethod() Dim VSTOSheet1 As CallingCodeFromVBA.Sheet1 Set VSTOSheet1 = GetManagedClass(Sheet1) Call VSTOSheet1.CreateVstoNamedRange(Sheet1.Range("A1"), "VstoNamedRange") End Sub  
    ```  
  
5.  F5 キーを押します。  
  
6.  開いたブックで **Sheet1** のセル **A1** をクリックします。 メッセージ ボックスが表示されることを確認します。  
  
7.  変更を保存せずに Excel を終了します。  
  
## 次の手順  
 Office ソリューションでの VBA からのコード呼び出しについて詳しくは、次のトピックを参照してください。  
  
-   VBA から Visual Basic カスタマイズのホスト項目のコードを呼び出します。 このプロセスは、Visual C\# のプロセスとは異なります。 詳細については、「[チュートリアル : VBA から Visual Basic プロジェクトのコードを呼び出す](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)」を参照してください。  
  
-   VBA から VSTO アドインのコードを呼び出します。 詳細については、「[チュートリアル : VSTO アドインのコードを VBA から呼び出す](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)」を参照してください。  
  
## 参照  
 [VBA とドキュメント レベルのカスタマイズの結合](../vsto/combining-vba-and-document-level-customizations.md)   
 [ドキュメント レベルのカスタマイズのプログラミング](../vsto/programming-document-level-customizations.md)   
 [方法 : Visual Basic プロジェクトのコードを VBA に公開する](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)   
 [方法 : Visual C&#35; プロジェクトのコードを VBA に公開する](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)   
 [チュートリアル : VBA から Visual Basic プロジェクトのコードを呼び出す](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)  
  
  
---
title: "ソリューションとプロジェクトを作成する | Microsoft Docs"
ms.custom: 
ms.date: 03/21/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.openprojectfromweb
- vs.newproject
- VS.ToolsOptionsPages.Projects.General
- SolutionItemsProject
helpviewer_keywords:
- solutions [Visual Studio], deleting
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
ms.assetid: 836f8ca0-3fc9-4f4b-9090-45f2e4d2e9c8
caps.latest.revision: 46
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 06cdfb076120ffd7459a16b56c659bb86942cd7f
ms.openlocfilehash: 21b27861fd935c882418723d8cc60872fe71473e
ms.lasthandoff: 03/31/2017

---
# <a name="create-solutions-and-projects"></a>ソリューションとプロジェクトを作成する
プロジェクトは、アプリケーションをビルドするのに必要なものすべての論理的なコンテナーです。 メイン メニューから **[ファイル]**、**[新規作成]**、**[プロジェクト]** を選択してプロジェクトを作成するとき、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] はプロジェクトを含むソリューションを作成します。 その後、必要に応じて新規または既存のプロジェクトをソリューションにさらに追加できます。 既存のコード ファイルからプロジェクトを作成することができますし、作業が終った時に削除する一時プロジェクト (.NET のみ) を作成することもできます。

> [!NOTE]
>  このトピックの説明は、Visual Studio Community エディション に基づいています。 実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、使用中の設定または Visual Studio のエディションによっては、この中の説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide)」を参照してください。

## <a name="create-a-project-from-an-installed-project-template"></a>インストールされたプロジェクト テンプレートからプロジェクトを作成する  
 メイン メニューで **[ファイル]**、**[新規作成]**、**[プロジェクト]** の順に選択して、[新しいプロジェクト] ダイアログを表示します。 **[インストール済み]** の **[テンプレート]** の下にある左のペインで、プログラミング言語とプラットフォームまたはテクノロジを選択します。それから、中央のペインで、使用可能なテンプレートを選択します。  

 **[新しいプロジェクト]** ダイアログでは、 **[ソリューション]** ドロップダウンで、新規プロジェクトを新規または既存のソリューションに作成するか、または Visual Studio の新しいインスタンスに作成するかについてのオプションが選べます。  

## <a name="create-a-project-from-existing-code-files"></a>既存のコード ファイルからプロジェクトを作成する  
 制約の緩いソース ファイルのコレクションがあれば、それらを含むプロジェクトを簡単に作成できます。 **[ファイル]**、**[新規作成]**、**[既存のコードからプロジェクトを作成]** の順に選択して、**[既存コード ファイルからの新しいプロジェクトの作成]** ウィザードを開始し、指示に従います。  

> [!TIP]
>  このオプションは、比較的単純なファイルのコレクションに最適です。  

## <a name="create-a-temporary-project-c-and-visual-basic"></a>一時プロジェクト (C# および Visual Basic) を作成する
 一時プロジェクトで作業することにより、ディスクの場所を指定しなくても、.NET プロジェクトを作成して試してみることができます。 プロジェクトを作成するとき、プロジェクトの種類とテンプレートを選択し、 **[新しいプロジェクト]** ダイアログ ボックスに名前を指定するだけでかまいません。 一時プロジェクトの作業中いつでも、プロジェクトを保存したり破棄できます。  

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>.NET Framework の特定のバージョンを対象とする .NET プロジェクトの作成  
 **[新しいプロジェクト]** ダイアログ ボックスの上部にある **[.NET Framework]** バージョンのドロップダウン メニューを使用して、.NET Framework の旧バージョンを対象とするプロジェクトを作成することもできます。 このバージョンの .NET Framework と互換性のあるテンプレートのみが一覧に表示されるため、プロジェクト テンプレートを選択する前にこの値を設定します。  

 4 以前のバージョンの .NET Framework にアクセスするには、.NET Framework 3.5 がシステムにインストールされている必要があります。  

## <a name="download-sample-solutions"></a>サンプル ソリューションのダウンロード  
 Visual Studio を使用して、[MSDN コード ギャラリー](http://go.microsoft.com/fwlink/?LinkId=254185)やその他のソース (Git リポジトリなど) から、サンプル ソリューションをダウンロードしてインストールすることができます。

 サンプルを個別にダウンロードすることも、テクノロジやトピックを共有する関連サンプルが含まれたサンプル パックをダウンロードすることもできます。 ダウンロードしたサンプルについてソース コードの変更が発行された場合は、そのことが通知されます。  

 詳細については、「[Visual Studio のサンプル](../ide/visual-studio-samples.md)」を参照してください。  

## <a name="add-single-files-at-the-solution-level"></a>ソリューション レベルで 1 つのファイルを追加  
 複数のプロジェクトが 1 つのファイルを参照することがあります。または、特定のプロジェクトの下ではなく、ソリューション レベルで論理的に属するテキストまたはその他のデータが 1 つのファイルに含まれていることがあります。  1 つの項目を 1 つのソリューションに追加するには:  

- **ソリューション エクスプローラー**でソリューション ノードを右クリックし、**[追加]**、**[新しい項目]** の順に選択するか、**[追加]**、**[既存の項目]** の順に選択します。  

## <a name="create-empty-solutions"></a>空のソリューションの作成  
 1 つのソリューションには複数のプロジェクトを含めることができます。一方、プロジェクトを含まないソリューションも作成できます。 また、ソリューションがなくてもコード プロジェクトを開くことができます。

#### <a name="to-create-an-empty-solution"></a>空のソリューションを作成するには  

1.  **[ファイル]** メニューで、**[新規作成]**、**[新しいプロジェクト]**の順に選択します。  

2.  左側のウィンドウで、**[インストール済み]**、**[その他のプロジェクトの種類]**、展開された一覧の **[Visual Studio ソリューション]** の順に選択します。  

3.  中央のペインで、**[空のソリューション]** を選択します。  

4.  ソリューションの **[名前]** と **[場所]** の値を設定し、**[OK]** を選択します。  

空のソリューションの作成後、**[プロジェクト]** メニューの **[新しい項目の追加]** または **[既存項目の追加]** を選んで、新規または既存のプロジェクトや項目を追加できます。

### <a name="delete-solutions"></a>ソリューションの削除  
 ソリューションを完全に削除することもできますが、その場合は、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] は使用しません。 ソリューションを削除する前に、別のソリューションで再利用するプロジェクトはすべて移動しておいてください。 次に、ファイル エクスプローラーを使用して、.sln および .suo ソリューション ファイルのあるディレクトリを削除します。  

> [!NOTE]
>  .suo ファイルは隠しファイルであり、ファイル エクスプローラーの既定の設定では表示されません。  

##### <a name="to-delete-a-solution"></a>ソリューションを削除するには  

1.  **ソリューション エクスプローラー**で、削除するソリューションのコンテキスト (右クリック) メニューから **[エクスプローラーでフォルダーを開く]** を選択します。

2.  ファイル エクスプローラーで、1 つ上の階層に移動します。

3.  ソリューションのあるディレクトリを選択し、Del キーを押します。

## <a name="see-also"></a>関連項目  
 [ソリューションおよびプロジェクト](../ide/solutions-and-projects-in-visual-studio.md)   

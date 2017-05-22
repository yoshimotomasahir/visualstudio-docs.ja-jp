---
title: "[オプション]、[テキスト エディター]、[すべての言語] | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Text_Editor.JavaScript.General"
  - "VS.ToolsOptionsPages.Text_Editor.ResJSON.General"
  - "vs.toolsoptionspages.text_editor.all_languages.scrollbars"
helpviewer_keywords: 
  - "[テキスト エディター] ([オプション] ダイアログ ボックス)"
  - "ステートメント入力候補"
  - "ワード ラップ"
  - "[全般] ダイアログ ボックス"
  - "行番号"
  - "仮想空間"
ms.assetid: 49ee7306-9d46-4170-850f-a1716171752d
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# [オプション]、[テキスト エディター]、[すべての言語]
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

このダイアログ ボックスを使用すると、コード エディターの既定の動作を変更できます。  これらの設定は、HTML デザイナーの \[ソース\] ビューなど、コード エディターを基にした他のエディターにも適用されます。  このダイアログ ボックスを表示するには、**\[ツール\]** メニューの **\[オプション\]** をクリックします。  **\[テキスト エディター\]** フォルダーで、**\[すべての言語\]** サブフォルダーを展開し、**\[全般\]** を選択します。  
  
> [!CAUTION]
>  このページでは、すべての開発言語に適用される既定のオプションを設定できます。  このダイアログ ボックスでオプションをリセットすると、すべての言語の \[全般\] のオプションが、ここで選択された内容に基づいてリセットされる点に注意してください。  1 つの言語についてのみテキスト エディターのオプションを変更するには、その言語のサブフォルダーを展開して、対応するオプション ページを選択します。  
  
 一部のプログラミング言語の \[全般\] オプション ページでのみ選択されているオプションには、チェック マークが淡色表示されます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## \[入力候補\]  
 \[自動メンバー表示\]  
 選択した場合、エディターでの入力時に、使用可能なメンバー、プロパティ、値、またはメソッドのポップアップ リストが自動的に表示されます。  ポップアップ リストで項目を選択すると、その項目がコードに挿入されます。  このオプションを選択すると、**\[メンバーの詳細を非表示\]** オプションが有効になります。  
  
 \[メンバーの詳細を非表示\]  
 選択した場合、ステートメント入力候補のポップアップ リストが簡略化され、使用頻度の高い項目だけが表示されます。  その他の項目は、リストに表示されません。  
  
 \[パラメーター ヒント\]  
 選択した場合、エディターのカーソル位置の下に、現在の宣言またはプロシージャの完全な構文と、対応するすべてのパラメーターが表示されます。  次に割り当て可能なパラメーターは、太字で表示されます。  
  
## 設定  
 \[仮想空間を使用\]  
 このオプションを選択し、**\[右端で折り返す\]** を選択しない場合、コード エディターで行末より右側にある任意の領域から入力を開始できます。  この機能を使用すると、コードの横の一貫した位置にコメントを配置できます。  
  
 \[右端で折り返す\]  
 選択した場合、エディターの表示領域を越えた部分は自動的に次の行に折り返して表示されます。  このオプションを選択すると、**\[右端の折り返しの記号を表示する\]** オプションが有効になります。  
  
> [!NOTE]
>  **\[右端で折り返す\]** を有効にすると、**\[仮想空間を使用\]** の機能は無効になります。  
  
 \[右端の折り返しの記号を表示する\]  
 選択した場合、複数行にわたる長い行には改行インジケーターが表示されます。  
  
 インジケーターを表示しない場合は、このオプションを解除します。  
  
> [!NOTE]
>  このような注意を促すための矢印は、コードに追加されたり、印刷されたりすることはありません。  これらは参照専用です。  
  
 \[選択領域がない場合は、切り取りまたはコピー コマンドを空白行に適用する\]  
 空白行に挿入ポインターを置き、何も選択せずにコピーまたは切り取り操作を行った場合のエディターの動作を設定するオプションです。  
  
-   このオプションを選択した場合、空白行のコピーと切り取りが可能になります。  貼り付けコマンドを実行すると、新しい空白行が挿入されます。  
  
-   このオプションがオフの場合、切り取りコマンドにより空白行が削除されます。  ただし、クリップボードのデータは維持されます。  このため、その後に貼り付けコマンドを実行すると、最後にクリップボードにコピーされた内容が貼り付けられます。  前にコピーされた内容がない場合、貼り付けは行われません。  
  
 この設定は、空白行以外の行のコピーまたは切り取り操作には影響しません。  何も選択されていない場合は、行全体のコピーまたは切り取りが行われます。  その後で貼り付けコマンドを実行すると、行全体およびその行末文字が貼り付けられます。  
  
> [!TIP]
>  空白、タブ、および行末のインジケーターを表示し、インデントの設定された行と、空白行とを区別できるようにするには、**\[編集\]** メニューの **\[詳細\]** をクリックし、**\[スペースの表示\]** を選択します。  
  
## 表示  
 \[行番号\]  
 選択した場合、各コード行の横に行番号が表示されます。  
  
> [!NOTE]
>  行番号は、コードには追加されず、印刷もされません。  これらは参照専用です。  
  
 \[シングル クリックでの URL ナビゲーションを有効にする\]  
 選択した場合、エディターでマウスのカーソルを URL に合わせると、カーソルが手の形に変わります。  URL をクリックすると、示されているページが Web ブラウザーに表示されます。  
  
 \[ナビゲーション バー\]  
 選択した場合、コード エディターの一番上に**ナビゲーション バー**が表示されます。  **\[オブジェクト\]** と **\[メンバー\]** のドロップダウン リストを使用すると、コード中の特定のオブジェクトおよび対応するメンバーを選択して、コード エディター上で、選択されたメンバーの宣言に移動できます。  
  
## 参照  
 [\[オプション\]、\[テキスト エディター\]、\[すべての言語\]、\[タブ\]](../../ide/reference/options-text-editor-all-languages-tabs.md)   
 [\[全般\] \(\[オプション\] ダイアログ ボックス \- \[環境\]\)](../Topic/General,%20Environment,%20Options%20Dialog%20Box.md)   
 [IntelliSense の使用方法](../../ide/using-intellisense.md)
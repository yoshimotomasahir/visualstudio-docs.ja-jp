---
title: "方法 : インポートした名前空間を追加または削除する (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "追加 (インポートされた名前空間を)"
  - "インポートされた名前空間 [Visual Studio]"
  - "名前空間 [Visual Studio], インポートされた"
  - "参照 [Visual Studio], インポートされた名前空間"
  - "削除 (インポートされた名前空間を)"
ms.assetid: 44cebec3-0ea0-47c2-8406-4edeab6a997e
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# 方法 : インポートした名前空間を追加または削除する (Visual Basic)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

名前空間をインポートすると、完全に限定しなくとも、コード内でその名前空間の要素を使用できるようになります。  たとえば、`System.Messaging.MessageQueue` クラスの `Create` メソッドにアクセスする場合は、`System.Messaging` 名前空間をインポートすると、コード内に `MessageQueue.Create` と指定するだけで、必要な要素を参照できます。  
  
 インポートした名前空間は、**プロジェクト デザイナー**の **\[参照設定\]** ページで管理されます。  このダイアログ ボックスで指定するインポート情報は、直接コンパイラに渡され \(`/imports`\)、プロジェクトのすべてのファイルに適用されます。  単一のソース コード ファイル内で名前空間を使用するには、`Imports` ステートメントを使用します。  
  
### インポートした名前空間を追加するには  
  
1.  **ソリューション エクスプローラー**で、対象のプロジェクトの **\[My Project\]** ノードをダブルクリックします。  
  
2.  **プロジェクト デザイナー**で、**\[参照設定\]** タブをクリックします。  
  
3.  **\[インポートされた名前空間\]** ボックスで、追加する名前空間のチェック ボックスをオンにします。  
  
    > [!NOTE]
    >  インポートするためには、目的の名前空間が、参照先コンポーネント内に存在する必要があります。  名前空間が一覧に表示されない場合は、その名前空間を含むコンポーネントへの参照を追加する必要があります。  詳細については、「[方法: &#91;参照の追加&#93; ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/ja-jp/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)」を参照してください。  
  
### インポートした名前空間を削除するには  
  
1.  **ソリューション エクスプローラー**で、対象のプロジェクトの **\[My Project\]** ノードをダブルクリックします。  
  
2.  **プロジェクト デザイナー**で、**\[参照設定\]** タブをクリックします。  
  
3.  **\[インポートされた名前空間\]** ボックスで、削除する名前空間のチェック ボックスをオフにします。  
  
## ユーザー インポート  
 ユーザー インポートでは、名前空間全体ではなく、名前空間内の特定のクラスをインポートできます。  たとえば、アプリケーションで `Systems.Diagnostics` 名前空間のインポートが存在する場合に、この名前空間にある `Debug` クラスだけが必要な場合があります。  この場合には、`System.Diagnostics.Debug` をユーザー インポートとして定義し、`System.Diagnostics` のインポートを削除できます。  
  
 後で方針を変更し、実際には `EventLog` クラスが必要になった場合、`System.Diagnostics.EventLog` クラスをユーザー インポートとして入力し、更新機能を使用して `System.Diagnostics.Debug` を上書きできます。  
  
#### ユーザー インポートを追加するには  
  
1.  **ソリューション エクスプローラー**で、対象のプロジェクトの **\[My Project\]** ノードをダブルクリックします。  
  
2.  **プロジェクト デザイナー**で、**\[参照設定\]** タブをクリックします。  
  
3.  **\[インポートされた名前空間\]** ボックスの下のテキスト ボックスに、インポートする名前空間の名前を、ルート名前空間を含む完全名で入力します。  
  
4.  **\[ユーザー インポートの追加\]** をクリックして、名前空間を **\[インポートされた名前空間\]** ボックスに追加します。  
  
    > [!NOTE]
    >  指定した名前空間が一覧にある名前空間の 1 つと一致する場合には、**\[ユーザー インポートの追加\]** ボタンは無効になります。同じインポートを 2 回追加することはできません。  
  
#### ユーザー インポートを更新するには  
  
1.  **ソリューション エクスプローラー**で、対象のプロジェクトの **\[My Project\]** ノードをダブルクリックします。  
  
2.  **プロジェクト デザイナー**で、**\[参照設定\]** タブをクリックします。  
  
3.  **\[インポートされた名前空間\]** ボックスで、変更する名前空間をオンにします。  
  
4.  **\[インポートされた名前空間\]** ボックスの下のテキスト ボックスに、新しい名前空間の名前を入力します。  
  
5.  **\[ユーザー インポートの更新\]** をクリックして、**\[インポートされた名前空間\]** ボックスの名前空間を更新します。  
  
## 参照  
 [プロジェクト内の参照の管理](../ide/managing-references-in-a-project.md)
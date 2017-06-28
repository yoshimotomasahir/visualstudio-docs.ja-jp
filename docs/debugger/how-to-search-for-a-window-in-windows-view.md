---
title: "How to: Search for a Window in Windows View | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "windows, searching in Windows view"
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# How to: Search for a Window in Windows View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ウィンドウ ビューでは、ウィンドウのハンドル、キャプション、クラス、またはキャプションとクラスの組み合わせを検索条件として使用して、特定のウィンドウを検索できます。  検索の最初の方向を指定することもできます。  ダイアログ ボックスのフィールドには、ウィンドウ ツリーで選択したウィンドウの属性が表示されます。  
  
 デスクトップ レベルのウィンドウをクラス名とタイトルで識別できるように、2 番目のレベル \(デスクトップの子のすべてのウィンドウ\) まで展開されたツリーから開始してください。  デスクトップ レベルのウィンドウを選択したら、そのレベルを展開して特定の子ウィンドウを探すことができます。  
  
### ウィンドウ ビューでウィンドウを検索するには  
  
1.  Spy\+\+、[ウィンドウ ビュー](../debugger/windows-view.md) ウィンドウ、および対象のウィンドウが表示されるように、ウィンドウの位置を調整します。  
  
2.  \[検索\] メニューの \[ウィンドウ検索\] をクリックします。  
  
     [&#91;ウィンドウ検索&#93; ダイアログ ボックス](../debugger/window-search-dialog-box.md)が開きます。  
  
    > [!TIP]
    >  画面を見やすくするには、\[Spy\+\+ を非表示\] チェック ボックスをオンにします。  このチェック ボックスをオンにすると、Spy\+\+ のメイン ウィンドウが非表示になり、\[ウィンドウ検索\] ダイアログ ボックスだけがそのまま他のアプリケーションの前面に表示された状態になります。  \[OK\] または \[キャンセル\] をクリックするか、\[Spy\+\+ を非表示\] チェック ボックスをオフにすると、Spy\+\+ のメイン ウィンドウが元に戻ります。  
  
3.  ファインダー ツールを対象のウィンドウの上にドラッグします。  ツールをドラッグすると、\[ウィンドウ検索\] ダイアログ ボックスに選択したウィンドウの詳細が表示されます。  
  
     または  
  
     デバッガーで調べたりして、目的のウィンドウのハンドルがわかっている場合は、それを \[ハンドル\] ボックスに入力できます。  
  
     または  
  
     目的のウィンドウのキャプションとクラスのどちらか一方または両方がわかっている場合は、それを \[キャプション\] ボックスと \[クラス\] ボックスに入力し、\[ハンドル\] ボックスは空白にすることができます。  
  
4.  検索の最初の方向として、\[上へ\] または \[下へ\] を選択します。  
  
5.  **\[OK\]** をクリックします。  
  
     一致するウィンドウが見つかると、それが[ウィンドウ ビュー](../debugger/windows-view.md) ウィンドウで強調表示されます。
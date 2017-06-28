---
title: "方法: 生成されたコードに対するコード分析の警告を抑制する | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法: 生成されたコードに対するコード分析の警告を抑制する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

マネージ コード コンパイラでは、多くの場合、迅速にコードを開発できるようにプロジェクトに追加されるコードが生成されます。  さらに、開発者は、短時間でアプリケーションを開発するのに役立つサードパーティ ツールを使用することがよくあります。  これらのツールでも、プロジェクトに追加されるコードが生成されます。  
  
 生成されたコード内でコード分析が検出した規則違反が表示される場合があります。  ただし、違反を含むコードを表示および保持できない場合は、違反が表示されないことがあります。  
  
 プロジェクトの \[コード分析\] プロパティ ページの **\[生成されたコードから結果を表示しない\]** チェック ボックスを使用すると、サードパーティ ツールで生成されたコードからコード分析の警告を表示するかどうかを選択できます。  
  
> [!NOTE]
>  コード分析のエラーおよび警告がフォームやテンプレートで表示される場合、このオプションを使用すると、生成されたコードからこのエラーおよび警告が表示されなくなります。  フォームまたはテンプレートのソース コードは表示することも保持することもできます。  
  
### プロジェクトで生成されたコードに対する警告を抑制するには  
  
1.  ソリューション エクスプローラーでプロジェクトを右クリックし、**\[プロパティ\]** をクリックします。  
  
2.  **\[コード分析\]** をクリックします。  
  
3.  **\[生成されたコードから結果を表示しない\]** チェック ボックスをオンにします。
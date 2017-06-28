---
title: "コード分析に関する問題のトラブルシューティング | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: 5
author: "erickson-doug"
ms.author: "douge"
manager: "douge"
caps.handback.revision: 5
---
# コード分析に関する問題のトラブルシューティング
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このトピックでは、次の Visual Studio コード分析の問題についてのトラブルシューティング情報を示します。  
  
-   [Visual Studio 2010 規則セットでの変更が以前のバージョンの Visual Studio に反映されない](#ChildRuleSetChangesInPreviousVersions)  
  
##  <a name="ChildRuleSetChangesInPreviousVersions"></a> Visual Studio 2010 規則セットでの変更が以前のバージョンの Visual Studio に反映されない  
 子規則セットを含む [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 規則セットを作成すると、子規則セットに対する変更が、旧バージョンの Visual Studio を使用するコンピューターで実行されるコード分析に適用されない場合があります。  この問題を解決するには、親規則セット、つまり子規則セットを含む規則セットを強制的に書き換える必要があります。  
  
1.  [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] で親規則セットを開きます。  
  
2.  規則の追加、削除などの変更を加え、規則セットを保存します。  
  
3.  規則セットを再度開き、変更を元に戻し、規則セットを再度保存します。  
  
## 参照  
 [アプリケーション品質の分析](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)   
 [マネージ コードの品質の分析](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [規則セットを使用したコード分析規則のグループ化](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
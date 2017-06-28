---
title: "IDiaStackWalkHelper::put_registerValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaStackWalkHelper2::put_registerValue メソッド"
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaStackWalkHelper::put_registerValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

レジスタの値を設定します。  
  
## 構文  
  
```cpp#  
HRESULT put_registerValue (   
   DWORD     index,  
   ULONGLONG NewVal  
);  
```  
  
#### パラメーター  
 `index`  
 \[入力\] に書き込むに [CV\_HREG\_e 列挙型](../../debugger/debug-interface-access/cv-hreg-e.md) のレジスタを指定する列挙体の値。  
  
 `NewVal`  
 \[入力\] 新しいレジスタの値。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 値のサイズにかかわらず実装は登録が保持するものだけを格納する必要があります。  たとえば8 ビット レジスタが指定した値から最小 8bit のみを保持します。  
  
## 参照  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [CV\_HREG\_e 列挙型](../../debugger/debug-interface-access/cv-hreg-e.md)
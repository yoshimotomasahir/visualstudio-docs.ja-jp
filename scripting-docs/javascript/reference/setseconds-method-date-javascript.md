---
title: "setSeconds メソッド (Date) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "setSeconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "seconds メソッド"
  - "setSeconds メソッド"
ms.assetid: 986ffa54-1db6-4af2-ab8b-8353f64f0b57
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# setSeconds メソッド (Date) (JavaScript)
`Date` オブジェクトの時刻の秒の部分を現地時間で設定します。  
  
## 構文  
  
```  
  
dateObj  
.setSeconds(  
numSeconds[, numMilli])   
```  
  
## パラメーター  
 `dateObj`  
 必須です。  任意の `Date` オブジェクトを指定します。  
  
 *numSeconds*  
 必須です。  設定する秒を表す数値を指定します。  
  
 `numMilli`  
 省略可能です。  設定するミリ秒を表す数値を指定します。  
  
## 解説  
 省略可能な引数を指定せずに、**set** で始まる名前の各メソッドを使用した場合、省略した設定の部分には対応する **get** で始まる名前のメソッドで返される値が設定されます。  たとえば、`numMilli` 引数を指定しない場合、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] は **getMilliseconds** メソッドが返する値を使用します。  
  
 世界協定時刻 \(UTC\) を使用して秒の値を設定するには、`setUTCSeconds` メソッドを使用します。  
  
 引数に有効範囲を超える値や負の値を指定すると、その値に応じて格納されている他の値が変更されます。  たとえば、格納されている日付が "Jan 5, 1996 00:00:00" の場合に **setSeconds\(150\)** メソッドを使用すると、日付は "Jan 5, 1996 00:02:30" に変更されます。  
  
 `setHours` メソッドを使用すると、時間、分、秒、ミリ秒を設定できます。  
  
## 使用例  
 `setSeconds` メソッドの使用例を次に示します。  
  
```javascript  
function SetSecondsDemo(nsec){  
   var d = new Date();         //Create Date object.  
   d.setSeconds(nsec);         //Set seconds.  
   var s = "Current setting is ";  
   s += d.toLocaleString();  
   return(s);                  //Return new setting.  
}  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **対象**: [Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getSeconds メソッド \(Date\)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [getUTCSeconds メソッド \(Date\)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [setUTCSeconds メソッド \(Date\)](../../javascript/reference/setutcseconds-method-date-javascript.md)
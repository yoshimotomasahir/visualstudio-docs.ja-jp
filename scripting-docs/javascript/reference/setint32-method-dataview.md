---
title: "setInt32 メソッド (DataView) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 07e5f068-0e3f-4c23-84b3-c72658d7f194
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# setInt32 メソッド (DataView)
指定されたビューの先頭からのバイト オフセット位置に Int32 値を設定します。  配置の制約はありません。オフセットにマルチバイト値が設定されている場合があります。  
  
## 構文  
  
```  
dataView.setInt32 (byteOffset, value, littleEndian);   
```  
  
## パラメーター  
 `byteOffset`  
 値が取得されるバッファーの位置。  
  
 `value`  
 設定する値。  
  
 `littleEndian`  
 省略可能です。  false または未定義の場合は、ビッグ エンディアンの値が書き込まれます。それ以外の場合はリトル エンディアンの値が書き込まれます。  
  
## 解説  
 これらのメソッドでは、ビューの終端を越えて書き込まれる場合に例外が発生します。  
  
## 使用例  
 次の例は、DataView の最初の Int32 を設定する方法を示します。  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setInt32(0, 9);  
        }  
    }  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]
---
title: IDebugFunctionPosition2 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugFunctionPosition2
helpviewer_keywords:
- IDebugFunctionPosition2 interface
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 73097a7133de095d72a6ae22b9aff701b52ef191
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugfunctionposition2"></a>IDebugFunctionPosition2
このインターフェイスは、ソース ドキュメント内の関数の抽象の位置を表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugFunctionPosition2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) では、ソース ドキュメント内の関数の位置を表すためには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスがの一部として提供される、 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)共用体 (具体的には、 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)構造) の一部で、さらに、 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)この構造を使用して、保留中のブレークポイントの作成に使用します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugFunctionPosition2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|この位置を基準には、関数の名前を取得します。|  
|[GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)|関数の先頭からのオフセットを取得します。|  
  
## <a name="remarks"></a>コメント  
 このインターフェイスによって表される位置は、テキスト ベース、具体的には、 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)構造体。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
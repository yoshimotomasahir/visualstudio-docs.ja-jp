---
title: "IDebugProcessEx2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 56483c55810f75042184439be9f0d7bcfb2d6836
ms.lasthandoff: 04/05/2017

---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
このインターフェイスにより、セッションのデバッグ マネージャー (SDM) にアタッチするか、プロセスからデタッチするプロセスに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugProcessEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 カスタム ポート業者と同じオブジェクトでこのインターフェイスを実装する、 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)にインターフェイスします。  
  
-   プロセスに接続されているセッションの追跡をサポート  
  
-   サポートのオート アタッチに複数のデバッグ エンジン  
  
 カスタム ポート サプライヤーは、選択した場合、このインターフェイスを実装できます。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
  
-   SDM 呼び出し[QueryInterface](/cpp/atl/queryinterface)上、`IDebugProcess2`インターフェイスをこのインターフェイスを取得します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugProcessEx2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[添付](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|セッションが今すぐ、プロセスをデバッグしているプロセスに通知します。|  
|[デタッチ](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|セッションが不要になった、プロセスをデバッグしているプロセスに通知します。|  
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|デバッグ エンジンの一覧については、プログラムのノードを追加します。|  
  
## <a name="remarks"></a>コメント  
 このインターフェイスは、SDM とプロセスの間にプライベートです。  
  
## <a name="requirements"></a>要件  
 ヘッダー: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
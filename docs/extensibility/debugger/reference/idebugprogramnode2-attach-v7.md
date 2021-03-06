---
title: IDebugProgramNode2::Attach_V7 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e77acd4091abd7da5c9d302fb4c4dd6eb66af379
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogramnode2attachv7"></a>IDebugProgramNode2::Attach_V7

> [!Note]
> 推奨されなくなりました。 使用しないでください。

## <a name="syntax"></a>構文

```cpp
HRESULT Attach_V7 (
   IDebugProgram2*       pMDMProgram,
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason
);
```

```csharp
int Attach_V7 (
   IDebugProgram2       pMDMProgram,
   IDebugEventCallback2 pCallback,
   uint                 dwReason
);
```

#### <a name="parameters"></a>パラメーター

`pMDMProgram` [in][IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)にアタッチするプログラムを表すインターフェイスです。

 `pCallback` [in][IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) SDM にデバッグ イベントを送信するために使用するインターフェイスです。

 `dwReason` [in]値、 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)列挙アタッチの理由を指定します。

## <a name="return-value"></a>戻り値

実装を常に返します`E_NOTIMPL`です。

## <a name="remarks"></a>コメント

> [!WARNING]
> Visual Studio 2005 の時点でこのメソッドは使用されなくを常に返す必要があります`E_NOTIMPL`です。 参照してください、 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)にアタッチできませんを示すために、[プログラム] ノードが必要な場合、または、[プログラム] ノードは、プログラムの設定だけで、その他の方法のためのインターフェイス`GUID`です。 それ以外の場合、実装、[アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)メソッドです。

## <a name="prior-to-visual-studio-2005"></a>Visual Studio 2005 より前

このメソッドは、DE がデバッグ中のプログラムのアドレス空間で実行している場合にのみに実装する必要があります。 それ以外の場合、このメソッドが返す`S_FALSE`です。

このメソッドが呼び出されたときに、DE を送信する必要があります、 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)イベント オブジェクトのこのインスタンスに既に送信されていない場合、 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)インターフェイスだけでなく[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)と[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)イベント オブジェクトです。 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)場合に、イベント オブジェクトが送信される、`dwReason`パラメーターは`ATTACH_REASON_LAUNCH`します。

呼び出す必要があります、DE、 [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)メソッドを[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)で指定されたオブジェクト、 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)イベント オブジェクト、およびそのアプリケーションの GUID を格納する必要がありますインスタンスのデータで、`IDebugProgram2`デによって実装されるオブジェクト。

## <a name="see-also"></a>関連項目

[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)  
[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)  
[添付](../../../extensibility/debugger/reference/idebugengine2-attach.md)  
[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)  
[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)  
[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)  
[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)  
[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)  
[ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
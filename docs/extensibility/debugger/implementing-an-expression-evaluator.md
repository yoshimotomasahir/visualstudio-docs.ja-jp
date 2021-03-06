---
title: 式エバリュエーターを実装する |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ed1df74c187b3f0a93e1a1ec84e8803bc164d223
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="implementing-an-expression-evaluator"></a>式エバリュエーターを実装します。
> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されなくなりました。 CLR 式エバリュエーターを実装する方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)です。  
  
 デバッグ エンジン (DE)、シンボル プロバイダー (SP)、バインダー オブジェクト、および、式エバリュエーター自体 (EE) の間の複雑な相互作用は、式を評価します。 これら 4 つのコンポーネントは、1 つのコンポーネントによって実装され、他で使用されるインターフェイスによって接続されます。  
  
 EE は、文字列の形式で DE から式を取得および解析または評価します。 EE は、DE で使用される、次のインターフェイスを実装します。  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
 EE は、シンボルとオブジェクトの値を取得、DE、によって提供される、バインダー オブジェクトを呼び出します。 EE は、デを実装する次のインターフェイスを使用します。  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
-   [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
-   [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
-   [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
-   [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
-   [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
 EE 実装[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)です。 `IDebugProperty2` ローカル変数、プリミティブまたは Visual Studio は、適切な情報を表示する、オブジェクトなど、式の評価の結果を記述するためのメカニズムを提供、**ローカル**、 **ウォッチ**、または**イミディ エイト**ウィンドウです。  
  
 SP は、情報のメッセージが表示されたら、DE、EE に付与されます。 SP では、アドレスと、次のインターフェイスとその派生物などのフィールドを表すインターフェイスを実装します。  
  
-   [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
 EE は、これらのインターフェイスのすべてを使用します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [式エバリュエーターの実装方法](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 式エバリュエーター (EE) の実装方法の 3 段階のプロセスを定義します。  
  
## <a name="see-also"></a>関連項目  
 [CLR 式エバリュエーターの書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
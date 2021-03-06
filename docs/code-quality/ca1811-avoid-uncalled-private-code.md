---
title: 'CA1811: 呼び出されていないプライベート コードを使用しません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUncalledPrivateCode
- CA1811
helpviewer_keywords:
- CA1811
- AvoidUncalledPrivateCode
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f37ef9cdc76b86d3ad3c18489f63fb5c340aa6a7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811: 呼び出されていないプライベート コードを使用しません
|||
|-|-|
|TypeName|AvoidUncalledPrivateCode|
|CheckId|CA1811|
|カテゴリ|Microsoft.Performance|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 プライベートまたは内部 (アセンブリ レベル) メンバーが呼び出し元アセンブリは、共通言語ランタイムによって呼び出されて、およびデリゲートでは呼び出されません。 次のメンバーは、このルールによってはチェックされません。

-   明示的なインターフェイス メンバー。

-   静的コンス トラクターです。

-   シリアル化コンス トラクターです。

-   マークされたメソッド<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>または<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>です。

-   オーバーライドであるメンバー。

## <a name="rule-description"></a>規則の説明
 このルールは、偽陽性のエントリ ポイントが発生した場合は、現在、規則のロジックによって識別されないレポートできます。 また、コンパイラは、アセンブリに noncallable コードを生成する可能性があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、noncallable コードを削除またはそれを呼び出すコードを追加します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告を抑制しても安全です。

## <a name="related-rules"></a>関連規則
 [CA1812: インスタンス化されていない内部クラスを使用しないでください](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: 使用されていないパラメーターをレビューします](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: 使用されていないローカルを削除します](../code-quality/ca1804-remove-unused-locals.md)
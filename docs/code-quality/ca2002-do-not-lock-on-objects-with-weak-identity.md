---
title: 'CA2002: ID が不十分なオブジェクトをロックしないでください'
ms.date: 01/31/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotLockOnObjectsWithWeakIdentity
- CA2002
helpviewer_keywords:
- CA2002
- DoNotLockOnObjectsWithWeakIdentity
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 7708f5e968fed8765ca27bff99d479957927440b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca2002-do-not-lock-on-objects-with-weak-identity"></a>CA2002: ID が不十分なオブジェクトをロックしないでください

|||
|-|-|
|TypeName|DoNotLockOnObjectsWithWeakIdentity|
|CheckId|CA2002|
|カテゴリ|Microsoft.Reliability|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因

スレッドは、id が不十分なオブジェクトのロックの取得を試みます。

## <a name="rule-description"></a>規則の説明

アプリケーション ドメインの境界を越えてオブジェクトに直接アクセスできる場合、そのオブジェクトの ID は不十分と表現されます。 スレッドで ID が不十分なオブジェクトをロックしようとすると、ブロックされることがあります。たとえば、異なるアプリケーション ドメインの別スレッドで、既に同じオブジェクトがロックされている場合です。

次の種類は、id は不十分と、ルールによってフラグが付けられます。

- <xref:System.String>

- 含む値の型の配列[整数型](/dotnet/csharp/language-reference/keywords/integral-types-table)、[浮動小数点型](/dotnet/csharp/language-reference/keywords/floating-point-types-table)、および<xref:System.Boolean>です。

- <xref:System.MarshalByRefObject>

- <xref:System.ExecutionEngineException>

- <xref:System.OutOfMemoryException>

- <xref:System.StackOverflowException>

- <xref:System.Reflection.MemberInfo>

- <xref:System.Reflection.ParameterInfo>

- <xref:System.Threading.Thread>

## <a name="how-to-fix-violations"></a>違反の修正方法

この規則違反を修正するには、[説明] セクションで、一覧に含まれていない型からオブジェクトを使用します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況

この規則による警告は抑制しないでください。

## <a name="related-rules"></a>関連規則

[CA2213: 破棄可能なフィールドは破棄されなければなりません](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

## <a name="example"></a>例

次の例は、ルールに違反しているオブジェクトのロックを示しています。

[!code-vb[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/VisualBasic/ca2002-do-not-lock-on-objects-with-weak-identity_1.vb)]
[!code-csharp[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/CSharp/ca2002-do-not-lock-on-objects-with-weak-identity_1.cs)]

## <a name="see-also"></a>関連項目

<xref:System.Threading.Monitor>
<xref:System.AppDomain>
[lock ステートメント (c#)](/dotnet/csharp/language-reference/keywords/lock-statement)
[SyncLock ステートメント (Visual Basic)](/dotnet/visual-basic/language-reference/statements/synclock-statement)
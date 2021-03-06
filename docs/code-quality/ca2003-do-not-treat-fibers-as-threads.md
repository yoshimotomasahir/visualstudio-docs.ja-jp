---
title: 'CA2003: ファイバーをスレッドとして扱いません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 799d0d04f8620c07be0583869eeba5dd760c7f70
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003: ファイバーをスレッドとして扱いません
|||
|-|-|
|TypeName|DoNotTreatFibersAsThreads|
|CheckId|CA2003|
|カテゴリ|Microsoft.Reliability|
|互換性に影響する変更点|なし|

## <a name="cause"></a>原因
 マネージ スレッドは Win32 スレッドとして扱われています。

## <a name="rule-description"></a>規則の説明
 マネージ スレッドが Win32 スレッドとは限りません。 ファイバーすることをお勧めします。 共通言語ランタイム (CLR) は、SQL によって所有されている実際のスレッドのコンテキストでファイバーとして、マネージ スレッドが実行されます。 これらのスレッドは、SQL Server プロセスの AppDomains ともデータベースで共有することができます。 マネージ スレッドのローカル記憶域が動作するが可能性がありますいないを使用するアンマネージ スレッド ローカル ストレージか、コードで実行される現在の OS スレッドもう一度前提としています。 などのスレッドのロケールの設定を変更することはできません。 呼び出す必要はありませんロケールなどの設定は変更 P/invoke ロックに入り、スレッドがロックを終了する必要がありますも必要なためです。 これができないため、ケース ファイバーを使用するときに、Win32 のクリティカル セクションとミュー テックスは SQL で使用できません。 ほとんどの状態は、System.Thread マネージ オブジェクトに安全に使用可能性があります。 これには、マネージ スレッド ローカル ストレージとのスレッドの現在のユーザー インターフェイス (UI) カルチャが含まれます。 ただし、モデル上の理由から、プログラミングのないことができますを SQL; を使用するときに、スレッドの現在のカルチャを変更するにはこれは、新しいアクセス許可を介して適用されます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 スレッドの使用状況を確認し、それに応じてコードを変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 このルールは抑制しないでください。
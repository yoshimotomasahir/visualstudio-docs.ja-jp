---
title: 選択したクラスは、1 つ以上の DataContext メソッドで戻り値の型として使用されているため、削除できません
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 76f7fcff3f05d38dff230799785e659417c6dcc1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>選択したクラスは、1 つ以上の DataContext メソッドで戻り値の型として使用されているため、削除できません

1 つ以上の <xref:System.Data.Linq.DataContext> メソッドの戻り値の型が、選択されたエンティティ クラスになっています。 <xref:System.Data.Linq.DataContext> メソッドの戻り値の型として使用されているエンティティ クラスを削除すると、プロジェクトのコンパイルに失敗する原因となります。 選択したエンティティ クラスを削除するには、そのエンティティ クラスを使用する <xref:System.Data.Linq.DataContext> メソッドを特定し、戻り値の型を別のエンティティ クラスに設定します。

戻り値の型を元に戻す<xref:System.Data.Linq.DataContext>元の自動生成された型をメソッドが最初に削除、<xref:System.Data.Linq.DataContext>メソッド ペインからメソッドからオブジェクトをドラッグして**サーバー エクスプ ローラー** / **データベース エクスプ ローラー**もう一度 O/R デザイナー。

## <a name="to-correct-this-error"></a>このエラーを解決するには

1. 識別<xref:System.Data.Linq.DataContext>を選択してエンティティ クラスを戻り値の型として使用するメソッド、<xref:System.Data.Linq.DataContext>メソッドにメソッド ペインを調べて、**戻り値の型**プロパティに、**プロパティ**ウィンドウ.

2. 設定、**戻り値の型**を別のエンティティ クラスまたは削除、<xref:System.Data.Linq.DataContext>メソッド ペインからのメソッドです。

## <a name="see-also"></a>関連項目

- [O/R デザイナーのメッセージ](../data-tools/o-r-designer-messages.md)
- [Visual Studio での LINQ to SQL ツールします。](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
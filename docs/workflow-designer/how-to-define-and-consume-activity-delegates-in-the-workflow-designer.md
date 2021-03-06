---
title: 'ワークフロー デザイナー - 方法: 定義およびアクティビティ デリゲートを使用します。'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 73bf61c845b0124a8350f61c161ded1cf0c80043
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>ワークフロー デザイナーでアクティビティ デリゲートを定義および使用する方法

.NET framework 4.5 には用の新しい既定のデザイナーが含まれています、<xref:System.Activities.Statements.InvokeDelegate>アクティビティ。 このデザイナーを使用すると、<xref:System.Activities.ActivityDelegate> や <xref:System.Activities.ActivityAction> など、<xref:System.Activities.ActivityFunc%601> から派生するアクティビティにデリゲートを割り当てることができます。

## <a name="define-an-activity-delegate"></a>アクティビティ デリゲートの定義

1.  Visual Studio で、次のように選択します。**ファイル**、**新規**、**プロジェクト**です。 選択、**ワークフロー** 、左側のノードと**ワークフロー コンソール アプリケーション**右側のテンプレートです。 (必要な場合)、プロジェクトの名前を指定し、をクリックして**Ok**です。

2.  プロジェクトを右クリックして**ソリューション エクスプ ローラー**選択**追加**、**新しい項目の追加.**.選択、**ワークフロー** 、左側のノードと**アクティビティ**右側のテンプレートです。 新しいアクティビティの名前を付けます**MyForEach.xaml**  をクリック**Ok**です。 ワークフロー デザイナーでアクティビティが開かれます。

3.  ワークフロー デザイナー内をクリックして、**引数**タブです。

4.  をクリックして**引数の作成**です。 新しい引数の名前を付けます**項目**です。

5.  **引数の型**列をオン**配列: [T]** です。

6.  型ブラウザーに次のように選択します。**オブジェクト**です。 Click **Ok**.

7.  をクリックして**引数の作成**もう一度です。 新しい引数の名前を付けます**本文**です。 **方向**列を選択、新しい引数を**プロパティ**です。

8.  引数の型 列を選択**型を参照しています.**

9. 型ブラウザーに次のように入力します。 **ActivityAction**で、**型名**フィールドです。 選択**ActivityAction\<T >** ツリー ビューでします。 選択**オブジェクト**タイプを割り当てるために表示されるドロップダウン リストに**ActivityAction\<オブジェクト >** 引数にします。

10. ドラッグ、<xref:System.Activities.Statements.While>からアクティビティを**制御フロー**デザイナー画面には、ツールボックスのセクションでします。

11. 選択、<xref:System.Activities.Statements.While>アクティビティ、および選択、**変数**タブです。

12. 選択**変数を作成**です。 新しい変数の名前**インデックス**です。

13. **変数型**列をオン**Int32**です。 ままにして、**スコープ**として**中**、および**既定**列は空白です。

14. 設定、**条件**のプロパティ、<xref:System.Activities.Statements.While>アクティビティを**インデックス < Items.Length;** です。

15. ドラッグ、<xref:System.Activities.Statements.InvokeDelegate>からアクティビティを**プリミティブ**にツールボックスのセクションで、**本文**の<xref:System.Activities.Statements.While>アクティビティ。

16. 選択**本文**デリゲートのドロップダウン リスト。

17. **プロパティ**のグリッド、<xref:System.Activities.Statements.InvokeDelegate>アクティビティをクリックして、**しています.** ボタンをクリックして、**デリゲート引数**プロパティです。

18. **値**という名前の引数の列**引数**、入力**Items [Index]** です。 をクリックして**Ok**を閉じる、 **DelegateArguments**ダイアログ。

19. <xref:System.Activities.Statements.Assign> アクティビティを <xref:System.Activities.Statements.InvokeDelegate> アクティビティの下の水平線にドラッグします。 <xref:System.Activities.Statements.Assign>アクティビティが作成され、および<xref:System.Activities.Statements.Sequence>アクティビティが 2 つのアクティビティを含めるように自動的に作成、**本文**のセクションで、 **MyForEach**アクティビティ。 ため、シーケンスが必要、**本文**セクションは 1 つのアクティビティのみを含めることができます。 自動的に新しいを作成する<xref:System.Activities.Statements.Sequence>アクティビティは、.NET Framework 4.5 の新機能です。

20. 設定、**に**のプロパティ、<xref:System.Activities.Statements.Assign>アクティビティを**インデックス**です。 設定、**値**のプロパティ、**割り当てる**アクティビティを**index+1**です。

 カスタム**MyForEach**アクティビティは、任意のアクティビティを通じてに渡された値ごとに 1 回呼び出し、**項目**をアクティビティの入力としてコレクション内の値のコレクション。

## <a name="use-the-custom-activity-in-a-workflow"></a>ワーク フローでのカスタム アクティビティの使用

1.  キーを押してプロジェクトをビルド**Ctrl + Shift + B**です。

2.  **ソリューション エクスプ ローラー**、開かれている**Workflow1.xaml**デザイナーでします。

3.  ドラッグ、 **MyForEach**アクティビティをツールボックスからデザイナー画面にします。 アクティビティは、プロジェクトと同じ名前のツールボックスのセクションにあります。

4.  設定、**項目**のプロパティ、 **MyForEach**アクティビティを**新しい object[] {1,"abc"}** です。

5.  ドラッグ、<xref:System.Activities.Statements.WriteLine>からアクティビティ、**プリミティブ**にツールボックスのセクションで、**デリゲートの本体:** のセクションで、 **MyForEach**アクティビティ。

6.  設定、**テキスト**のプロパティ、<xref:System.Activities.Statements.WriteLine>アクティビティを**Argument.ToString()** です。

ワークフローを実行すると、コンソールは次に示します。

**1**
**abc**
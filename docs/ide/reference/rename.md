---
title: "Visual Studio で名前の変更をリファクタリングする | Microsoft Docs"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: bd15d1b59eb5d593fe2b069c2b6721ca623ae99c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="rename-a-code-symbol-refactoring"></a>コード シンボルの名前の変更のリファクタリング

このリファクタリングは以下に適用されます。

- C#

- Visual Basic

**概要:** フィールド、ローカル変数、メソッド、名前空間、プロパティ、型などのコード シンボルの識別子の名前を変更します。

**タイミング:** すべてのインスタンスを検索して新しい名前をコピー/貼り付けすることなく、安全に名前を変更したいとき。

**理由:** プロジェクト全体で新しい名前をコピーおよび貼り付けることは、エラーにつながる可能性があるため。 このリファクタリング ツールでは、正確に名前変更操作が実行されます。

## <a name="how-to"></a>方法

1. 名前を変更する項目を強調表示するか、項目の内側にテキスト カーソルを置きます。

   - C#: 

    ![強調表示されたコード - C#](media/rename-highlight-cs.png)

   - Visual Basic: 

    ![強調表示されたコード - Visual Basic](media/rename-highlight-vb.png)

1. 次に、以下のいずれかを実行します。

   - **キーボード**
     - **Ctrl + R** キーを押し、次に **Ctrl + R** キーを押します。 選ばれているプロファイルによってキーボード ショートカットが異なる場合があることに注意してください。
   - **マウス**
     - **[編集] > [リファクター] > [名前の変更]** の順に選択します。
     - コードを右クリックし **[名前の変更]** を選択します。

1. 新しい名前を入力して、項目の名前を変更します。

   - C#: 

    ![名前の変更のアニメーション - C#](media/rename-animated-cs.gif)

   - Visual Basic: 

    ![名前の変更 - VB](media/rename-rename-vb.png)

   > [!TIP]
   > この新しい名前を使うように、コメントや他の文字列も更新できます。また、エディターの右上に表示される **[名前の変更]** ボックスのチェック ボックスを使って、保存前に[変更をプレビューする](../../ide/preview-changes.md)こともできます。

1. 変更を確認した後は、**[適用]** ボタンを選ぶか、**Enter** キーを押すと、変更がコミットされます。

> [!NOTE]
> 競合が発生する可能性がある既存の名前を使うと、**[名前の変更]** ボックスに警告が表示されます。
>
> ![名前変更の競合](media/rename-conflict-cs.png)

## <a name="see-also"></a>関連項目

[リファクタリング](../refactoring-in-visual-studio.md)  
[変更のプレビュー](../../ide/preview-changes.md)
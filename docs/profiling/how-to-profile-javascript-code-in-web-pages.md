---
title: '方法: Web ページ内の JavaScript コードをプロファイリングする | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- JavaScript performance profiling
- Profiling Tools,JavaScript
- web site performance profiling
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7da608523430724e279efc3d5c7c5d5b27564845
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>方法: Web ページ内の JavaScript コードをプロファイリングする

Visual Studio プロファイリング ツールは、インストルメンテーション プロファイリング メソッドを使用して、[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web アプリケーション、任意の Web ページ、または JavaScript アプリケーションで実行する JavaScript コードのパフォーマンス データを収集できます。 Internet Explorer 8 以降が必要です。

> [!WARNING]
> UWP アプリで JavaScript をプロファイリングするには、「[JavaScript メモリ](../profiling/javascript-memory.md)」をご覧ください 

プロファイル ウィザードを使用して、パフォーマンス セッションを作成できます。 インストルメンテーション メソッドを指定し、パフォーマンス セッションの [プロパティ] ダイアログ ボックスの [インストルメンテーション] ページで、JavaScript のプロファイル オプションを指定します。

JavaScript のプロファイルを指定すると、ブラウザーで実行する JavaScript コードとサーバーで実行される [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] コードのどちらもプロファイリングされます。

- [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web アプリケーションの場合、ブラウザーで実行される JavaScript コードとサーバーで実行される [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] コードのどちらもプロファイリングされます。

- 任意の Web ページの場合、ブラウザーで実行される JavaScript コードがプロファイリングされます。

## <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>ASP.NET Web アプリケーション プロジェクトで、JavaScript をプロファイリングするには

1. Visual Studio で [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web プロジェクトを開きます。

2. **[分析]** メニューの **[パフォーマンス ウィザードの起動]** をクリックします。

3. パフォーマンス ウィザードの最初のページで、 **インストルメンテーション** プロファイリング メソッドを指定して、 **[次へ]** をクリックします。

4. ウィザードの 2 番目のページで、ターゲットの一覧で現在のプロジェクトが選ばれていることを確認し、 **[次へ]** をクリックします。

5. ウィザードの 3 番目のページで、 **[プロファイル JavaScript]** チェック ボックスを選び、 **[次へ]** をクリックします。

6. ウィザードの 4 番目のページで、 **[完了]** をクリックして、ブラウザーで Web アプリケーションを開始します。

7. プロファイリングする機能を実行します。

8. プロファイル セッションを終了するには、ブラウザーを閉じます。

### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>個々の Web ページや JavaScript アプリケーションで JavaScript をプロファイリングするには

1. Visual Studio を開きます。

2. **[分析]** メニューの **[パフォーマンス ウィザードの起動]** をクリックします。

3. パフォーマンス ウィザードの最初のページで、 **インストルメンテーション** プロファイリング メソッドを指定して、 **[次へ]** をクリックします。

4. ウィザードの 2 番目のページで、An ASP.NET、または JavaScript のアプリケーションをクリックし、 **[次へ]** をクリックします。

5. ウィザードの 3 番目のページ:

    1. **[アプリケーションを実行する URL またはパス]** ボックスのページの URL を入力します。

    2. **[プロファイル JavaScript]** チェック ボックスを選び、 **[次へ]** をクリックします。

6. ウィザードの 4 番目のページで、 **[完了]** をクリックし、ブラウザーで Web ページを開始します。

7. プロファイリングする機能を実行します。

8. プロファイル セッションを終了するには、ブラウザーを閉じます。
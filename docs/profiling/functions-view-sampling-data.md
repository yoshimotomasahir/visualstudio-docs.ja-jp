---
title: "関数ビュー - プロファイラー サンプリング データ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "サンプリング プロファイル方法、関数ビュー"
  - "関数ビュー"
ms.assetid: 029d5ebb-e551-46b0-b64e-2c553d9dbb8e
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# <a name="functions-view---sampling-data"></a>関数ビュー - サンプリング データ
サンプリング プロファイル方式の関数のレポート ビューには、プロファイリング実行中にサンプリングされた関数が一覧表示されます。  
  
> [!NOTE]
>  Windows 8 および Windows Server 2012 の強化されたセキュリティ機能によって、Visual Studio プロファイラーがこれらのプラットフォームでデータを収集する方法に大幅な変更が必要になりました。 Windows ストア アプリにも新しい収集手法が必要です。 ｢[Windows 8 および Windows Server 2012 アプリケーションのパフォーマンス ツール](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)」を参照してください。  
  
|列|説明|  
|------------|-----------------|  
|**プロセス ID**|プロファイリング実行のプロセス ID (PID) です。|  
|**プロセス名**|プロセスの名前です。|  
|**モジュール名**|関数を含むモジュールの名前です。|  
|**モジュール パス**|関数を含むモジュールのパスです。|  
|**ソース ファイル**|この関数の定義を含むソース ファイルです。|  
|**関数名**|関数の完全修飾名です。|  
|**関数行番号**|ソース ファイルでのこの関数の開始行番号です。|  
|**関数アドレス**|関数のアドレス。|  
|**包括サンプル数**|この関数が実行されたときに収集されたサンプルの合計数。つまり、この関数が呼び出し履歴上にあったときに収集されたサンプルの数。 この数には、その関数によって呼び出された関数の実行中に収集されたサンプルが含まれます。|  
|**包括サンプル %**|プロファイル実行のすべてのサンプルに対する、この関数の包括サンプルの割合。|  
|**サンプル数 (関数のみ)**|この関数の本文内のコードが実行されたとき、つまり、この関数が呼び出し履歴の一番上にあったときに収集されたサンプルの合計数。 この関数によって呼び出された関数で収集されたサンプルは含まれません。|  
|**サンプル % (関数のみ)**|プロファイル実行のすべてのサンプルに対する、この関数の排他サンプルの割合。|  
  
## <a name="see-also"></a>関連項目  
 [方法: レポート ビューの列をカスタマイズする](../profiling/how-to-customize-report-view-columns.md)   
 [関数ビュー - インストルメンテーション](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [関数ビュー - サンプリング](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [関数ビュー](../profiling/functions-view-instrumentation-data.md)


<!--HONumber=Feb17_HO4-->


---
title: "方法: コマンド ラインからプロファイラーを使用してスタンドアロンのネイティブ コンポーネントをインストルメントし、タイミング データを収集する | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 36883074-9be8-4e90-a66f-7e87f21fcd30
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 方法: コマンド ラインからプロファイラーを使用してスタンドアロンのネイティブ コンポーネントをインストルメントし、タイミング データを収集する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ここでは、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロファイリング ツールのコマンド ライン ツールを使用して、C\+\+ .exe や .dll ファイルなどのネイティブ コンポーネントをインストルメントし、詳細なタイミング データを収集する方法について説明します。  
  
> [!NOTE]
>  プロファイリング ツールのコマンド ライン ツールは、[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] インストール ディレクトリの \\Team Tools\\Performance Tools サブディレクトリにあります。  64 ビット コンピューター上では、64 ビット バージョンのツールと 32 ビット バージョンのツールの両方を使用できます。  プロファイラー コマンド ライン ツールを使用するには、コマンド プロンプト ウィンドウの PATH 環境変数にツールのパスを追加するか、コマンド自体にそれを追加します。  詳細については、「[コマンド ライン ツールへのパスの指定](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)」を参照してください。  
  
 インストルメンテーション メソッドを使用してコンポーネントから詳細なタイミング データを収集するには、[VSInstr.exe](../profiling/vsinstr.md) ツールを使用して、コンポーネントのインストルメントされたバージョンを生成します。  次に、プロファイラーを起動します。  インストルメントされたコンポーネントを実行すると、タイミング データがデータ ファイルに自動的に収集されます。  プロファイル セッション中にデータ収集を一時停止および再開できます。  
  
 プロファイル セッションを終了するには、対象のアプリケーションを終了し、プロファイラーを明示的に終了します。  
  
## プロファイル セッションの開始  
  
#### インストルメンテーション メソッドを使用してプロファイルを開始するには  
  
1.  コマンド プロンプト ウィンドウを開きます。  
  
2.  **VSInstr** ツールを使用して、対象アプリケーションのインストルメントされたバージョンを生成します。  
  
3.  プロファイラーを起動します。  Type:  
  
     **VSPerfCmd \/start:trace \/output:** `OutputFile` \[`Options`\]  
  
    -   [\/start](../profiling/start.md) **:trace** オプションによってプロファイラーが初期化されます。  
  
    -   **\/start** を使用する場合は [\/output](../profiling/output.md)**:**`OutputFile` オプションを指定する必要があります。  `OutputFile` には、プロファイル データ \(.vsp\) ファイルの名前と場所を指定します。  
  
     **\/start:trace** オプションを使用する場合は、次の 1 つ以上のオプションを指定できます。  
  
    |オプション|説明|  
    |-----------|--------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|プロファイリングされたプロセスを所有するアカウントのドメインおよびユーザー名を指定します。  このオプションは、ログオンしているユーザーとは別のユーザーがプロセスを実行している場合にのみ指定する必要があります。  プロセスの所有者は、Windows タスク マネージャーの \[プロセス\] タブの \[ユーザー名\] 列に表示されます。|  
    |[\/crosssession](../profiling/crosssession.md)|他のセッションにおけるプロセスのプロファイリングを有効にします。  このオプションは、アプリケーションが別のセッションで実行されている場合に必要です。  セッション ID は、Windows タスク マネージャーの \[プロセス\] タブの \[セッション ID\] 列に表示されます。  **\/crosssession** の省略形として、**\/CS** を指定することができます。|  
    |[\/globaloff](../profiling/globalon-and-globaloff.md)|データ収集を一時停止した状態でプロファイラーを起動します。  プロファイリングを再開するには、[\/globalon](../profiling/globalon-and-globaloff.md) を使用します。|  
    |[\/counter](../profiling/counter.md) **:** `Config`|`Config` で指定されたプロセッサのパフォーマンス カウンターから情報を収集します。  カウンター情報は、プロファイル イベントが発生するたびに、収集されたデータに追加されます。|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|プロファイリング実行中に収集する Windows パフォーマンス カウンターを指定します。|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|**\/wincounter** と共にのみ使用します。  Windows パフォーマンス カウンター コレクション イベントの間隔をミリ秒単位で指定します。  既定値は 500 ミリ秒です。|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|プロファイリング実行中に収集する ETW \(Event Tracing for Windows\) イベントを指定します。  ETW イベントは独立した \(.etl\) ファイルに収集されます。|  
  
4.  一般的な方法で対象のアプリケーションを起動します。  
  
## データ収集の制御  
 対象アプリケーションの実行中は、**VSPerfCmd.exe** のオプションを使用してファイルへのデータ書き込みを開始および停止することにより、データ収集を制御できます。  データ収集を制御することにより、アプリケーションの起動や終了など、プログラム実行の特定の部分についてのデータ収集を行うことができます。  
  
#### データ収集を開始および停止するには  
  
-   次に示すオプションの組み合わせにより、データ収集を開始および停止します。  個別のコマンド ラインで各オプションを指定します。  データ収集のオンとオフは複数回切り替えることができます。  
  
    |オプション|説明|  
    |-----------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|すべてのプロセスのデータ収集を開始 \(**\/globalon**\) または停止 \(**\/globaloff**\) します。|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|プロセス ID \(`PID`\) で指定されたプロセスのデータ収集を開始 \(**\/processon**\) または停止 \(**\/processoff**\) します。|  
    |[\/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [\/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|スレッド ID \(`TID`\) で指定されたスレッドのデータ収集を開始 \(**\/threadon**\) または停止 \(**\/threadoff**\) します。|  
  
## プロファイル セッションの終了  
 プロファイル セッションを終了するには、インストルメントされたコンポーネントを実行しているアプリケーションを終了し、**VSPerfCmd** [\/shutdown](../profiling/shutdown.md) オプションを呼び出してプロファイラーをオフにした後、プロファイル データ ファイルを閉じます。  
  
#### プロファイル セッションを終了するには  
  
1.  対象アプリケーションを終了します。  
  
2.  プロファイラーをシャットダウンします。  Type:  
  
     **VSPerfCmd \/shutdown**  
  
## 参照  
 [スタンドアロン アプリケーションのプロファイリング](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [インストルメンテーション メソッドのデータ ビュー](../profiling/instrumentation-method-data-views.md)
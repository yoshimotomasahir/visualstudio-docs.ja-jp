---
title: "方法: プロファイラーのコマンド ラインを使用してネイティブ サービスをインストルメントし、詳細なタイミング データを収集する | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dfe58b39-63f8-4a87-ab3a-2b5b14faa8d0
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 方法: プロファイラーのコマンド ラインを使用してネイティブ サービスをインストルメントし、詳細なタイミング データを収集する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ここでは、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロファイリング ツールのコマンド ライン ツールを使用してネイティブ \(C\/C\+\+\) サービスをインストルメントし、詳細なタイミング データを収集する方法について説明します。  
  
> [!NOTE]
>  コンピューターの開始後にサービスを再開できない場合、インストルメンテーション メソッドを使用してサービスをプロファイルすることはできません。このようなサービスが開始されるのは、オペレーティング システムの開始時のみです。  
>   
>  プロファイリング ツールのコマンド ライン ツールは、[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] インストール ディレクトリの \\Team Tools\\Performance Tools サブディレクトリにあります。  64 ビット コンピューター上では、64 ビット バージョンのツールと 32 ビット バージョンのツールの両方を使用できます。  プロファイラーのコマンド ライン ツールを使用するには、コマンド プロンプト ウィンドウの PATH 環境変数にツールのパスを追加するか、コマンド自体にそれを追加します。  詳細については、「[コマンド ライン ツールへのパスの指定](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)」を参照してください。  
  
 インストルメンテーション メソッドを使用してネイティブ サービスから詳細なタイミング データを収集するには、[VSInstr.exe](../profiling/vsinstr.md) ツールを使用して、コンポーネントのインストルメントされたバージョンを生成します。  次に、サービスのインストルメントされていないバージョンをインストルメントされたバージョンに置き換え、サービスを手動で開始するように構成します。  次に、プロファイラーを起動します。  
  
 サービスが開始すると、タイミング データがデータ ファイルに自動的に収集されます。  プロファイル セッション中にデータ収集を一時停止および再開できます。  
  
 プロファイル セッションを終了するには、サービスをオフにし、プロファイラーを明示的に終了します。  
  
## プロファイラーによるアプリケーションの起動  
  
#### ネイティブ サービスのプロファイルを開始するには  
  
1.  コマンド プロンプト ウィンドウを開きます。  
  
2.  **VSInstr** ツールを使用して、サービス バイナリのインストルメントされたバージョンを生成します。  
  
3.  元のバイナリをインストルメントされたバージョンに置き換えます。  Windows サービス コントロール マネージャーで、サービスの \[スタートアップの種類\] が \[手動\] に設定されていることを確認します。  
  
4.  プロファイラーを起動します。  Type:  
  
     **VSPerfCmd** [\/start](../profiling/start.md)**:trace** [\/output](../profiling/output.md)**:**`OutputFile` \[`Options`\]  
  
    -   **\/start:trace** オプションによってプロファイラーが初期化されます。  
  
    -   **\/start** を使用する場合は **\/output:**`OutputFile` オプションを指定する必要があります。  `OutputFile` には、プロファイル データ \(.vsp\) ファイルの名前と場所を指定します。  
  
     **\/start:trace** オプションを使用する場合は、次のうちいずれかのオプションを指定できます。  
  
    > [!NOTE]
    >  **\/user** オプションと **\/crosssession** オプションは、通常、ASP.NET アプリケーションで必要です。  
  
    |オプション|説明|  
    |-----------|--------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|ASP.NET ワーカー プロセスを所有するアカウントのドメインおよびユーザー名を指定します。  このオプションは、ログオンしているユーザーとは別のユーザーがプロセスを実行している場合に指定する必要があります。  プロセスの所有者は、Windows タスク マネージャーの \[プロセス\] タブの \[ユーザー名\] 列に表示されます。|  
    |[\/crosssession](../profiling/crosssession.md)|他のログオン セッションにおけるプロセスのプロファイリングを有効にします。  このオプションは、ASP.NET アプリケーションが別のセッションで実行されている場合に必要です。  セッション ID は、Windows タスク マネージャーの \[プロセス\] タブの \[セッション ID\] 列に表示されます。  **\/crosssession** の省略形として、**\/CS** を指定することができます。|  
    |[\/waitstart](../profiling/waitstart.md)\[**:**`Interval`\]|プロファイラーがエラーを返すまでプロファイラーの初期化を待機する秒数を指定します。  `Interval` を指定しなかった場合、プロファイラーは無期限に待機します。  既定では、**\/start** が直ちに返されます。|  
    |[\/globaloff](../profiling/globalon-and-globaloff.md)|データ収集を一時停止してプロファイラーを起動するには、**\/globaloff** オプションを **\/start** コマンド ラインに追加します。  プロファイリングを再開するには、**\/globalon** を使用します。|  
    |[\/counter](../profiling/counter.md) **:** `Config`|Config で指定されたプロセッサのパフォーマンス カウンターから情報を収集します。  カウンター情報は、プロファイル イベントが発生するたびに、収集されたデータに追加されます。|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|プロファイリング実行中に収集する Windows パフォーマンス カウンターを指定します。|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|**\/wincounter** と共にのみ使用します。  Windows パフォーマンス カウンター コレクション イベントの間隔をミリ秒単位で指定します。  既定値は 500 ミリ秒です。|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|プロファイリング実行中に収集する ETW \(Event Tracing for Windows\) イベントを指定します。  ETW イベントは独立した \(.etl\) ファイルに収集されます。|  
  
5.  サービス コントロール マネージャーからサービスを開始します。  
  
## データ収集の制御  
 サービスの実行中に、**VSPerfCmd.exe** のオプションを使用して、プロファイラー データ ファイルへのデータ書き込みを開始または停止できます。  データ収集を制御することにより、サービスの開始、終了などの、プログラム実行の特定の部分についてのデータを収集できます。  
  
#### データ収集を開始および停止するには  
  
-   次に示す **VSPerfCmd** のオプションの組み合わせにより、データ収集を開始および停止します。  個別のコマンド ラインで各オプションを指定します。  データ収集のオンとオフは複数回切り替えることができます。  
  
    |オプション|説明|  
    |-----------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|すべてのプロセスのデータ収集を開始 \(**\/globalon**\) または停止 \(**\/globaloff**\) します。|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|プロセス ID \(`PID`\) で指定されたプロセスのデータ収集を開始 \(**\/processon**\) または停止 \(**\/processoff**\) します。|  
    |[\/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [\/threadoff](../profiling/threadon-and-threadoff.md)**:**`TID`|スレッド ID \(`TID`\) で指定されたスレッドのデータ収集を開始 \(**\/threadon**\) または停止 \(**\/threadoff**\) します。|  
  
## プロファイル セッションの終了  
 プロファイル セッションを終了するには、インストルメントされたコンポーネントを実行しているサービスを停止し、**VSPerfCmd** [\/shutdown](../profiling/shutdown.md) オプションを呼び出してプロファイラーをオフにした後、プロファイル データ ファイルを閉じます。  
  
#### プロファイル セッションを終了するには  
  
1.  サービス コントロール マネージャーからサービスを停止します。  
  
2.  プロファイラーをシャットダウンします。  Type:  
  
     **VSPerfCmd \/shutdown**  
  
3.  インストルメントされたモジュールを元のモジュールに置き換えます。  必要に応じて、サービスの \[スタートアップの種類\] を再構成します。  
  
## 参照  
 [プロファイリング \(サービスの\)](../profiling/command-line-profiling-of-services.md)   
 [インストルメンテーション メソッドのデータ ビュー](../profiling/instrumentation-method-data-views.md)
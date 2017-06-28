---
title: "実行中のプロセスへのアタッチ | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.processes.attach"
  - "vs.debug.process"
  - "vs.debug.programs"
  - "vs.debug.detaching"
  - "vs.debug.processes"
  - "vs.debug.error.attach"
  - "vs.debug.remotemachine"
dev_langs: 
  - "C++"
  - "CSharp"
  - "FSharp"
  - "VB"
  - "c++"
helpviewer_keywords: 
  - "リモート デバッグ、プログラムへのアタッチ"
  - "プロセス、実行中のプロセスへのアタッチ"
  - "[プロセスにアタッチ] ダイアログ ボックス"
  - "デバッグ [Visual Studio]、プロセスへのアタッチ"
  - "デバッガー、プロセス"
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
caps.latest.revision: 57
caps.handback.revision: 53
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 実行中のプロセスへのアタッチ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio デバッガーをアタッチするプロセスには、Visual Studio からアプリを起動していないが、それをデバッグする場合に多くの場合、役立ちます。 たとえば、IIS プロセスまたは .NET アプリケーションをホストする Windows サービスにアタッチすることができます。 アタッチするプロセスは、ローカルまたはリモートにあります。 別の例は、次デバッグを開始するアプリケーションを実行しているプロセスをアタッチ、デバッガーを使用しないでアプリケーションを実行するいるし、例外が発生すると、可能性があります。

(Windows ストア アプリ) のようなアプリの種類によって、プロセス名に直接アタッチしない] が使用して、 **インストール済みアプリ パッケージのデバッグ** メニュー オプション (テーブルを参照してください)。

シナリオでは、プロセスにアタッチする必要があるかどうかを識別するために、最も一般的なデバッグ シナリオをいくつか次に示します。 複数の手順については、ここでは、リンクを提供しています。

|シナリオ|メソッドをデバッグします。|プロセス名|注とリンク|
|-|-|-|-|
|Visual Studio から起動して、ローカル コンピューターに、すべての種類のサポートされているアプリのデバッグします。|標準的な f5 キーによるデバッグ|N/A|参照してください [デバッガーの概要](../debugger/getting-started-with-the-debugger.md)|
|リモート デバッグ ASP.NET 4 または 4.5 を IIS サーバー|リモート ツールを使用し、プロセスにアタッチします。|w3wp.exe|参照してください [リモート IIS のリモート コンピューター上の ASP.NET のデバッグ](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|IIS サーバー上のリモート デバッグ ASP.NET Core|リモート ツールを使用し、プロセスにアタッチします。|dnx.exe|アプリの展開を参照してください。 [IIS への発行](https://docs.asp.net/en/latest/publishing/iis.html)します。 デバッグは、次を参照してください [リモート IIS のリモート コンピューター上の ASP.NET のデバッグ。](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|サーバー プロセスの他のサポートされているアプリの種類をデバッグします。|(リモート サーバーの場合)、リモート ツールを使用し、プロセスにアタッチします。|iexplore.exe または他のプロセス|必要に応じて、タスク マネージャーを使用して、プロセスを識別しやすくします。 参照してください [リモート デバッグ](../debugger/remote-debugging.md) と以降のセクションでは、このトピック|
|リモート デバッグ、Windows デスクトップ アプリ|リモート ツールと、f5 キー|N/A| 参照してください [リモート デバッグ](../debugger/remote-debugging.md)|
|リモートは、Windows Universal (UWP)、OneCore、HoloLens、または IoT アプリをデバッグします。|インストール済みのアプリ パッケージをデバッグします。|N/A|使用 **デバッグ]、[その他のデバッグ ターゲット]、[インストール済みアプリ パッケージをデバッグ** の代わりに **プロセスにアタッチします。**|
|Visual Studio から開始していない場合、Windows ユニバーサル (UWP) や OneCore、HoloLens、IoT のアプリをデバッグします。|インストール済みのアプリ パッケージをデバッグします。|N/A|使用 **デバッグ]、[その他のデバッグ ターゲット]、[インストール済みアプリ パッケージをデバッグ** の代わりに **プロセスにアタッチします。**|
  
> [!WARNING]
>  JavaScript で記述された Windows ユニバーサル アプリにアタッチするには、まずそのアプリに対してデバッグを有効にする必要があります。 Windows デベロッパー センター内の「 [Attach the debugger](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Attach_the_debugger) 」をご覧ください。  
  
> [!NOTE]
>  C++ で記述されたコードにデバッガーをアタッチするには、コードが `DebuggableAttribute`を生成する必要があります。 [/ASSEMBLYDEBUG](/visual-cpp/build/reference/assemblydebug-add-debuggableattribute) リンカー オプションを使ってリンクすると、これを自動的にコードに追加できます。

## <a name="what-debugger-features-can-i-use"></a>どのようなデバッガー機能を使用できますか。

Visual Studio デバッガー (ブレークポイントにヒット) などの完全な機能を使用する実行可能ファイルとまったく同じにローカル ソースとシンボル (つまり、デバッガーが、正しいを読み込むことにする必要があります [シンボル (.pbd) ファイルを](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md))。 既定では、デバッグ ビルドが必要です。

リモートのデバッグ シナリオでは、いずれか、ソース コードのソース コードのコピー Visual Studio で既に開かれているが必要です。 リモート コンピューターでコンパイルされたアプリのバイナリは、ローカル コンピューター上と同じビルドから取得する必要です。

いくつかのローカル デバッグ シナリオでデバッグできます Visual Studio で、ソースにアクセスできず、適正なシンボル ファイルがアプリケーションに存在している場合 (既定では、これが必要、デバッグ ビルド)。 詳細については、次を参照してください。 [指定シンボルとソース ファイル](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)します。

Windows デスクトップ アプリでは、JIT デバッガー (Visual Studio が表示され、エラーが発生した後、アプリケーション コードを中断する) を使用して実行中のアプリをデバッグすることもできます。

##  <a name="a-namebkmkattachtoaprocessonaremotecomputera-attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> リモート コンピューター上のプロセスにアタッチします。  
 プロセスにアタッチするには、プロセスの名前を知っている必要があります。 IIS に配置されている ASP.NET アプリケーションを参照してください。 [リモート IIS コンピューター上でリモート デバッグの ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) または [を IIS に発行](https://docs.asp.net/en/latest/publishing/iis.html) ASP.NET Core アプリです。 他のアプリについては、タスク マネージャーで、プロセスの名前を検索できる場合があります。
  
 **[プロセスにアタッチ]** ダイアログ ボックスでは、リモート デバッグ用にセットアップした他のコンピューターを選択できます。 詳細については、次を参照してください。 [リモート デバッグ](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)します。 リモート コンピューターを選択すると、そのコンピューターで実行されている選択可能なプロセスの一覧を表示して、1 つ以上のプロセスにアタッチしてデバッグを実行できます。
  
 **リモート コンピューターを選択します。**  

1. Visual Studio で、 **[デバッグ]、[プロセスにアタッチ]**の順に選択します。

2.  **[プロセスにアタッチ]** ダイアログ ボックスの **[トランスポート]** ボックスの一覧で、該当する接続の種類を選択します。 **[既定値]** は、ほとんどの場合に適切な設定です。

    **[トランスポート]** の設定は、デバッグ セッション間で保持されます。 
  
3.  **[修飾子]** ボックスの一覧でリモート コンピューター名を選択します。以下のいずれかの方法を使用します。  
  
    1.  **[修飾子]** ボックスの一覧に名前を入力します。
    
        >**注** 場合、後の手順では、リモート コンピューター名を使用して接続できない、IP アドレスを使用します。 (ポート番号が自動的に表示プロセスを選択した後。 手動で入力することもできます。 次の図で 4020 はリモート デバッガーの既定のポート) です。  
  
    2.  **[修飾子]** ボックスの一覧の横のドロップダウン矢印をクリックし、一覧でコンピューター名を選択します。  
  
    3.  **[修飾子]** ボックスの一覧の横にある**[検索]** ボタンをクリックして、 **[リモート デバッガー接続の選択]** ダイアログ ボックスを開きます。 **[リモート デバッガー接続の選択]** ダイアログ ボックスには、ローカル サブネット上にあるデバイスと、イーサネット ケーブルで自分のコンピューターに直接接続されているデバイスがすべて表示されます。 目的のコンピューターまたはデバイスをクリックし、 **[選択]**をクリックします。 
    
    ![DBG_Basics_Attach_To_Process](../debugger/media/dbg_basics_attach_to_process.png "DBG_Basics_Attach_To_Process") 
  
     **[修飾子]** の設定は、その修飾子でデバッグ接続が成功した場合のみ、デバッグ セッション間で保持されます。
     
4.   **[更新]**を生成する必要があります。

      **[プロセス]** ダイアログ ボックスを開くと、 **[選択可能なプロセス]** ボックスが自動的に表示されます。 このダイアログ ボックスが開いている間に、プロセスをバックグラウンドで開始および停止できます。 このため、内容が常に最新であるとは限りません。 **[更新]**をクリックすると、いつでも一覧の内容を更新して、現在のプロセス一覧を確認できます。 
     
4.  **[プロセスにアタッチ]** ダイアログ ボックスの **[選択可能なプロセス]** ボックスの一覧で、アタッチするプログラムを探します。  
  
     プロセスが別のユーザー アカウントで実行されている場合は、 **[すべてのユーザーからのプロセスを表示する]** チェック ボックスをオンにします。
     
5.  **[アタッチ]**をクリックします。  
  
##  <a name="a-namebkmkattachtoarunningprocessa-attach-to-a-running-process-on-the-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a> ローカル コンピューターで実行中のプロセスにアタッチします。  
 プロセスにアタッチするには、プロセスの名前を知っている必要があります。  タスク マネージャーで、プロセスの名前を検索できる場合があります。  
  
1.  Visual Studio で、 **[デバッグ]、[プロセスにアタッチ]**の順に選択します。
  
2.  **[プロセスにアタッチ]** ダイアログ ボックスの **[選択可能なプロセス]** ボックスの一覧で、アタッチするプログラムを探します。  
  
     プロセスが別のユーザー アカウントで実行されている場合は、 **[すべてのユーザーからのプロセスを表示する]** チェック ボックスをオンにします。
  
3.  **[アタッチ先]** ボックスに、デバッグするコードの種類が表示されていることを確認します。 既定の **[自動]** 設定では、デバッグするコードの種類が自動的に判断されます。 コードの種類を手動で設定するには、次の操作を行います  
  
    1.  **[プロセスにアタッチ]** ボックスで、 **[選択]**をクリックします。  
  
    2.  **[コードの種類の選択]** ダイアログ ボックスで、 **[次のコードの種類をデバッグする]** をクリックし、デバッグする種類を選択します。  
  
    3.  **[OK]**をクリックします。  
  
4.  **[アタッチ]**をクリックします。

## <a name="additional-info"></a>追加情報

デバッグ中には複数のプログラムにアタッチできますが、デバッガーでアクティブになっているプログラムは常に 1 つだけです。 アクティブなプログラムは、 **[デバッグの場所]** ツール バーまたは **[プロセス]** ウィンドウで設定できます。 詳細については、「 [方法 : 現在のプロセスを設定する](http://msdn.microsoft.com/ja-jp/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e)」を参照してください。  
  
信頼関係のないユーザー アカウントによって所有されているプロセスにアタッチしようとすると、セキュリティ警告の確認ダイアログ ボックスが表示されます。 詳細については、次を参照してください。 [セキュリティ警告: 信頼されていないユーザーが所有するプロセスにアタッチするのは危険です。次の情報に関して疑わしい、または不明ながこのプロセスにアタッチしません。](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)します。  
  
リモート デスクトップ (ターミナル サービス) セッションでのデバッグ時には、 **[選択可能なプロセス]** ボックスに、使用可能なプロセスのすべてが表示されない場合があります。 Visual Studio を、制限付きユーザー アカウントを持つユーザーとして実行している場合、 **[選択可能なプロセス]** ボックスの一覧には、セッション 0 で実行しているプロセスは表示されません。セッション 0 は、サービスおよび w3wp.exe を含むその他のサーバー プロセス用に使用されます。 この問題を解決するには、管理者アカウントで [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を実行するか、ターミナル サービス セッションからではなくサーバー コンソールから [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を実行します。 どちらの方法も実行できない場合、3 つ目の方法として、Windows コマンド ラインから `vsjitdebugger.exe -p` *ProcessId* を実行することによって、プロセスにアタッチできます。 プロセス ID は tlist.exe を使用して確認できます。 tlist.exe を入手するには、「  [WDK と WinDbg のダウンロード](http://go.microsoft.com/fwlink/?LinkId=168279)」で Windows 対応のデバッグ ツールをダウンロードし、インストールします。
  
##  <a name="a-namebkmktroubleshootattacherrorsa-troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> トラブルシューティング: アタッチ エラー  
 実行中のプロセスにデバッガーがアタッチすると、このプロセスは、1 種類以上のコードを含むことができます。 デバッガーをアタッチできるコードの種類は **[コードの種類の選択]** ダイアログ ボックスで表示されて選択されています。  
  
 デバッガーは、ある種類のコードに正常にアタッチできても、別の種類にはアタッチできないことがあります。 この問題は、リモート コンピューターで動作しているプロセスにアタッチしようとする場合に発生することがあります。 リモート コンピューターには、一部の種類のコードにしか対応しないリモート デバッグ コンポーネントがインストールされている場合があるためです。 また、ダイレクト データベース デバッグのために複数のプロセスにアタッチしようとした場合にも発生することがあります。 SQL デバッグ機能は、単一プロセスへのアタッチのみをサポートします。  
  
 デバッガーが一部の種類のコードにしかアタッチできない場合は、アタッチできなかった種類を識別するメッセージが表示されます。  
  
 デバッガーが少なくとも 1 種類のコードに正常にアタッチできる場合は、プロセスのデバッグを開始できます。 正常にアタッチされたコードの種類のみをデバッグできます。 上記のメッセージの例は、種類がスクリプトのコードにアタッチできなかったことを示しています。 この場合、プロセス内でスクリプト コードをデバッグできません。 プロセス内のスクリプト コードはそのまま実行されますが、スクリプトでのブレークポイントの設定、データの表示、またはその他のデバッグ操作は実行できません。  
  
 デバッガーがコードの種類へのアタッチに失敗した理由についてより詳しい情報が必要な場合は、該当するコードの種類のみに再アタッチを試行できます。  
  
 **コードの種類の接続が失敗した理由に関する特定の情報を取得するには**  
  
1.  プロセスからデタッチします。 **[デバッグ]** メニューの **[すべてデタッチ]**をクリックします。  
  
2.  コードの種類を 1 つだけ選択して、プロセスに再度アタッチします。  
  
    1.  **[プロセスにアタッチ]** ダイアログ ボックスの **[選択可能なプロセス]** ボックスの一覧で、プロセスを選択します。  
  
    2.  **[選択]**をクリックします。  
  
    3.  **[コードの種類の選択]** ダイアログ ボックスの **[次のコードの種類をデバッグする]** をクリックし、アタッチに失敗したコードの種類を選択します。 他のコードをすべてオフにします。  
  
    4.  **[OK]**をクリックします。 **[コードの種類の選択]** ダイアログ ボックスが閉じます。  
  
    5.  **[プロセスにアタッチ]** ダイアログ ボックスで、 **[アタッチ]**をクリックします。  
  
     このとき、アタッチは完全に失敗し、詳細なエラー メッセージが表示されます。  
  
## <a name="see-also"></a>「  
 [複数のプロセスをデバッグします。](../debugger/debug-multiple-processes.md)   
 [ジャスト イン タイム デバッグ](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [リモート デバッグ](../debugger/remote-debugging.md)
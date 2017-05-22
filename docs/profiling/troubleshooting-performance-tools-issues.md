---
title: "プロファイリング ツールの問題のトラブルシューティング | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# プロファイリング ツールの問題のトラブルシューティング
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

プロファイリング ツールを使用するときに、次の問題のいずれかが発生する場合があります。  
  
-   [プロファイリング ツールでデータが収集されない](#NoDataCollected)  
  
-   [パフォーマンス ビューとレポートに関数名ではなく番号が表示される](#NoSymbols)  
  
##  <a name="NoDataCollected"></a> プロファイリング ツールでデータが収集されない  
 アプリケーションのプロファイリングを実行しても、プロファイリング データ \(.vsp\) ファイルが作成されず、出力ウィンドウまたはコマンド ウィンドウに次の警告が表示されます。  
  
 PRF0025: データは収集されませんでした。  
  
 この問題は、次の複数の問題が原因で発生することがあります。  
  
-   サンプリングまたは .NET メモリ メソッドを使用してプロファイリングしたプロセスによって、子プロセスが起動されます。この子プロセスは、アプリケーションの作業を実行するプロセスになります。  たとえば、一部のアプリケーションでは、コマンド ラインを読み取り、Windows アプリケーションまたはコマンド ライン アプリケーションのどちらとして起動したかを決定します。  Windows アプリケーションが要求された場合、元のプロセスは Windows アプリケーションとして構成された新しいプロセスを起動し、元のプロセスは終了します。  プロファイリング ツールは子プロセスのデータを自動的に収集しないため、データは収集されません。  
  
     この状況でプロファイリング データを収集するには、プロファイラーでアプリケーションを起動するのではなく、子プロセスにプロファイラーをアタッチします。  詳細については、「[方法 : 実行中のプロセスにプロファイラーをアタッチする\/実行中のプロセスからプロファイラーをデタッチする](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)」および「[Attach \(VSPerfCmd\)](../profiling/attach.md)」を参照してください。  
  
##  <a name="NoSymbols"></a> パフォーマンス ビューとレポートに関数名ではなく番号が表示される  
 アプリケーションのプロファイリング後、レポートとビューに関数名ではなく番号が表示されます。  
  
 この問題の原因は、ソース コード情報 \(関数名や行番号\) をコンパイル済みのファイルにマップするシンボル情報を含む .pdb ファイルが、プロファイリング ツールの分析エンジンによって見つけられなかったことです。  既定では、アプリケーション ファイルのビルド時に .pdb ファイルが作成されます。  .pdb ファイルのローカル ディレクトリへの参照は、コンパイル済みのアプリケーションに格納されます。  分析エンジンは、.pdb ファイルについて参照されるディレクトリを検索し、次に現在アプリケーション ファイルなどのファイルのディレクトリを検索します。  .pdb ファイルが見つからない場合、分析エンジンは関数名ではなく関数のオフセットを使用します。  
  
 この問題は、2 つの方法のいずれかで修復できます。  
  
-   .pdb ファイルを検索し、アプリケーション ファイルと同じディレクトリに配置します。  
  
-   プロファイリング データ \(.vsp\) ファイルにシンボル情報を埋め込みます。  詳細については、「[プロファイル データ ファイルを使ったシンボル情報の保存](../profiling/saving-symbol-information-with-performance-data-files.md)」を参照してください。  
  
> [!NOTE]
>  分析エンジンを使用する場合、.pdb ファイルと、コンパイル済みのアプリケーション ファイルを同じバージョンにする必要があります。  古いビルドまたは新しいビルドのアプリケーション ファイルの .pdb ファイルでは機能しません。
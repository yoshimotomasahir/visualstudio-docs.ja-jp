---
title: Event Tracing for Windows (ETW) レポート | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3804ad0ff2a64a8e7a20e963bc4f5baa10d3320c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="event-tracing-for-windows-etw-report"></a>ETW (Event Tracing for Windows) レポート
Windows イベント トレーシング (ETW) レポートには、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロファイル ツールのパフォーマンス セッションで記録された ETW イベントが一覧表示されます。 ETW データはバイナリ (.etl) ファイルで収集されます。  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] インターフェイスでは ETW レポートを表示できません。  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] インターフェイスのプロファイル ツールを利用して ETW データを収集する方法については、「[方法: ETW (Event Tracing for Windows) データを収集する](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)」を参照してください。  
  
-   [VSPerfCmd](../profiling/vsperfcmd.md) コマンド ライン ツールを利用して ETW データを収集する方法については、「[Events](../profiling/events-vsperfcmd.md)」を参照してください。  
  
-   ETW レポートは **VSReport/Summary:ETW** コマンドを利用して生成します。 詳細については、「[VSPerfReport](../profiling/vsperfreport.md)」を参照してください。  
  
|Column|説明|  
|------------|-----------------|  
|**タイムスタンプ**|イベントが発生した日時を識別します。|  
|**プロセス ID**|イベントを生成したプロセスを識別します。|  
|**スレッド ID**|イベントを生成したスレッドを識別します。|  
|**説明**|イベント プロバイダーを識別します。|  
|**Type**|イベントの種類を識別します。|  
|**プロパティ**|イベントのプロパティ。 各イベントは角かっこで囲まれた名前と値のペアになり、コンマで区切られます。|
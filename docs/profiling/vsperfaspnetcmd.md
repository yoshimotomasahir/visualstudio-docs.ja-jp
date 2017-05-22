---
title: VSPerfASPNetCmd | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: f9e9f895-57bb-41e8-8bd1-cdaa738ec220
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 970593f1141c2fc067ce181f6f756889180a231b
ms.lasthandoff: 02/22/2017

---
# <a name="vsperfaspnetcmd"></a>VSPerfASPNetCmd
**VSPerfASPNetCmd.exe** コマンド ライン ツールを使用すれば、環境変数を設定したり、コンピューターを再起動したりしなくても、ASP.Net Web サイトをプロファイルすることができます。 ASP.NET Web サイトをプロファイルするときに、**VSPerCmd** で提供される追加機能が不要な場合は、[VSPerfCmd](../profiling/vsperfcmd.md) ではなく **VSPerfASPNetCmd.exe** を使用します。 **VSPerfASPNetCmd** の詳細については、「[VSPerfASPNETCmd を使用した迅速な Web サイト プロファイリング](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)」を参照してください。 **VSPerfASPNetCmd** は、スタンドアロン プロファイラーを使用して ASP.NET Web サイトをプロファイルするときに推奨されるコマンド ライン ツールです。  
  
## <a name="syntax"></a>構文  
 **vsperfaspnetcmd** [/*Options*] *Website*  
  
## <a name="options"></a>オプション  
  
|オプション|説明|  
|------------|-----------------|  
|**/Sample** または **/s**|サンプリング メソッドを使用して Web サイトをプロファイルします。 **/Sample** は既定のメソッドです。 /Sample を **/Trace** と一緒に使用することはできません。|  
|**/Trace** または **/t**|インストルメンテーション メソッドを使用して Web サイトをプロファイルします。 /Trace を **/Sample** と一緒に使用することはできません。|  
|**/Memory**[**:**`Type`] または **/m**[**:**{**a**&#124;**l**}]|メモリ割り当て、および必要に応じてオブジェクトの有効期間 (ガベージ コレクション) をプロファイルします。 **/Memory** は、サンプリングまたはインストルメンテーション メソッドで使用できます。<br /><br /> *Type* は次のいずれかになります。<br /><br /> -   **allocation** (または **a**): メモリの割り当てデータのみを収集します。<br />-   **lifetime** (または **l**): メモリの割り当ておよびオブジェクトの有効期間データを収集します。<br /><br /> 既定の `Type` は **allocation** です。|  
|**/Tip** または **/i**|プロファイル データに詳細な ASP.NET 要求と ADO.NET 呼び出し情報を追加します。 **/Tip** はサンプリングまたはインストルメンテーション メソッドで使用でき、**/Memory** オプションと共に使用できます。|  
|**/Output:** `File` または **/o:**`File`|プロファイル データ (.vsp) ファイルのパスとファイル名を指定します。|  
|**/NoWait** または **/n**|コマンド プロンプトを直ちに返し、コマンド プロンプト ウィンドウで追加のコマンドを使用できるようにします。 別のコマンド ラインで **VSPerfASPNETCmd /Shutdown** を入力して、プロファイルをオフにする必要があります。|  
|**/PackSymbols**[:{**on**&#124;**off**} または **/p**[:{**on**&#124;**off**}|プロファイル データ (.vsp) ファイルにシンボル (関数やパラメーター名など) を埋め込みます。|  
|**/Shutdown:** `Website`または **/d:**`Website`|プロファイルをオフにします。 **/NoWait** オプションを使用してプロファイルを開始した後、またはプロファイラーが予期せず終了した場合に、コマンド ラインで唯一のオプションとして使用します。 元の **VSPerfASPNETCmd** コマンドで使用していたのと同じ URL を指定します。|  
|`Website`|プロファイル対象の Web サイトの URL です。|  
  
## <a name="see-also"></a>関連項目  
 [VSPerfASPNETCmd を使用した迅速な Web サイト プロファイリング](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)   
 [ASP.NET Web アプリケーションのプロファイリング](../profiling/command-line-profiling-of-aspnet-web-applications.md)
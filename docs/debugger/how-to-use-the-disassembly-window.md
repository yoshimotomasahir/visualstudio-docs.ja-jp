---
title: In the Debugger in Visual Studio の逆アセンブリ コードの表示 |Microsoft ドキュメント
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.disassembly
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- assembly language, debugging inline assembly code
- breakpoints, Disassembly window
- Disassembly window
- machine code
ms.assetid: eaf84dd0-c82d-481b-af51-690b74e7794c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 46c0ae689a9d514983aeb747bebc6cb9905c6e11
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="view-disassembly-code-in-the-visual-studio-debugger"></a>Visual Studio デバッガーで逆アセンブリ コードの表示
この機能は、アドレス レベルのデバッグが有効になっている場合にのみ使用可能な**オプション**ダイアログ ボックスで、**デバッグ**ノード。 スクリプトまたは SQL のデバッグには使用できません。  
  
 **逆アセンブル**ウィンドウは、コンパイラによって作成された命令に対応するアセンブリ コードを示しています。 マネージ コードをデバッグする場合、これらのアセンブリ命令は、Visual Studio コンパイラが生成した Microsoft Intermediate Language (MSIL) ではなく、Just-In-Time (JIT) コンパイラが作成したネイティブ コードに対応しています。  
  
 アセンブリ命令だけでなく、**逆アセンブル**ウィンドウは、次の省略可能な情報を表示できます。  
  
-   各命令が配置されているメモリ アドレス。 ネイティブ アプリケーションの場合は、実際のメモリ アドレスです。 Visual Basic、C#、またはマネージ コードの場合は、関数の先頭からのオフセットです。  
  
-   アセンブリ コードの派生元のソース コード。  
  
-   コード バイト。これは、実際のマシン語命令または MSIL 命令のバイト表現です。  
  
-   メモリ アドレスのシンボル名。  
  
-   ソース コードに対応する行番号。  
  
 アセンブリ言語命令は、命令名の省略形であるニーモニックと、変数、レジスタ、および定数を表す記号で構成されます。 各マシン語命令は 1 つのアセンブリ言語ニーモニックで表現され、通常はその後に 1 つ以上の変数、レジスタ、または定数が続きます。  
  
 アセンブリ言語を読み取ることができない状況において [逆アセンブル] ウィンドウを最大限に活用するには、アセンブリ言語プログラミングに関して詳しく説明している文献を参照してください。 [逆アセンブル] ウィンドウに関するこの簡単な紹介では、アセンブリ言語のプログラミングについては説明しません。  
  
 アセンブリ コードは、プロセッサのレジスタ (マネージ コードの場合は共通言語ランタイムのレジスタ) に大きく依存するため、[逆アセンブル] ウィンドウと一緒に [レジスタ] ウィンドウを使用すると、レジスタの内容をチェックできるので便利です。  
  
 ほとんどの場合、アセンブリ言語ではなく生の数値の形式でマシン語コード命令を表示する必要はありません。 ただし、必要に応じて、[メモリ] ウィンドウを使用するか、[逆アセンブル] ウィンドウのショートカット メニューの [コード バイトの表示] を選択すると表示できます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
### <a name="to-display-the-disassembly-window"></a>[逆アセンブル] ウィンドウを表示するには  
  
-   デバッグしている間は、選択**デバッグ > Windows**  をクリックし、**逆アセンブル**です。
  
### <a name="to-turn-optional-information-on-or-off"></a>オプション情報の表示と非表示を切り替えるには  
  
-   右クリックし、**逆アセンブル**ウィンドウで、しまたはショートカット メニューを開き、目的のオプションをオフにします。  
  
     左マージンの黄色の矢印は、現在の実行ポイントの位置を示します。 ネイティブ コードの場合、これは CPU のプログラム カウンターに対応します。 この位置は、プログラム内で次に実行される命令を示します。  
  
     詳細については、次を参照してください。[上下メモリ内](../debugger/how-to-page-up-or-down-in-memory.md)です。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーでのデータの表示](../debugger/viewing-data-in-the-debugger.md)   
 [方法: [レジスタ] ウィンドウを使用する](../debugger/how-to-use-the-registers-window.md)
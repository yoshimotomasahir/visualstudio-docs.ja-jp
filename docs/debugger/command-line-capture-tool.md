---
title: "コマンド ライン キャプチャ ツール | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: db75b3a7-80b2-4a74-91d2-fd6e0f73b45d
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# コマンド ライン キャプチャ ツール
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

DXCap.exe は、グラフィックス診断のキャプチャと再生に使用されるコマンド ライン ツールです。  すべての機能レベルで、Direct3D 10 から Direct3D 12 をサポートしています。  
  
## 構文  
  
```ms-dos  
DXCap.exe [-file filename] [-frame frames | -period periods | -manual] -c app [args...]  
DXCap.exe -p [filename] [-debug | -warp | -hw] [-config] [-rawmode]  
DXCap.exe –p [filename] –screenshot [-frame frames]  
DXCap.exe –p [filename] –toXML [xml_filename]  
DXCap.exe –v [–file filename] [-examine events] [-haltonfail | -exitonfail] [-showprogress]  
DXCap.exe -e [search_string]  
DXCap.exe –info  
```  
  
#### パラメーター  
 `-file` `filename`  
 キャプチャ モードの場合 \(`-c`\)、`filename` には、グラフィックス情報の記録先となる、グラフィックス ログ ファイルの名前を指定します。  `filename` が指定されていない場合、グラフィックス情報は、既定で `<appname>-<date>-<time>.vsglog` という名前のファイルに記録されます。  
  
 検証 \(\-v\) モードの場合、`filename` には、検証するグラフィックス ログ ファイルの名前を指定します。  `filename` が指定されていない場合、最後に検証されたグラフィックス ログがもう一度使用されます。  
  
 `-frame` `frames`  
 キャプチャ モードの場合、`frames` には、キャプチャするフレームを指定します。  最初のフレームは 1 です。  コンマおよび範囲を使用して、複数のフレームを指定できます。  たとえば、`frames` が `2, 5, 7-9, 15` の場合、フレーム `2`、`5`、`7`、`8`、`9`、および `15` がキャプチャされます。  
  
 `-period` `periods`  
 キャプチャ モードの場合、`periods` には、フレームをキャプチャする時間の範囲を秒単位で指定します。  コンマおよび範囲を使用して、複数の期間を指定できます。  たとえば、`periods` が `2.1-5, 7.0-9.3` の場合、`2.1` ～ `5` 秒のフレームがレンダリングされ、`7` ～ `9.3` 秒のフレームがキャプチャされます。  
  
 `-manual`  
 キャプチャ モードの場合、`-manual` は、PrintScreen キーを押してフレームを手動でキャプチャすることを指定します。  フレームはアプリの起動時にキャプチャできます。フレームのキャプチャを停止するには、コマンド ライン インターフェイスに戻り、Enter キーを押します。  
  
 `-c` `app` \[`args...`\]  
 キャプチャ モード。  キャプチャ モードの場合、`app` には、グラフィックス情報の取得元となるアプリの名前を指定します。`args...` には、そのアプリに対する追加のコマンド ライン パラメーターを指定します。  
  
 `-p` \[`filename`\]  
 再生モード \(`-p`\)。  再生モードの場合、`filename` には、再生するグラフィックス ログ ファイルの名前を指定します。  `filename` が指定されていない場合、最後に再生されたグラフィックス ログがもう一度使用されます。  
  
 `-debug`  
 再生モードの場合、`-debug` は、Direct3D デバッグ レイヤーを有効にした状態で再生を実行する必要があることを指定します。  
  
 `-warp`  
 再生モードの場合、`-warp` は、WARP ソフトウェア レンダラーを使用して再生を実行する必要があることを指定します。  
  
 `-hw`  
 再生モードの場合、`-hw` は、GPU ハードウェアを使用して再生を実行する必要があることを指定します。  
  
 `-config`  
 再生モードの場合、`-config` は、グラフィックス ログ ファイルのキャプチャに使用されたコンピューターに関する情報がログに記録されている場合、その情報を表示します。  
  
 `-rawmode`  
 再生モードの場合、`- rawmode` は、記録されたイベントを変更することなく、再生を実行する必要があることを指定します。  再生モードの通常の動作では、デバッグを単純化し、再生を高速化するために、再生に若干の変更が加えられる場合があります。  たとえば、スワップ チェーンのコマンドを実行する代わりに、スワップ チェーンの出力をシミュレートする場合があります。  通常、この動作が問題になることはありませんが、場合によっては、記録されたイベントに対してより忠実に、再生を実行する必要があります。たとえば、このオプションを使用して、全画面モードでの実行中にキャプチャされたアプリの全画面レンダリング動作を復元できます。  
  
 `-toXML` \[`xml_filename`\]  
 再生モードの場合、`xml_filename` には、再生の XML 表現の書き込み先となるファイルの名前を指定します。  `xml_filename` が指定されていない場合、XML 表現は、再生するファイルと同じ名前を持ち、`.xml` 拡張子が付けられたファイルに書き込まれます。  
  
 `-v`  
 検証モード。  検証モードの場合、キャプチャしたフレームはハードウェアと WARP の両方で再生され、イメージ比較関数によって、それらの結果が比較されます。  この機能を使用すると、レンダリングに影響を与えるドライバーの問題をすばやく識別できます。  
  
 `-examine` `events`  
 検証モードの場合、`events` には、直近の結果を比較する一連のグラフィックス イベントを指定します。  たとえば、`-examine present,draw,copy,clear` は、比較対象を、これらのカテゴリに属するイベントに限定します。  
  
> [!TIP]
>  最初は `-examine present,draw,copy,clear` を指定することをお勧めします。より広範な一連のイベントを指定した場合よりも、大幅に短い時間で、ほとんどの問題を明らかにすることができます。  必要に応じて、より多くの、または異なる一連のイベントを指定して、それらのイベントを検証し、その他の種類の問題を明らかにすることもできます。  
  
 `-haltonfail`  
 検証モードの場合、`- haltonfail` は、ハードウェア レンダラーと WARP レンダラーの違いが検出されたときに、検証を停止します。  検証は、キーが押された後に再開されます。  
  
 `-exitonfail`  
 検証モードの場合、`-exitonfail` は、ハードウェア レンダラーと WARP レンダラーの違いが検出された直後に、検証を終了します。  この方法でプログラムを終了した場合、`0` が環境に返されます。それ以外の場合、`1` が返されます。  
  
 `-showprogress`  
 検証モードの場合、`-showprogress` は、検証セッションの進行状況に関する情報を表示します。  WARP の進行状況が左側に表示され、ハードウェアの進行状況が右側に表示されます。  
  
 `-e` `search_string`  
 インストールされている Windows ストア アプリを列挙します。  この情報を使用して、Windows ストア アプリでコマンド ライン キャプチャを実行できます。  
  
 `-info`  
 コンピューターとキャプチャの DLL に関する情報を表示します。  
  
## 解説  
 DXCap.exe は 3 つのモードで動作します。  
  
 キャプチャ モード \(\-c\)  
 実行中のアプリからグラフィックス情報をキャプチャし、その情報をグラフィックス ログ ファイルに記録します。  キャプチャ機能とファイル形式は、Visual Studio と同じです。  
  
 再生モード \(\-p\)  
 以前にキャプチャしたグラフィックス イベントを、既存のグラフィックス ログ ファイルから再生します。  既定では、グラフィックス ログ ファイルが全画面アプリからキャプチャされた場合でも、再生はウィンドウ内で実行されます。  再生が全画面で実行されるのは、グラフィックス ログ ファイルが全画面アプリからキャプチャされ、`–rawmode` が指定された場合のみです。  
  
 検証モード \(`-v`\)  
 キャプチャしたフレームをハードウェアと WARP の両方で再生してレンダリング動作を検証した後、イメージ比較関数を使用して、結果を比較します。  この機能を使用すると、レンダリングに影響を与えるドライバーの問題をすばやく識別できます。  
  
 これらのモードに加えて、dxcap.exe は、グラフィックス情報のキャプチャや再生を実行しない、他の 2 つの機能を実行します。  
  
 列挙機能 \(`-e`\)  
 コンピューターにインストールされている Windows ストア アプリの詳細を表示します。  これらの詳細には、パッケージ名と、Windows ストア アプリ内の実行可能ファイルを識別するためのアプリ ID が含まれます。  DXCap.exe を使用して、Windows ストア アプリからグラフィックス情報をキャプチャするには、デスクトップ アプリをキャプチャするときに使用する実行可能ファイルの名前ではなく、このパッケージ名とアプリ ID を使用します。  
  
 情報機能 \(`-info)`  
 コンピューターとキャプチャの DLL の詳細を表示します。  
  
## 例  
  
### デスクトップ アプリからのグラフィックス情報のキャプチャ  
 `–c` を使用して、グラフィックス情報のキャプチャ元となるアプリを指定します。  
  
```ms-dos  
DXCap.exe –c BasicHLSL11.exe  
```  
  
 既定では、グラフィックス情報は `<appname>-<date>-<time>.vsglog` という名前のファイルに記録されます。  記録先として別のファイルを指定するには、`–file` を使用します。  
  
```ms-dos  
DXCap.exe –file regression_test_12.vsglog –c BasicHLSL11.exe  
```  
  
 キャプチャ元のアプリに対する追加のコマンド ライン パラメーターを、そのアプリのファイル名の後に含めることによって指定します。  
  
```ms-dos  
DXCap.exe –c "C:\Program Files\Internet Explorer\iexplorer.exe" "www.fishgl.com"  
```  
  
 上記の例のコマンドでは、WebGL API を使用して 3\-D コンテンツをレンダリングする、www.fishgl.com にある Web ページの表示中に、Internet Explorer のデスクトップ バージョンからグラフィックス情報をキャプチャします。  
  
> [!NOTE]
>  アプリの後に指定したコマンド ライン引数はアプリに渡されるため、`–c` オプションを使用する前に、DXCap.exe の引数を指定する必要があります。  
  
### Windows ストア アプリからグラフィックス情報をキャプチャします。  
 Windows ストア アプリからグラフィックス情報をキャプチャできます。  
  
```ms-dos  
DXCap.exe –c Microsof.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps  
```  
  
 DXCap.exe を使用した Windows ストア アプリからのキャプチャは、DXCap.exe を使用した Windows デスクトップ アプリからのキャプチャに似ていますが、デスクトップ アプリをファイル名で識別する代わりに、Windows ストア アプリは、キャプチャ元のパッケージ内にある実行可能ファイルの名前または ID で識別します。  より簡単に、コンピューターにインストールされている Windows ストア アプリを識別する方法は、DXCap.exe に `–e` オプションを指定して、それらのアプリを列挙することです。  
  
```ms-dos  
DXCap.exe -e  
```  
  
 オプションの検索文字列を指定して、探しているアプリの検索に役立てることもできます。  検索文字列を指定した場合、DXCap.exe は、パッケージ名、アプリ名またはアプリ ID が検索文字列に一致する Windows ストア アプリを列挙します。  検索では、大文字と小文字を区別しません。  
  
```ms-dos  
DXCap.exe –e map  
```  
  
 上記のコマンドでは、"map" に一致する Windows ストア アプリが列挙されます。出力を次に示します。  
  
  **Package "Microsoft.BingMaps":**  
 **InstallDirectory : C:\\Program Files\\WindowsApps\\Microsoft.BingMaps\_2.1.2914.1734\_x64\_\_8wekyb3d8bbwe**  
 **FullName         : Microsoft.BingMaps\_2.1.2914.1734\_x64\_\_8wekyb3d8bbwe**  
 **UserSID          : S\-1\-5\-21\-2127521184\-1604012920\-1887927527\-5603533**  
 **Name             : Microsoft.BingMaps**  
 **Publisher        : CN\=Microsoft Corporation, O\=Microsoft Corporation, L\=Redmond, S\=Washington, C\=US**  
 **Version          : 2.1.2914.1734**  
 **Launchable Applications:**  
 **Id   : AppexMaps**  
 **Exe  : C:\\Program Files\\WindowsApps\\Microsoft.BingMaps\_2.1.2914.1734\_x64\_\_8wekyb3d8bbwe\\Map.exe**  
 **IsWWA: No**  
 **AppSpec \(to launch\): **DXCap.exe \-c Microsoft.BingMaps\_2.1.2914.1734\_x64\_\_8wekyb3d8bbwe,AppexMaps****  列挙された各アプリの出力の最後の行に、そのアプリからグラフィックス情報をキャプチャするために使用できるコマンドが表示されます。  
  
### 特定のフレームまたは特定の期間のフレームのキャプチャ  
 `–frame` と共に、コンマと範囲を使用して、キャプチャするフレームを指定します。  
  
```ms-dos  
DXCap.exe –frame 2,5,7-9,15 –c SimpleBezier11.exe  
```  
  
 または、`–period` を使用して、フレームをキャプチャする一連の時間範囲を指定します。  時間の範囲は秒単位で指定し、複数の範囲を指定することもできます。  
  
```ms-dos  
DXCap.exe –period 2.1-5, 7.0-9.3 –c SimpleBezier11.exe  
```  
  
### フレームの対話的なキャプチャ  
 `–manual` を使用して、フレームを対話的にキャプチャします。  Enter キーを押してキャプチャを開始し、もう一度 Enter キーを押して停止します。  
  
```ms-dos  
DXCap.exe –manual -c SimpleBezier11.exe  
```  
  
### グラフィックス ログ ファイルの再生  
 `-p` を使用して、以前にキャプチャしたグラフィックス ログ ファイルを再生します。  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog  
```  
  
 最後にキャプチャされたグラフィックス ログを再生する場合は、ファイル名を指定しません。  
  
```ms-dos  
DXCap.exe –p  
```  
  
### Raw モードでの再生  
 `-rawmode` を使用して、キャプチャしたコマンドを発生順に再生します。  通常の再生では、特定のコマンドがエミュレートされます。たとえば、全画面アプリからキャプチャされたグラフィックス ログ ファイルは、ウィンドウ内で再生されます。Raw モードが有効になっている場合は、同じファイルの再生が全画面で試行されます。  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog -rawmode  
```  
  
### WARP またはハードウェア デバイスの使用の再生  
 ハードウェア デバイス上でキャプチャしたグラフィックス ログ ファイルの再生で、WARP を強制的に使用したり、WARP 上でキャプチャされたログの再生で、強制的にハードウェア デバイスを使用したりできます。  WARP を使用して再生するには、`-warp` を使用します。  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog -warp  
```  
  
 ハードウェアを使用して再生するには、`-hw` を使用します。  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog -hw  
```  
  
### WARP に対するグラフィックス ログ ファイルの検証  
 検証モードの場合、グラフィックス ログ ファイルはハードウェアと WARP の両方で再生され、その結果が比較されます。  これは、ドライバーが原因で発生するレンダリング エラーを識別するのに役立ちます。  \-v を使用すると、WARP に対してグラフィックス ハードウェアが正しく動作するかどうかを検証できます。  
  
```ms-dos  
DXCap.exe -v regression_test_12.vsglog  
```  
  
 比較の量を減らすために、比較する検証用コマンドのサブセットを指定できます。この場合、他のコマンドは無視されます。  結果を比較するコマンドを指定するには、\-examine を使用します。  
  
```ms-dos  
DXCap.exe -v regression_test_12.vsglog –examine present,draw,copy,clear  
```  
  
### PNG へのグラフィックス ログ ファイルの変換  
 グラフィックス ログ ファイルのフレームを表示または分析するために、DXCap.exe は、キャプチャしたフレームを .png \(ポータブル ネットワーク グラフィックス\) イメージ ファイルとして保存できます。  再生モードで、キャプチャしたフレームを .png ファイルとして出力するには、`-screenshot` を使用します。  
  
```ms-dos  
DXCap.exe -p BasicHLSL11.vsglog -screenshot  
```  
  
 出力するフレームを指定するには、`–frame` と `–screenshot` を使用します。  
  
```ms-dos  
DXCap.exe -p BasicHLSL11.vsglog -screenshot –frame 5, 7-9  
```  
  
### XML へのグラフィックス ログ ファイルの変換  
 FindStr や XSLT などの使い慣れたツールを使用して、グラフィックス ログを処理および分析するために、DXCap.exe はグラフィックス ログ ファイルを XML に変換できます。  再生モードで、ログを再生せずに XML に変換するには、`-toXML` を使用します。  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog –toXML  
```  
  
 既定では、XML 出力は、グラフィックス ログと同じ名前を持ち、.xml 拡張子が付けられたファイルに書き込まれます。  上記の例では、XML ファイルの名前は **regression\_test\_12.xml** です。  XML ファイルに別の名前を付けるには、その名前を `-toXML` の後に指定します。  
  
```ms-dos  
DXCap.exe –p regression_test_12.vsglog –toXML temp.xml  
```  
  
 結果のファイルには、次のような XML が格納されます。  
  
```xml  
<Moment value="67"/>  
<Method name="CreateDXGIFactory1" >  
    <Return type="HRESULT" value="S_OK" />  
    <Parameter name="riid" type="IID" value="770AAE78-F26F-4DBA-A829-253C83D1B387" />  
    <Parameter name="ppFactory" type="void" handle="1" isOutput="true" />  
</Method>  
  
<Moment value="167"/>  
<Method name="D3D11CreateDevice" >  
    <Return type="HRESULT" value="S_OK" />  
    <Parameter name="pAdapter" type="IDXGIAdapter" handle="34" />  
    <Parameter name="DriverType" type="D3D_DRIVER_TYPE" value="D3D_DRIVER_TYPE_UNKNOWN" />  
    <Parameter name="Software" type="HMODULE" value="pointer" />  
    <Parameter name="Flags" type="UINT" value="0" />  
    <Parameter name="pFeatureLevels" type="D3D_FEATURE_LEVEL" arrSize="1" >  
        <Element value="D3D_FEATURE_LEVEL_11_0" />  
    </Parameter>  
    <Parameter name="FeatureLevels" type="UINT" value="1" />  
    <Parameter name="SDKVersion" type="UINT" value="7" />  
    <Parameter name="ppDevice" type="ID3D11Device" handle="35" isOutput="true" />  
    <Parameter name="pFeatureLevel" type="D3D_FEATURE_LEVEL" value="D3D_FEATURE_LEVEL_11_0" isOutput="true" />  
    <Parameter name="ppImmediateContext" type="ID3D11DeviceContext" value="nullptr" isOutput="true" />  
</Method>  
```  
  
## 必要条件
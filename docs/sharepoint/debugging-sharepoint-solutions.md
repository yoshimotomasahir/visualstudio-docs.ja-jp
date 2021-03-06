---
title: SharePoint ソリューションのデバッグ |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.WebConfigModificationDialog
- VS.SharePointTools.Project.DebuggingNotEnabled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4937bcdef14cadccfa940b2176cf002a976fa16d
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766416"
---
# <a name="debug-sharepoint-solutions"></a>SharePoint ソリューションをデバッグします。
  SharePoint ソリューションは、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] デバッガーを使用してデバッグできます。 デバッグを開始するときに[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]が SharePoint サーバーに、プロジェクト ファイルを展開し、Web ブラウザーで SharePoint サイトのインスタンスを開きます。 以下のセクションでは、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で SharePoint アプリケーションをデバッグする方法について説明します。  
  
-   [デバッグの有効化](#EnableDebug)  
  
-   [F5 キーによるデバッグと配置プロセス](#Deployment)  
  
-   [SharePoint プロジェクトのフィーチャー](#Features)  
  
-   [ワークフローのデバッグ](#Workflow)  
  
-   [フィーチャー イベント レシーバーのデバッグ](#FeatureEvents)  
  
-   [拡張デバッグ情報を有効にします。](#EnhancedDebug)  
  
## <a name="enable-debugging"></a>デバッグの有効化
 SharePoint ソリューションを [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で初めてデバッグするとき、デバッグを有効にするように web.config ファイルが構成されていないことを警告するダイアログ ボックスが表示されます。 web.config ファイルは SharePoint サーバーのインストール時に作成されます。 詳細については、次を参照してください[Web.config ファイルで作業](http://go.microsoft.com/fwlink/?LinkID=149266)。)。このダイアログ ボックスでは、デバッグせずにプロジェクトを実行するか、デバッグを有効にするように web.config ファイルを編集するかを選択できるようになっています。 前者を選択した場合、プロジェクトは通常どおりに実行されます。 後者を選択した場合、web.config ファイルは次のように構成されます。  
  
-   呼び出し履歴は有効にする (`CallStack="true"`)  
  
-   カスタム エラーを無効にする[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)](`<customErrors mode="Off" />`)  
  
-   コンパイル デバッグは有効にする (`<compilation debug="true">`)  
  
 結果として生成される web.config ファイルは、次のとおりです。  
  
```xml  
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <configuration>  
        ...  
        <SharePoint>  
            <SafeMode MaxControls="200"  
                CallStack="true"  
                DirectFileDependencies="10"  
                TotalFileDependencies="50"  
                AllowPageLevelTrace="false">  
                ...  
            </SafeMode>  
        ...  
        </SharePoint>  
        <system.web>  
            ...  
            <customErrors mode="Off" />  
            ...  
            <compilation debug="true">  
            ...  
            </compilation>  
            ...  
        </system.web>  
        ...  
    </configuration>  
```  
  
 変更を破棄し、デバッグを無効にするには、次を変更[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]web.config ファイルで。  
  
-   呼び出し履歴は無効にする (`CallStack="false"`)  
  
-   カスタム エラーを有効にする[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)](`<customErrors mode="On" />`)  
  
-   コンパイル デバッグは無効にする (`<compilation debug="false">`)  
  
## <a name="f5-debug-and-deployment-process"></a>F5 キーを押してデバッグ構成と展開プロセス
 SharePoint プロジェクトをデバッグ モードで実行するとき、SharePoint の配置プロセスによって、次のタスクが実行されます。  
  
1.  カスタマイズ可能な配置前コマンドが実行されます。  
  
2.  [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] コマンドを使用して、Web ソリューション パッケージ (.wsp) ファイルが作成されます。 この .wsp ファイルには、すべての必要なファイルおよびフィーチャーが含まれます。 詳細については、次を参照してください。[ソリューションの概要](http://go.microsoft.com/fwlink/?LinkID=128154)です。  
  
3.  SharePoint ソリューションがファーム ソリューションである場合は、指定されたサイトの [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] の [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] アプリケーション プールがリサイクルされます。 この段階で、[!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] のワーカー プロセスによってロックされたファイルが解放されます。  
  
4.  以前のバージョンのパッケージが既に存在する場合は、.wsp ファイル内の以前のバージョンのフィーチャーおよびファイルが取り消されます。 この段階で、フィーチャーが非アクティブ化され、ソリューション パッケージがアンインストールされた後に、ソリューション パッケージが SharePoint サーバーから削除されます。  
  
5.  .wsp ファイル内の最新のバージョンのフィーチャーおよびファイルがインストールされます。 この段階で、SharePoint サーバーにソリューションが追加され、インストールされます。  
  
6.  ワークフローの場合は、ワークフロー アセンブリがインストールされます。 使用してその場所を変更することができます、*アセンブリの場所*プロパティです。  
  
7.  スコープがサイトまたは Web の場合は、SharePoint でプロジェクトのフィーチャーがアクティブ化されます。 ファーム スコープおよび Web アプリケーション スコープのフィーチャーはアクティブ化されません。  
  
8.  ワークフローの場合に、SharePoint ライブラリ、リスト、または 選択したサイトをワークフローを関連付けます、 **SharePoint カスタマイズ ウィザード**です。  
  
    > [!NOTE]  
    >  選択した場合にのみ、この関連付けが発生した**自動的に関連付けるワークフロー**ウィザードでします。  
  
9. カスタマイズ可能な配置後コマンドが実行されます。  
  
10. アタッチ、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]するデバッガー、[!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)]プロセス (*w3wp.exe*)。 プロジェクトの種類を変更できる場合、*サンド ボックス ソリューション*プロパティとその値に設定されている**true**、デバッガーは、別のプロセスにアタッチし、(*SPUCWorkerProcess.exe*). 詳細については、次を参照してください。[サンド ボックス ソリューションの考慮事項](../sharepoint/sandboxed-solution-considerations.md)です。  
  
11. SharePoint ソリューションがファーム ソリューションである場合は、JavaScript デバッガーが開始されます。  
  
12. 適切なライブラリ、リスト、またはサイト ページが Web ブラウザーに表示されます。  
  
 タスクが 1 つ完了するたびに、ステータス メッセージが [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] の出力ウィンドウに表示されます。 タスクを完了できなかった場合は、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] の [エラー一覧] ウィンドウにエラー メッセージが表示されます。  
  
## <a name="sharepoint-project-features"></a>SharePoint プロジェクトのフィーチャー
 フィーチャーは、サイト定義を使用することによってサイトの変更を単純化する、移植性のあるモジュール式の機能単位です。 パッケージも[!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)](WSS) 要素を特定のスコープに対してアクティブ化できるし、ユーザーが特定の目的またはタスクを達成するのに役立ちます。 テンプレートはフィーチャーとして配置されます。  
  
 展開プロセスが内のフォルダーを作成するプロジェクトをデバッグ モードで実行するときに、*機能*ディレクトリに *%COMMONPROGRAMFILES%\Microsoft shared \web server \14\template\features*です。 機能名の形式である*プロジェクト名*破棄*x*、TestProject_Feature1 などです。  
  
 Feature ディレクトリにソリューションのフォルダーが含まれています、*機能定義*ファイルと*ワークフロー定義*ファイル。 フィーチャー定義ファイル (Feature.xml) は、プロジェクトのください。 プロジェクト定義ファイル内のファイルをについて説明します (*Elements.xml*) プロジェクト テンプレートを説明します。 *Elements.xml*は含まれて**ソリューション エクスプ ローラー**が Feature.xml がソリューション パッケージが作成されたときに発生します。 これらのファイルに関する詳細については、次を参照してください。 [SharePoint プロジェクトとプロジェクト項目テンプレート](../sharepoint/sharepoint-project-and-project-item-templates.md)です。  
  
## <a name="debug-workflows"></a>ワークフローをデバッグします。
 ワークフロー プロジェクトをデバッグすると、その種類に応じたワークフロー テンプレートが [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] によってライブラリまたはリストに追加されます。 このワークフロー テンプレートは手動で開始できるほか、項目を追加または更新することによって開始することもできます。 これで、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を使用してワークフローをデバッグできます。  
  
> [!NOTE]  
>  その他のアセンブリに参照を追加する場合は、アセンブリがグローバル アセンブリ キャッシュ ([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]) にインストールされていることを確認してください。 そうしないと、ワークフロー ソリューションは失敗します。 アセンブリをインストールする方法については、次を参照してください。[ドキュメントや項目でワークフローを手動で開始](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963)です。  
  
 ただし、配置プロセスでは、ワークフローは開始されません。 SharePoint Web サイトからワークフローを開始する必要があります。 Microsoft Office Word 2010 などのクライアント アプリケーションや別個のサーバー側のコードを使用して、ワークフローを開始することもできます。 指定するアプローチのいずれかを使用して、 **SharePoint カスタマイズ ウィザード**です。  
  
 たとえば、ワークフローの手動での開始を許可した場合は、ライブラリまたはリスト内のアイテムから、ワークフローを直接開始します。 ワークフローを手動で開始する方法の詳細については、次を参照してください。[ドキュメント項目に対するワークフローを手動で開始](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963)です。  
  
## <a name="debug-feature-event-receivers"></a>フィーチャー イベント レシーバーをデバッグします。
 既定では、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint アプリケーションを実行すると、そのフィーチャーが SharePoint サーバー上で自動的にアクティブ化されます。 ただし、これにより、問題フィーチャー イベント レシーバーをデバッグするときにためで機能をアクティブにするタイミング[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]デバッガーとは異なるプロセスで実行されます。 つまり、ブレークポイントなどの一部のデバッグ機能が正常に機能しなくなるということです。  
  
 SharePoint の機能の自動ライセンス認証を無効にして、フィーチャーのイベント レシーバーが適切にデバッグできるように、プロジェクトの値を設定**アクティブな配置構成**プロパティを**アクティブ化しません。** デバッグする前にします。 そのうえで、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で SharePoint アプリケーションのデバッグを開始してから、SharePoint でフィーチャーを手動でアクティブ化します。 機能をアクティブ化、開く、**サイトの操作**メニューを SharePoint では、**サイト設定**を選択、**サイト機能の管理**リンク、および、を選択し**Activate**通常どおりデバッグを続行する、機能の横にあるボタンをクリックします。  
  
## <a name="enable-enhanced-debug-information"></a>拡張デバッグ情報を有効にします。
 間の複雑な相互作用のため、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]プロセス (devenv.exe)、 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint ホスト プロセス (*vssphost4.exe*)、SharePoint、および WCF レイヤーは、発生したエラーを診断するときにビルド、配置、およびなどは、たいへんになることができます。 拡張デバッグ情報を有効にすると、こうしたエラーが解決しやすくなります。 これを行うには、まず Windows レジストリで次のレジストリ キーに移動します。  
  
 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools**  
  
 場合、"EnableDiagnostics" **REG_DWORD**値はありません、既に存在する、手動で作成します。 "EnableDiagnostics"値「1」に設定します。  
  
 トレースに表示される情報の 1 の原因がスタックにこのキー値を設定、**出力**で実行している間に、プロジェクト システム エラーが発生する場合は、常に[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。 強化されたデバッグ情報を無効にするには、EnableDiagnostics を 0 に戻すか、この値を削除します。  
  
 その他の SharePoint のレジストリ キーの詳細については、次を参照してください。 [Visual Studio での SharePoint ツールの拡張機能のデバッグ](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)です。  
  
## <a name="see-also"></a>関連項目
 [SharePoint ソリューションのトラブルシューティング](../sharepoint/troubleshooting-sharepoint-solutions.md)  
  

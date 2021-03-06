---
title: 'チュートリアル: DTE オブジェクトからエディター拡張機能へのアクセス |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b888136f51e7893c6ad44ab888d8079ee92d8edf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-accessing-the-dte-object-from-an-editor-extension"></a>チュートリアル: DTE オブジェクトからエディター拡張機能へのアクセス
Vspackage を呼び出して、DTE オブジェクトを取得することができます、 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> DTE オブジェクトの型を持つメソッドです。 Managed Extensibility Framework (MEF) 拡張機能ではインポートできる<xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>を呼び出すと、<xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>の型を持つメソッド<xref:EnvDTE.DTE>です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルに従うには、Visual Studio SDK をインストールする必要があります。 詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)です。  
  
## <a name="getting-the-dte-object"></a>DTE オブジェクトを取得します。  
  
#### <a name="to-get-the-dte-object-from-the-serviceprovider"></a>DTE オブジェクトをサービス プロバイダーから取得するには  
  
1.  という名前の C# の場合は、VSIX プロジェクトを作成する`DTETest`です。 エディター分類子項目テンプレートを追加し、名前`DTETest`です。 詳細については、次を参照してください。[エディター項目テンプレートに、拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)です。  
  
2.  プロジェクトに次のアセンブリ参照を追加します。  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.Shell.Immutable.10.0  
  
3.  DTETest.cs ファイルに移動し、次の追加`using`ディレクティブ。  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio.Shell;  
  
    ```  
  
4.  `GetDTEProvider`クラス、インポート、<xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>です。  
  
    ```csharp  
    [Import]  
    internal SVsServiceProvider ServiceProvider = null;  
  
    ```  
  
5.  `GetClassifier()` メソッドに次のコードを追加します。  
  
    ```csharp  
    DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
  
    ```  
  
6.  使用する必要がある場合、<xref:EnvDTE80.DTE2>インターフェイス、DTE オブジェクトをそれをキャストすることができます。  
  
## <a name="see-also"></a>関連項目  
 [言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)
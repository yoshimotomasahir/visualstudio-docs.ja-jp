---
title: "方法: シェーダーをエクスポートする | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0bd48bf4-9792-4456-a545-e462a2be668d
caps.latest.revision: 11
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 11
---
# 方法: シェーダーをエクスポートする
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このドキュメントでは、Directed Graph Shader Language \(DGSL\) シェーダーをアプリで使用できるようにシェーダー デザイナーを使用してエクスポートする方法を説明します。  
  
 このドキュメントでは、このアクティビティについて説明します。  
  
-   シェーダーのエクスポート  
  
## シェーダーのエクスポート  
 シェーダー デザイナーを使用して作成したシェーダーをアプリで使用するには、グラフィックス API が理解できる形式でシェーダーをエクスポートする必要があります。  シェーダーはニーズに応じてさまざまな方法でエクスポートできます。  
  
#### シェーダーをエクスポートするには  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で、**視覚シェーダー グラフ \(.dgsl\)** ファイルを開きます。  
  
     開く**視覚シェーダー グラフ \(.dgsl\)** ファイルがない場合、「[方法: 基本カラー シェーダーを作成する](../designers/how-to-create-a-basic-color-shader.md)」に示された手順で作成します。  
  
2.  **\[シェーダー デザイナー モード\]** ツール バーで、**\[エクスポート\]**、**\[ファイルのエクスポート\]\[詳細\]** をクリックします。  **\[シェーダーのエクスポート\]** ダイアログ ボックスが表示されます。  
  
3.  **\[保存の種類\]** ドロップダウン リストで、エクスポートする形式を選択します。  
  
     ここでは次の形式を選択できます。  
  
     **HLSL ピクセル シェーダー \(\*.hlsl\)**  
     上位レベル シェーダー言語 \(HLSL\) のソース コードとしてシェーダーをエクスポートします。  このオプションにより、アプリに配置した後でも、シェーダーを変更することができます。  これによりエンド ユーザーの問題に基づくコードのデバッグと修正が簡単になりますが、競争ゲームで不正にスコアを獲得するためなど、ユーザーが望ましくない方法でシェーダーを変更することが簡単になります。  また、シェーダーの読み込み時間がかかることがあります。  
  
     **コンパイル済みピクセル シェーダー \(\*.cso\)**  
     HLSL バイトコードとしてシェーダーをエクスポートします。  このオプションにより、アプリに配置した後でも、シェーダーを変更することができます。  これによりエンド ユーザーの問題に基づくコードのデバッグと修正が簡単になりますが、シェーダーがプリコンパイルされるため、シェーダーがアプリに読み込まれるときも追加ランタイム オーバーヘッドは発生しません。  この場合もある程度のスキルを持つユーザーであれば望ましくない方法でシェーダーを変更できますが、シェーダーがコンパイルされているため、変更が大幅に難しくなります。  
  
     **C\+\+ ヘッダー \(\*.h\)**  
     HLSL バイトコードを含むバイト配列を定義する C\+\+ スタイル ヘッダーとしてシェーダーをエクスポートします。  このオプションでは、修正のテストにアプリの再コンパイルが必要になるため、エンド ユーザーの問題に基づくコードのデバッグと修正に時間がかかる可能性があります。  しかし、アプリへの配置後のシェーダーの変更は不可能とはいえないまでも困難になるため、ユーザーが望ましくない方法でシェーダーを変更することが最も困難になります。  
  
4.  **\[ファイル名\]** ボックスにエクスポートするシェーダーの名前を指定し、**\[保存\]** ボタンをクリックします。  
  
## 参照  
 [方法: 基本カラー シェーダーを作成する](../designers/how-to-create-a-basic-color-shader.md)   
 [シェーダー デザイナー](../designers/shader-designer.md)
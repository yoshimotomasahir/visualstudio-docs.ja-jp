---
title: "イメージ シェイプのプロパティ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.selectimagedialog"
  - "vs.dsltools.dsldesigner.imageshape"
helpviewer_keywords: 
  - "ドメイン固有言語, イメージ シェイプ"
ms.assetid: 9ce00ccd-07f2-4640-ac96-2a60481d0d72
caps.latest.revision: 25
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 25
---
# イメージ シェイプのプロパティ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ドメイン クラスによって生成されたデザイナーでどのように表示するかを指定するにはイメージの図形を使用できます。  定義済みのイメージ ファイルにクラスの `Image` のプロパティを設定してイメージの図形を定義します。  次の形式はサポートされています :  
  
-   .gif  
  
-   .jpg  
  
-   .jpeg  
  
-   .bmp  
  
-   .wmf  
  
-   .emf  
  
-   .png  
  
 既定ではデザイナーのリソース ファイルはイメージ ファイルなど **\*\*\* Dsl \*\*\*** プロジェクトの  **リソース**  のフォルダーにあります。  
  
 詳細については、「[方法: ドメイン固有言語を定義する](../modeling/how-to-define-a-domain-specific-language.md)」を参照してください。  これらのプロパティを使用する方法の詳細については[ドメイン固有言語のカスタマイズおよび拡張](../modeling/customizing-and-extending-a-domain-specific-language.md) を参照してください。  
  
 イメージの図形には次の表に示すプロパティがあります。  
  
|プロパティ|Description|既定値|  
|-----------|-----------------|---------|  
|塗りつぶしの色|この図形の塗りつぶしの色。|白|  
|グラデーションの塗りつぶしモード|このシェイプのグラデーションの塗りつぶしモード。|\[水平方向\]|  
|既定のコネクション ポイントを持っています。|`True` が図形生成されるデザイナーの上部下部左と右のコネクション ポイントを使用します。|False|  
|外枠の色|この図形のアウトラインの色。|黒|  
|アウトラインの破線スタイル|この図形 \(実線ダッシュドットDashDotDashDotDotカスタム\) のアウトラインの破線スタイル。|\[実線\]|  
|アウトラインの太さ|この図形のアウトラインの太さ。|0.03125|  
|テキストの色|このシェイプに関連付けられたテキスト デコレータに使用される色。|黒|  
|Access 修飾子|ジオメトリの図形のアクセス修飾子 \(public または internal\)。|Public|  
|カスタム属性|この図形から生成されるソース・コードに属性を追加するために使用されるクラスが含まれています。|なし|  
|派生型が生成されます。|`True` が基本クラスおよび部分クラスの両方 \(オーバーライドによってカスタマイズをサポートする\) 生成されます。  詳細については、「[生成済みクラスのオーバーライドおよび拡張](../modeling/overriding-and-extending-the-generated-classes.md)」を参照してください。|False|  
|カスタム コンストラクターがあります。|`True` がソース・コードでカスタム コンストラクター提供されます。  詳細については、「[生成済みクラスのオーバーライドおよび拡張](../modeling/overriding-and-extending-the-generated-classes.md)」を参照してください。|False|  
|継承の修飾子|イメージの図形 \(`none``abstract` または `sealed`\) から生成されるソース・コードのクラスの継承について説明します。|\[none\]|  
|イメージの基本図形|このシェイプの基本クラスです。|\(なし\)|  
|名前|このシェイプの名前。|現在の名前|  
|名前空間|このシェイプとサブスクライブする名前空間。|現在の名前空間|  
|ツールヒントの種類|ツールヒントが定義されている場所 \(修正変数または None。\)   修正ツールヒントとして `Fixed Tooltip Text` のプロパティの値が使用されています ; 変数がカスタム コードでツールヒントに指定します。|\[none\]|  
|説明|このシェイプに関連付けられている単純に注意してください。|なし|  
|最初の高さ|表されます。このシェイプの最初の高さ。|1|  
|初期の幅|表されます。このシェイプの初期の幅。|1.5|  
|プロパティとして公開された塗りつぶしの色<br /><br /> 公開されたグラデーションの塗りつぶしモード<br /><br /> プロパティとして公開された外枠の色<br /><br /> プロパティとして公開されたアウトラインの破線スタイル<br /><br /> プロパティとして公開されたアウトラインの太さ<br /><br /> 発行のテキストの色|`True`ユーザーが指定した図形のプロパティを設定できます。  これを設定するには図形定義を右クリックし\[ENT0ENT\] をクリックします。|False|  
|Description|生成されたデザイナーを作成するために使用します。|なし|  
|\[表示名\]|このシェイプの生成されたデザイナーに表示される名前。|なし|  
|固定ツール ヒント テキスト|固定ツールヒントに使用されるテキスト。|なし|  
|ヘルプ キーワード|この要素のキー インデックスを付けるために使用されるヘルプ キーワードです。|なし|  
|Image|このシェイプで使用されるイメージ ファイルへのパス。|なし|  
  
## 参照  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/ja-jp/ca5e84cb-a315-465c-be24-76aa3df276aa)
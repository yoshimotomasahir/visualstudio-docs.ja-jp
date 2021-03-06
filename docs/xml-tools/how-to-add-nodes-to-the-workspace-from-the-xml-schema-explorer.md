---
title: '方法: XML スキーマ エクスプローラーからワークスペースにノードを追加する'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3e1f5821d3a4207d89eb62b9344cff967c73b536
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34752054"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>方法: XML スキーマ エクスプ ローラーからワークスペースにノードを追加

このトピックにノードを追加する方法について説明、 [XML スキーマ デザイナーのワークスぺース](../xml-tools/xml-schema-designer-workspace.md)から、 **XML スキーマ エクスプ ローラー**です。 ドラッグ アンド ドロップのノードでこれを行う、 **XML スキーマ エクスプ ローラー** XSD デザイナーのビューにまたはを使用して、 **XML スキーマ エクスプ ローラー**コンテキスト メニュー。 実行された検索の結果として強調表示されているノードを追加することも、 **XML スキーマ エクスプ ローラー**です。 詳細については、次を参照してください。[する方法: スキーマ セットの検索結果のノードをワークスペースに追加](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md)です。

> [!NOTE]
> グローバル ノードだけに追加することができます、 [XML スキーマ デザイナーのワークスぺース](../xml-tools/xml-schema-designer-workspace.md)です。

## <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>XML のエクスプ ローラーのコンテキスト メニューからノードを追加するには

1.  手順に従います[する方法: を作成し、XSD スキーマ ファイルを編集](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)です。

2.  右クリックして、 `PurchaseOrderType` XSD エクスプ ローラーでノード。 選択**グラフ ビューで表示**です。

     `purchaseOrderType` ノードがグラフ ビューのデザイン サーフェイスに表示されます。

## <a name="to-drag-and-drop-a-node-on-to-a-view"></a>ビューにノードをドラッグ アンド ドロップするには

1.  右クリックし、`PurchaseOrderType`グラフ ビューのノードです。 選択**XML スキーマ エクスプ ローラーで表示**です。

     ノードが強調表示されて、 **XML スキーマ エクスプ ローラー**です。

2.  右クリックして、`PurchaseOrderType`内のノード、 **XML スキーマ エクスプ ローラー**選択**すべての参照**です。

     `purchaseOrder` ノードが強調表示されます。

3.  `purchaseOrder` ノードをグラフ ビューにドラッグします。

     `purchaseOrder` ノードおよび `PurchaseOrderType` ノードがグラフ ビューのデザイン サーフェイスに並べて表示されます。 2 つのノードは関連があるため (`purchaseOrder` 要素は `PurchaseOrderType` 型)、これらの間に矢印が引かれます。

## <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>スキーマ エクスプローラーの検索機能を使用してノードを追加するには

1.  検索 ボックスに「purchaseOrder」を入力、 [XML エクスプ ローラー](../xml-tools/xml-schema-explorer.md)ツールバーや検索ボタンをクリックします。

     ![XML スキーマ エクスプローラー キーワード検索](../xml-tools/media/schemaexplorersearch.gif)

     検索結果が強調表示されて、 **XML スキーマ エクスプ ローラー**垂直スクロール バーのチックでマークされています。

2.  クリックして、ワークスペースに検索結果を追加、**強調表示されたノードをワークスペースに追加**概要結果ペインでボタンをクリックします。

     ![XML スキーマ エクスプローラー検索結果](../xml-tools/media/schemaexplorersearchresult.gif)

     `purchaseOrder`ノードおよび`PurchaseOrderType`ノードがのデザイン サーフェイスに並べて表示されます、[グラフ ビュー](../xml-tools/graph-view.md)です。 2 つのノードは関連があるため (`purchaseOrder` 要素は `PurchaseOrderType` 型)、これらの間に矢印が引かれます。

## <a name="see-also"></a>関連項目

- [XML スキーマ エクスプローラー](../xml-tools/xml-schema-explorer.md)
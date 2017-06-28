---
title: "オブジェクトの有効期間ビュー | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.objectlifetime"
helpviewer_keywords: 
  - "有効期間, オブジェクト"
  - "[オブジェクトの有効期間] ビュー"
  - "パフォーマンス レポート, [オブジェクトの有効期間] ビュー"
  - "プロファイル ツールのレポート, [有効期間] ビュー"
  - "プロファイル ツール, [有効期間] ビュー"
ms.assetid: d0501fdd-4b3a-4e74-b6ac-51d950a2e15b
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# オブジェクトの有効期間ビュー
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

オブジェクトの有効期間ビューは、\[パフォーマンス セッション\] プロパティ ページで **\[.NET オブジェクトの有効期間情報も収集\]** チェック ボックスがオンになっている場合に使用できます。  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] のガベージ コレクターは、アプリケーションのメモリの割り当ておよび解放を管理します。  ガベージ コレクターのパフォーマンスを最適化するために、マネージ ヒープは 0、1、および 2 の 3 つのジェネレーションに分割されます。  ランタイムのガベージ コレクターは、新しいオブジェクトをジェネレーション 0 に格納します。  ガベージ コレクションでごみではないと判断されたオブジェクトは昇格してジェネレーション 1 とジェネレーション 2 に格納されます。  
  
 ガベージ コレクターは、オブジェクトのジェネレーション全体を解放してメモリをクリアします。  プロファイル対象アプリケーションで作成されたオブジェクトの場合、オブジェクトの有効期間ビューにはオブジェクトの数とサイズ、および解放されるオブジェクトが格納されているジェネレーションが表示されます。  
  
## 一般  
  
|列|説明|  
|-------|--------|  
|**\[クラス名\]**|割り当てられた型のクラス名。|  
|**プロセス ID**|プロファイリング実行のプロセス ID。|  
|**プロセス名**|プロセスの名前。|  
|**\[モジュール名\]**|関数を含むモジュールの名前。|  
|**\[モジュール パス\]**|関数を含むモジュールのパス。|  
  
## \[インスタンス データ\]  
 インスタンス データには、プロファイリング実行で作成された型のオブジェクトの数、およびガベージ コレクターで解放されたオブジェクトが格納されているジェネレーションが示されます。  
  
|列|説明|  
|-------|--------|  
|**インスタンス**|この型のオブジェクトの割り当て数。|  
|**\[インスタンス合計 \(%\)\]**|プロファイリング実行で行われた割り当ての合計数の割合。|  
|**\[ジェネレーション 0 収集インスタンス数\]**|ガベージ コレクション アルゴリズムのジェネレーション 0 で解放された型のインスタンスの数。|  
|**\[ジェネレーション 1 収集インスタンス数\]**|ガベージ コレクション アルゴリズムのジェネレーション 1 で解放された型のインスタンスの数。|  
|**\[ジェネレーション 2 収集インスタンス数\]**|ガベージ コレクション アルゴリズムのジェネレーション 2 で解放された型のインスタンスの数。|  
|**\[終了時アクティブ インスタンス数\]**|プロファイリング実行の終了までに解放されなかった型のインスタンスの数。|  
  
## \[サイズ \(バイト\) データ\]  
 サイズ \(バイト\) データは、プロファイリング実行で作成された型のオブジェクトのサイズ、および解放されたオブジェクトが格納されている各ジェネレーションでクリアされたメモリの量を示します。  
  
|列|説明|  
|-------|--------|  
|**\[割り当てバイト数合計\]**|型のすべてのインスタンスの合計バイト数。|  
|**\[バイト数合計 \(%\)\]**|プロファイリング実行で割り当てられた合計バイト数に対する、この型のインスタンスに対して割り当てられた割合。|  
|**\[ジェネレーション 0 収集バイト数\]**|ガベージ コレクション アルゴリズムのジェネレーション 0 で解放された型のインスタンスのサイズ。|  
|**\[ジェネレーション 1 収集バイト数\]**|ガベージ コレクション アルゴリズムのジェネレーション 1 で解放された型のインスタンスのサイズ。|  
|**\[ジェネレーション 2 収集バイト数\]**|ガベージ コレクション アルゴリズムのジェネレーション 2 で解放された型のインスタンスのサイズ。|  
  
## \[ラージ オブジェクト ヒープ データ\]  
 .NET メモリ アロケーターは標準のマネージ ヒープとは別の場所で非常に大きいオブジェクトを管理します。  ラージ オブジェクト ヒープ データは、この場所で管理された型のオブジェクトの数とサイズを示します。  
  
|列|説明|  
|-------|--------|  
|**\[収集された大きなオブジェクト ヒープ \(インスタンス数\)\]**|プロファイリング実行で収集されたラージ オブジェクト ヒープ内に保存されていたこの型のインスタンスの数。|  
|**\[収集された大きなオブジェクト ヒープ \(バイト数\)\]**|プロファイリング実行で収集されたラージ オブジェクト ヒープ内に保存されていたこの型のインスタンスのサイズ \(バイト数\)。|  
  
## 参照  
 [.NET メモリのデータ ビュー](../profiling/dotnet-memory-data-views.md)
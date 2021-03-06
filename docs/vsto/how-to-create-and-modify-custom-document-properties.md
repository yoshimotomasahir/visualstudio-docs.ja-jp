---
title: '方法: を作成し、カスタム ドキュメント プロパティの変更 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8c997fbe764ba355d16def278c9beda8c177faed
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-and-modify-custom-document-properties"></a>方法 : カスタム ドキュメント プロパティを作成および変更する
  上記の Microsoft Office アプリケーションは、ドキュメントで保存される組み込みのプロパティを提供します。 さらに、ドキュメントで保存する追加情報がある場合は、カスタム ドキュメント プロパティを作成し、変更することができます。  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
 カスタム プロパティを使用するには、ドキュメントの CustomDocumentProperties プロパティを使用します。 たとえば、Microsoft Office Excel のドキュメント レベルのプロジェクトでは、 <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A> クラスの `ThisWorkbook` プロパティを使用します。 Excel の VSTO アドイン プロジェクトでは、 <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A> オブジェクトの <xref:Microsoft.Office.Interop.Excel.Workbook> プロパティを使用します。 これらのプロパティは、 <xref:Microsoft.Office.Core.DocumentProperties> オブジェクトのコレクションである <xref:Microsoft.Office.Core.DocumentProperty> オブジェクトを返します。 このコレクションの `Item` プロパティを使用すると、名前またはコレクション内のインデックスに基づいて特定のプロパティを取得できます。  
  
 次の例は、Excel のドキュメント レベルのカスタマイズでカスタム プロパティを追加し、値を割り当てる方法を示します。  
  
 ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください。 [i: アクセスの方法は、Microsoft Word のカスタム ドキュメント プロパティの操作?](http://go.microsoft.com/fwlink/?LinkId=136772)です。  
  
## <a name="example"></a>例  
 [!code-vb[Trin_VstcoreProgramming#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#6)]
 [!code-csharp[Trin_VstcoreProgramming#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#6)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 未定義の `Value` プロパティにアクセスしようとすると、例外が発生します。  
  
## <a name="see-also"></a>関連項目  
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [ドキュメント レベルのカスタマイズのプログラミング](../vsto/programming-document-level-customizations.md)   
 [方法: ドキュメント プロパティの読み込みと書き込みを行う](../vsto/how-to-read-from-and-write-to-document-properties.md)  
  
  
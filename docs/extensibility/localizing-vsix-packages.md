---
title: VSIX パッケージのローカライズ |Microsoft ドキュメント
ms.custom: ''
ms.date: 10/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d94e390374ca2eb77b4332b3a5c253acce69f051
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="localizing-vsix-packages"></a>VSIX パッケージのローカライズ

ターゲット言語ごとに Extension.vsixlangpack ファイルを作成し、正しいフォルダーに配置して、VSIX パッケージをローカライズできます。 ローカライズされたパッケージがインストールされているときに、拡張機能のローカライズされた名前がローカライズされた説明と共に表示されます。 ローカライズされたライセンス ファイル、またはローカライズされた情報を指す URL を指定する場合も表示されます。

場合は、コンテンツ、VSIX パッケージに追加する VSPackage は、メニュー コマンドやその他の UI を参照してください[メニュー コマンドのローカライズ](../extensibility/localizing-menu-commands.md)新しい UI 要素をローカライズする方法についてです。

## <a name="directory-structure"></a>ディレクトリ構造

 ユーザーが、拡張機能をインストール**拡張機能と更新**VSIX パッケージの名前、ターゲット コンピューターの Visual Studio のロケールに一致するフォルダーの最上位のレベルを確認します。 場合**拡張機能と更新**.vsixlangpack 見つかるとファイルを .vsixmanifest ファイル内の対応する値をそのファイル内のローカライズされた値を代入しています。 拡張機能がインストールされるときに、これらの値が表示されます。 次の例は、スペイン語 (ES-ES) とフランス語 (FR) にローカライズされた VSIX パッケージのディレクトリ構造を示しています。  

```text
.
├── MyExtension.dll
├── Extension.vsixmanifest
├── [Content_Types].xml
├── es-ES
│   └── Extension.vsixlangpack
└── fr-FR
    └── Extension.vsixlangpack
```

> [!NOTE]
> VSIX でサポートされているプロジェクト テンプレート、 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] VSIX マニフェストを生成し、source.extension.vsixmanifest という名前を付けます。 Visual Studio でプロジェクトを作成、そのファイルの内容にコピー Extension.VsixManifest VSIX パッケージにします。

## <a name="the-extensionvsixlangpack-file"></a>Extension.vsixlangpack ファイル

Extension.vsixlangpack ファイルは次の[VSIX Language Pack スキーマ 2.0](../extensibility/vsix-language-pack-schema-2-0-reference.md)です。 このスキーマは、 `PackageLanguagePackManifest`、これがすぐに続く、`Metadata`子要素です。 メタデータ要素は、最大 6 個の子要素を含めることができます`DisplayName`、 `Description`、 `MoreInfo`、 `License`、 `ReleaseNotes`、および`Icon`です。 これらの子要素に対応、 `DisplayName`、 `Description`、 `MoreInfo`、 `License`、 `ReleaseNotes`、および`Icon`の子要素、 `Metadata` Extension.vsixmanifest ファイルの要素。

設定する必要があります vsixlangpack ファイルを作成するときに、`Include in Vsix`プロパティを`true`です。 それ以外の場合は、ローカライズされたインストールのテキストは無視されます。

### <a name="to-set-the-include-in-vsix-property"></a>Vsix プロパティで、含めるを設定するには

1. **ソリューション エクスプ ローラー**Extension.vsixlangpack ファイルを右クリックし、クリックして**プロパティ**です。

2.  プロパティ グリッドで、クリックして**Vsix に含める**、その値に設定し、`true`です。

## <a name="example"></a>例

### <a name="description"></a>説明

次の例では、スペイン語に対応する Extension.vsixlangpack ファイルと共に、Extension.vsixmanifest ファイルの関連部分を示します。 言語パックからの値は、ターゲット コンピューターの Visual Studio のロケールがスペイン語に設定されている場合、マニフェストから値を置き換えます。

### <a name="code"></a>コード

 [Extension.vsixmanifest]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageManifest ...>
  <Metadata ...>
    <DisplayName>Family Tree</DisplayName>
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>
    <MoreInfo>http://www.contoso.com/products/FamilyTree.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
  <Installation .../>
  <Dependencies .../>
  <Prerequisites .../>
  <Assets .../>
</PackageManifest>
```

 [Extension.vsixlangpack]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</DisplayName>
    <Description> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</Description>
    <MoreInfo> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
</PackageLanguagePackManifest>
```

## <a name="see-also"></a>関連項目

|Title|説明|
|-----------|-----------------|
|[VSIX LanguagePack スキーマ 2.0 リファレンス](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|VSIX の言語パックでは、.vsix 展開ファイルのローカライズ情報について説明します。|
|[VSIX パッケージの構造](../extensibility/anatomy-of-a-vsix-package.md)|構造と、vsix パッケージの内容について説明します。|
|[メニュー コマンドのローカライズ](../extensibility/localizing-menu-commands.md)|拡張機能では、他の文字列リソースをローカライズする方法を示します。|
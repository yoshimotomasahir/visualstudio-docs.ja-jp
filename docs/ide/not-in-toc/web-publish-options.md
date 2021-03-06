---
title: 状況に適した発行オプション
ms.date: 03/09/2017
ms.reviewer: riande
ms.prod: visual-studio-dev15
ms.technology: vs-ide-deployment
ms.topic: conceptual
helpviewer_keywords:
- ASP.NET, web applications, deployment, publishing
ms.assetid: 3A13F685-531C-457D-A98E-631888011E4B
author: Mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0fd980aa7da59c98348c4dede5aee9835863d522
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# 状況に適した発行オプション

Visual Studio 内から、次のターゲットに Web アプリケーションを直接発行できます。

- [Azure App Service](#azure-app-service)
- [Azure Virtual Machines](#azure-virtual-machines)
- [ファイル システム](#file-system)
- [カスタム ターゲット (IIS、FTP など)](#custom-targets) (任意の Web サーバーをすべて含みます)

**[発行]** タブでは、既存の発行プロファイルを選んだり、既存の発行プロファイルをインポートしたり、ここで説明するオプションを使って新しい発行プロファイルを作成したりできます。 IDE でのアプリの種類別の発行オプションについては、[デプロイの概要](../../deployment/deploying-applications-services-and-components.md)に関する記事を参照してください。

## Azure App Service Web Apps

[Azure App Service Web Apps](/azure/app-service/app-service-web-overview) (または Web Apps) では、インフラストラクチャを保守せずに、スケーラブルでバラエティに富んだ Web アプリケーションやサービスをすばやく作成できます。

App Service の[価格レベルまたはプラン](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)を選ぶことで、Web アプリが備えるコンピューティング能力を決定します。 また、価格レベルを変更することなく、複数の Web アプリ (および他の種類のアプリ) で同じ App Service を共有することもできます。 たとえば、開発、ステージング、運用の Web アプリを同じ App Service でホストすることができます。

App Service は Azure のクラウドでホストされる仮想マシン上で実行されますが、これらの仮想マシンはユーザーが管理します。 App Service の各 Web アプリには、\*.azurewebsites.net という一意の URL が割り当てられます。Free 以外のすべての価格レベルでは、カスタム ドメイン名をサイトに割り当てることもできます。

### Azure App Service Web Apps を選ぶ状況

- インターネット経由でアクセスできる Web アプリケーションをデプロイしたい。
- 再デプロイする必要なしに、需要に応じて Web アプリケーションを自動的に拡張したい。
- サーバーのインフラストラクチャを管理したくない (すべてのソフトウェアの更新を含む)。
- Web アプリケーションをホストするサーバーで、コンピューター レベルのカスタマイズを行う必要がない。

> 自社のデータセンターまたは他のオンプレミス コンピューターで Azure App Service を使いたい場合は、[Azure Stack](https://azure.microsoft.com/overview/azure-stack/) を使って行うことができます。

ASP.NET Core アプリの発行方法の詳細については、「[Visual Studio を使用して Azure App Service に ASP.NET Core アプリを発行する](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)」を参照してください。

## Azure Virtual Machines

[Azure Virtual Machines (VM)](https://azure.microsoft.com/documentation/services/virtual-machines/) を使うと、任意の数のコンピューティング リソースをクラウドに作成して管理できます。 VM 上のすべてのソフトウェアと更新プログラムについての責任を負うことにより、ユーザーは Web アプリケーションで必要なだけいくらでもカスタマイズできます。 また、ユーザーはリモート デスクトップを介して仮想マシンに直接アクセスでき、各マシンは必要な限り割り当てられた IP アドレスを保持します。

仮想マシンでホストされている Web アプリケーションの拡張には、需要に応じた追加 VM のスピンアップと、必要なソフトウェアのデプロイが含まれます。 このような制御レベルの追加により、グローバル リージョンごとに拡張方法を変えることができます。 たとえば、異なるリージョンの従業員がアプリケーションを利用している場合、リージョンの従業員の数に従って VM を拡張でき、コストを削減できる可能性があります。

詳しくは、Visual Studio の [カスタム] オプションを使ってデプロイ ターゲットとして使うことができる Azure App Service、Azure Virtual Machines、他の Azure サービスの間の[詳細な違い](https://azure.microsoft.com/documentation/articles/choose-web-site-cloud-service-vm/)をご覧ください。

### Azure Virtual Machines を選ぶ状況

- インターネット経由でアクセス可能な Web アプリケーションをデプロイし、割り当てられた IP アドレスの有効期間全体を通して完全に制御したい。
- 専用データベース システムなどの追加ソフトウェア、特定のネットワーク構成、ディスク パーティションなど、サーバーでコンピューター レベルのカスタマイズが必要である。
- Web アプリケーションのスケーリングをきめ細かく制御したい。
- その他の理由で、アプリケーションをホストするサーバーに直接アクセスする必要がある。

> 自社のデータセンターまたは他のオンプレミス コンピューターで Azure Virtual Machines を使いたい場合は、[Azure Stack](https://azure.microsoft.com/overview/azure-stack/) を使って行うことができます。


## ファイル システム

ファイル システムへのデプロイとは、ユーザーが所有するコンピューターの特定のフォルダーに Web アプリケーションのファイルを単にコピーすることです。 この方法は、テスト目的で、またはコンピューターが Web サーバーも実行している場合に限られた数のユーザーが使うアプリケーションをデプロイする場合に、最もよく使われます。 ターゲット フォルダーがネットワークで共有されている場合、ファイル システムにデプロイすると、他のユーザーも Web アプリケーション ファイルを使用して特定のサーバーにデプロイできます。

アプリケーションの構成方法およびアプリケーションが接続されているネットワークに応じて、Web サーバーを実行しているすべてのローカル コンピューターが、インターネットまたはイントラネットを通してアプリケーションを利用できます (コンピューターがインターネットに直接接続されている場合、外部のセキュリティ脅威からの保護に特に注意が必要です)。ユーザーは、これらのコンピューターを管理するので、ソフトウェアとハードウェアの構成を完全に制御できます。

何らかの理由で (コンピューターのアクセスなど) ユーザーが Azure App Service や Azure Virtual Machines などのクラウド サービスを使用できない場合、ユーザーは自社のデータセンターで [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) を使用できます。 Azure Stack を使うと、ユーザーは Azure App Service および Azure Virtual Machines によってコンピューティング リソースを管理および使用しながら、すべてのものをオンプレミスに保持できます。

### ファイル システムのデプロイを選ぶ状況

- ファイル共有にアプリケーションをデプロイし、他のユーザーがそれを別のサーバーにデプロイすることだけが必要である。
- ローカル テスト デプロイのみが必要である。
- 別のデプロイ ターゲットに送る前にアプリケーション ファイルを調べて場合によっては個別に変更したい。

.NET Core アプリを展開する方法の詳細については、「[Visual Studio で .NET Core アプリを展開する](/dotnet/core/deploying/deploy-with-vs)」を参照してください。

## カスタム ターゲット

カスタム ターゲットを使うと、Azure App Service、Azure Virtual Machines、ローカル ファイル システム以外のターゲットに Web アプリケーションをデプロイできます。 アクセスできるファイル システムや他のサーバー (インターネットまたはイントラネット) にデプロイできます。他のクラウド サービスも含まれます。 Web デプロイ (ファイルまたは .ZIP) および FTP で使用できます。

カスタム ターゲットを選ぶと、Visual Studio はユーザーにプロファイル名の指定を求めた後、ターゲット サーバーまたは場所、サイト名、資格情報などの追加の**接続**情報を収集します。 **[設定]** タブで次のビヘイビアーをコントロールできます。

- デプロイする構成。
- 宛先から既存のファイルを削除するかどうか。
- 発行中にプリコンパイルするかどうか。
- App_Data フォルダーのファイルをデプロイから除外するかどうか。

Visual Studio では任意の数のカスタム デプロイ プロファイルを作成し、異なる設定でプロファイルを管理できます。

### カスタム デプロイを選ぶ状況

- URL でアクセスできる Azure 以外のプロバイダーでクラウド サービスを使っている。
- Visual Studio で使っている資格情報または Azure アカウントに直接結び付けられている資格情報とは異なる資格情報を使ってデプロイしたい。
- デプロイするたびに、ターゲットからファイルを削除したい。

IIS への発行の詳細については、「[IIS 8.0 Using ASP.NET 3.5 and ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)」 (ASP.NET 3.5 および ASP.NET 4.5 を使用する IIS 8.0) および「[Remote Debug ASP.NET on a Remote IIS Computer](../../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)」(リモート IIS コンピューター上の ASP.NET のリモート デバッグ) を参照してください。

---
title: Outils pour les développeurs .NET d’Azure
description: Obtenez les outils pour commencer à utiliser les bibliothèques .NET Azure à partir d’un environnement Windows, Linux et Mac.
ms.date: 06/19/2020
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: fa645b152f15550b25a3542ba0cdbb43799536b9
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174927"
---
# <a name="azure-tools-for-developing-with-net"></a>Outils Azure pour le développement avec .NET

## <a name="sdk-downloads"></a>Téléchargements du SDK

Les bibliothèques Azure pour .NET sont implémentées en tant que [packages NuGet](https://www.nuget.org/packages?q=windowsazureofficial). Consultez les informations de référence sur l' [API](/dotnet/api/overview/azure/?view=azure-dotnet) pour la documentation de référence organisée par le service Azure.

## <a name="development-tools"></a>Outils de développement

Visual Studio propose des outils pour de nombreux services Azure intégrés. Certains services Azure disposent d’outils ou d’émulateurs supplémentaires, comme [Explorateur stockage Azure](https://azure.microsoft.com/features/storage-explorer/). Consultez la documentation de votre service Azure pour obtenir des outils supplémentaires, si nécessaire.

Sélectionnez votre environnement de développement par défaut ci-dessous.

## <a name="visual-studio-on-windows"></a>[Visual Studio sur Windows](#tab/vs)

Visual Studio version 2017 et versions ultérieures intègrent la prise en charge du développement Azure. Les étapes ci-dessous décrivent l’activation de la prise en charge du développement Azure dans Visual Studio.

Pour Visual Studio 2015 et versions antérieures, <a href="vs2015-install.md">suivez ces instructions</a>.

### <a name="step-1-download-visual-studio-2019"></a>Étape 1 : Télécharger Visual Studio 2019

Vous pouvez ignorer cette étape si vous avez déjà installé Visual Studio 2019.

> [!div class="nextstepaction"]
> [Télécharger Visual Studio 2019](https://www.visualstudio.com/downloads/)

### <a name="step-2-install-the-two-azure-workloads"></a>Étape 2 : Installer les deux charges de travail Azure

Dans le programme d’installation de Visual Studio, installez Visual Studio (ou modifiez une installation existante). Assurez-vous que les charges de travail *développement Azure* et développement *Web et ASP.net* sont sélectionnées.

### <a name="step-3-develop-with-net-on-azure"></a>Étape 3 : Développer avec .NET sur Azure

Commencez par [déployer votre première application web ASP.NET Core sur Azure App Service](/azure/app-service-web/app-service-web-get-started-dotnet).

## <a name="visual-studio-code-cross-platform"></a>[Visual Studio Code (multiplateforme)](#tab/vscode)

Visual Studio Code dispose de tout ce dont vous avez besoin pour le développement Azure multiplateforme.

### <a name="step-1-download-the-net-core-sdk"></a>Étape 1 : Télécharger le kit SDK .NET Core

Le Kit de développement logiciel (SDK) et les outils de ligne de commande pour les applications .NET Core.

> [!div class="nextstepaction"]
> [Télécharger le kit de développement logiciel (SDK) .NET Core](https://dotnet.microsoft.com/download)

### <a name="step-2-visual-studio-code"></a>Étape 2 : Visual Studio Code

Modifiez et déboguez des applications .NET Core sur n’importe quel système d’exploitation : Windows, Mac et Linux.

> [!div class="nextstepaction"]
> [Télécharger Visual Studio Code](https://code.visualstudio.com)

### <a name="step-3-azure-tools-extension"></a>Étape 3 : extension Azure Tools

Installez l’extension Azure Tools dans Visual Studio Code.

> [!div class="nextstepaction"]
> [Installer l’extension Azure Tools](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack)

### <a name="step-4-develop-with-net-on-azure"></a>Étape 4 : développer avec .NET sur Azure

Commencez par [déployer votre première ASP.net Core application Web sur Azure App service sur Linux](/azure/app-service/containers/quickstart-dotnetcore).

---

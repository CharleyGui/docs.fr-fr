---
title: Outils Azure pour Visual Studio 2015
description: Obtenez les outils pour commencer à utiliser les bibliothèques Azure .NET à partir de Visual Studio 2015.
ms.date: 06/19/2020
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: 72229ce0c0276912ddc5658e34f4572a7948a4e6
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174924"
---
# <a name="azure-tools-for-visual-studio-2015"></a>Outils Azure pour Visual Studio 2015

Le moyen le plus rapide et le plus simple d’installer le **Kit de développement logiciel (SDK) Azure pour Visual Studio 2015** ainsi que le **Kit de développement logiciel (SDK) et outils Service Fabric pour Visual Studio 2015** consiste à utiliser [Web Platform Installer](https://www.microsoft.com/web/downloads/platform.aspx). Microsoft Web Platform Installer est un outil gratuit qui simplifie le téléchargement, l’installation et la mise à jour de certains composants de Microsoft Web Platform, y compris les outils Azure pour Visual Studio 2015. Ces Kits de développement logiciel (SDK) peuvent également être téléchargés et installés en tant que composants individuels à partir de la [page Téléchargements Azure](https://azure.microsoft.com/downloads/).

## <a name="using-the-web-platform-installer"></a>Utiliser Web Platform Installer

1. Téléchargez et exécutez le [programme d’amorçage Web Platform Installer](https://www.microsoft.com/web/handlers/webpi.ashx?command=getinstallerredirect&appid=VWDOrVs2015AzurePack;MicrosoftAzure-ServiceFabric-VS2015).

2. Le programme d’amorçage installe Web Platform Installer (si nécessaire) et place automatiquement les dernières versions des éléments **Kit de développement logiciel (SDK) pour Visual Studio 2015** et **Kit de développement logiciel (SDK) et outils Service Fabric pour Visual Studio 2015** dans votre liste des *Éléments à installer*. Cliquez sur **Installer**.

    ![Web Platform Installer](media/vs2015-install/webpi.png)

3. Dans l’écran suivant, cliquez sur **J’accepte**. Web PI télécharge et installe les composants que vous avez sélectionnés.

4. Une fois l’installation terminée, il affiche un écran de confirmation. Cliquez sur **Terminer**. Vous pouvez maintenant fermer Web Platform Installer.

## <a name="verifying-the-installation"></a>Vérification de l'installation

1. Dans Visual Studio 2015, cliquez sur le menu **Outils**, puis cliquez sur **Extensions et mises à jour...**.

2. La liste affichée contient plusieurs outils Azure, tel que les **Outils Microsoft Azure App Service**, le **Service connecté du stockage Microsoft Azure**, et les **Outils Service Fabric**.

    ![Extensions et mises à jour](media/vs2015-install/ext-tools.png)

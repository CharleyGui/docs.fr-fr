---
title: Installer .NET Framework 3,5 sur Windows 10, 8,1, 8
description: Découvrez comment installer .NET Framework 3.5 sur Windows 10, Windows 8.1 et Windows 8.
ms.date: 07/16/2018
ms.openlocfilehash: a385c46d2b3b384bc0a413d1dfa80e88ba7fb00a
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223805"
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a>Installer le .NET Framework 3.5 sur Windows 10, Windows 8.1 et Windows 8

Vous pouvez avoir besoin de .NET Framework 3.5 pour exécuter une application sur Windows 10, Windows 8.1 et Windows 8. Vous pouvez également utiliser ces instructions pour les versions antérieures de Windows.

## <a name="download-the-offline-installer"></a>Télécharger le programme d’installation hors connexion

Le programme d’installation hors connexion de .NET Framework 3,5 SP1 est disponible sur la [page de téléchargement .NET Framework 3,5 SP1](https://dotnet.microsoft.com/download/dotnet-framework/net35-sp1) et est disponible pour les versions de Windows antérieures à Windows 10.

## <a name="install-the-net-framework-35-on-demand"></a>Installer .NET Framework 3.5 à la demande

Vous pouvez voir la boîte de dialogue de configuration suivante si vous essayez d’exécuter une application qui nécessite .NET Framework 3.5. Choisissez **Installer cette fonctionnalité** pour activer le .NET Framework 3.5. Cette option requiert une connexion Internet.

![Capture d’écran de la boîte de dialogue d’installation de .NET Framework.](./media/dotnet-35-windows-10/dotnet-framework-installation-dialog.png)

### <a name="why-am-i-getting-this-pop-up"></a>Pourquoi cette fenêtre contextuelle apparaît-elle ?

Le .NET Framework est créé par Microsoft et fournit un environnement d’exécution d’applications. Différentes versions sont disponibles. De nombreuses entreprises développent leurs applications pour qu’elles s’exécutent avec le .NET Framework, et ces applications en ciblent une version spécifique. Si vous voyez cette fenêtre contextuelle, cela signifie que vous tentez d’exécuter une application qui nécessite le .NET Framework version 3.5, mais que cette version n’est pas installée sur votre système.

## <a name="enable-the-net-framework-35-in-control-panel"></a>Activer .NET Framework 3.5 dans le Panneau de configuration

Vous pouvez activer le .NET Framework 3.5 dans le Panneau de configuration de Windows. Cette option requiert une connexion Internet.

1. Appuyez sur la touche Windows ![ du logo de la touche Windows.](./media/dotnet-35-windows-10/windows-keyboard-logo.png) sur votre clavier, tapez « fonctionnalités Windows », puis appuyez sur entrée. La boîte de dialogue **Activer ou désactiver des fonctionnalités Windows** apparaît.

2. Cochez la case **.NET Framework 3.5 (inclut .NET 2.0 et 3.0)**, sélectionnez **OK** et redémarrez l’ordinateur si vous y êtes invité.

   ![Capture d’écran montrant l’installation de .NET à l’aide du panneau de configuration.](./media/dotnet-35-windows-10/dotnet-control-panel.png)

   Vous n’avez pas besoin de sélectionner des éléments enfants pour **Activation HTTP de Windows Communication Foundation** et **Activation non-HTTP de Windows Communication Foundation**, sauf si vous êtes un développeur ou un administrateur de serveur ayant besoin de cette fonctionnalité.

## <a name="troubleshoot-the-installation-of-the-net-framework-35"></a>Résoudre les problèmes d’installation du .NET Framework 3.5

Pendant l’installation, si vous rencontrez l’erreur 0x800f0906, 0x800f0907, 0x800f081f ou 0x800F0922, consultez [Erreur d’installation de .NET Framework 3.5 : 0x800f0906, 0x800f0907 ou 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) pour découvrir comment résoudre ces problèmes.

Si vous ne pouvez toujours pas résoudre votre problème d’installation ou si vous n’avez pas de connexion Internet, vous pouvez essayer de l’installer en utilisant votre support d’installation Windows. Pour plus d’informations, consultez [Déployer le .NET Framework 3.5 à l’aide de Gestion et maintenance des images de déploiement (DISM)](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism). Si vous utilisez Windows 7, Windows 8.1 ou la version la plus récente de Windows 10, mais que vous n’avez pas le support d’installation, créez un support d’installation à jour ici : [créer un support d’installation pour Windows](https://support.microsoft.com/help/15088/windows-create-installation-media). Informations supplémentaires sur les fonctionnalités de Windows 10 à la demande : [fonctionnalités à la demande](/windows-hardware/manufacture/desktop/features-on-demand-v2--capabilities).

> [!WARNING]
> Si vous ne vous basez pas sur Windows Update comme source pour l’installation de .NET Framework 3.5, vous devez veiller à utiliser strictement des sources de la même version du système d’exploitation Windows correspondant. L’utilisation de sources à partir d’une version différente du système d’exploitation Windows installe une version incompatible de .NET Framework 3,5 ou provoque l’échec de l’installation, ce qui laisse le système dans un État non pris en charge et inutilisable.

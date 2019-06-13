---
title: 'Procédure : installer et désinstaller des services Windows'
ms.date: 02/05/2019
helpviewer_keywords:
- Windows Service applications, deploying
- services, uninstalling
- services, installing
- installing Windows Services
- uninstalling applications, apps, Windows services
- installation, Windows services
- uninstalling Windows services
- installutil.exe tool
ms.assetid: c89c5169-f567-4305-9d62-db31a1de5481
author: ghogen
ms.openlocfilehash: 4f6e25467e713263ab5cdecc08078153098fdede
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690682"
---
# <a name="how-to-install-and-uninstall-windows-services"></a>Procédure : installer et désinstaller des services Windows

Si vous développez un service Windows à l’aide du .NET Framework, vous pouvez installer rapidement votre application de service à l’aide de l’utilitaire en ligne de commande [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md). Les développeurs désireux de mettre à la disposition de certains utilisateurs un service Windows qu’ils peuvent installer et désinstaller doivent utiliser InstallShield. Pour plus d’informations, consultez [Créer un package d’installation (client Windows)](https://docs.microsoft.com/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client).

> [!WARNING]
> Si vous voulez désinstaller un service de votre ordinateur, ne suivez pas les étapes décrites dans cet article. Au lieu de cela, déterminez quel programme ou package logiciel a installé le service, puis choisissez **Applications** dans les paramètres pour désinstaller ce programme. Notez que de nombreux services font partie intégrante de Windows. Si vous les supprimez, vous pouvez rendre le système instable.

Pour utiliser les étapes décrites dans cet article, vous devez d’abord ajouter un programme d’installation de service à votre service Windows. Pour plus d’informations, consultez [Procédure pas à pas : Création d’une application de service Windows](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).

Vous ne pouvez pas exécuter les projets de service Windows directement à partir de l’environnement de développement Visual Studio en appuyant sur F5. Avant de pouvoir exécuter le projet, vous devez installer le service dans le projet.

> [!TIP]
> Vous pouvez utiliser l’**Explorateur de serveurs** pour vérifier que vous avez bien installé ou désinstallé le service. Pour plus d’informations, consultez [Guide pratique pour utiliser l’Explorateur de serveurs dans Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).

### <a name="install-your-service-manually"></a>Installer votre service manuellement

1. Dans le menu **Démarrer**, sélectionnez le répertoire **Visual Studio \<*version*>** , puis **Invite de commandes développeur pour VS \<*version*>** .

     L’invite de commandes développeur pour Visual Studio s’affiche.

2. Accédez au répertoire dans lequel se trouve le fichier exécutable compilé de votre projet.

3. Exécutez *InstallUtil.exe* à partir de l’invite de commandes avec le fichier exécutable de votre projet en guise de paramètre :

    ```console
    installutil <yourproject>.exe
    ```

     Si vous utilisez l’invite de commandes développeur pour Visual Studio, *InstallUtil.exe* doit se trouver dans le chemin système. Si ce n’est pas le cas, vous pouvez l’ajouter au chemin ou utiliser le chemin complet pour l’appeler. Cet outil est installé avec le .NET Framework dans *% WINDIR%\Microsoft.NET\Framework[64]\\< version_framework\>* .

     Par exemple :
     - Pour la version 32 bits de .NET Framework 4 ou 4.5 et ultérieur, si votre répertoire d’installation Windows est *C:\Windows*, le chemin par défaut est *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.
     - Pour la version 64 bits de .NET Framework 4 ou 4.5 et ultérieur, le chemin par défaut est *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.

### <a name="uninstall-your-service-manually"></a>Désinstaller votre service manuellement

1. Dans le menu **Démarrer**, sélectionnez le répertoire **Visual Studio \<*version*>** , puis **Invite de commandes développeur pour VS \<*version*>** .

     L’invite de commandes développeur pour Visual Studio s’affiche.

2. Exécutez *InstallUtil.exe* à partir de l’invite de commandes avec la sortie de votre projet en guise de paramètre :

    ```console
    installutil /u <yourproject>.exe
    ```

3. Après avoir supprimé l’exécutable d’un service, il est possible que ce service soit toujours présent dans le Registre. Si c’est le cas, utilisez la commande [sc delete](/windows-server/administration/windows-commands/sc-delete) pour supprimer l’entrée du service dans le Registre.

## <a name="see-also"></a>Voir aussi

- [Introduction aux applications de service Windows](../windows-services/introduction-to-windows-service-applications.md)
- [Guide pratique pour créer des services Windows](../windows-services/how-to-create-windows-services.md)
- [Guide pratique pour ajouter des programmes d’installation à votre application de service](../windows-services/how-to-add-installers-to-your-service-application.md)
- [Installutil.exe (outil Installer)](../tools/installutil-exe-installer-tool.md)

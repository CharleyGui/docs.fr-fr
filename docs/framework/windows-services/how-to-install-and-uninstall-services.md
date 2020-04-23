---
title: 'Comment : installer et désinstaller des services Windows'
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
ms.openlocfilehash: 8937ef8b4007253b06444e59b292395084e4df2f
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607917"
---
# <a name="how-to-install-and-uninstall-windows-services"></a>Comment : installer et désinstaller des services Windows

Si vous développez un service Windows avec l' .NET Framework, vous pouvez installer rapidement votre application de service à l’aide de l’utilitaire de ligne de commande [*installutil. exe*](../tools/installutil-exe-installer-tool.md) ou de [PowerShell](/powershell/scripting/overview). Les développeurs désireux de mettre à la disposition de certains utilisateurs un service Windows qu’ils peuvent installer et désinstaller doivent utiliser InstallShield. Pour plus d’informations, consultez [créer un package d’installation (Windows Desktop)](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop).

> [!WARNING]
> Si vous voulez désinstaller un service de votre ordinateur, ne suivez pas les étapes décrites dans cet article. Au lieu de cela, déterminez quel programme ou package logiciel a installé le service, puis choisissez **Applications** dans les paramètres pour désinstaller ce programme. Notez que de nombreux services font partie intégrante de Windows. Si vous les supprimez, vous pouvez rendre le système instable.

Pour utiliser les étapes décrites dans cet article, vous devez d’abord ajouter un programme d’installation de service à votre service Windows. Pour plus d’informations, consultez [procédure pas à pas : création d’une application de service Windows](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).

Vous ne pouvez pas exécuter les projets de service Windows directement à partir de l’environnement de développement Visual Studio en appuyant sur F5. Avant de pouvoir exécuter le projet, vous devez installer le service dans le projet.

> [!TIP]
> Vous pouvez utiliser l’**Explorateur de serveurs** pour vérifier que vous avez bien installé ou désinstallé le service. Pour plus d’informations, consultez [Guide pratique pour utiliser l’Explorateur de serveurs dans Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio).

### <a name="install-your-service-manually-using-installutilexe-utility"></a>Installer votre service manuellement à l’aide de l’utilitaire InstallUtil. exe

1. Dans le menu **Démarrer**, sélectionnez le répertoire **Visual Studio \<*version*>**, puis **Invite de commandes développeur pour VS \<*version*>**.

     L’invite de commandes développeur pour Visual Studio s’affiche.

2. Accédez au répertoire dans lequel se trouve le fichier exécutable compilé de votre projet.

3. Exécutez *InstallUtil.exe* à partir de l’invite de commandes avec le fichier exécutable de votre projet en guise de paramètre :

    ```console
    installutil <yourproject>.exe
    ```

     Si vous utilisez l’invite de commandes développeur pour Visual Studio, *InstallUtil.exe* doit se trouver dans le chemin système. Si ce n’est pas le cas, vous pouvez l’ajouter au chemin ou utiliser le chemin complet pour l’appeler. Cet outil est installé avec le .NET Framework dans *%windir%\Microsoft.NET\Framework [64]\\<framework_version\>*.

     Par exemple :
     - Pour la version 32 bits de .NET Framework 4 ou 4.5 et ultérieur, si votre répertoire d’installation Windows est *C:\Windows*, le chemin par défaut est *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.
     - Pour la version 64 bits de .NET Framework 4 ou 4.5 et ultérieur, le chemin par défaut est *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*.

### <a name="uninstall-your-service-manually-using-installutilexe-utility"></a>Désinstaller manuellement votre service à l’aide de l’utilitaire InstallUtil. exe

1. Dans le menu **Démarrer**, sélectionnez le répertoire **Visual Studio \<*version*>**, puis **Invite de commandes développeur pour VS \<*version*>**.

     L’invite de commandes développeur pour Visual Studio s’affiche.

2. Exécutez *InstallUtil.exe* à partir de l’invite de commandes avec la sortie de votre projet en guise de paramètre :

    ```console
    installutil /u <yourproject>.exe
    ```

3. Après avoir supprimé l’exécutable d’un service, il est possible que ce service soit toujours présent dans le Registre. Si c’est le cas, utilisez la commande [sc delete](/windows-server/administration/windows-commands/sc-delete) pour supprimer l’entrée du service dans le Registre.

### <a name="install-your-service-manually-using-powershell"></a>Installer votre service manuellement à l’aide de PowerShell

1. Dans le menu **Démarrer** , sélectionnez le répertoire **Windows PowerShell** , puis sélectionnez **Windows PowerShell**.

2. Accédez au répertoire dans lequel se trouve le fichier exécutable compilé de votre projet.

3. Exécutez l’applet de commande [**New-service**](/powershell/module/microsoft.powershell.management/new-service) avec avec la sortie de votre projet et un nom de service comme paramètres :

    ```powershell
    New-Service -Name "YourServiceName" -BinaryPathName <yourproject>.exe
    ```

### <a name="uninstall-your-service-manually-using-powershell"></a>Désinstaller manuellement votre service à l’aide de PowerShell

1. Dans le menu **Démarrer** , sélectionnez le répertoire **Windows PowerShell** , puis sélectionnez **Windows PowerShell**.

2. Exécutez l’applet de commande [**Remove-service**](/powershell/module/microsoft.powershell.management/remove-service) avec le nom de votre service comme paramètre :

    ```powershell
    Remove-Service -Name "YourServiceName"
    ```

3. Après avoir supprimé l’exécutable d’un service, il est possible que ce service soit toujours présent dans le Registre. Si c’est le cas, utilisez la commande [sc delete](/windows-server/administration/windows-commands/sc-delete) pour supprimer l’entrée du service dans le Registre.

    ```powershell
    sc.exe delete "YourServiceName"
    ```

## <a name="see-also"></a>Voir aussi

- [Introduction aux applications de service Windows](../windows-services/introduction-to-windows-service-applications.md)
- [Comment : créer des services Windows](../windows-services/how-to-create-windows-services.md)
- [Comment : ajouter des programmes d’installation à votre application de service](../windows-services/how-to-add-installers-to-your-service-application.md)
- [Installutil.exe (outil d’installation)](../tools/installutil-exe-installer-tool.md)

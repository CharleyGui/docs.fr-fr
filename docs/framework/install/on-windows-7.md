---
title: Installer le .NET Framework sur Windows 7 SP1
description: Découvrez comment installer le .NET Framework sur Windows 7 SP1.
ms.date: 04/18/2019
ms.openlocfilehash: 900b38110626a93f37829045a8676ea87101d7e9
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899085"
---
# <a name="install-the-net-framework-on-windows-7-sp1-and-windows-server-2008-r2"></a>Installer le .NET Framework sur Windows 7 SP1 et Windows Server 2008 R2

Un grand nombre d’applications sur Windows nécessitent l’installation du .NET Framework. Pour l’installer, vous pouvez vous aider des instructions suivantes. Votre présence ici s’explique peut-être par l’affichage sur votre machine de la boîte de dialogue suivante après une tentative d’exécution d’une application.

![Impossible de démarrer cette application](./media/this-application-could-not-be-started.png)

Ces instructions ont pour but de vous aider à installer les versions du .NET Framework dont vous avez besoin. [.NET Framework 4.8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) est la dernière version. Cette version est prise en charge sur Windows 7 SP1 et Windows Server 2008 R2. Elle est fournie avec la [Mise à jour de Windows 10 de mai 2019](https://support.microsoft.com/help/4028685/windows-10-get-the-update).

## <a name="net-framework-48"></a>.NET Framework 4.8

> [!div class="button"]
> [Télécharger .NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48)

[.NET Framework 4.8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) peut être utilisé pour exécuter des applications conçues pour .NET Framework version 4.0 ou ultérieure.

### <a name="offline-installer"></a>programme d’installation hors connexion

Lorsque vous effectuez une installation hors connexion de .NET Framework sur Windows 7, vous devez d’abord vous assurer que la dernière [autorité de certification racine Microsoft 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm) a été installée sur l’ordinateur cible.

L’outil _certmgr.exe_ peut automatiser l’installation d’un certificat et est obtenu à partir de Visual Studio ou du SDK Windows. La commande suivante est utilisée pour installer le certificat avant d’exécuter le programme d’installation de .NET Framework :

```console
certmgr.exe /add MicRooCerAut2011_2011_03_22.crt /s /r localMachine root
```

## <a name="net-framework-35"></a>.NET Framework 3.5

Le [.NET Framework 3.5](https://dotnet.microsoft.com/download/dotnet-framework/net35-sp1) est fourni avec Windows 7.

.NET Framework 3.5 prend en charge les applications conçues pour .NET Framework 1.0 à 3.5.

## <a name="help"></a>Aide

Vous pouvez [contacter Microsoft pour obtenir de l’aide](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help) si vous ne pouvez installer la version correcte du .NET Framework.

## <a name="see-also"></a>Voir aussi

- [Télécharger le .NET Framework](https://dotnet.microsoft.com/download)
- [Résolution des problèmes liés aux installations et désinstallations bloquées du .NET Framework](troubleshoot-blocked-installations-and-uninstallations.md)
- [Installer le .NET Framework pour les développeurs](guide-for-developers.md)

---
title: Installer le .NET Framework sur Windows 10
description: Découvrez comment installer le .NET Framework sur Windows 10 ou Windows Server 2016.
ms.date: 04/18/2019
ms.custom: updateeachrelease
ms.openlocfilehash: eed15b9088d6ba46d8f5bc6d16ba779dd6115b0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76965969"
---
# <a name="install-the-net-framework-on-windows-10-and-windows-server-2016-and-later"></a>Installer le .NET Framework sur Windows 10 et Windows Server 2016 et ultérieur

Un grand nombre d’applications sur Windows nécessitent l’installation du .NET Framework. Les instructions contenues dans cet article ont pour but de vous aider à installer les versions du .NET Framework dont vous avez besoin. [.NET Framework 4.8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) est la dernière version disponible.

Votre présence ici s’explique peut-être par l’apparition sur votre ordinateur d’une boîte de dialogue semblable à la suivante après une tentative d’exécution d’une application :

![Impossible de démarrer cette application](./media/this-application-could-not-be-started.png)

## <a name="net-framework-48"></a>.NET Framework 4.8

La version .NET Framework 4.8 est fournie avec :

- [Mise à jour de Windows 10 de mai 2019](https://support.microsoft.com/help/4028685/windows-10-get-the-update)

> [!div class="button"]
> [Télécharger .NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48)

[.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48) peut être utilisé pour exécuter des applications créées pour .NET Framework versions 4.0 via 4.7.2.

Vous pouvez installer [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48) sur :

- Mise à jour de Windows 10 d’octobre 2018 (Version 1809)
- Windows 10 - Mise à jour d’avril 2018 (version 1803)
- Windows 10 Fall Creators Update (version 1709)
- Windows 10 Creators Update (version 1703)
- Mise à jour anniversaire Windows 10 (version 1607)
- Windows Server 2019
- Windows Server, version 1809
- Windows Server, version 1803
- Windows Server 2016

La version .NET Framework 4.8 n’est pas prise en charge sur :

- Windows 10 1507
- Windows 10 1511

Si vous utilisez Windows 10 version 1507 ou 1511 et que vous souhaitez installer .NET Framework 4.8, vous devez d’abord mettre à niveau vers une version Windows 10 ultérieure.

## <a name="net-framework-462"></a>.NET Framework 4.6.2

Le [.NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/net462) est la dernière version prise en charge du .NET Framework sur Windows 10 1507 et 1511.

Le .NET Framework 4.6.2 prend en charge les applications conçues pour le .NET Framework 4.0 à 4.6.2.

## <a name="net-framework-35"></a>.NET Framework 3.5

Suivez les instructions pour installer le [.NET Framework 3.5 sur Windows 10](dotnet-35-windows-10.md).

Le .NET Framework 3.5 prend en charge les applications conçues pour le .NET Framework 1.0 à 3.5.

## <a name="additional-information"></a>Informations supplémentaires

Les versions 4.x du .NET Framework sont des mises à jour sur place de versions antérieures. Ainsi :

- Une seule version du .NET Framework 4.x peut être installée sur votre ordinateur.

- Vous ne pouvez pas installer une version antérieure du .NET Framework sur votre ordinateur si une version ultérieure est déjà installée.

- Les versions 4.x du .NET Framework peuvent être utilisées pour exécuter des applications conçues pour le .NET Framework 4.0 jusqu’à cette version. Par exemple, le .NET Framework 4.7 peut être utilisé pour exécuter des applications conçues pour le .NET Framework 4.0 à 4.7. La dernière version (.NET Framework 4.8) peut être utilisée pour exécuter des applications créées avec toutes les versions .NET Framework à compter de la version 4.0.

Pour obtenir la liste de toutes les versions du .NET Framework disponibles en téléchargement, consultez la page [Téléchargements .NET](https://dotnet.microsoft.com/download).

## <a name="help"></a>Aide

Si vous ne parvenez pas à installer la bonne version du .NET Framework, [contactez Microsoft pour obtenir de l’aide](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help).

## <a name="see-also"></a>Voir aussi

- [Téléchargements ASP.NET](https://dotnet.microsoft.com/download)
- [Résolution des problèmes liés aux installations et désinstallations bloquées du .NET Framework](troubleshoot-blocked-installations-and-uninstallations.md)
- [Installer le .NET Framework pour les développeurs](guide-for-developers.md)

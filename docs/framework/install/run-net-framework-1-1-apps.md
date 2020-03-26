---
title: Exécuter des applications .NET Framework 1.1 sur Windows 8, Windows 8.1 ou Windows 10
description: Décrit comment accueillir les applications qui nécessitent .NET Framework 1.1, qui n’est plus pris en charge sur de nombreuses versions du système d’exploitation Windows.
ms.date: 05/26/2017
helpviewer_keywords:
- Windows 8, running .NET Framework 1.1 apps
- .NET Framework 1.1, running on Windows 8
ms.assetid: fb14e195-fea5-4561-b9a8-60a67283edb9
ms.openlocfilehash: 6d1cb2f9251bba96d0a378bf4dbab9f7da267037
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111788"
---
# <a name="run-net-framework-11-apps-on-windows-8-windows-81-or-windows-10"></a>Exécuter des applications .NET Framework 1.1 sur Windows 8, Windows 8.1 ou Windows 10

.NET Framework 1.1 n’est pas pris en charge sur Windows 8, Windows 8.1, Windows Server 2012, Windows Server 2012 R2, ou les systèmes d’exploitation Windows 10. Dans certains cas, .NET Framework 1.1 est nécessaire pour qu’une application s’exécute. Dans ces cas, contactez votre fournisseur de logiciels indépendant (ISV) pour que l’application soit mise à niveau pour fonctionner sur .NET Framework 3.5 SP1 ou une version ultérieure. Pour plus d’informations, voir [Migrating from .NET Framework 1.1](../migration-guide/migrating-from-the-net-framework-1-1.md).

## <a name="install-net-framework-11-from-a-cd-or-download-center"></a>Installer .NET Framework 1.1 à partir d’un CD ou d’un centre de téléchargement

Il n’est pas possible d’installer manuellement .NET Framework 1.1 sur Windows 8, Windows 8.1, Windows Server 2012, Windows Server 2012 R2, ou Windows 10 à partir d’un CD ou d’un centre de téléchargement. Il n’est plus pris en charge. Si vous essayez d'installer le package, le message d'erreur suivant s'affiche : « Le programme d'installation ne peut pas continuer, car cette version du .NET Framework est incompatible avec une version précédemment installée. ». Pour résoudre ce problème, installez [.NET Framework 3.5 SP1](https://www.microsoft.com/download/details.aspx?id=22). Cette version comprend .NET Framework 2.0 (la version qui suit .NET Framework 1.1), qui est pris en charge sur Windows 8, Windows 8.1, et Windows 10. Vous devez toujours essayer d’installer l’application d’abord pour déterminer si elle sera automatiquement mise à jour à une version ultérieure de .NET Framework. Si ce n’est pas le cas, contactez votre ISV pour une mise à jour de l’application.

## <a name="see-also"></a>Voir aussi

- [Migration à partir du .NET Framework 1.1](../migration-guide/migrating-from-the-net-framework-1-1.md)
- [Installer le .NET Framework 3.5 sur Windows 10, Windows 8.1 et Windows 8](dotnet-35-windows-10.md)

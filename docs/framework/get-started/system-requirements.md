---
title: Configuration requise pour le .NET Framework
description: Découvrez la configuration requise en termes de matériel, de système d’exploitation et de logiciels pour installer .NET Framework 4.5 et versions ultérieures.
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- software requirements
- .NET Framework, system requirements
- system requirements
- operating systems supported
- hardware requirements
ms.assetid: 298275e2-da1d-4618-9f74-6a3567832350
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bed0084fd576ba9b9f9eeb51e9e2466938e43490
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106510"
---
# <a name="net-framework-system-requirements"></a>Configuration requise pour le .NET Framework

Les tableaux de cette rubrique indiquent la configuration matérielle et logicielle requise, ainsi que celle du système d'exploitation pour les versions .NET Framework suivantes :

- .NET Framework 4.5 et ses versions intermédiaires (4.5.1 et 4.5.2).
- .NET Framework 4.6 et ses versions intermédiaires (4.6.1 et 4.6.2).
- .NET Framework 4.7 et ses versions intermédiaires (4.7.1 et 4.7.2).
- .NET Framework 4.8

Pour plus d’informations sur les versions .NET Framework antérieures à .NET Framework 4.5, consultez [Versions et dépendances de .NET Framework](../migration-guide/versions-and-dependencies.md).

Les environnements de développement qui vous permettent de développer des applications pour le .NET Framework ont des exigences différentes.

[!INCLUDE[net-framework-4-versions](../../../includes/net-framework-4x-versions.md)]

Pour obtenir des informations et des liens pour le téléchargement, consultez [Installer le .NET Framework pour les développeurs](../../../docs/framework/install/guide-for-developers.md).

Pour plus d’informations sur le cycle de vie du support des versions du .NET Framework, consultez [Cycle de vie de support des produits Microsoft](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=Microsoft%20.NET%20Framework&Filter=FilterNO).

## <a name="hardware-requirements"></a>Configuration matérielle requise

|                          |        |
| ------------------------ | ------ |
| **Processeur**            | 1 GHz  |
| **Mémoire vive**                  | 512 Mo |
| **Espace disque (minimum)** |        |
| 32 bits                   | 4,5 Go |
| 64 bits                   | 4,5 Go |

## <a name="installation-requirements"></a>Configuration requise pour l’installation

L’installation du .NET Framework nécessite des privilèges d’administrateur. Si vous n’avez pas de droits d’administrateur sur l’ordinateur sur lequel vous voulez installer le .NET Framework, contactez votre administrateur réseau.

## <a name="supported-client-operating-systems"></a>Systèmes d'exploitation clients pris en charge

| Système d'exploitation | Éditions prises en charge | Préinstallé avec le système d'exploitation | Installable séparément |
| ---------------- | ------------------ | ------------------------ | ---------------------- |
| Mise à jour de Windows 10 de mai 2019 | 32 bits et 64 bits | .NET Framework 4.8 | -- |
| Windows 10 avec la mise à jour d’octobre 2018 | 32 bits et 64 bits | .NET Framework 4.7.2 | .NET Framework 4.8 |
| Mise à jour d’avril 2018 de Windows 10 | 32 bits et 64 bits | .NET Framework 4.7.2 |.NET Framework 4.8|
| Windows 10 Fall Creators Update | 32 bits et 64 bits | .NET Framework 4.7.1 | .NET Framework 4.7.2<br/><br/>.NET Framework 4.8 |
| Windows 10 Creators Update | 32 bits et 64 bits | .NET Framework 4.7 | .NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4.8 |
| Mise à jour anniversaire Windows 10 | 32 bits et 64 bits | .NET Framework 4.6.2 |.NET Framework 4.7<br/><br/>.NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4.8  |
| Mise à jour de novembre de Windows 10 | 32 bits et 64 bits | .NET Framework 4.6.1 | .NET Framework 4.6.2 |
| Windows 10 | 32 bits et 64 bits | .NET Framework 4.6 | .NET Framework 4.6.1 <br/><br/> .NET Framework 4.6.2 |
| [!INCLUDE[win81](../../../includes/win81-md.md)] | 32 bits, 64 bits et ARM | .NET Framework 4.5.1 | .NET Framework 4.5.2<br /><br /> .NET Framework 4.6<br /><br /> .NET Framework 4.6.1<br /><br /> .NET Framework 4.6.2<br /><br />.NET Framework 4.7<br/><br/>.NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4.8 |
| [!INCLUDE[win8](../../../includes/win8-md.md)] | 32 bits, 64 bits et ARM | .NET Framework 4.5 | .NET Framework 4.5.1<br /><br />.NET Framework 4.5.2<br /><br /> .NET Framework 4.6<br /><br /> .NET Framework 4.6.1 |
| Windows 7 SP1|32 bits et 64 bits | -- | .NET Framework 4<br /><br /> .NET Framework 4.5<br /><br /> .NET Framework 4.5.1<br /><br /> .NET Framework 4.5.2<br /><br /> .NET Framework 4.6<br /><br /> .NET Framework 4.6.1<br /><br /> .NET Framework 4.6.2<br /><br />.NET Framework 4.7<br/><br/>.NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4.8 |
| Windows Vista SP2|32 bits et 64 bits | -- | .NET Framework 4<br /><br /> .NET Framework 4.5<br /><br /> .NET Framework 4.5.1<br /><br /> .NET Framework 4.5.2<br /><br /> .NET Framework 4.6 |
| Windows XP |32 bits et 64 bits | -- | .NET Framework 4 |

 **Remarques :**

- Sur les systèmes Windows 7, le .NET Framework nécessite Windows 7 SP1. Si vous êtes sur Windows 7 et que vous n’avez pas encore installé le Service Pack 1, vous devez le faire avant d’installer le .NET Framework.

- .NET Framework 4.5 est pris en charge sur l'environnement de préinstallation Windows (WinPE). Les fonctionnalités ne sont pas toutes prises en charge dans Windows PE.

- .NET Framework 4 prend également en charge la plateforme IA64.

- Pour toutes les plateformes, nous recommandons d’effectuer une mise à niveau vers le dernier Service Pack Windows et d’installer les mises à jour critiques disponibles à partir du [site web Windows Update](https://go.microsoft.com/fwlink/?LinkId=168461) afin de garantir une compatibilité et une sécurité optimales.

- Sur les systèmes d’exploitation 64 bits, le .NET Framework prend en charge WOW64 (processus 32 bits sur un ordinateur 64 bits) et le processus 64 bits natif.

## <a name="supported-server-operating-systems"></a>Systèmes d'exploitation serveurs pris en charge

| Système d'exploitation | Éditions prises en charge | Préinstallé avec le système d'exploitation | Installable séparément |
| ---------------- | ------------------ | ------------------------ | ---------------------- |
| Windows Server 2019 | 64 bits | .NET Framework 4.7.2 | .NET Framework 4.8 |
| Windows Server, version 1809 | 64 bits | .NET Framework 4.7.2 | .NET Framework 4.8 |
| Windows Server, version 1803 | 64 bits | .NET Framework 4.7.2 | .NET Framework 4.8 |
| Windows Server, version 1709 | 64 bits | .NET Framework 4.7.1 | .NET Framework 4.7.2|
| Windows Server 2016 | 64 bits | .NET Framework 4.6.2 | .NET Framework 4.7<br/><br/> .NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4.8 |
| Windows Server 2012 R2 | 64 bits | .NET Framework 4.5.1 | .NET Framework 4.5.2<br /><br /> .NET Framework 4.6<br /><br /> .NET Framework 4.6.1<br /><br /> .NET Framework 4.6.2<br /><br />.NET Framework 4.7<br/><br/> .NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4.8 |
| Windows Server 2012 (édition 64 bits) | 64 bits| .NET Framework 4.5 | .NET Framework 4.5.1<br /><br /> .NET Framework 4.5.2<br /><br /> .NET Framework 4.6<br /><br /> .NET Framework 4.6.1<br /><br /> .NET Framework 4.6.2<br /><br />.NET Framework 4.7<br/><br/>.NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4.8 |
| Windows Server 2008 R2 SP1|64 bits | -- | .NET Framework 4<br /><br /> .NET Framework 4.5<br /><br /> .NET Framework 4.5.1<br /><br /> .NET Framework 4.5.2<br /><br /> .NET Framework 4.6<br /><br /> .NET Framework 4.6.1<br /><br /> .NET Framework 4.6.2<br /><br />.NET Framework 4.7<br/><br/>.NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4.8 |
| Windows Server 2008 SP2|32 bits et 64 bits | -- | .NET Framework 4<br /><br /> .NET Framework 4.5<br /><br /> .NET Framework 4.5.1<br /><br /> .NET Framework 4.5.2<br /><br /> .NET Framework 4.6 |

 **Remarques :**

- [!INCLUDE[winserver8](../../../includes/winserver8-md.md)] inclut .NET Framework 4.5, il n’est donc pas nécessaire de l’installer séparément. De même, [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)] inclut .NET Framework 4.5.1.

- Le .NET Framework offre une prise en charge limitée du rôle Server Core avec Windows Server 2008 R2 SP1 ou ultérieur. Pour obtenir la liste des API non prises en charge, consultez la [fonctionnalité .NET Server Core](https://docs.microsoft.com/previous-versions//dd745015(v=vs.85)).

- Le .NET Framework n’est pas pris en charge sur Windows Server 2008 R2 pour les systèmes Itanium.

- Sur Windows Server 2008 SP2, le .NET Framework n’est pas pris en charge dans le rôle principal du serveur.

- Pour toutes les plateformes, nous recommandons une mise à niveau vers le dernier Service Pack Windows et le téléchargement des mises à jour critiques disponibles depuis le [site web Windows Update](https://go.microsoft.com/fwlink/?LinkId=168461) afin de garantir une compatibilité et une sécurité optimales. L'installation du dernier Service Pack Windows peut être obligatoire sur certains systèmes d'exploitation.

- Sur les systèmes d'exploitation 64 bits, le .NET Framework prend en charge WOW64 (processus 32 bits sur un ordinateur 64 bits) et le processus 64 bits natif.

## <a name="see-also"></a>Voir aussi

- [Guide d’installation](../../../docs/framework/install/index.md)
- [Prise en main](../../../docs/framework/get-started/index.md)
- [Résolution des problèmes liés aux installations et désinstallations bloquées du .NET Framework](../../../docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)

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
ms.openlocfilehash: 571075f7d0f330cf88ac9618376876b4f72e75ed
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389472"
---
# <a name="net-framework-system-requirements"></a>Configuration requise pour le .NET Framework

Les tableaux de cet article fournissent le matériel, le système d’exploitation et les exigences logicielles pour les versions cadres .NET suivantes :

- .NET Framework 4.5 et ses versions intermédiaires (4.5.1 et 4.5.2).
- .NET Framework 4.6 et ses versions intermédiaires (4.6.1 et 4.6.2).
- .NET Framework 4.7 et ses versions intermédiaires (4.7.1 et 4.7.2).
- .NET Framework 4.8

Pour plus d’informations sur les versions .NET Framework antérieures à .NET Framework 4.5, consultez [Versions et dépendances de .NET Framework](../migration-guide/versions-and-dependencies.md).

Les environnements de développement qui vous permettent de développer des applications pour .NET Framework ont un ensemble distinct d’exigences.

[!INCLUDE[net-framework-4-versions](../../../includes/net-framework-4x-versions.md)]

Pour obtenir des informations et des liens pour le téléchargement, consultez [Installer le .NET Framework pour les développeurs](../install/guide-for-developers.md).

Pour plus d’informations sur le cycle de vie du support des versions du .NET Framework, consultez [Cycle de vie de support des produits Microsoft](https://support.microsoft.com/lifecycle/search?sort=PN&alpha=Microsoft%20.NET%20Framework&Filter=FilterNO).

## <a name="hardware-requirements"></a>Configuration matérielle requise

|                          |        |
| ------------------------ | ------ |
| **Processeur**            | 1 GHz  |
| **RAM**                  | 512 MO |
| **Espace disque (minimum)** |        |
| 32 bits                   | 4,5 Go |
| 64 bits                   | 4,5 Go |

## <a name="installation-requirements"></a>Configuration requise

.NET Framework exige des privilèges d’administrateur pour l’installation. Si vous n’avez pas de droits d’administrateur sur l’ordinateur où vous souhaitez installer .NET Framework, contactez votre administrateur réseau.

## <a name="supported-client-operating-systems"></a>Systèmes d'exploitation clients pris en charge

| Système d’exploitation | Éditions prises en charge | Préinstallé avec le système d'exploitation | Installable séparément |
| ---------------- | ------------------ | ------------------------ | ---------------------- |
| Mise à jour de Windows 10 de mai 2019<br/> (version 1903) | 32 bits et 64 bits | .NET Framework 4.8 | -- |
| Windows 10 avec la mise à jour d’octobre 2018<br/> (version 1809) | 32 bits et 64 bits | .NET Framework 4.7.2 | .NET Framework 4.8 |
| Mise à jour d’avril 2018 de Windows 10<br/> (version 1803) | 32 bits et 64 bits | .NET Framework 4.7.2 |.NET Framework 4.8|
| Windows 10 Fall Creators Update<br/> (version 1709) | 32 bits et 64 bits | .NET Framework 4.7.1 | .NET Framework 4.7.2<br/><br/>.NET Framework 4.8 |
| Windows 10 Creators Update<br/> (version 1703) | 32 bits et 64 bits | .NET Framework 4.7 | .NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4.8 |
| Mise à jour anniversaire Windows 10<br/> (version 1607) | 32 bits et 64 bits | .NET Framework 4.6.2 |.NET Framework 4.7<br/><br/>.NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4.8  |
| Mise à jour de novembre de Windows 10<br/> (version 1511) | 32 bits et 64 bits | .NET Framework 4.6.1 | .NET Framework 4.6.2 |
| Windows 10<br/> (version 1507) | 32 bits et 64 bits | .NET Framework 4.6 | .NET Framework 4.6.1 <br/><br/> .NET Framework 4.6.2 |
| Windows 8.1 | 32 bits, 64 bits et ARM | .NET Framework 4.5.1 | .NET Framework 4.5.2<br /><br /> .NET Framework 4.6<br /><br /> .NET Framework 4.6.1<br /><br /> .NET Framework 4.6.2<br /><br />.NET Framework 4.7<br/><br/>.NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4.8 |
| Windows 8 | 32 bits, 64 bits et ARM | .NET Framework 4.5 | .NET Framework 4.5.1<br /><br />.NET Framework 4.5.2<br /><br /> .NET Framework 4.6<br /><br /> .NET Framework 4.6.1 |
| Windows 7 SP1|32 bits et 64 bits | -- | .NET Framework 4<br /><br /> .NET Framework 4.5<br /><br /> .NET Framework 4.5.1<br /><br /> .NET Framework 4.5.2<br /><br /> .NET Framework 4.6<br /><br /> .NET Framework 4.6.1<br /><br /> .NET Framework 4.6.2<br /><br />.NET Framework 4.7<br/><br/>.NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4.8 |
| Windows Vista SP2|32 bits et 64 bits | -- | .NET Framework 4<br /><br /> .NET Framework 4.5<br /><br /> .NET Framework 4.5.1<br /><br /> .NET Framework 4.5.2<br /><br /> .NET Framework 4.6 |
| Windows XP |32 bits et 64 bits | -- | .NET Framework 4 |

 **Remarques :**

- Sur les systèmes Windows 7, .NET Framework nécessite Windows 7 SP1. Si vous êtes sur Windows 7 et que vous n’avez pas encore installé le Service Pack 1, vous devez le faire avant d’installer le .NET Framework.

- .NET Framework 4.5 est pris en charge sur l'environnement de préinstallation Windows (WinPE). Les fonctionnalités ne sont pas toutes prises en charge dans Windows PE.

- .NET Framework 4 prend également en charge la plateforme IA64.

- Pour toutes les plates-formes, nous vous recommandons de passer au dernier Pack de services Windows et d’installer des mises à jour critiques disponibles à partir de [Windows Update](https://support.microsoft.com/help/12373/windows-update-faq) pour assurer la meilleure compatibilité et sécurité.

- Sur les systèmes d’exploitation 64 bits, .NET Framework prend en charge à la fois WOW64 (traitement 32 bits sur une machine 64 bits) et le traitement 64 bits natif.

## <a name="supported-server-operating-systems"></a>Systèmes d'exploitation serveurs pris en charge

| Système d’exploitation | Éditions prises en charge | Préinstallé avec le système d'exploitation | Installable séparément |
| ---------------- | ------------------ | ------------------------ | ---------------------- |
| Windows Server 2019 | 64 bits | .NET Framework 4.7.2 | .NET Framework 4.8 |
| Windows Server, version 1809 | 64 bits | .NET Framework 4.7.2 | .NET Framework 4.8 |
| Windows Server, version 1803 | 64 bits | .NET Framework 4.7.2 | .NET Framework 4.8 |
| Windows Server, version 1709 | 64 bits | .NET Framework 4.7.1 | .NET Framework 4.7.2|
| Windows Server 2016 | 64 bits | .NET Framework 4.6.2 | .NET Framework 4.7<br/><br/> .NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4.8 |
| Windows Server 2012 R2 | 64 bits | .NET Framework 4.5.1 | .NET Framework 4.5.2<br /><br /> .NET Framework 4.6<br /><br /> .NET Framework 4.6.1<br /><br /> .NET Framework 4.6.2<br /><br />.NET Framework 4.7<br/><br/> .NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4.8 |
| Windows Server 2012 (édition 64 bits) | 64 bits| .NET Framework 4.5 | .NET Framework 4.5.1<br /><br /> .NET Framework 4.5.2<br /><br /> .NET Framework 4.6<br /><br /> .NET Framework 4.6.1<br /><br /> .NET Framework 4.6.2<br /><br />.NET Framework 4.7<br/><br/>.NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4.8 |
| Windows Server 2008 R2 SP1|64 bits | -- | .NET Framework 4<br /><br /> .NET Framework 4.5<br /><br /> .NET Framework 4.5.1<br /><br /> .NET Framework 4.5.2<br /><br /> .NET Framework 4.6<br /><br /> .NET Framework 4.6.1<br /><br /> .NET Framework 4.6.2<br /><br />.NET Framework 4.7<br/><br/>.NET Framework 4.7.1<br/><br/>.NET Framework 4.7.2<br/><br/>.NET Framework 4.8 |
| Windows Server 2008 SP2|32 bits et 64 bits | -- | .NET Framework 4<br /><br /> .NET Framework 4.5<br /><br /> .NET Framework 4.5.1<br /><br /> .NET Framework 4.5.2<br /><br /> .NET Framework 4.6 |

**Remarques :**

- Windows Server 2012 comprend .NET Framework 4.5, de sorte que vous n’avez pas à l’installer séparément. De même, Windows Server 2012 R2 comprend .NET Framework 4.5.1.

- .NET Framework a une prise en charge limitée pour le rôle de base serveur avec Windows Server 2008 R2 SP1 ou plus tard. Pour obtenir la liste des API non prises en charge, consultez la [fonctionnalité .NET Server Core](https://docs.microsoft.com/previous-versions//dd745015(v=vs.85)).

- .NET Framework n’est pas pris en charge sur Windows Server 2008 R2 pour les systèmes itanium-basés.

- Sur Windows Server 2008 SP2, .NET Framework n’est pas pris en charge dans le rôle de base du serveur.

- Pour toutes les plates-formes, nous vous recommandons de passer au dernier Pack de services Windows et des mises à jour critiques disponibles à partir de [Windows Update](https://support.microsoft.com/help/12373/windows-update-faq) pour assurer la meilleure compatibilité et sécurité. L'installation du dernier Service Pack Windows peut être obligatoire sur certains systèmes d'exploitation.

- Sur les systèmes d’exploitation 64 bits, .NET Framework prend en charge à la fois WOW64 (traitement 32 bits sur une machine 64 bits) et le traitement 64 bits natif.

## <a name="see-also"></a>Voir aussi

- [Guide d’installation](../install/index.md)
- [Prise en main](index.md)
- [Résolution des problèmes liés aux installations et désinstallations bloquées du .NET Framework](../install/troubleshoot-blocked-installations-and-uninstallations.md)

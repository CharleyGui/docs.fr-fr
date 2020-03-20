---
title: Changements d’exécution et de retargeting - Cadre .NET
ms.date: 10/29/2019
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
ms.openlocfilehash: c46f781d495b87a4f24e77935df7c4814c8567ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73196698"
---
# <a name="application-compatibility-in-the-net-framework"></a>Compatibilité des applications dans le cadre .NET

La compatibilité est un objectif important de chaque version .NET. La compatibilité garantit que chaque version est additive, de sorte que les versions précédentes continueront à fonctionner. D’autre part, les modifications apportées aux fonctionnalités précédentes (par exemple, pour améliorer les performances, résoudre les problèmes de sécurité ou corriger les bogues) peuvent causer des problèmes de compatibilité dans le code existant ou les applications existantes qui s’exécutent sous une version ultérieure.

Chaque application cible une version spécifique du cadre .NET en :

- La définition d’une version cible de .NET Framework dans Visual Studio.
- La spécification de la version cible de .NET Framework dans un fichier projet.
- L’application d’un <xref:System.Runtime.Versioning.TargetFrameworkAttribute> au code source.

Lors de la migration d’une version du cadre .NET à une autre, il existe deux types de changements à considérer:

- [Changements d’exécution](#runtime-changes)
- [Changements de retargeting](#retargeting-changes)

## <a name="runtime-changes"></a>Modifications du runtime

Les problèmes d’exécution sont ceux qui se posent lorsqu’un nouveau temps d’exécution est placé sur une machine et que le comportement d’une application change. Lors de l’exécution sur une version plus récente que ce qui a été ciblé, le cadre .NET utilise un comportement *bizarre* pour imiter l’ancienne version ciblée. L’application s’exécute sur la version la plus récente, mais agit comme si elle est en cours d’exécution sur l’ancienne version. La plupart des problèmes de compatibilité entre les versions du .NET Framework sont atténués via ce modèle de subterfuge. Par exemple, si un binaire a été compilé pour .NET Framework 4.0 mais fonctionne sur une machine avec .NET Framework 4.5 ou plus tard, il fonctionne en mode de compatibilité .NET Framework 4.0. Cela signifie que beaucoup de changements dans la version ultérieure n’affectent pas le binaire.

La version du cadre .NET qu’une application cible est déterminée par la version cible de l’assemblage d’entrée pour le domaine d’application dans lequel le code s’exécute. Tous les assemblages supplémentaires chargés dans ce domaine d’application ciblent cette version. Par exemple, dans le cas d’un exécutable, la version que les cibles exécutables est le mode de compatibilité de tous les assemblages dans ce domaine d’application s’exécutent sous.

Pour voir une liste des modifications d’exécution qui s’appliquent à votre environnement, sélectionnez la version cadre .NET que vous ciblez actuellement, puis la version que vous souhaitez migrer vers :

[!INCLUDE[versionselector](../../../includes/migration-guide/runtime/versionselector.md)]

## <a name="retargeting-changes"></a>Modifications de reciblage

Les modifications de retargeting sont celles qui surviennent lorsqu’une assemblée est recompilée pour cibler une version plus récente. Cibler une version plus récente signifie que l’assemblage opte pour les nouvelles fonctionnalités ainsi que les problèmes de compatibilité potentiels pour les anciennes fonctionnalités.

Pour voir une liste de modifications de retargeting qui s’appliquent à votre environnement, sélectionnez la version cadre .NET que vous ciblez actuellement, puis la version que vous souhaitez migrer vers :

[!INCLUDE[versionselector](../../../includes/migration-guide/retargeting/versionselector.md)]

## <a name="impact-classification"></a>Classification de l’impact

Dans les sujets qui décrivent les changements de temps d’exécution et de retargeting, par exemple, [les changements de retargeting pour la migration de 4.7.2 à 4.8](retargeting/4.7.2-4.8.md), les éléments individuels sont classés par leur impact prévu comme suit :

**Majeur**\
Modification importante qui affecte un grand nombre d'applications ou qui nécessite de modifier significativement le code.

**Mineur**\
Modification qui affecte un petit nombre d’applications ou qui nécessite peu de modifications du code.

**Cas Edge**\
Modification qui affecte des applications dans des scénarios très spécifiques qui ne sont pas courants.

**Transparent**\
Modification qui n'a pas d'effet visible pour le développeur ou l'utilisateur de l'application. L'application n'a pas besoin d'être modifiée en raison de cette modification.

## <a name="see-also"></a>Voir aussi

- [Versions et dépendances](versions-and-dependencies.md)
- [Nouveautés](../whats-new/index.md)
- [Ce qui est obsolète](../whats-new/whats-obsolete.md)

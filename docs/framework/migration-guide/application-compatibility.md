---
title: Modifications du runtime et du reciblage-.NET Framework
description: En savoir plus sur la compatibilité des applications dans .NET Framework et sur la manière dont elle est affectée par le runtime et les modifications de reciblage lors de la migration vers une autre version.
ms.date: 10/29/2019
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
ms.openlocfilehash: 26f36dd34c6c5ecae8fc5ab373ff60d9e56f8245
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475487"
---
# <a name="application-compatibility-in-the-net-framework"></a>Compatibilité des applications dans le .NET Framework

La compatibilité est un objectif important de chaque version de .NET. La compatibilité garantit que chaque version est additive, de sorte que les versions précédentes continuent de fonctionner. En revanche, les modifications apportées à la fonctionnalité précédente (par exemple, pour améliorer les performances, résoudre les problèmes de sécurité ou corriger les bogues) peuvent entraîner des problèmes de compatibilité dans le code existant ou dans des applications existantes qui s’exécutent sous une version ultérieure.

Chaque application cible une version spécifique du .NET Framework par :

- La définition d’une version cible de .NET Framework dans Visual Studio.
- La spécification de la version cible de .NET Framework dans un fichier projet.
- L’application d’un <xref:System.Runtime.Versioning.TargetFrameworkAttribute> au code source.

Lors de la migration d’une version de la .NET Framework vers une autre, il existe deux types de modifications à prendre en compte :

- [Modifications du runtime](#runtime-changes)
- [Modifications de reciblage](#retargeting-changes)

## <a name="runtime-changes"></a>Modifications du runtime

Les problèmes d’exécution sont ceux qui surviennent lorsqu’un nouveau Runtime est placé sur un ordinateur et que le comportement d’une application change. En cas d’exécution sur une version plus récente que celle ciblée, le .NET Framework utilise un comportement *excentrique* pour imiter l’ancienne version ciblée. L’application s’exécute sur la version plus récente, mais agit comme si elle s’exécutait sur l’ancienne version. La plupart des problèmes de compatibilité entre les versions du .NET Framework sont atténués via ce modèle de subterfuge. Par exemple, si un fichier binaire a été compilé pour .NET Framework 4,0, mais qu’il s’exécute sur un ordinateur avec .NET Framework 4,5 ou version ultérieure, il s’exécute en mode de compatibilité .NET Framework 4,0. Cela signifie que la plupart des modifications apportées à la version ultérieure n’affectent pas le binaire.

La version de la .NET Framework qu’une application cible est déterminée par la version cible de l’assembly d’entrée pour le domaine d’application dans lequel le code s’exécute. Tous les assemblys supplémentaires chargés dans ce domaine d’application ciblent cette version. Par exemple, dans le cas d’un exécutable, la version ciblée par l’exécutable est le mode de compatibilité dans lequel tous les assemblys de ce domaine d’application s’exécutent.

Pour afficher la liste des modifications à l’exécution qui s’appliquent à votre environnement, sélectionnez la version de .NET Framework que vous ciblez actuellement, puis la version vers laquelle vous souhaitez effectuer la migration :

[!INCLUDE[versionselector](../../../includes/migration-guide/runtime/versionselector.md)]

## <a name="retargeting-changes"></a>Modifications de reciblage

Les modifications de reciblage sont celles qui surviennent lorsqu’un assembly est recompilé pour cibler une version plus récente. Le ciblage d’une version plus récente signifie que l’assembly choisit les nouvelles fonctionnalités, ainsi que les problèmes de compatibilité potentiels pour les anciennes fonctionnalités.

Pour afficher la liste des modifications de reciblage qui s’appliquent à votre environnement, sélectionnez la version de .NET Framework que vous ciblez actuellement, puis la version vers laquelle vous souhaitez effectuer la migration :

[!INCLUDE[versionselector](../../../includes/migration-guide/retargeting/versionselector.md)]

## <a name="impact-classification"></a>Classification d’impact

Dans les rubriques qui décrivent les modifications du runtime et du reciblage, par exemple, les [modifications de reciblage pour la migration de 4.7.2 vers 4,8](retargeting/4.7.2-4.8.md), les éléments individuels sont classés en fonction de leur impact attendu comme suit :

**Envergure**\
Modification importante qui affecte un grand nombre d'applications ou qui nécessite de modifier significativement le code.

**Mineure**\
Modification qui affecte un petit nombre d’applications ou qui nécessite peu de modifications du code.

**Cas limite**\
Modification qui affecte des applications dans des scénarios très spécifiques qui ne sont pas courants.

**Transparente**\
Modification qui n'a pas d'effet visible pour le développeur ou l'utilisateur de l'application. L'application n'a pas besoin d'être modifiée en raison de cette modification.

## <a name="see-also"></a>Voir aussi

- [Versions et dépendances](versions-and-dependencies.md)
- [Nouveautés](../whats-new/index.md)
- [Éléments obsolètes](../whats-new/whats-obsolete.md)

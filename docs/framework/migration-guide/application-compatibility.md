---
title: Compatibilité des applications dans le .NET Framework
ms.date: 05/19/2017
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 56f0ebccc1bd46a26b5247ac2668e963cbeac828
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106484"
---
# <a name="application-compatibility-in-the-net-framework"></a>Compatibilité des applications dans le .NET Framework

## <a name="introduction"></a>Introduction
La compatibilité est un objectif très important de chaque version de .NET. La compatibilité garantit que chaque version est additive et que les versions précédentes fonctionnent donc toujours. En revanche, les modifications apportées aux fonctionnalités précédentes (pour améliorer les performances, résoudre des problèmes de sécurité ou corriger des bogues) peuvent provoquer des problèmes de compatibilité dans le code ou des applications qui s’exécutent sous une version ultérieure. Le .NET Framework reconnaît les modifications de reciblage et du runtime. Les modifications de reciblage concernent les applications qui ciblent une version spécifique du .NET Framework, mais sont exécutées sur une version ultérieure. Les modifications du runtime concernent toutes les applications qui s’exécutent sur une version particulière.

Chaque application cible une version spécifique du .NET Framework, qui peut être indiquée par :

- La définition d’une version cible de .NET Framework dans Visual Studio.
- La spécification de la version cible de .NET Framework dans un fichier projet.
- L’application d’un <xref:System.Runtime.Versioning.TargetFrameworkAttribute> au code source.

Lors de l’exécution sur une version plus récente que celle qui était ciblée, le .NET Framework utilise un subterfuge afin de simuler l’ancienne version ciblée. En d’autres termes, l’application s’exécute sur la version la plus récente du .NET Framework, mais agit comme si elle était exécutée sur la version antérieure. La plupart des problèmes de compatibilité entre les versions du .NET Framework sont atténués via ce modèle de subterfuge. La version du .NET Framework que cible une application est déterminée par la version cible de l’assembly d’entrée pour le domaine d’application dans lequel le code s’exécute. Tous les autres assemblys chargés dans ce domaine d’application ciblent cette version du .NET Framework. Par exemple, dans le cas d’un exécutable, le framework que cible l’exécutable correspond au mode de compatibilité sous lequel tous les assemblys inclus dans ce domaine d’application s’exécutent.

## <a name="runtime-changes"></a>Modifications du runtime

Les problèmes de runtime sont ceux qui surviennent quand un nouveau runtime est placé sur un ordinateur, que les mêmes fichiers binaires sont exécutés, mais qu’un comportement différent est détecté. Si un fichier binaire a été compilé pour .NET Framework 4.0, il est exécuté en mode de compatibilité .NET Framework 4.0 sur les versions 4.5 ou ultérieures. La plupart des modifications qui affectent 4.5 n’affectent pas un fichier binaire compilé pour la version 4.0. Cela est spécifique au domaine d’application et dépend des paramètres de l’assembly d’entrée.

## <a name="retargeting-changes"></a>Modifications de reciblage

Les problèmes de reciblage sont ceux qui surviennent quand un assembly qui ciblait 4.0 est maintenant défini pour cibler 4.5. Maintenant, l’assembly accepte les nouvelles fonctionnalités ainsi que les éventuels problèmes de compatibilité des anciennes fonctionnalités. Là encore, cela dépend de l’assembly d’entrée, comme l’application console qui utilise l’assembly ou le site web qui fait référence à l’assembly.

## <a name="net-compatibility-diagnostics"></a>Diagnostics de compatibilité .NET

Les diagnostics de compatibilité .NET sont des analyseurs issus de la technologie Roslyn qui permettent d’identifier les problèmes de compatibilité entre les différentes versions du .NET Framework. Cette liste contient tous les analyseurs disponibles, même si chaque migration ne nécessite qu’une partie de ces analyseurs. Les analyseurs permettent de déterminer les problèmes liés à la migration planifiée et signalent uniquement ce type de problèmes.

Chaque problème comprend les informations suivantes :

- La description de ce qui a changé par rapport à la version précédente.

- La façon dont ce changement affecte les clients et si d’éventuelles solutions de contournement sont disponibles pour préserver la compatibilité entre les versions.

- Une évaluation de l’importance du changement. Les problèmes de compatibilité entre applications sont classés de la façon suivante :

    |   |   |
    |---|---|
    |Majeur|Modification importante qui affecte un grand nombre d’applications ou qui nécessite de modifier significativement le code.|
    |Mineur|Modification qui affecte un petit nombre d’applications ou qui nécessite peu de modifications du code.|
    |Cas limite|Modification qui affecte des applications dans des scénarios très spécifiques et peu courants.|
    |Transparent|Modification qui n’a pas d’effet visible pour le développeur ou l’utilisateur de l’application.|

- La version indique à quel moment cette modification est apparue pour la première fois dans le .NET Framework. Certaines modifications sont introduites dans une version particulière et annulées dans une version ultérieure ; cela est également indiqué.

- Type de modification :

    |   |   |
    |---|---|
    |Reciblage|La modification affecte les applications qui sont recompilées pour cibler une nouvelle version du .NET Framework.|
    |Runtime|La modification affecte une application existante qui cible une version antérieure du .NET Framework, mais s’exécute sur une version ultérieure.|

- Les API affectées, le cas échéant.

- Les ID des diagnostics disponibles

## <a name="usage"></a>Utilisation
Pour commencer, sélectionnez le type de modification de la compatibilité ci-dessous :

- [Modifications de reciblage](./retargeting/index.md)
- [Modifications du runtime](./runtime/index.md)

## <a name="see-also"></a>Voir aussi

- [Versions et dépendances](../../../docs/framework/migration-guide/versions-and-dependencies.md)
- [Nouveautés](../../../docs/framework/whats-new/index.md)
- [Éléments obsolètes dans la bibliothèque de classes](../../../docs/framework/whats-new/whats-obsolete.md)

---
title: 'Guide de migration vers le .NET Framework 4.8, 4.7, 4.6 et 4.5 '
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
ms.openlocfilehash: fbaee646f7adcfe1a53d4231790e4258fd95a892
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102630"
---
# <a name="migrate-to-net-framework-48-47-46-and-45"></a>Migrer vers .NET Framework 4.8, 4.7, 4.6, et 4.5

Si vous avez créé votre application à l’aide d’une version antérieure de .NET Framework, vous pouvez généralement la mettre à niveau vers .NET Framework 4.5 et ses versions point (4.5.1 et 4.5.2), .NET Framework 4.6 et ses versions point (4.6.1 et 4.6.2), .NET Framework 4.7 et ses communiqués de points (4.7.1 et 4.7.2), ou .NET Framework 4.8 facilement. Ouvrez votre projet dans Visual Studio. Si votre projet a été créé dans une version antérieure de Visual Studio, la boîte de dialogue **Compatibilité des projets** s’ouvre automatiquement. Pour plus d’informations sur la mise à niveau d’un projet dans Visual Studio, consultez [Porter, migrer et mettre à niveau des projets Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) et [Ciblage et compatibilité de la plateforme Visual Studio 2019](/visualstudio/releases/2019/compatibility).

 Cependant, certaines modifications du cadre .NET nécessitent des modifications à votre code. Vous pouvez également bénéficier des nouvelles fonctionnalités du .NET Framework 4.5 et ses versions intermédiaires, de .NET Framework 4.6 et ses versions intermédiaires, de .NET Framework 4.7 et ses versions intermédiaires ou de .NET Framework 4.8. Faire ces types de modifications à votre application pour une nouvelle version de .NET Framework est généralement appelé *migration*. Si votre application n’a pas besoin d’être migrée, vous pouvez l’exécuter dans .NET Framework 4.5 ou une version ultérieure sans la recompiler.

## <a name="migration-resources"></a>Ressources de migration

Passez en revue les documents suivants avant de migrer votre application à partir de versions antérieures de .NET Framework à la version 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2, 4.7.2, ou 4.8:

- Consultez [Versions et dépendances](versions-and-dependencies.md) pour comprendre la version CLR sous-jacente à chaque version du .NET Framework, et pour passer en revue les instructions qui vous permettront de cibler correctement vos applications.

- Examinez [la compatibilité](application-compatibility.md) des applications pour en savoir plus sur les changements de temps d’exécution et de retargeting qui pourraient affecter votre application et comment les gérer.

- Consultez [Éléments obsolètes dans la bibliothèque de classes](../whats-new/whats-obsolete.md) pour déterminer les types ou membres rendus obsolètes dans votre code, et les alternatives recommandées.

- Consultez [Nouveautés](../whats-new/index.md) pour obtenir la description des nouvelles fonctionnalités que vous pouvez ajouter à votre application.

## <a name="see-also"></a>Voir aussi

- [Compatibilité des applications](application-compatibility.md)
- [Migration à partir du .NET Framework 1.1](migrating-from-the-net-framework-1-1.md)
- [Compatibilité de la version](version-compatibility.md)
- [Versions et dépendances](versions-and-dependencies.md)
- [Comment configurer une application pour prendre en charge .NET Framework 4 ou versions ultérieures](how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [Nouveautés](../whats-new/index.md)
- [Éléments obsolètes dans la bibliothèque de classes](../whats-new/whats-obsolete.md)
- [.NET Politique de soutien officiel du Cadre](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [Problèmes de migration du .NET Framework 4](net-framework-4-migration-issues.md)

---
title: 'Guide de migration vers le .NET Framework 4.8, 4.7, 4.6 et 4.5 '
description: Guide de migration vers des versions plus récentes de .NET Framework qui incluent des ressources pour les nouvelles fonctionnalités et la compatibilité des applications.
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
ms.openlocfilehash: a5b632824efacdb5e99228727b8751dc7f17d363
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86443414"
---
# <a name="migrate-to-net-framework-48-47-46-and-45"></a>Migrer vers .NET Framework 4,8, 4,7, 4,6 et 4,5

Si vous avez créé votre application à l’aide d’une version antérieure de .NET Framework, vous pouvez généralement la mettre à niveau vers .NET Framework 4,5 et ses versions intermédiaires (4.5.1 et 4.5.2), .NET Framework 4,6 et ses versions intermédiaires (4.6.1 et 4.6.2), .NET Framework 4,7 et ses versions intermédiaires (4.7.1 et 4.7.2) ou .NET Framework 4,8 facilement. Ouvrez votre projet dans Visual Studio. Si votre projet a été créé dans une version antérieure de Visual Studio, la boîte de dialogue **Compatibilité des projets** s’ouvre automatiquement. Pour plus d’informations sur la mise à niveau d’un projet dans Visual Studio, consultez [Porter, migrer et mettre à niveau des projets Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) et [Ciblage et compatibilité de la plateforme Visual Studio 2019](/visualstudio/releases/2019/compatibility).

 Toutefois, certaines modifications apportées à .NET Framework requièrent des modifications de votre code. Vous pouvez également bénéficier des nouvelles fonctionnalités du .NET Framework 4.5 et ses versions intermédiaires, de .NET Framework 4.6 et ses versions intermédiaires, de .NET Framework 4.7 et ses versions intermédiaires ou de .NET Framework 4.8. Il est généralement fait appel à la *migration*pour apporter ces types de modifications à votre application pour une nouvelle version de .NET Framework. Si votre application n’a pas besoin d’être migrée, vous pouvez l’exécuter dans .NET Framework 4,5 ou une version ultérieure sans la recompiler.

## <a name="migration-resources"></a>Ressources de migration

Passez en revue les documents suivants avant de migrer votre application à partir de versions antérieures de .NET Framework vers la version 4,5, 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 ou 4,8 :

- Consultez [Versions et dépendances](versions-and-dependencies.md) pour comprendre la version CLR sous-jacente à chaque version du .NET Framework, et pour passer en revue les instructions qui vous permettront de cibler correctement vos applications.

- Vérifiez la [compatibilité des applications](application-compatibility.md) pour découvrir les modifications d’exécution et de reciblage qui peuvent affecter votre application et comment les gérer.

- Consultez [Éléments obsolètes dans la bibliothèque de classes](../whats-new/whats-obsolete.md) pour déterminer les types ou membres rendus obsolètes dans votre code, et les alternatives recommandées.

- Consultez [Nouveautés](../whats-new/index.md) pour obtenir la description des nouvelles fonctionnalités que vous pouvez ajouter à votre application.

## <a name="see-also"></a>Voir aussi

- [Compatibilité des applications](application-compatibility.md)
- [Migration à partir du .NET Framework 1.1](migrating-from-the-net-framework-1-1.md)
- [Compatibilité des versions](version-compatibility.md)
- [Versions et dépendances](versions-and-dependencies.md)
- [Comment : configurer une application pour prendre en charge .NET Framework 4 ou versions ultérieures](how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [Nouveautés](../whats-new/index.md)
- [Éléments obsolètes dans la bibliothèque de classes](../whats-new/whats-obsolete.md)
- [.NET Framework la stratégie de support officielle](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [Problèmes de migration du .NET Framework 4](net-framework-4-migration-issues.md)

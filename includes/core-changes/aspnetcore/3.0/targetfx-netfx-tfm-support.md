---
ms.openlocfilehash: 4c676a185ff4a7a825acb059bf0a5842ca3922fc
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393893"
---
### <a name="target-framework-net-framework-support-dropped"></a>Framework cible : la prise en charge de .NET Framework a été supprimée

À compter de ASP.NET Core 3,0, .NET Framework est un Framework cible non pris en charge.

#### <a name="change-description"></a>Modifier la description

.NET Framework 4,8 est la dernière version principale de .NET Framework. Les nouvelles applications de ASP.NET Core doivent être basées sur .NET Core. À compter de la version 3,0 de .NET Core, vous pouvez considérer ASP.NET Core 3,0 comme faisant partie de .NET Core.

Les clients qui utilisent ASP.NET Core avec .NET Framework peuvent continuer de manière totalement prise en charge à l’aide de la [version 2,1 LTS](https://www.microsoft.com/net/download/dotnet-core/2.1). Le support et la maintenance pour 2,1 se poursuivent jusqu’au 21 août 2021. Cette date est de trois ans après la déclaration de la version LTS pour la [stratégie de support .net](https://www.microsoft.com/net/platform/support-policy). La prise en charge des packages ASP.NET Core 2,1 **sur .NET Framework** s’étend indéfiniment, de manière similaire à la [stratégie de maintenance pour d’autres frameworks ASP.net basés sur des packages](https://dotnet.microsoft.com/platform/support/policy/aspnet).

Pour plus d’informations sur le portage à partir de .NET Framework vers .NET Core, consultez [portage vers .net Core](~/docs/core/porting/index.md).

les packages `Microsoft.Extensions` (tels que la journalisation, l’injection de dépendances et la configuration) et les Entity Framework Core ne sont pas affectés. Ils continueront de prendre en charge .NET Standard.

Pour plus d’informations sur la motivation de cette modification, consultez le billet de [blog d’origine](https://blogs.msdn.microsoft.com/webdev/2018/10/29/a-first-look-at-changes-coming-in-asp-net-core-3-0).

#### <a name="version-introduced"></a>Version introduite

3,0

#### <a name="old-behavior"></a>Ancien comportement

ASP.NET Core applications peuvent s’exécuter sur .NET Core ou sur .NET Framework.

#### <a name="new-behavior"></a>Nouveau comportement

Les applications ASP.NET Core ne peuvent être exécutées que sur .NET Core.

#### <a name="recommended-action"></a>Action recommandée

Effectuez l’une des actions suivantes :

- Conservez votre application sur ASP.NET Core 2,1.
- Migrez votre application et les dépendances vers .NET Core.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

aucune.

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

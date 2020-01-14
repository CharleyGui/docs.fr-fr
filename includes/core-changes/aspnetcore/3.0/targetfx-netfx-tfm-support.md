---
ms.openlocfilehash: b60f74947a537c602c7bd1a89587b76bd847c82a
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937284"
---
### <a name="target-framework-net-framework-support-dropped"></a>Framework cible : la prise en charge de .NET Framework a été supprimée

À compter de ASP.NET Core 3,0, .NET Framework est un Framework cible non pris en charge.

#### <a name="change-description"></a>Description des modifications

.NET Framework 4,8 est la dernière version principale de .NET Framework. Les nouvelles applications de ASP.NET Core doivent être basées sur .NET Core. À compter de la version 3,0 de .NET Core, vous pouvez considérer ASP.NET Core 3,0 comme faisant partie de .NET Core.

Les clients qui utilisent ASP.NET Core avec .NET Framework peuvent continuer de manière totalement prise en charge à l’aide de la [version 2,1 LTS](https://www.microsoft.com/net/download/dotnet-core/2.1). Le support et la maintenance pour 2,1 se poursuivent jusqu’au 21 août 2021. Cette date est de trois ans après la déclaration de la version LTS pour la [stratégie de support .net](https://www.microsoft.com/net/platform/support-policy). La prise en charge des packages ASP.NET Core 2,1 **sur .NET Framework** s’étend indéfiniment, de manière similaire à la [stratégie de maintenance pour d’autres frameworks ASP.net basés sur des packages](https://dotnet.microsoft.com/platform/support/policy/aspnet).

Pour plus d’informations sur le portage à partir de .NET Framework vers .NET Core, consultez [portage vers .net Core](~/docs/core/porting/index.md).

les packages de `Microsoft.Extensions` (tels que la journalisation, l’injection de dépendances et la configuration) et les Entity Framework Core ne sont pas affectés. Ils continueront de prendre en charge .NET Standard.

Pour plus d’informations sur la motivation de cette modification, consultez le billet de [blog d’origine](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

ASP.NET Core applications peuvent s’exécuter sur .NET Core ou sur .NET Framework.

#### <a name="new-behavior"></a>Nouveau comportement

Les applications ASP.NET Core ne peuvent être exécutées que sur .NET Core.

#### <a name="recommended-action"></a>Action recommandée

Effectuez l’une des actions suivantes :

- Conservez votre application sur ASP.NET Core 2,1.
- Migrez votre application et les dépendances vers .NET Core.

#### <a name="category"></a>Catégorie

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

Aucun

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

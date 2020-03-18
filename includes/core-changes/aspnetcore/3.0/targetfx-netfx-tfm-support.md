---
ms.openlocfilehash: b60f74947a537c602c7bd1a89587b76bd847c82a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937284"
---
### <a name="target-framework-net-framework-support-dropped"></a>Cadre cible : le soutien cadre net supprimé

À partir de ASP.NET Core 3.0, le cadre NET est un cadre cible non pris en soutien.

#### <a name="change-description"></a>Description de la modification

.NET Framework 4.8 est la dernière version majeure du cadre .NET. Les nouvelles applications ASP.NET Core devraient être construites sur .NET Core. En commençant par la version .NET Core 3.0, vous pouvez penser à ASP.NET Core 3.0 comme faisant partie de .NET Core.

Les clients utilisant ASP.NET Core avec .NET Framework peuvent continuer d’une manière entièrement pris en charge en utilisant la [version 2.1 LTS](https://www.microsoft.com/net/download/dotnet-core/2.1). Le soutien et l’entretien de 2,1 se poursuivent au moins jusqu’au 21 août 2021. Cette date est de trois ans après la déclaration de la version LTS par la [politique de soutien .NET](https://www.microsoft.com/net/platform/support-policy). Le soutien aux paquets ASP.NET Core 2.1 **sur le cadre .NET** s’étendra indéfiniment, semblable à la [politique de service pour d’autres cadres ASP.NET fondés sur des paquets](https://dotnet.microsoft.com/platform/support/policy/aspnet).

Pour plus d’informations sur le portage de .NET Framework à .NET Core, voir [Porting à .NET Core](~/docs/core/porting/index.md).

`Microsoft.Extensions`(tels que l’exploitation forestière, l’injection de dépendance et la configuration) et le cadre d’entité n’est pas affecté. Ils continueront à soutenir .NET Standard.

Pour plus d’informations sur la motivation de ce changement, voir [le blog original](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

ASP.NET applications de base pourraient s’exécuter sur .NET Core ou .NET Framework.

#### <a name="new-behavior"></a>Nouveau comportement

ASP.NET les applications Core ne peuvent être exécutées que sur .NET Core.

#### <a name="recommended-action"></a>Action recommandée

Effectuez l'une des opérations suivantes :

- Gardez votre application sur ASP.NET Core 2.1.
- Migrez votre application et dépendances à .NET Core.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

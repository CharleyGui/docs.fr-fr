---
ms.openlocfilehash: 82103d82a6f68c62f3532608718bc71b0ba126bf
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032504"
---
### <a name="hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle"></a>Hébergement : AspNetCoreModule v1 supprimé du bundle d’hébergement Windows

À compter de ASP.NET Core 3,0, le bundle d’hébergement Windows ne contient pas AspNetCoreModule (ANCM) v1.

ANCM V2 offre une compatibilité descendante avec ANCM OutOfProcess et il est recommandé de l’utiliser avec les applications ASP.NET Core 3,0.

Pour plus d’informations, consultez [dotnet/aspnetcore # 7095](https://github.com/dotnet/aspnetcore/issues/7095).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

ANCM v1 est inclus dans le bundle d’hébergement Windows.

#### <a name="new-behavior"></a>Nouveau comportement

ANCM v1 n’est pas inclus dans le bundle d’hébergement Windows.

#### <a name="reason-for-change"></a>Motif de modification

ANCM V2 offre une compatibilité descendante avec ANCM OutOfProcess et il est recommandé de l’utiliser avec les applications ASP.NET Core 3,0.

#### <a name="recommended-action"></a>Action recommandée

Utilisez ANCM v2 avec les applications ASP.NET Core 3,0.

Si ANCM v1 est requis, il peut être installé à l’aide de l’offre groupée d’hébergement Windows ASP.NET Core 2,1 ou 2,2.

Cette modification s’interrompt ASP.NET Core applications 3,0 qui :

- Optez explicitement pour l’utilisation de ANCM v1 avec `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>` .
- Avoir un fichier de *web.config* personnalisé avec `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />` .

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

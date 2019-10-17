---
ms.openlocfilehash: 04e5ca41374fc333a31f0422bc2e89f54b3cb049
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394297"
---
### <a name="hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle"></a>Hébergement : AspNetCoreModule v1 supprimé du bundle d’hébergement Windows

À compter de ASP.NET Core 3,0, le bundle d’hébergement Windows ne contient pas AspNetCoreModule (ANCM) v1.

ANCM V2 offre une compatibilité descendante avec ANCM OutOfProcess et il est recommandé de l’utiliser avec les applications ASP.NET Core 3,0.

Pour plus d’informations, consultez [ASPNET/AspNetCore # 7095](https://github.com/aspnet/AspNetCore/issues/7095).

#### <a name="version-introduced"></a>Version introduite

3,0

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

- Optez explicitement pour l’utilisation de ANCM v1 avec `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`.
- Avoir un fichier *Web. config* personnalisé avec `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

aucune.

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

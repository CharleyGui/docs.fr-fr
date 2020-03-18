---
ms.openlocfilehash: 82103d82a6f68c62f3532608718bc71b0ba126bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901959"
---
### <a name="hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle"></a>Hébergement: AspNetCoreModule V1 supprimé de Windows Hosting Bundle

En commençant par ASP.NET Core 3.0, le Windows Hosting Bundle ne contiendra pas aspNetCoreModule (ANCM) V1.

ANCM V2 est compatible vers l’arrière avec ANCM OutOfProcess et est recommandé pour une utilisation avec ASP.NET applications Core 3.0.

Pour discussion, voir [dotnet/aspnetcore 7095](https://github.com/dotnet/aspnetcore/issues/7095).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

ANCM V1 est inclus dans le Windows Hosting Bundle.

#### <a name="new-behavior"></a>Nouveau comportement

ANCM V1 n’est pas inclus dans le Windows Hosting Bundle.

#### <a name="reason-for-change"></a>Raison du changement

ANCM V2 est compatible vers l’arrière avec ANCM OutOfProcess et est recommandé pour une utilisation avec ASP.NET applications Core 3.0.

#### <a name="recommended-action"></a>Action recommandée

Utilisez ANCM V2 avec ASP.NET applications Core 3.0.

Si ANCM V1 est nécessaire, il peut être installé à l’aide du ASP.NET Core 2.1 ou 2.2 Windows Hosting Bundle.

Ce changement va briser ASP.NET applications Core 3.0 qui:

- Explicitement choisi d’utiliser ANCM V1 avec `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`.
- Avoir un fichier *web.config* personnalisé avec `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

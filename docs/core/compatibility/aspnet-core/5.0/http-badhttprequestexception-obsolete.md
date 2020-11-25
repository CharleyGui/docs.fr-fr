---
title: 'Modification avec rupture : HTTP : Kestrel et types de BadHttpRequestException IIS marqués comme obsolètes et remplacés'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 intitulée HTTP : Kestrel et les types de BadHttpRequestException IIS marqués comme obsolètes et remplacés'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: c51b1dd9d708c04bc1bbcfb65ea2e9daea5330b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760960"
---
# <a name="http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced"></a>HTTP : Kestrel et les types de BadHttpRequestException IIS marqués comme obsolètes et remplacés

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` et `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` ont été marqués comme obsolètes et ont été modifiés pour dériver de `Microsoft.AspNetCore.Http.BadHttpRequestException` . Les serveurs Kestrel et IIS lèvent toujours leurs anciens types d’exception à des fins de compatibilité descendante. Les types obsolètes seront supprimés dans une version ultérieure.

Pour plus d’informations, consultez [dotnet/aspnetcore # 20614](https://github.com/dotnet/aspnetcore/issues/20614).

## <a name="version-introduced"></a>Version introduite

5,0 Preview 4

## <a name="old-behavior"></a>Ancien comportement

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` et `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` dérivées de <xref:System.IO.IOException?displayProperty=nameWithType> .

## <a name="new-behavior"></a>Nouveau comportement

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` et `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` sont obsolètes. Les types dérivent également de `Microsoft.AspNetCore.Http.BadHttpRequestException` , qui dérive de `System.IO.IOException` .

## <a name="reason-for-change"></a>Motif de modification

La modification a été apportée à :

* Consolidez les types dupliqués.
* Unifiez le comportement entre les implémentations de serveur.

Une application peut maintenant intercepter l’exception de base `Microsoft.AspNetCore.Http.BadHttpRequestException` lors de l’utilisation de Kestrel ou IIS.

## <a name="recommended-action"></a>Action recommandée

Remplacer les utilisations de `Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` et de `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` par `Microsoft.AspNetCore.Http.BadHttpRequestException` .

## <a name="affected-apis"></a>API affectées

- [Microsoft. AspNetCore. Server. IIS. BadHttpRequestException](/dotnet/api/microsoft.aspnetcore.server.iis.badhttprequestexception?view=aspnetcore-3.1)
- [Microsoft. AspNetCore. Server. Kestrel. BadHttpRequestException](/dotnet/api/microsoft.aspnetcore.server.kestrel.badhttprequestexception?view=aspnetcore-1.1)

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.AspNetCore.Server.IIS.BadHttpRequestException`
- `T:Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`

-->

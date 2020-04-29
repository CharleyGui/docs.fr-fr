---
ms.openlocfilehash: c4e7864262a11aafa4b7f1f4bdf632fbf084c560
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507078"
---
### <a name="http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced"></a>HTTP : Kestrel et les types de BadHttpRequestException IIS marqués comme obsolètes et remplacés

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`et `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` ont été marqués comme obsolètes et ont été `Microsoft.AspNetCore.Http.BadHttpRequestException`modifiés pour dériver de. Les serveurs Kestrel et IIS lèvent toujours leurs anciens types d’exception à des fins de compatibilité descendante. Les types obsolètes seront supprimés dans une version ultérieure.

Pour plus d’informations, consultez [dotnet/aspnetcore # 20614](https://github.com/dotnet/aspnetcore/issues/20614).

#### <a name="version-introduced"></a>Version introduite

5,0 Preview 4

#### <a name="old-behavior"></a>Ancien comportement

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`et `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` dérivées <xref:System.IO.IOException?displayProperty=nameWithType>de.

#### <a name="new-behavior"></a>Nouveau comportement

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`et `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` sont obsolètes. Les types dérivent `Microsoft.AspNetCore.Http.BadHttpRequestException`également de, qui dérive de `System.IO.IOException`.

#### <a name="reason-for-change"></a>Motif de modification

La modification a été apportée à :

* Consolidez les types dupliqués.
* Unifiez le comportement entre les implémentations de serveur.

Une application peut maintenant intercepter l’exception `Microsoft.AspNetCore.Http.BadHttpRequestException` de base lors de l’utilisation de KESTREL ou IIS.

#### <a name="recommended-action"></a>Action recommandée

Remplacer les utilisations de `Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` et `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` de `Microsoft.AspNetCore.Http.BadHttpRequestException`par.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

- [Microsoft. AspNetCore. Server. IIS. BadHttpRequestException](/dotnet/api/microsoft.aspnetcore.server.iis.badhttprequestexception?view=aspnetcore-3.1)
- [Microsoft. AspNetCore. Server. Kestrel. BadHttpRequestException](/dotnet/api/microsoft.aspnetcore.server.kestrel.badhttprequestexception?view=aspnetcore-1.1)

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Server.IIS.BadHttpRequestException`
- `T:Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`

-->

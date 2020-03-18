---
ms.openlocfilehash: 06d5f48566c239e37355496c3f27163d952602c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901664"
---
### <a name="kestrel-connection-adapters-removed"></a>Kestrel: adaptateurs de connexion supprimés

Dans le cadre du mouvement des API `public`"pubtérinaires" à , le concept d’un `IConnectionAdapter` a été retiré de Kestrel. Les adaptateurs de connexion sont remplacés par des middleware de connexion (semblable à HTTP middleware dans le pipeline ASP.NET Core, mais pour les connexions de niveau inférieur). HTTPS et l’enregistrement de connexion sont passés des adaptateurs de connexion à la connexion middleware. Ces méthodes d’extension devraient continuer à fonctionner de manière transparente, mais les détails de la mise en œuvre ont changé.

Pour plus d’informations, voir [dotnet/aspnetcore 11412](https://github.com/dotnet/aspnetcore/pull/11412). Pour discussion, voir [dotnet/aspnetcore 11475](https://github.com/dotnet/aspnetcore/issues/11475).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Kestrel extensibility composants ont `IConnectionAdapter`été créés en utilisant .

#### <a name="new-behavior"></a>Nouveau comportement

Kestrel extensibility composants sont créés comme [middleware](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).

#### <a name="reason-for-change"></a>Raison du changement

Ce changement vise à fournir une architecture d’extéponsabilité plus flexible.

#### <a name="recommended-action"></a>Action recommandée

Convertir toutes les `IConnectionAdapter` implémentations de pour utiliser le nouveau modèle middleware comme indiqué [ici](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

`Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

-->

---
ms.openlocfilehash: 06d5f48566c239e37355496c3f27163d952602c6
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032575"
---
### <a name="kestrel-connection-adapters-removed"></a>Kestrel : adaptateurs de connexion supprimés

Dans le cadre du déplacement vers lequel déplacer les API « pubternal » vers `public` , le concept d’un `IConnectionAdapter` a été supprimé de Kestrel. Les adaptateurs de connexion sont remplacés par un intergiciel de connexion (similaire à l’intergiciel HTTP dans le pipeline ASP.NET Core, mais pour les connexions de niveau inférieur). HTTPs et la journalisation des connexions ont été déplacées des adaptateurs de connexion vers l’intergiciel de connexion. Ces méthodes d’extension doivent continuer à fonctionner de manière transparente, mais les détails de l’implémentation ont changé.

Pour plus d’informations, consultez [dotnet/aspnetcore # 11412](https://github.com/dotnet/aspnetcore/pull/11412). Pour plus d’informations, consultez [dotnet/aspnetcore # 11475](https://github.com/dotnet/aspnetcore/issues/11475).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Les composants d’extensibilité de Kestrel ont été créés à l’aide de `IConnectionAdapter` .

#### <a name="new-behavior"></a>Nouveau comportement

Les composants d’extensibilité Kestrel sont créés en tant que [middleware](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).

#### <a name="reason-for-change"></a>Motif de modification

Cette modification vise à fournir une architecture d’extensibilité plus flexible.

#### <a name="recommended-action"></a>Action recommandée

Convertissez toutes les implémentations de `IConnectionAdapter` pour utiliser le nouveau modèle d’intergiciel (middleware) comme indiqué [ici](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

`Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

-->

---
ms.openlocfilehash: 771238c53dc97f4cf4068968f3c68500ba9f87da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73198425"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a>Caching: Microsoft.Extensions.Caching.SqlServer utilise le nouveau paquet SqlClient

Le `Microsoft.Extensions.Caching.SqlServer` paquet utilisera `Microsoft.Data.SqlClient` le `System.Data.SqlClient` nouveau paquet au lieu du paquet. Ce changement pourrait provoquer de légers changements de rupture comportementale. Pour plus d’informations, voir [Présentation du nouveau Microsoft.Data.SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Le `Microsoft.Extensions.Caching.SqlServer` paquet `System.Data.SqlClient` a utilisé le paquet.

#### <a name="new-behavior"></a>Nouveau comportement

`Microsoft.Extensions.Caching.SqlServer`utilise maintenant `Microsoft.Data.SqlClient` le paquet.

#### <a name="reason-for-change"></a>Raison du changement

`Microsoft.Data.SqlClient`est un nouveau paquet qui `System.Data.SqlClient`est construit hors de . C’est là que tout nouveau travail de fonctionnalité sera fait à partir de maintenant.

#### <a name="recommended-action"></a>Action recommandée

Les clients ne devraient pas avoir à s’inquiéter de `Microsoft.Extensions.Caching.SqlServer` ce changement `System.Data.SqlClient` de rupture à moins qu’ils ont été en utilisant des types retournés par le paquet et de les jeter à des types. Par exemple, si quelqu’un jetait un `DbConnection` à [l’ancien type SqlConnection](xref:System.Data.SqlClient.SqlConnection), ils auraient besoin de changer le casting pour le nouveau `Microsoft.Data.SqlClient.SqlConnection` type.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

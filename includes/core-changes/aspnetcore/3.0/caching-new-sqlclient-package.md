---
ms.openlocfilehash: 771238c53dc97f4cf4068968f3c68500ba9f87da
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032484"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a>Mise en cache : Microsoft. extensions. Caching. SqlServer utilise le nouveau package SqlClient

Le `Microsoft.Extensions.Caching.SqlServer` package utilise le nouveau package à la `Microsoft.Data.SqlClient` place du `System.Data.SqlClient` Package. Cette modification peut entraîner de légères modifications avec rupture de comportement. Pour plus d’informations, consultez [Présentation du nouveau Microsoft. Data. SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Le `Microsoft.Extensions.Caching.SqlServer` package a utilisé le `System.Data.SqlClient` Package.

#### <a name="new-behavior"></a>Nouveau comportement

`Microsoft.Extensions.Caching.SqlServer` utilise maintenant le `Microsoft.Data.SqlClient` Package.

#### <a name="reason-for-change"></a>Motif de modification

`Microsoft.Data.SqlClient` est un nouveau package qui est créé à partir de `System.Data.SqlClient` . C’est là que tous les nouveaux travaux de fonctionnalités seront effectués à partir de maintenant.

#### <a name="recommended-action"></a>Action recommandée

Les clients ne doivent pas avoir à se soucier de cette modification avec rupture, sauf s’ils utilisaient des types retournés par le `Microsoft.Extensions.Caching.SqlServer` package et les castant en `System.Data.SqlClient` types. Par exemple, si quelqu’un effectuait un cast de `DbConnection` en l' [ancien type SqlConnection](xref:System.Data.SqlClient.SqlConnection), il aurait besoin de remplacer le cast par le nouveau `Microsoft.Data.SqlClient.SqlConnection` type.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

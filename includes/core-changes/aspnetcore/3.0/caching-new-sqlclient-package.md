---
ms.openlocfilehash: 771238c53dc97f4cf4068968f3c68500ba9f87da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73198425"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a>Mise en cache : Microsoft. extensions. Caching. SqlServer utilise le nouveau package SqlClient

Le `Microsoft.Extensions.Caching.SqlServer` package utilise le nouveau `Microsoft.Data.SqlClient` package à la place `System.Data.SqlClient` du package. Cette modification peut entraîner de légères modifications avec rupture de comportement. Pour plus d’informations, consultez [Présentation du nouveau Microsoft. Data. SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Le `Microsoft.Extensions.Caching.SqlServer` package a utilisé `System.Data.SqlClient` le package.

#### <a name="new-behavior"></a>Nouveau comportement

`Microsoft.Extensions.Caching.SqlServer`utilise maintenant le `Microsoft.Data.SqlClient` package.

#### <a name="reason-for-change"></a>Motif de modification

`Microsoft.Data.SqlClient`est un nouveau package qui est créé à partir `System.Data.SqlClient`de. C’est là que tous les nouveaux travaux de fonctionnalités seront effectués à partir de maintenant.

#### <a name="recommended-action"></a>Action recommandée

Les clients ne doivent pas avoir à se soucier de cette modification avec rupture, sauf `Microsoft.Extensions.Caching.SqlServer` s’ils utilisaient des `System.Data.SqlClient` types retournés par le package et les castant en types. Par exemple, si quelqu’un effectuait un `DbConnection` cast de en l' [ancien type SqlConnection](xref:System.Data.SqlClient.SqlConnection), il aurait besoin de remplacer le cast par `Microsoft.Data.SqlClient.SqlConnection` le nouveau type.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

Aucun

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

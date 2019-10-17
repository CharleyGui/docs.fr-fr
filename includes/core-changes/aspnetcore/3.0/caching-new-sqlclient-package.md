---
ms.openlocfilehash: 32c7f4e9e4736145f9275b74f34c04404e7c770a
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394110"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a>Mise en cache : Microsoft. extensions. Caching. SqlServer utilise le nouveau package SqlClient

Le package `Microsoft.Extensions.Caching.SqlServer` utilise le nouveau package `Microsoft.Data.SqlClient` au lieu du package `System.Data.SqlClient`. Cette modification peut entraîner de légères modifications avec rupture de comportement. Pour plus d’informations, consultez [Présentation du nouveau Microsoft. Data. SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).

#### <a name="version-introduced"></a>Version introduite

3,0

#### <a name="old-behavior"></a>Ancien comportement

Le package `Microsoft.Extensions.Caching.SqlServer` utilisait le package `System.Data.SqlClient`.

#### <a name="new-behavior"></a>Nouveau comportement

`Microsoft.Extensions.Caching.SqlServer` utilise maintenant le package `Microsoft.Data.SqlClient`.

#### <a name="reason-for-change"></a>Motif de modification

`Microsoft.Data.SqlClient` est un nouveau package qui est créé à partir de `System.Data.SqlClient`. C’est là que tous les nouveaux travaux de fonctionnalités seront effectués à partir de maintenant.

#### <a name="recommended-action"></a>Action recommandée

Les clients ne doivent pas avoir à se soucier de cette modification avec rupture, sauf s’ils utilisaient des types retournés par le package `Microsoft.Extensions.Caching.SqlServer` et les castant en types `System.Data.SqlClient`. Par exemple, si quelqu’un effectuait un cast d’un `DbConnection` vers l' [ancien type SqlConnection](xref:System.Data.SqlClient.SqlConnection), il aurait besoin de remplacer le cast par le nouveau type `Microsoft.Data.SqlClient.SqlConnection`. 

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

aucune.

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

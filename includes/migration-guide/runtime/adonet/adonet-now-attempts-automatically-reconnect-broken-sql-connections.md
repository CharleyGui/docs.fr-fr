---
ms.openlocfilehash: 23ba6064a283b47312a66f3636c2834a7d58106e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619944"
---
### <a name="adonet-now-attempts-to-automatically-reconnect-broken-sql-connections"></a>ADO.NET tente maintenant de reconnecter automatiquement les connexions SQL rompues

#### <a name="details"></a>Détails

À compter de .NET Framework 4.5.1, le .NET Framework tente de reconnecter automatiquement les connexions SQL rompues. Bien que cette opération améliore généralement la fiabilité des applications, il existe des cas particuliers où une application doit savoir que la connexion a été perdue afin de pouvoir prendre des mesures lors de la reconnexion.

#### <a name="suggestion"></a>Suggestion

Si cette fonctionnalité n’est pas souhaitable pour des raisons de compatibilité, elle peut être désactivée en affectant à la propriété <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=fullName> d’une chaîne de connexion (ou <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=fullName>) la valeur 0.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4.5.1|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Data.IDbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Configuration.ConnectionStringSettings.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor(System.String)></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor(System.Boolean)></li></ul>|

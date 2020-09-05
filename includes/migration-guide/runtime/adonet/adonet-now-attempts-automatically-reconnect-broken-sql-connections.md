---
ms.openlocfilehash: 7f7e718d543a4abdf2b8a87e52d8c0e2ba28203f
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497422"
---
### <a name="adonet-now-attempts-to-automatically-reconnect-broken-sql-connections"></a>ADO.NET tente maintenant de reconnecter automatiquement les connexions SQL rompues

#### <a name="details"></a>Détails

À compter de .NET Framework 4.5.1, le .NET Framework tente de reconnecter automatiquement les connexions SQL rompues. Bien que cette opération améliore généralement la fiabilité des applications, il existe des cas particuliers où une application doit savoir que la connexion a été perdue afin de pouvoir prendre des mesures lors de la reconnexion.

#### <a name="suggestion"></a>Suggestion

Si cette fonctionnalité n’est pas souhaitable pour des raisons de compatibilité, elle peut être désactivée en affectant à la propriété <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=fullName> d’une chaîne de connexion (ou <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=fullName>) la valeur 0.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4.5.1|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Data.IDbConnection.ConnectionString?displayProperty=nameWithType>
- <xref:System.Data.SqlClient.SqlConnection.ConnectionString?displayProperty=nameWithType>
- <xref:System.Configuration.ConnectionStringSettings.ConnectionString?displayProperty=nameWithType>
- <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType>
- <xref:System.Data.Common.DbConnectionStringBuilder.ConnectionString?displayProperty=nameWithType>
- <xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor>
- <xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor(System.String)>
- <xref:System.Data.Common.DbConnectionStringBuilder.%23ctor>
- <xref:System.Data.Common.DbConnectionStringBuilder.%23ctor(System.Boolean)>

<!--

#### Affected APIs

- `P:System.Data.IDbConnection.ConnectionString`
- `P:System.Data.SqlClient.SqlConnection.ConnectionString`
- `P:System.Configuration.ConnectionStringSettings.ConnectionString`
- `P:System.Data.Common.DbConnection.ConnectionString`
- `P:System.Data.Common.DbConnectionStringBuilder.ConnectionString`
- `M:System.Data.SqlClient.SqlConnectionStringBuilder.#ctor`
- `M:System.Data.SqlClient.SqlConnectionStringBuilder.#ctor(System.String)`
- `M:System.Data.Common.DbConnectionStringBuilder.#ctor`
- `M:System.Data.Common.DbConnectionStringBuilder.#ctor(System.Boolean)`

-->

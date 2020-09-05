---
ms.openlocfilehash: 7f7e718d543a4abdf2b8a87e52d8c0e2ba28203f
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497422"
---
### <a name="adonet-now-attempts-to-automatically-reconnect-broken-sql-connections"></a><span data-ttu-id="6b334-101">ADO.NET tente maintenant de reconnecter automatiquement les connexions SQL rompues</span><span class="sxs-lookup"><span data-stu-id="6b334-101">ADO.NET now attempts to automatically reconnect broken SQL connections</span></span>

#### <a name="details"></a><span data-ttu-id="6b334-102">Détails</span><span class="sxs-lookup"><span data-stu-id="6b334-102">Details</span></span>

<span data-ttu-id="6b334-103">À compter de .NET Framework 4.5.1, le .NET Framework tente de reconnecter automatiquement les connexions SQL rompues.</span><span class="sxs-lookup"><span data-stu-id="6b334-103">Beginning in the .NET Framework 4.5.1, the .NET Framework will attempt to automatically reconnect broken SQL connections.</span></span> <span data-ttu-id="6b334-104">Bien que cette opération améliore généralement la fiabilité des applications, il existe des cas particuliers où une application doit savoir que la connexion a été perdue afin de pouvoir prendre des mesures lors de la reconnexion.</span><span class="sxs-lookup"><span data-stu-id="6b334-104">Although this will typically make apps more reliable, there are edge cases in which an app needs to know that the connection was lost so that it can take some action upon reconnection.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6b334-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="6b334-105">Suggestion</span></span>

<span data-ttu-id="6b334-106">Si cette fonctionnalité n’est pas souhaitable pour des raisons de compatibilité, elle peut être désactivée en affectant à la propriété <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=fullName> d’une chaîne de connexion (ou <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=fullName>) la valeur 0.</span><span class="sxs-lookup"><span data-stu-id="6b334-106">If this feature is undesirable due to compatibility concerns, it can be disabled by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=fullName> property of a connection string (or <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=fullName>) to 0.</span></span>

| <span data-ttu-id="6b334-107">Name</span><span class="sxs-lookup"><span data-stu-id="6b334-107">Name</span></span>    | <span data-ttu-id="6b334-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="6b334-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6b334-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="6b334-109">Scope</span></span>   |<span data-ttu-id="6b334-110">Edge</span><span class="sxs-lookup"><span data-stu-id="6b334-110">Edge</span></span>|
|<span data-ttu-id="6b334-111">Version</span><span class="sxs-lookup"><span data-stu-id="6b334-111">Version</span></span>|<span data-ttu-id="6b334-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="6b334-112">4.5.1</span></span>|
|<span data-ttu-id="6b334-113">Type</span><span class="sxs-lookup"><span data-stu-id="6b334-113">Type</span></span>|<span data-ttu-id="6b334-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="6b334-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="6b334-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="6b334-115">Affected APIs</span></span>

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

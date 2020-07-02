---
ms.openlocfilehash: 23ba6064a283b47312a66f3636c2834a7d58106e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619944"
---
### <a name="adonet-now-attempts-to-automatically-reconnect-broken-sql-connections"></a><span data-ttu-id="5603c-101">ADO.NET tente maintenant de reconnecter automatiquement les connexions SQL rompues</span><span class="sxs-lookup"><span data-stu-id="5603c-101">ADO.NET now attempts to automatically reconnect broken SQL connections</span></span>

#### <a name="details"></a><span data-ttu-id="5603c-102">Détails</span><span class="sxs-lookup"><span data-stu-id="5603c-102">Details</span></span>

<span data-ttu-id="5603c-103">À compter de .NET Framework 4.5.1, le .NET Framework tente de reconnecter automatiquement les connexions SQL rompues.</span><span class="sxs-lookup"><span data-stu-id="5603c-103">Beginning in the .NET Framework 4.5.1, the .NET Framework will attempt to automatically reconnect broken SQL connections.</span></span> <span data-ttu-id="5603c-104">Bien que cette opération améliore généralement la fiabilité des applications, il existe des cas particuliers où une application doit savoir que la connexion a été perdue afin de pouvoir prendre des mesures lors de la reconnexion.</span><span class="sxs-lookup"><span data-stu-id="5603c-104">Although this will typically make apps more reliable, there are edge cases in which an app needs to know that the connection was lost so that it can take some action upon reconnection.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5603c-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="5603c-105">Suggestion</span></span>

<span data-ttu-id="5603c-106">Si cette fonctionnalité n’est pas souhaitable pour des raisons de compatibilité, elle peut être désactivée en affectant à la propriété <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=fullName> d’une chaîne de connexion (ou <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=fullName>) la valeur 0.</span><span class="sxs-lookup"><span data-stu-id="5603c-106">If this feature is undesirable due to compatibility concerns, it can be disabled by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=fullName> property of a connection string (or <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=fullName>) to 0.</span></span>

| <span data-ttu-id="5603c-107">Nom</span><span class="sxs-lookup"><span data-stu-id="5603c-107">Name</span></span>    | <span data-ttu-id="5603c-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="5603c-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5603c-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="5603c-109">Scope</span></span>   |<span data-ttu-id="5603c-110">Edge</span><span class="sxs-lookup"><span data-stu-id="5603c-110">Edge</span></span>|
|<span data-ttu-id="5603c-111">Version</span><span class="sxs-lookup"><span data-stu-id="5603c-111">Version</span></span>|<span data-ttu-id="5603c-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="5603c-112">4.5.1</span></span>|
|<span data-ttu-id="5603c-113">Type</span><span class="sxs-lookup"><span data-stu-id="5603c-113">Type</span></span>|<span data-ttu-id="5603c-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="5603c-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5603c-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="5603c-115">Affected APIs</span></span>

-<xref:System.Data.IDbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Configuration.ConnectionStringSettings.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor(System.String)></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor(System.Boolean)></li></ul>|

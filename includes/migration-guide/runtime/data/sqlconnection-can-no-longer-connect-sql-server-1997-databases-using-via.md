---
ms.openlocfilehash: e65ba0edb132f5cded244a69d58e43ffea76a039
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606807"
---
### <a name="sqlconnection-can-no-longer-connect-to-sql-server-1997-or-databases-using-the-via-adapter"></a><span data-ttu-id="33cff-101">SqlConnection ne peut plus se connecter à SQL Server 1997 ou des bases de données à l’aide de l’adaptateur VIA</span><span class="sxs-lookup"><span data-stu-id="33cff-101">SqlConnection can no longer connect to SQL Server 1997 or databases using the VIA adapter</span></span>

#### <a name="details"></a><span data-ttu-id="33cff-102">Détails</span><span class="sxs-lookup"><span data-stu-id="33cff-102">Details</span></span>

<span data-ttu-id="33cff-103">Les connexions aux bases de données SQL Server à l’aide du [protocole via (Virtual interface adapter)](/previous-versions/sql/sql-server-2008-r2/ms191229(v=sql.105)) ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="33cff-103">Connections to SQL Server databases using the [Virtual Interface Adapter (VIA) protocol](/previous-versions/sql/sql-server-2008-r2/ms191229(v=sql.105)) are no longer supported.</span></span> <span data-ttu-id="33cff-104">Le protocole utilisé pour se connecter à une base de données SQL Server est visible dans la chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="33cff-104">The protocol used to connect to a SQL Server database is visible in the connection string.</span></span> <span data-ttu-id="33cff-105">Une connexion VIA contiendra via:&lt;nom_serveur&gt;.</span><span class="sxs-lookup"><span data-stu-id="33cff-105">A VIA connection will contain via:&lt;servername&gt;.</span></span> <span data-ttu-id="33cff-106">Si cette application se connecte à SQL via un protocole autre que VIA (TCP : ou NP : par exemple), aucune modification avec rupture ne sera détectée.</span><span class="sxs-lookup"><span data-stu-id="33cff-106">If this app is connecting to SQL via a protocol other than VIA (tcp: or np: for example), then no breaking change will be encountered.</span></span> <span data-ttu-id="33cff-107">En outre, les connexions à SQL Server 7 (1997) ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="33cff-107">Also, connections to SQL Server 7 (1997) are no longer supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="33cff-108">Suggestion</span><span class="sxs-lookup"><span data-stu-id="33cff-108">Suggestion</span></span>

<span data-ttu-id="33cff-109">Comme le protocole VIA est déprécié, un autre protocole doit être utilisé pour se connecter aux bases de données SQL.</span><span class="sxs-lookup"><span data-stu-id="33cff-109">The VIA protocol is deprecated, so an alternative protocol should be used to connect to SQL databases.</span></span> <span data-ttu-id="33cff-110">Le protocole utilisé le plus courant est TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="33cff-110">The most common protocol used is TCP/IP.</span></span> <span data-ttu-id="33cff-111">Pour plus d’informations sur la connexion TCP/IP, voir [Activer le protocole TCP/IP pour une instance de base de données](/previous-versions/visualstudio/visual-studio-2008/bb909712(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="33cff-111">For more information about connecting through TCP/IP, see [Enable the TCP/IP protocol for a database instance](/previous-versions/visualstudio/visual-studio-2008/bb909712(v=vs.90)).</span></span> <span data-ttu-id="33cff-112">Si la base de données est accessible uniquement à partir d’un intranet, le protocole des canaux nommés peut offrir de meilleures performances en cas de réseau lent.</span><span class="sxs-lookup"><span data-stu-id="33cff-112">If the database is only accessed from within an intranet, the shared pipes protocol may provide better performance if the network is slow.</span></span>

| <span data-ttu-id="33cff-113">Name</span><span class="sxs-lookup"><span data-stu-id="33cff-113">Name</span></span>    | <span data-ttu-id="33cff-114">Valeur</span><span class="sxs-lookup"><span data-stu-id="33cff-114">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="33cff-115">Étendue</span><span class="sxs-lookup"><span data-stu-id="33cff-115">Scope</span></span>   |<span data-ttu-id="33cff-116">Edge</span><span class="sxs-lookup"><span data-stu-id="33cff-116">Edge</span></span>|
|<span data-ttu-id="33cff-117">Version</span><span class="sxs-lookup"><span data-stu-id="33cff-117">Version</span></span>|<span data-ttu-id="33cff-118">4.5</span><span class="sxs-lookup"><span data-stu-id="33cff-118">4.5</span></span>|
|<span data-ttu-id="33cff-119">Type</span><span class="sxs-lookup"><span data-stu-id="33cff-119">Type</span></span>|<span data-ttu-id="33cff-120">Runtime</span><span class="sxs-lookup"><span data-stu-id="33cff-120">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="33cff-121">API affectées</span><span class="sxs-lookup"><span data-stu-id="33cff-121">Affected APIs</span></span>

- <xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)>
- <xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String,System.Data.SqlClient.SqlCredential)>

<!--

#### Affected APIs

- `M:System.Data.SqlClient.SqlConnection.#ctor(System.String)`
- `M:System.Data.SqlClient.SqlConnection.#ctor(System.String,System.Data.SqlClient.SqlCredential)`

-->

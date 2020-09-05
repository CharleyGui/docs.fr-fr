---
ms.openlocfilehash: bbeca87b3f498213b91d942cc4f197c9d80457a8
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496977"
---
### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a><span data-ttu-id="74f89-101">Une tentative de connexion TCP/IP à une base de données SQL Server qui se résout en `localhost` échoue</span><span class="sxs-lookup"><span data-stu-id="74f89-101">Attempting a TCP/IP connection to a SQL Server database that resolves to `localhost` fails</span></span>

#### <a name="details"></a><span data-ttu-id="74f89-102">Détails</span><span class="sxs-lookup"><span data-stu-id="74f89-102">Details</span></span>

<span data-ttu-id="74f89-103">Dans .NET Framework 4.6 et 4.6.1, une tentative de connexion TCP/IP à une base de données SQL Server qui se résout en <code>localhost</code> échoue avec l’erreur &quot;Une erreur liée au réseau ou spécifique à l’instance s’est produite lors de l’établissement d’une connexion à SQL Server.</span><span class="sxs-lookup"><span data-stu-id="74f89-103">In the .NET Framework 4.6 and 4.6.1, attempting a TCP/IP connection to a SQL Server database that resolves to <code>localhost</code> fails with the error, &quot;A network-related or instance-specific error occurred while establishing a connection to SQL Server.</span></span> <span data-ttu-id="74f89-104">Le serveur est introuvable ou inaccessible.</span><span class="sxs-lookup"><span data-stu-id="74f89-104">The server was not found or was not accessible.</span></span> <span data-ttu-id="74f89-105">Vérifiez que le nom de l’instance est correct et que SQL Server est configuré pour autoriser les connexions à distance.</span><span class="sxs-lookup"><span data-stu-id="74f89-105">Verify that the instance name is correct and that SQL Server is configured to allow remote connections.</span></span> <span data-ttu-id="74f89-106">(fournisseur : interfaces réseau SQL, erreur : 26 - Erreur lors de la localisation du serveur/de l’instance spécifiés)&quot;</span><span class="sxs-lookup"><span data-stu-id="74f89-106">(provider: SQL Network Interfaces, error: 26 - Error Locating Server/Instance Specified)&quot;</span></span>

#### <a name="suggestion"></a><span data-ttu-id="74f89-107">Suggestion</span><span class="sxs-lookup"><span data-stu-id="74f89-107">Suggestion</span></span>

<span data-ttu-id="74f89-108">Ce problème a été résolu et le comportement précédent a été restauré dans .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="74f89-108">This issue has been addressed and the previous behavior restored in the .NET Framework 4.6.2.</span></span> <span data-ttu-id="74f89-109">Pour vous connecter à une base de données SQL Server qui se résout en <code>localhost</code>, effectuez une mise à niveau vers .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="74f89-109">To connect to a SQL Server database that resolves to <code>localhost</code>, upgrade to the .NET Framework 4.6.2.</span></span>

| <span data-ttu-id="74f89-110">Name</span><span class="sxs-lookup"><span data-stu-id="74f89-110">Name</span></span>    | <span data-ttu-id="74f89-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="74f89-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="74f89-112">Étendue</span><span class="sxs-lookup"><span data-stu-id="74f89-112">Scope</span></span>   |<span data-ttu-id="74f89-113">Secondaire</span><span class="sxs-lookup"><span data-stu-id="74f89-113">Minor</span></span>|
|<span data-ttu-id="74f89-114">Version</span><span class="sxs-lookup"><span data-stu-id="74f89-114">Version</span></span>|<span data-ttu-id="74f89-115">4,6</span><span class="sxs-lookup"><span data-stu-id="74f89-115">4.6</span></span>|
|<span data-ttu-id="74f89-116">Type</span><span class="sxs-lookup"><span data-stu-id="74f89-116">Type</span></span>|<span data-ttu-id="74f89-117">Runtime</span><span class="sxs-lookup"><span data-stu-id="74f89-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="74f89-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="74f89-118">Affected APIs</span></span>

<span data-ttu-id="74f89-119">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="74f89-119">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->

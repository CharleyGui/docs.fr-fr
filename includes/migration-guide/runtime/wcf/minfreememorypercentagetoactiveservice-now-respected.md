---
ms.openlocfilehash: b23182ad1da8208a69b78fc7bc872780d386a59a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496266"
---
### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a><span data-ttu-id="7bce4-101">Le paramètre MinFreeMemoryPercentageToActiveService est désormais pris en compte</span><span class="sxs-lookup"><span data-stu-id="7bce4-101">MinFreeMemoryPercentageToActiveService is now respected</span></span>

#### <a name="details"></a><span data-ttu-id="7bce4-102">Détails</span><span class="sxs-lookup"><span data-stu-id="7bce4-102">Details</span></span>

<span data-ttu-id="7bce4-103">Ce paramètre détermine la mémoire minimale devant être disponible sur le serveur avant l’activation d’un service WCF.</span><span class="sxs-lookup"><span data-stu-id="7bce4-103">This setting establishes the minimum memory that must be available on the server before a WCF service can be activated.</span></span> <span data-ttu-id="7bce4-104">Il a pour but de prévenir les exceptions <xref:System.OutOfMemoryException?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="7bce4-104">It is designed to prevent <xref:System.OutOfMemoryException?displayProperty=fullName> exceptions.</span></span> <span data-ttu-id="7bce4-105">Dans le .NET Framework 4.5, ce paramètre était sans effet.</span><span class="sxs-lookup"><span data-stu-id="7bce4-105">In the .NET Framework 4.5, this setting had no effect.</span></span> <span data-ttu-id="7bce4-106">Dans le .NET Framework 4.5.1, ce paramètre est pris en compte.</span><span class="sxs-lookup"><span data-stu-id="7bce4-106">In the .NET Framework 4.5.1, the setting is observed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7bce4-107">Suggestion</span><span class="sxs-lookup"><span data-stu-id="7bce4-107">Suggestion</span></span>

<span data-ttu-id="7bce4-108">Une exception se produit si la mémoire disponible sur le serveur web est inférieure au pourcentage défini par le paramètre de configuration.</span><span class="sxs-lookup"><span data-stu-id="7bce4-108">An exception occurs if the free memory available on the web server is less than the percentage defined by the configuration setting.</span></span> <span data-ttu-id="7bce4-109">Certains services WCF qui ont réussi à démarrer et à s'exécuter dans un environnement où la mémoire est limitée risquent à présent d'échouer.</span><span class="sxs-lookup"><span data-stu-id="7bce4-109">Some WCF services that successfully started and ran in a constrained memory environment may now fail.</span></span>

| <span data-ttu-id="7bce4-110">Name</span><span class="sxs-lookup"><span data-stu-id="7bce4-110">Name</span></span>    | <span data-ttu-id="7bce4-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="7bce4-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7bce4-112">Étendue</span><span class="sxs-lookup"><span data-stu-id="7bce4-112">Scope</span></span>   |<span data-ttu-id="7bce4-113">Secondaire</span><span class="sxs-lookup"><span data-stu-id="7bce4-113">Minor</span></span>|
|<span data-ttu-id="7bce4-114">Version</span><span class="sxs-lookup"><span data-stu-id="7bce4-114">Version</span></span>|<span data-ttu-id="7bce4-115">4.5.1</span><span class="sxs-lookup"><span data-stu-id="7bce4-115">4.5.1</span></span>|
|<span data-ttu-id="7bce4-116">Type</span><span class="sxs-lookup"><span data-stu-id="7bce4-116">Type</span></span>|<span data-ttu-id="7bce4-117">Runtime</span><span class="sxs-lookup"><span data-stu-id="7bce4-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="7bce4-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="7bce4-118">Affected APIs</span></span>

<span data-ttu-id="7bce4-119">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="7bce4-119">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->

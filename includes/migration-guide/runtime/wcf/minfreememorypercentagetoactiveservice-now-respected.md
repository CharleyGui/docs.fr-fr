---
ms.openlocfilehash: f8e5dee9e97956cea78b7c8ec999af1afe9ac66b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620051"
---
### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a><span data-ttu-id="66b71-101">Le paramètre MinFreeMemoryPercentageToActiveService est désormais pris en compte</span><span class="sxs-lookup"><span data-stu-id="66b71-101">MinFreeMemoryPercentageToActiveService is now respected</span></span>

#### <a name="details"></a><span data-ttu-id="66b71-102">Détails</span><span class="sxs-lookup"><span data-stu-id="66b71-102">Details</span></span>

<span data-ttu-id="66b71-103">Ce paramètre détermine la mémoire minimale devant être disponible sur le serveur avant l’activation d’un service WCF.</span><span class="sxs-lookup"><span data-stu-id="66b71-103">This setting establishes the minimum memory that must be available on the server before a WCF service can be activated.</span></span> <span data-ttu-id="66b71-104">Il a pour but de prévenir les exceptions <xref:System.OutOfMemoryException?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="66b71-104">It is designed to prevent <xref:System.OutOfMemoryException?displayProperty=fullName> exceptions.</span></span> <span data-ttu-id="66b71-105">Dans le .NET Framework 4.5, ce paramètre était sans effet.</span><span class="sxs-lookup"><span data-stu-id="66b71-105">In the .NET Framework 4.5, this setting had no effect.</span></span> <span data-ttu-id="66b71-106">Dans le .NET Framework 4.5.1, ce paramètre est pris en compte.</span><span class="sxs-lookup"><span data-stu-id="66b71-106">In the .NET Framework 4.5.1, the setting is observed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="66b71-107">Suggestion</span><span class="sxs-lookup"><span data-stu-id="66b71-107">Suggestion</span></span>

<span data-ttu-id="66b71-108">Une exception se produit si la mémoire disponible sur le serveur web est inférieure au pourcentage défini par le paramètre de configuration.</span><span class="sxs-lookup"><span data-stu-id="66b71-108">An exception occurs if the free memory available on the web server is less than the percentage defined by the configuration setting.</span></span> <span data-ttu-id="66b71-109">Certains services WCF qui ont réussi à démarrer et à s'exécuter dans un environnement où la mémoire est limitée risquent à présent d'échouer.</span><span class="sxs-lookup"><span data-stu-id="66b71-109">Some WCF services that successfully started and ran in a constrained memory environment may now fail.</span></span>

| <span data-ttu-id="66b71-110">Nom</span><span class="sxs-lookup"><span data-stu-id="66b71-110">Name</span></span>    | <span data-ttu-id="66b71-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="66b71-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="66b71-112">Étendue</span><span class="sxs-lookup"><span data-stu-id="66b71-112">Scope</span></span>   |<span data-ttu-id="66b71-113">Secondaire</span><span class="sxs-lookup"><span data-stu-id="66b71-113">Minor</span></span>|
|<span data-ttu-id="66b71-114">Version</span><span class="sxs-lookup"><span data-stu-id="66b71-114">Version</span></span>|<span data-ttu-id="66b71-115">4.5.1</span><span class="sxs-lookup"><span data-stu-id="66b71-115">4.5.1</span></span>|
|<span data-ttu-id="66b71-116">Type</span><span class="sxs-lookup"><span data-stu-id="66b71-116">Type</span></span>|<span data-ttu-id="66b71-117">Runtime</span><span class="sxs-lookup"><span data-stu-id="66b71-117">Runtime</span></span>|

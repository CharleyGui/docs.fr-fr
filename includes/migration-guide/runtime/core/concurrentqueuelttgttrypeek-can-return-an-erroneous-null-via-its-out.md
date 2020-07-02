---
ms.openlocfilehash: 02a15f6b9c02002b60c568b9e1d871af49744092
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622051"
---
### <a name="concurrentqueuelttgttrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a><span data-ttu-id="e5bd8-101">ConcurrentQueue&lt;T&gt;.TryPeek peut retourner une valeur Null erronée via son paramètre de sortie</span><span class="sxs-lookup"><span data-stu-id="e5bd8-101">ConcurrentQueue&lt;T&gt;.TryPeek can return an erroneous null via its out parameter</span></span>

#### <a name="details"></a><span data-ttu-id="e5bd8-102">Détails</span><span class="sxs-lookup"><span data-stu-id="e5bd8-102">Details</span></span>

<span data-ttu-id="e5bd8-103">Dans certains scénarios multithreads, <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=fullName> peut retourner la valeur true, mais renseigner le paramètre de sortie avec la valeur Null (au lieu de la valeur correcte).</span><span class="sxs-lookup"><span data-stu-id="e5bd8-103">In some multi-threaded scenarios, <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=fullName> can return true, but populate the out parameter with a null value (instead of the correct, peeked value).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e5bd8-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="e5bd8-104">Suggestion</span></span>

<span data-ttu-id="e5bd8-105">Ce problème a été résolu dans le .NET Framework 4.5.1.</span><span class="sxs-lookup"><span data-stu-id="e5bd8-105">This issue is fixed in the .NET Framework 4.5.1.</span></span> <span data-ttu-id="e5bd8-106">Pour résoudre votre problème, effectuez une mise niveau vers le .NET Framework 4.5.1.</span><span class="sxs-lookup"><span data-stu-id="e5bd8-106">Upgrading to that Framework will solve the issue.</span></span>

| <span data-ttu-id="e5bd8-107">Nom</span><span class="sxs-lookup"><span data-stu-id="e5bd8-107">Name</span></span>    | <span data-ttu-id="e5bd8-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="e5bd8-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e5bd8-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="e5bd8-109">Scope</span></span>   |<span data-ttu-id="e5bd8-110">Majeure</span><span class="sxs-lookup"><span data-stu-id="e5bd8-110">Major</span></span>|
|<span data-ttu-id="e5bd8-111">Version</span><span class="sxs-lookup"><span data-stu-id="e5bd8-111">Version</span></span>|<span data-ttu-id="e5bd8-112">4,5</span><span class="sxs-lookup"><span data-stu-id="e5bd8-112">4.5</span></span>|
|<span data-ttu-id="e5bd8-113">Type</span><span class="sxs-lookup"><span data-stu-id="e5bd8-113">Type</span></span>|<span data-ttu-id="e5bd8-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="e5bd8-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e5bd8-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="e5bd8-115">Affected APIs</span></span>

-<xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType></li></ul>|

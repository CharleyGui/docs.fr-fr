---
ms.openlocfilehash: 004e2d1883b631e88ab5e164b1120c3b081b7041
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497565"
---
### <a name="concurrentqueuelttgttrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a><span data-ttu-id="e4fe0-101">ConcurrentQueue&lt;T&gt;.TryPeek peut retourner une valeur Null erronée via son paramètre de sortie</span><span class="sxs-lookup"><span data-stu-id="e4fe0-101">ConcurrentQueue&lt;T&gt;.TryPeek can return an erroneous null via its out parameter</span></span>

#### <a name="details"></a><span data-ttu-id="e4fe0-102">Détails</span><span class="sxs-lookup"><span data-stu-id="e4fe0-102">Details</span></span>

<span data-ttu-id="e4fe0-103">Dans certains scénarios multithreads, <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=fullName> peut retourner la valeur true, mais renseigner le paramètre de sortie avec la valeur Null (au lieu de la valeur correcte).</span><span class="sxs-lookup"><span data-stu-id="e4fe0-103">In some multi-threaded scenarios, <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=fullName> can return true, but populate the out parameter with a null value (instead of the correct, peeked value).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e4fe0-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="e4fe0-104">Suggestion</span></span>

<span data-ttu-id="e4fe0-105">Ce problème a été résolu dans le .NET Framework 4.5.1.</span><span class="sxs-lookup"><span data-stu-id="e4fe0-105">This issue is fixed in the .NET Framework 4.5.1.</span></span> <span data-ttu-id="e4fe0-106">Pour résoudre votre problème, effectuez une mise niveau vers le .NET Framework 4.5.1.</span><span class="sxs-lookup"><span data-stu-id="e4fe0-106">Upgrading to that Framework will solve the issue.</span></span>

| <span data-ttu-id="e4fe0-107">Name</span><span class="sxs-lookup"><span data-stu-id="e4fe0-107">Name</span></span>    | <span data-ttu-id="e4fe0-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="e4fe0-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e4fe0-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="e4fe0-109">Scope</span></span>   |<span data-ttu-id="e4fe0-110">Majeure</span><span class="sxs-lookup"><span data-stu-id="e4fe0-110">Major</span></span>|
|<span data-ttu-id="e4fe0-111">Version</span><span class="sxs-lookup"><span data-stu-id="e4fe0-111">Version</span></span>|<span data-ttu-id="e4fe0-112">4,5</span><span class="sxs-lookup"><span data-stu-id="e4fe0-112">4.5</span></span>|
|<span data-ttu-id="e4fe0-113">Type</span><span class="sxs-lookup"><span data-stu-id="e4fe0-113">Type</span></span>|<span data-ttu-id="e4fe0-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="e4fe0-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="e4fe0-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="e4fe0-115">Affected APIs</span></span>

- <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``M:System.Collections.Concurrent.ConcurrentQueue`1.TryPeek(`0@)``

-->

---
ms.openlocfilehash: a8f51dfa1c82e3b166449d2432dfe8a9b96564b9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619950"
---
### <a name="blockingcollectionlttgttrytakefromany-does-not-throw-anymore"></a><span data-ttu-id="d2bb1-101">BlockingCollection&lt;T&gt;.TryTakeFromAny ne lève plus d’exceptions</span><span class="sxs-lookup"><span data-stu-id="d2bb1-101">BlockingCollection&lt;T&gt;.TryTakeFromAny does not throw anymore</span></span>

#### <a name="details"></a><span data-ttu-id="d2bb1-102">Détails</span><span class="sxs-lookup"><span data-stu-id="d2bb1-102">Details</span></span>

<span data-ttu-id="d2bb1-103">Si l’une des collections d’entrée est marquée comme terminée, <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> ne retourne plus -1, et <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> ne lève plus d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="d2bb1-103">If one of the input collections is marked completed, <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> no longer returns -1 and <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> no longer throws an exception.</span></span> <span data-ttu-id="d2bb1-104">Cette modification permet d'utiliser des collections lorsque l'une est vide ou terminée, alors que l'autre comporte toujours des éléments pouvant être récupérés.</span><span class="sxs-lookup"><span data-stu-id="d2bb1-104">This change makes it possible to work with collections when one of the collections is either empty or completed, but the other collection still has items that can be retrieved.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d2bb1-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="d2bb1-105">Suggestion</span></span>

<span data-ttu-id="d2bb1-106">Si vous utilisiez TryTakeFromAny pour retourner -1 ou TakeFromAny pour lever des exceptions à des fins de flux de contrôle, dans le contexte d’une collection bloquante terminée, ce code doit à présent être modifié pour utiliser <code>.Any(b =&gt; b.IsCompleted)</code> de manière à détecter cette condition.</span><span class="sxs-lookup"><span data-stu-id="d2bb1-106">If TryTakeFromAny returning -1 or TakeFromAny throwing were used for control-flow purposes in cases of a blocking collection being completed, such code should now be changed to use <code>.Any(b =&gt; b.IsCompleted)</code> to detect that condition.</span></span>

| <span data-ttu-id="d2bb1-107">Nom</span><span class="sxs-lookup"><span data-stu-id="d2bb1-107">Name</span></span>    | <span data-ttu-id="d2bb1-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="d2bb1-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d2bb1-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="d2bb1-109">Scope</span></span>   |<span data-ttu-id="d2bb1-110">Secondaire</span><span class="sxs-lookup"><span data-stu-id="d2bb1-110">Minor</span></span>|
|<span data-ttu-id="d2bb1-111">Version</span><span class="sxs-lookup"><span data-stu-id="d2bb1-111">Version</span></span>|<span data-ttu-id="d2bb1-112">4,5</span><span class="sxs-lookup"><span data-stu-id="d2bb1-112">4.5</span></span>|
|<span data-ttu-id="d2bb1-113">Type</span><span class="sxs-lookup"><span data-stu-id="d2bb1-113">Type</span></span>|<span data-ttu-id="d2bb1-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="d2bb1-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d2bb1-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="d2bb1-115">Affected APIs</span></span>

-<xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.TimeSpan)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.TimeSpan)?displayProperty=nameWithType></li></ul>|

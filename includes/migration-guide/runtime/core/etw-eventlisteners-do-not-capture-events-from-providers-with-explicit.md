---
ms.openlocfilehash: 5a96b40e5e0df6a47415acecab410444a713632b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496100"
---
### <a name="etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a><span data-ttu-id="cd694-101">Les EventListeners ETW ne capturent pas les événements provenant de fournisseurs avec des mots clés explicites (comme le fournisseur TPL)</span><span class="sxs-lookup"><span data-stu-id="cd694-101">ETW EventListeners do not capture events from providers with explicit keywords (like the TPL provider)</span></span>

#### <a name="details"></a><span data-ttu-id="cd694-102">Détails</span><span class="sxs-lookup"><span data-stu-id="cd694-102">Details</span></span>

<span data-ttu-id="cd694-103">Les EventListeners ETW avec un masque de mot clé vide ne capturent pas correctement les événements provenant de fournisseurs ayant des mots clés explicites.</span><span class="sxs-lookup"><span data-stu-id="cd694-103">ETW EventListeners with a blank keyword mask do not properly capture events from providers with explicit keywords.</span></span> <span data-ttu-id="cd694-104">Dans le .NET Framework 4.5, le fournisseur TPL fournissait des mots clés explicites et provoquait ce problème.</span><span class="sxs-lookup"><span data-stu-id="cd694-104">In the .NET Framework 4.5, the TPL provider began providing explicit keywords and triggered this issue.</span></span> <span data-ttu-id="cd694-105">Dans le .NET Framework 4.6, les EventListeners ont été mis à jour pour ne plus causer ce problème.</span><span class="sxs-lookup"><span data-stu-id="cd694-105">In the .NET Framework 4.6, EventListeners have been updated to no longer have this issue.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="cd694-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="cd694-106">Suggestion</span></span>

<span data-ttu-id="cd694-107">Pour contourner ce problème, remplacez les appels à <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> par des appels à la surcharge EnableEvents qui spécifie explicitement le masque &quot;tous les mots clés&quot; à utiliser : <code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code>. Étant donné que ce problème a été résolu dans .NET Framework 4.6, vous pouvez également effectuer la mise à niveau vers cette version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cd694-107">To work around this problem, replace calls to <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> with calls to the EnableEvents overload that explicitly specifies the &quot;any keywords&quot; mask to use: <code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code>.Alternatively, this issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="cd694-108">Name</span><span class="sxs-lookup"><span data-stu-id="cd694-108">Name</span></span>    | <span data-ttu-id="cd694-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="cd694-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="cd694-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="cd694-110">Scope</span></span>   |<span data-ttu-id="cd694-111">Edge</span><span class="sxs-lookup"><span data-stu-id="cd694-111">Edge</span></span>|
|<span data-ttu-id="cd694-112">Version</span><span class="sxs-lookup"><span data-stu-id="cd694-112">Version</span></span>|<span data-ttu-id="cd694-113">4,5</span><span class="sxs-lookup"><span data-stu-id="cd694-113">4.5</span></span>|
|<span data-ttu-id="cd694-114">Type</span><span class="sxs-lookup"><span data-stu-id="cd694-114">Type</span></span>|<span data-ttu-id="cd694-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="cd694-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="cd694-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="cd694-116">Affected APIs</span></span>

- <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)`

-->

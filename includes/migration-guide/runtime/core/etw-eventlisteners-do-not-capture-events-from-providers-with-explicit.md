---
ms.openlocfilehash: 7d50962b518c15875a5f1a82f5b89ab87a1db02e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619973"
---
### <a name="etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a><span data-ttu-id="4edfd-101">Les EventListeners ETW ne capturent pas les événements provenant de fournisseurs avec des mots clés explicites (comme le fournisseur TPL)</span><span class="sxs-lookup"><span data-stu-id="4edfd-101">ETW EventListeners do not capture events from providers with explicit keywords (like the TPL provider)</span></span>

#### <a name="details"></a><span data-ttu-id="4edfd-102">Détails</span><span class="sxs-lookup"><span data-stu-id="4edfd-102">Details</span></span>

<span data-ttu-id="4edfd-103">Les EventListeners ETW avec un masque de mot clé vide ne capturent pas correctement les événements provenant de fournisseurs ayant des mots clés explicites.</span><span class="sxs-lookup"><span data-stu-id="4edfd-103">ETW EventListeners with a blank keyword mask do not properly capture events from providers with explicit keywords.</span></span> <span data-ttu-id="4edfd-104">Dans le .NET Framework 4.5, le fournisseur TPL fournissait des mots clés explicites et provoquait ce problème.</span><span class="sxs-lookup"><span data-stu-id="4edfd-104">In the .NET Framework 4.5, the TPL provider began providing explicit keywords and triggered this issue.</span></span> <span data-ttu-id="4edfd-105">Dans le .NET Framework 4.6, les EventListeners ont été mis à jour pour ne plus causer ce problème.</span><span class="sxs-lookup"><span data-stu-id="4edfd-105">In the .NET Framework 4.6, EventListeners have been updated to no longer have this issue.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4edfd-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="4edfd-106">Suggestion</span></span>

<span data-ttu-id="4edfd-107">Pour contourner ce problème, remplacez les appels à <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> par des appels à la surcharge EnableEvents qui spécifie explicitement le masque &quot;tous les mots clés&quot; à utiliser : <code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code>. Étant donné que ce problème a été résolu dans .NET Framework 4.6, vous pouvez également effectuer la mise à niveau vers cette version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4edfd-107">To work around this problem, replace calls to <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> with calls to the EnableEvents overload that explicitly specifies the &quot;any keywords&quot; mask to use: <code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code>.Alternatively, this issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="4edfd-108">Nom</span><span class="sxs-lookup"><span data-stu-id="4edfd-108">Name</span></span>    | <span data-ttu-id="4edfd-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="4edfd-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4edfd-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="4edfd-110">Scope</span></span>   |<span data-ttu-id="4edfd-111">Edge</span><span class="sxs-lookup"><span data-stu-id="4edfd-111">Edge</span></span>|
|<span data-ttu-id="4edfd-112">Version</span><span class="sxs-lookup"><span data-stu-id="4edfd-112">Version</span></span>|<span data-ttu-id="4edfd-113">4,5</span><span class="sxs-lookup"><span data-stu-id="4edfd-113">4.5</span></span>|
|<span data-ttu-id="4edfd-114">Type</span><span class="sxs-lookup"><span data-stu-id="4edfd-114">Type</span></span>|<span data-ttu-id="4edfd-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="4edfd-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4edfd-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="4edfd-116">Affected APIs</span></span>

-<xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li></ul>|

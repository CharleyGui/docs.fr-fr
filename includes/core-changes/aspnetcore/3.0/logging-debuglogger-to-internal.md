---
ms.openlocfilehash: 958dede03e1c15f69f4ee676f13713ff43c29e96
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394101"
---
### <a name="logging-debuglogger-class-made-internal"></a><span data-ttu-id="d1fa6-101">Journalisation : classe DebugLogger rendue interne</span><span class="sxs-lookup"><span data-stu-id="d1fa6-101">Logging: DebugLogger class made internal</span></span>

<span data-ttu-id="d1fa6-102">Avant ASP.NET Core 3,0, `DebugLogger`le modificateur d’accès était `public`.</span><span class="sxs-lookup"><span data-stu-id="d1fa6-102">Prior to ASP.NET Core 3.0, `DebugLogger`'s access modifier was `public`.</span></span> <span data-ttu-id="d1fa6-103">Dans ASP.NET Core 3,0, le modificateur d’accès a `internal`la valeur.</span><span class="sxs-lookup"><span data-stu-id="d1fa6-103">In ASP.NET Core 3.0, the access modifier changed to `internal`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d1fa6-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="d1fa6-104">Version introduced</span></span>

<span data-ttu-id="d1fa6-105">3.0</span><span class="sxs-lookup"><span data-stu-id="d1fa6-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d1fa6-106">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="d1fa6-106">Reason for change</span></span>

<span data-ttu-id="d1fa6-107">La modification est apportée à :</span><span class="sxs-lookup"><span data-stu-id="d1fa6-107">The change is being made to:</span></span>

* <span data-ttu-id="d1fa6-108">Garantissez la cohérence avec d’autres implémentations `ConsoleLogger`d’enregistreur d’événements telles que.</span><span class="sxs-lookup"><span data-stu-id="d1fa6-108">Enforce consistency with other logger implementations such as `ConsoleLogger`.</span></span>
* <span data-ttu-id="d1fa6-109">Réduisez la surface de l’API.</span><span class="sxs-lookup"><span data-stu-id="d1fa6-109">Reduce the API surface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d1fa6-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="d1fa6-110">Recommended action</span></span>

<span data-ttu-id="d1fa6-111">Utilisez la <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` méthode d’extension pour activer la journalisation du débogage.</span><span class="sxs-lookup"><span data-stu-id="d1fa6-111">Use the <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` extension method to enable debug logging.</span></span> <span data-ttu-id="d1fa6-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider>est également toujours `public` dans le cas où le service doit être inscrit manuellement.</span><span class="sxs-lookup"><span data-stu-id="d1fa6-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> is also still `public` in the event the service needs to be registered manually.</span></span>

#### <a name="category"></a><span data-ttu-id="d1fa6-113">Category</span><span class="sxs-lookup"><span data-stu-id="d1fa6-113">Category</span></span>

<span data-ttu-id="d1fa6-114">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d1fa6-114">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d1fa6-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="d1fa6-115">Affected APIs</span></span>

<xref:Microsoft.Extensions.Logging.Debug.DebugLogger?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.Extensions.Logging.Debug.DebugLogger`

-->

---
ms.openlocfilehash: 958dede03e1c15f69f4ee676f13713ff43c29e96
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394101"
---
### <a name="logging-debuglogger-class-made-internal"></a><span data-ttu-id="762f6-101">Journalisation : classe DebugLogger rendue interne</span><span class="sxs-lookup"><span data-stu-id="762f6-101">Logging: DebugLogger class made internal</span></span>

<span data-ttu-id="762f6-102">Avant le ASP.NET Core 3,0, le modificateur d’accès de `DebugLogger` était `public`.</span><span class="sxs-lookup"><span data-stu-id="762f6-102">Prior to ASP.NET Core 3.0, `DebugLogger`'s access modifier was `public`.</span></span> <span data-ttu-id="762f6-103">Dans ASP.NET Core 3,0, le modificateur d’accès est passé à `internal`.</span><span class="sxs-lookup"><span data-stu-id="762f6-103">In ASP.NET Core 3.0, the access modifier changed to `internal`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="762f6-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="762f6-104">Version introduced</span></span>

<span data-ttu-id="762f6-105">3,0</span><span class="sxs-lookup"><span data-stu-id="762f6-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="762f6-106">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="762f6-106">Reason for change</span></span>

<span data-ttu-id="762f6-107">La modification est apportée à :</span><span class="sxs-lookup"><span data-stu-id="762f6-107">The change is being made to:</span></span>

* <span data-ttu-id="762f6-108">Garantissez la cohérence avec d’autres implémentations d’enregistreur d’événements telles que `ConsoleLogger`.</span><span class="sxs-lookup"><span data-stu-id="762f6-108">Enforce consistency with other logger implementations such as `ConsoleLogger`.</span></span>
* <span data-ttu-id="762f6-109">Réduisez la surface de l’API.</span><span class="sxs-lookup"><span data-stu-id="762f6-109">Reduce the API surface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="762f6-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="762f6-110">Recommended action</span></span>

<span data-ttu-id="762f6-111">Utilisez la méthode d’extension <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` pour activer la journalisation du débogage.</span><span class="sxs-lookup"><span data-stu-id="762f6-111">Use the <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` extension method to enable debug logging.</span></span> <span data-ttu-id="762f6-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> est également `public` dans le cas où le service doit être inscrit manuellement.</span><span class="sxs-lookup"><span data-stu-id="762f6-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> is also still `public` in the event the service needs to be registered manually.</span></span>

#### <a name="category"></a><span data-ttu-id="762f6-113">Category</span><span class="sxs-lookup"><span data-stu-id="762f6-113">Category</span></span>

<span data-ttu-id="762f6-114">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="762f6-114">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="762f6-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="762f6-115">Affected APIs</span></span>

<xref:Microsoft.Extensions.Logging.Debug.DebugLogger?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.Extensions.Logging.Debug.DebugLogger`

-->

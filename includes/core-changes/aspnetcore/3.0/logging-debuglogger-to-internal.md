---
ms.openlocfilehash: 958dede03e1c15f69f4ee676f13713ff43c29e96
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394101"
---
### <a name="logging-debuglogger-class-made-internal"></a><span data-ttu-id="18ac9-101">Enregistrement: DebugLogger classe rendue interne</span><span class="sxs-lookup"><span data-stu-id="18ac9-101">Logging: DebugLogger class made internal</span></span>

<span data-ttu-id="18ac9-102">Avant ASP.NET Core 3.0, `DebugLogger`« le modificateur d’accès était `public`.</span><span class="sxs-lookup"><span data-stu-id="18ac9-102">Prior to ASP.NET Core 3.0, `DebugLogger`'s access modifier was `public`.</span></span> <span data-ttu-id="18ac9-103">Dans ASP.NET Core 3.0, le modificateur `internal`d’accès a changé pour .</span><span class="sxs-lookup"><span data-stu-id="18ac9-103">In ASP.NET Core 3.0, the access modifier changed to `internal`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="18ac9-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="18ac9-104">Version introduced</span></span>

<span data-ttu-id="18ac9-105">3.0</span><span class="sxs-lookup"><span data-stu-id="18ac9-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="18ac9-106">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="18ac9-106">Reason for change</span></span>

<span data-ttu-id="18ac9-107">Le changement est apporté à :</span><span class="sxs-lookup"><span data-stu-id="18ac9-107">The change is being made to:</span></span>

* <span data-ttu-id="18ac9-108">Appliquer la cohérence avec d’autres implémentations d’enregistreur tels que `ConsoleLogger`.</span><span class="sxs-lookup"><span data-stu-id="18ac9-108">Enforce consistency with other logger implementations such as `ConsoleLogger`.</span></span>
* <span data-ttu-id="18ac9-109">Réduire la surface de l’API.</span><span class="sxs-lookup"><span data-stu-id="18ac9-109">Reduce the API surface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="18ac9-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="18ac9-110">Recommended action</span></span>

<span data-ttu-id="18ac9-111">Utilisez <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` la méthode d’extension pour permettre l’exploitation forestière de débogé.</span><span class="sxs-lookup"><span data-stu-id="18ac9-111">Use the <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` extension method to enable debug logging.</span></span> <span data-ttu-id="18ac9-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider>est également `public` toujours dans le cas où le service doit être enregistré manuellement.</span><span class="sxs-lookup"><span data-stu-id="18ac9-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> is also still `public` in the event the service needs to be registered manually.</span></span>

#### <a name="category"></a><span data-ttu-id="18ac9-113">Category</span><span class="sxs-lookup"><span data-stu-id="18ac9-113">Category</span></span>

<span data-ttu-id="18ac9-114">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="18ac9-114">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="18ac9-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="18ac9-115">Affected APIs</span></span>

<xref:Microsoft.Extensions.Logging.Debug.DebugLogger?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.Extensions.Logging.Debug.DebugLogger`

-->

---
ms.openlocfilehash: 9d138f79fcede4acac837f8d7793aa343ced737c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78290754"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a><span data-ttu-id="8c79d-101">HTTP: DefaultHttpContext extétabilité supprimée</span><span class="sxs-lookup"><span data-stu-id="8c79d-101">HTTP: DefaultHttpContext extensibility removed</span></span>

<span data-ttu-id="8c79d-102">Dans le cadre de ASP.NET’amélioration des performances de Core 3.0, l’extéabilité de `DefaultHttpContext` a été supprimée.</span><span class="sxs-lookup"><span data-stu-id="8c79d-102">As part of ASP.NET Core 3.0 performance improvements, the extensibility of `DefaultHttpContext` was removed.</span></span> <span data-ttu-id="8c79d-103">La classe `sealed`est maintenant .</span><span class="sxs-lookup"><span data-stu-id="8c79d-103">The class is now `sealed`.</span></span> <span data-ttu-id="8c79d-104">Pour plus d’informations, voir [dotnet/aspnetcore 6504](https://github.com/dotnet/aspnetcore/pull/6504).</span><span class="sxs-lookup"><span data-stu-id="8c79d-104">For more information, see [dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504).</span></span>

<span data-ttu-id="8c79d-105">Si vos tests `Mock<DefaultHttpContext>`unitaires utilisent, utilisez `Mock<HttpContext>` ou `new DefaultHttpContext()` à la place.</span><span class="sxs-lookup"><span data-stu-id="8c79d-105">If your unit tests use `Mock<DefaultHttpContext>`, use `Mock<HttpContext>` or `new DefaultHttpContext()` instead.</span></span>

<span data-ttu-id="8c79d-106">Pour discussion, voir [dotnet/aspnetcore 6534](https://github.com/dotnet/aspnetcore/issues/6534).</span><span class="sxs-lookup"><span data-stu-id="8c79d-106">For discussion, see [dotnet/aspnetcore#6534](https://github.com/dotnet/aspnetcore/issues/6534).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8c79d-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="8c79d-107">Version introduced</span></span>

<span data-ttu-id="8c79d-108">3.0</span><span class="sxs-lookup"><span data-stu-id="8c79d-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="8c79d-109">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="8c79d-109">Old behavior</span></span>

<span data-ttu-id="8c79d-110">Les classes `DefaultHttpContext`peuvent dériver de .</span><span class="sxs-lookup"><span data-stu-id="8c79d-110">Classes can derive from `DefaultHttpContext`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="8c79d-111">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="8c79d-111">New behavior</span></span>

<span data-ttu-id="8c79d-112">Les cours ne `DefaultHttpContext`peuvent pas dériver de .</span><span class="sxs-lookup"><span data-stu-id="8c79d-112">Classes can't derive from `DefaultHttpContext`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="8c79d-113">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="8c79d-113">Reason for change</span></span>

<span data-ttu-id="8c79d-114">L’extéabilité a été initialement fournie `HttpContext`pour permettre la mise en commun de la , mais il a introduit une complexité inutile et entravé d’autres optimisations.</span><span class="sxs-lookup"><span data-stu-id="8c79d-114">The extensibility was provided initially to allow pooling of the `HttpContext`, but it introduced unnecessary complexity and impeded other optimizations.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8c79d-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="8c79d-115">Recommended action</span></span>

<span data-ttu-id="8c79d-116">Si vous utilisez `Mock<DefaultHttpContext>` dans vos tests `Mock<HttpContext>` unitaires, commencez à utiliser à la place.</span><span class="sxs-lookup"><span data-stu-id="8c79d-116">If you're using `Mock<DefaultHttpContext>` in your unit tests, begin using `Mock<HttpContext>` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="8c79d-117">Category</span><span class="sxs-lookup"><span data-stu-id="8c79d-117">Category</span></span>

<span data-ttu-id="8c79d-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8c79d-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8c79d-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="8c79d-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->

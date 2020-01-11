---
ms.openlocfilehash: 1b4b0aba3ea24682ae972bf283ac387692c83781
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901583"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a><span data-ttu-id="da953-101">HTTP : extensibilité de DefaultHttpContext supprimée</span><span class="sxs-lookup"><span data-stu-id="da953-101">HTTP: DefaultHttpContext extensibility removed</span></span>

<span data-ttu-id="da953-102">Dans le cadre de l’amélioration des performances de ASP.NET Core 3,0, l’extensibilité de `DefaultHttpContext` a été supprimée.</span><span class="sxs-lookup"><span data-stu-id="da953-102">As part of ASP.NET Core 3.0 performance improvements, the extensibility of `DefaultHttpContext` was removed.</span></span> <span data-ttu-id="da953-103">La classe est désormais `sealed`.</span><span class="sxs-lookup"><span data-stu-id="da953-103">The class is now `sealed`.</span></span> <span data-ttu-id="da953-104">Pour plus d’informations, consultez [dotnet/aspnetcore # 6504](https://github.com/dotnet/aspnetcore/pull/6504).</span><span class="sxs-lookup"><span data-stu-id="da953-104">For more information, see [dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504).</span></span>

<span data-ttu-id="da953-105">Si vos tests unitaires utilisent `Mock<DefaultHttpContext>`, utilisez `Mock<HttpContext>` à la place.</span><span class="sxs-lookup"><span data-stu-id="da953-105">If your unit tests use `Mock<DefaultHttpContext>`, use `Mock<HttpContext>` instead.</span></span>

<span data-ttu-id="da953-106">Pour plus d’informations, consultez [dotnet/aspnetcore # 6534](https://github.com/dotnet/aspnetcore/issues/6534).</span><span class="sxs-lookup"><span data-stu-id="da953-106">For discussion, see [dotnet/aspnetcore#6534](https://github.com/dotnet/aspnetcore/issues/6534).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="da953-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="da953-107">Version introduced</span></span>

<span data-ttu-id="da953-108">3.0</span><span class="sxs-lookup"><span data-stu-id="da953-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="da953-109">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="da953-109">Old behavior</span></span>

<span data-ttu-id="da953-110">Les classes peuvent dériver de `DefaultHttpContext`.</span><span class="sxs-lookup"><span data-stu-id="da953-110">Classes can derive from `DefaultHttpContext`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="da953-111">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="da953-111">New behavior</span></span>

<span data-ttu-id="da953-112">Les classes ne peuvent pas dériver de `DefaultHttpContext`.</span><span class="sxs-lookup"><span data-stu-id="da953-112">Classes can't derive from `DefaultHttpContext`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="da953-113">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="da953-113">Reason for change</span></span>

<span data-ttu-id="da953-114">L’extensibilité a été fournie initialement pour permettre le regroupement des `HttpContext`, mais elle a introduit une complexité inutile et empêchait d’autres optimisations.</span><span class="sxs-lookup"><span data-stu-id="da953-114">The extensibility was provided initially to allow pooling of the `HttpContext`, but it introduced unnecessary complexity and impeded other optimizations.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="da953-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="da953-115">Recommended action</span></span>

<span data-ttu-id="da953-116">Si vous utilisez `Mock<DefaultHttpContext>` dans vos tests unitaires, commencez à utiliser `Mock<HttpContext>` à la place.</span><span class="sxs-lookup"><span data-stu-id="da953-116">If you're using `Mock<DefaultHttpContext>` in your unit tests, begin using `Mock<HttpContext>` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="da953-117">Catégorie</span><span class="sxs-lookup"><span data-stu-id="da953-117">Category</span></span>

<span data-ttu-id="da953-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="da953-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="da953-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="da953-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->

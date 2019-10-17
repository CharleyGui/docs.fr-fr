---
ms.openlocfilehash: 177617569a93e09f4c2a05acc21dce362edd58bc
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394075"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a><span data-ttu-id="afa8c-101">HTTP : extensibilité de DefaultHttpContext supprimée</span><span class="sxs-lookup"><span data-stu-id="afa8c-101">HTTP: DefaultHttpContext extensibility removed</span></span>

<span data-ttu-id="afa8c-102">Dans le cadre de l’amélioration des performances de ASP.NET Core 3,0, l’extensibilité de `DefaultHttpContext` a été supprimée.</span><span class="sxs-lookup"><span data-stu-id="afa8c-102">As part of ASP.NET Core 3.0 performance improvements, the extensibility of `DefaultHttpContext` was removed.</span></span> <span data-ttu-id="afa8c-103">La classe est maintenant `sealed`.</span><span class="sxs-lookup"><span data-stu-id="afa8c-103">The class is now `sealed`.</span></span> <span data-ttu-id="afa8c-104">Pour plus d’informations, consultez [ASPNET/AspNetCore # 6504](https://github.com/aspnet/AspNetCore/pull/6504).</span><span class="sxs-lookup"><span data-stu-id="afa8c-104">For more information, see [aspnet/AspNetCore#6504](https://github.com/aspnet/AspNetCore/pull/6504).</span></span>

<span data-ttu-id="afa8c-105">Si vos tests unitaires utilisent `Mock<DefaultHttpContext>`, utilisez à la place `Mock<HttpContext>`.</span><span class="sxs-lookup"><span data-stu-id="afa8c-105">If your unit tests use `Mock<DefaultHttpContext>`, use `Mock<HttpContext>` instead.</span></span> 

<span data-ttu-id="afa8c-106">Pour plus d’informations, consultez [ASPNET/AspNetCore # 6534](https://github.com/aspnet/AspNetCore/issues/6534).</span><span class="sxs-lookup"><span data-stu-id="afa8c-106">For discussion, see [aspnet/AspNetCore#6534](https://github.com/aspnet/AspNetCore/issues/6534).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="afa8c-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="afa8c-107">Version introduced</span></span>

<span data-ttu-id="afa8c-108">3,0</span><span class="sxs-lookup"><span data-stu-id="afa8c-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="afa8c-109">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="afa8c-109">Old behavior</span></span>

<span data-ttu-id="afa8c-110">Les classes peuvent dériver de `DefaultHttpContext`.</span><span class="sxs-lookup"><span data-stu-id="afa8c-110">Classes can derive from `DefaultHttpContext`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="afa8c-111">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="afa8c-111">New behavior</span></span>

<span data-ttu-id="afa8c-112">Les classes ne peuvent pas dériver de `DefaultHttpContext`.</span><span class="sxs-lookup"><span data-stu-id="afa8c-112">Classes can't derive from `DefaultHttpContext`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="afa8c-113">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="afa8c-113">Reason for change</span></span>

<span data-ttu-id="afa8c-114">L’extensibilité a été fournie initialement pour permettre le regroupement des `HttpContext`, mais elle a introduit une complexité inutile et a entravé d’autres optimisations.</span><span class="sxs-lookup"><span data-stu-id="afa8c-114">The extensibility was provided initially to allow pooling of the `HttpContext`, but it introduced unnecessary complexity and impeded other optimizations.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="afa8c-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="afa8c-115">Recommended action</span></span>

<span data-ttu-id="afa8c-116">Si vous utilisez `Mock<DefaultHttpContext>` dans vos tests unitaires, commencez à utiliser `Mock<HttpContext>` à la place.</span><span class="sxs-lookup"><span data-stu-id="afa8c-116">If you're using `Mock<DefaultHttpContext>` in your unit tests, begin using `Mock<HttpContext>` instead.</span></span> 

#### <a name="category"></a><span data-ttu-id="afa8c-117">Category</span><span class="sxs-lookup"><span data-stu-id="afa8c-117">Category</span></span>

<span data-ttu-id="afa8c-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="afa8c-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="afa8c-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="afa8c-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->

---
ms.openlocfilehash: ab7c097f6b65d539117e5a6ef38eb67b24695a32
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394026"
---
### <a name="http-synchronous-io-disabled-in-all-servers"></a><span data-ttu-id="2070c-101">HTTP : e/s synchrone désactivée sur tous les serveurs</span><span class="sxs-lookup"><span data-stu-id="2070c-101">HTTP: Synchronous IO disabled in all servers</span></span>

<span data-ttu-id="2070c-102">À compter de ASP.NET Core 3,0, les opérations de serveur synchrones sont désactivées par défaut.</span><span class="sxs-lookup"><span data-stu-id="2070c-102">Starting with ASP.NET Core 3.0, synchronous server operations are disabled by default.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2070c-103">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="2070c-103">Change description</span></span>

<span data-ttu-id="2070c-104">`AllowSynchronousIO` est une option dans chaque serveur qui active ou désactive les API d’e/s synchrones comme `HttpRequest.Body.Read`, `HttpResponse.Body.Write` et `Stream.Flush`.</span><span class="sxs-lookup"><span data-stu-id="2070c-104">`AllowSynchronousIO` is an option in each server that enables or disables synchronous IO APIs like `HttpRequest.Body.Read`, `HttpResponse.Body.Write`, and `Stream.Flush`.</span></span> <span data-ttu-id="2070c-105">Ces API ont longtemps été une source d’insuffisance de thread et de blocages d’application.</span><span class="sxs-lookup"><span data-stu-id="2070c-105">These APIs have long been a source of thread starvation and app hangs.</span></span> <span data-ttu-id="2070c-106">À partir de ASP.NET Core 3,0 Preview 3, ces opérations synchrones sont désactivées par défaut.</span><span class="sxs-lookup"><span data-stu-id="2070c-106">Starting in ASP.NET Core 3.0 Preview 3, these synchronous operations are disabled by default.</span></span>

<span data-ttu-id="2070c-107">Serveurs affectés :</span><span class="sxs-lookup"><span data-stu-id="2070c-107">Affected servers:</span></span>

- <span data-ttu-id="2070c-108">Kestrel</span><span class="sxs-lookup"><span data-stu-id="2070c-108">Kestrel</span></span>
- <span data-ttu-id="2070c-109">HttpSys</span><span class="sxs-lookup"><span data-stu-id="2070c-109">HttpSys</span></span>
- <span data-ttu-id="2070c-110">IIS in-process</span><span class="sxs-lookup"><span data-stu-id="2070c-110">IIS in-process</span></span>
- <span data-ttu-id="2070c-111">TestServer</span><span class="sxs-lookup"><span data-stu-id="2070c-111">TestServer</span></span>

<span data-ttu-id="2070c-112">Des erreurs similaires à celles-ci sont attendues :</span><span class="sxs-lookup"><span data-stu-id="2070c-112">Expect errors similar to:</span></span>

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

<span data-ttu-id="2070c-113">Chaque serveur a une option `AllowSynchronousIO` qui contrôle ce comportement et la valeur par défaut pour tous les éléments est désormais `false`.</span><span class="sxs-lookup"><span data-stu-id="2070c-113">Each server has an `AllowSynchronousIO` option that controls this behavior and the default for all of them is now `false`.</span></span>

<span data-ttu-id="2070c-114">Le comportement peut également être remplacé en fonction de la demande comme une atténuation temporaire.</span><span class="sxs-lookup"><span data-stu-id="2070c-114">The behavior can also be overridden on a per-request basis as a temporary mitigation.</span></span> <span data-ttu-id="2070c-115">Exemple :</span><span class="sxs-lookup"><span data-stu-id="2070c-115">For example:</span></span>

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

<span data-ttu-id="2070c-116">Si vous rencontrez des problèmes avec un `TextWriter` ou un autre flux appelant une API synchrone dans `Dispose`, appelez plutôt la nouvelle API `DisposeAsync`.</span><span class="sxs-lookup"><span data-stu-id="2070c-116">If you have trouble with a `TextWriter` or another stream calling a synchronous API in `Dispose`, call the new `DisposeAsync` API instead.</span></span>

<span data-ttu-id="2070c-117">Pour plus d’informations, consultez [ASPNET/AspNetCore # 7644](https://github.com/aspnet/AspNetCore/issues/7644).</span><span class="sxs-lookup"><span data-stu-id="2070c-117">For discussion, see [aspnet/AspNetCore#7644](https://github.com/aspnet/AspNetCore/issues/7644).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2070c-118">Version introduite</span><span class="sxs-lookup"><span data-stu-id="2070c-118">Version introduced</span></span>

<span data-ttu-id="2070c-119">3,0</span><span class="sxs-lookup"><span data-stu-id="2070c-119">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="2070c-120">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="2070c-120">Old behavior</span></span>

<span data-ttu-id="2070c-121">`HttpRequest.Body.Read`, `HttpResponse.Body.Write` et `Stream.Flush` étaient autorisés par défaut.</span><span class="sxs-lookup"><span data-stu-id="2070c-121">`HttpRequest.Body.Read`, `HttpResponse.Body.Write`, and `Stream.Flush` were allowed by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="2070c-122">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="2070c-122">New behavior</span></span>

<span data-ttu-id="2070c-123">Ces API synchrones ne sont pas autorisées par défaut :</span><span class="sxs-lookup"><span data-stu-id="2070c-123">These synchronous APIs are disallowed by default:</span></span> 

<span data-ttu-id="2070c-124">Des erreurs similaires à celles-ci sont attendues :</span><span class="sxs-lookup"><span data-stu-id="2070c-124">Expect errors similar to:</span></span>

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

#### <a name="reason-for-change"></a><span data-ttu-id="2070c-125">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="2070c-125">Reason for change</span></span>

<span data-ttu-id="2070c-126">Ces API synchrones ont longtemps été une source de privation de thread et des blocages d’application.</span><span class="sxs-lookup"><span data-stu-id="2070c-126">These synchronous APIs have long been a source of thread starvation and app hangs.</span></span> <span data-ttu-id="2070c-127">À partir de ASP.NET Core 3,0 Preview 3, les opérations synchrones sont désactivées par défaut.</span><span class="sxs-lookup"><span data-stu-id="2070c-127">Starting in ASP.NET Core 3.0 Preview 3, the synchronous operations are disabled by default.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2070c-128">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="2070c-128">Recommended action</span></span>

<span data-ttu-id="2070c-129">Utilisez les versions asynchrones des méthodes.</span><span class="sxs-lookup"><span data-stu-id="2070c-129">Use the asynchronous versions of the methods.</span></span> <span data-ttu-id="2070c-130">Le comportement peut également être remplacé en fonction de la demande comme une atténuation temporaire.</span><span class="sxs-lookup"><span data-stu-id="2070c-130">The behavior can also be overridden on a per-request basis as a temporary mitigation.</span></span>

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

#### <a name="category"></a><span data-ttu-id="2070c-131">Category</span><span class="sxs-lookup"><span data-stu-id="2070c-131">Category</span></span>

<span data-ttu-id="2070c-132">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2070c-132">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2070c-133">API affectées</span><span class="sxs-lookup"><span data-stu-id="2070c-133">Affected APIs</span></span>

- <xref:System.IO.Stream.Flush%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.IO.Stream.Flush`
- `Overload:System.IO.Stream.Read`
- `Overload:System.IO.Stream.Write`

-->

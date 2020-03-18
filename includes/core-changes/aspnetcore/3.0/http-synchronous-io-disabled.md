---
ms.openlocfilehash: 53d2c989120c92f4e2d18f50ce4b364bd4c9b604
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901871"
---
### <a name="http-synchronous-io-disabled-in-all-servers"></a><span data-ttu-id="f9453-101">HTTP: Synchronous IO désactivé dans tous les serveurs</span><span class="sxs-lookup"><span data-stu-id="f9453-101">HTTP: Synchronous IO disabled in all servers</span></span>

<span data-ttu-id="f9453-102">En commençant par ASP.NET Core 3.0, les opérations de serveur synchrone sont désactivées par défaut.</span><span class="sxs-lookup"><span data-stu-id="f9453-102">Starting with ASP.NET Core 3.0, synchronous server operations are disabled by default.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f9453-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="f9453-103">Change description</span></span>

<span data-ttu-id="f9453-104">`AllowSynchronousIO`est une option dans chaque serveur qui permet ou désactive synchrone IO API comme `HttpRequest.Body.Read`, `HttpResponse.Body.Write`et `Stream.Flush`.</span><span class="sxs-lookup"><span data-stu-id="f9453-104">`AllowSynchronousIO` is an option in each server that enables or disables synchronous IO APIs like `HttpRequest.Body.Read`, `HttpResponse.Body.Write`, and `Stream.Flush`.</span></span> <span data-ttu-id="f9453-105">Ces API ont longtemps été une source de famine de fil et d’application se bloque.</span><span class="sxs-lookup"><span data-stu-id="f9453-105">These APIs have long been a source of thread starvation and app hangs.</span></span> <span data-ttu-id="f9453-106">À partir de ASP.NET Core 3.0 Preview 3, ces opérations synchrones sont désactivées par défaut.</span><span class="sxs-lookup"><span data-stu-id="f9453-106">Starting in ASP.NET Core 3.0 Preview 3, these synchronous operations are disabled by default.</span></span>

<span data-ttu-id="f9453-107">Serveurs concernés :</span><span class="sxs-lookup"><span data-stu-id="f9453-107">Affected servers:</span></span>

- <span data-ttu-id="f9453-108">Kestrel</span><span class="sxs-lookup"><span data-stu-id="f9453-108">Kestrel</span></span>
- <span data-ttu-id="f9453-109">HttpSys (en)</span><span class="sxs-lookup"><span data-stu-id="f9453-109">HttpSys</span></span>
- <span data-ttu-id="f9453-110">IIS en cours de traitement</span><span class="sxs-lookup"><span data-stu-id="f9453-110">IIS in-process</span></span>
- <span data-ttu-id="f9453-111">TestServer</span><span class="sxs-lookup"><span data-stu-id="f9453-111">TestServer</span></span>

<span data-ttu-id="f9453-112">Attendez-vous à des erreurs similaires à :</span><span class="sxs-lookup"><span data-stu-id="f9453-112">Expect errors similar to:</span></span>

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

<span data-ttu-id="f9453-113">Chaque serveur `AllowSynchronousIO` a une option qui contrôle ce comportement `false`et la valeur par défaut pour chacun d’eux est maintenant .</span><span class="sxs-lookup"><span data-stu-id="f9453-113">Each server has an `AllowSynchronousIO` option that controls this behavior and the default for all of them is now `false`.</span></span>

<span data-ttu-id="f9453-114">Le comportement peut également être remplacé sur une base par demande comme une atténuation temporaire.</span><span class="sxs-lookup"><span data-stu-id="f9453-114">The behavior can also be overridden on a per-request basis as a temporary mitigation.</span></span> <span data-ttu-id="f9453-115">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="f9453-115">For example:</span></span>

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

<span data-ttu-id="f9453-116">Si vous avez `TextWriter` des problèmes avec un ou un `Dispose`autre flux `DisposeAsync` appelant une API synchrone, appelez la nouvelle API à la place.</span><span class="sxs-lookup"><span data-stu-id="f9453-116">If you have trouble with a `TextWriter` or another stream calling a synchronous API in `Dispose`, call the new `DisposeAsync` API instead.</span></span>

<span data-ttu-id="f9453-117">Pour discussion, voir [dotnet/aspnetcore 7644](https://github.com/dotnet/aspnetcore/issues/7644).</span><span class="sxs-lookup"><span data-stu-id="f9453-117">For discussion, see [dotnet/aspnetcore#7644](https://github.com/dotnet/aspnetcore/issues/7644).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f9453-118">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f9453-118">Version introduced</span></span>

<span data-ttu-id="f9453-119">3.0</span><span class="sxs-lookup"><span data-stu-id="f9453-119">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f9453-120">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="f9453-120">Old behavior</span></span>

<span data-ttu-id="f9453-121">`HttpRequest.Body.Read`, `HttpResponse.Body.Write`et `Stream.Flush` ont été autorisés par défaut.</span><span class="sxs-lookup"><span data-stu-id="f9453-121">`HttpRequest.Body.Read`, `HttpResponse.Body.Write`, and `Stream.Flush` were allowed by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="f9453-122">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="f9453-122">New behavior</span></span>

<span data-ttu-id="f9453-123">Ces API synchrones sont refusées par défaut :</span><span class="sxs-lookup"><span data-stu-id="f9453-123">These synchronous APIs are disallowed by default:</span></span>

<span data-ttu-id="f9453-124">Attendez-vous à des erreurs similaires à :</span><span class="sxs-lookup"><span data-stu-id="f9453-124">Expect errors similar to:</span></span>

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

#### <a name="reason-for-change"></a><span data-ttu-id="f9453-125">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="f9453-125">Reason for change</span></span>

<span data-ttu-id="f9453-126">Ces API synchrones ont longtemps été une source de famine de fil et d’app hangs.</span><span class="sxs-lookup"><span data-stu-id="f9453-126">These synchronous APIs have long been a source of thread starvation and app hangs.</span></span> <span data-ttu-id="f9453-127">À partir de ASP.NET Core 3.0 Preview 3, les opérations synchrones sont désactivées par défaut.</span><span class="sxs-lookup"><span data-stu-id="f9453-127">Starting in ASP.NET Core 3.0 Preview 3, the synchronous operations are disabled by default.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f9453-128">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="f9453-128">Recommended action</span></span>

<span data-ttu-id="f9453-129">Utilisez les versions asynchrones des méthodes.</span><span class="sxs-lookup"><span data-stu-id="f9453-129">Use the asynchronous versions of the methods.</span></span> <span data-ttu-id="f9453-130">Le comportement peut également être remplacé sur une base par demande comme une atténuation temporaire.</span><span class="sxs-lookup"><span data-stu-id="f9453-130">The behavior can also be overridden on a per-request basis as a temporary mitigation.</span></span>

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

#### <a name="category"></a><span data-ttu-id="f9453-131">Category</span><span class="sxs-lookup"><span data-stu-id="f9453-131">Category</span></span>

<span data-ttu-id="f9453-132">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f9453-132">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f9453-133">API affectées</span><span class="sxs-lookup"><span data-stu-id="f9453-133">Affected APIs</span></span>

- <xref:System.IO.Stream.Flush%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.IO.Stream.Flush`
- `Overload:System.IO.Stream.Read`
- `Overload:System.IO.Stream.Write`

-->

---
ms.openlocfilehash: 46f6f77a543dfcf2073063d8ec200ef7d71e6b1f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077590"
---
### <a name="blazor-jsobjectreference-and-jsinprocessobjectreference-types-changed-to-internal"></a><span data-ttu-id="71b0f-101">Éblouissant : les types JSObjectReference et JSInProcessObjectReference sont devenus internes</span><span class="sxs-lookup"><span data-stu-id="71b0f-101">Blazor: JSObjectReference and JSInProcessObjectReference types changed to internal</span></span>

<span data-ttu-id="71b0f-102">Les nouveaux `Microsoft.JSInterop.JSObjectReference` `Microsoft.JSInterop.JSInProcessObjectReference` types et introduits dans ASP.net Core 5,0 RC1 ont été marqués comme `internal` .</span><span class="sxs-lookup"><span data-stu-id="71b0f-102">The new `Microsoft.JSInterop.JSObjectReference` and `Microsoft.JSInterop.JSInProcessObjectReference` types introduced in ASP.NET Core 5.0 RC1 have been marked as `internal`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="71b0f-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="71b0f-103">Version introduced</span></span>

<span data-ttu-id="71b0f-104">5,0 RC2</span><span class="sxs-lookup"><span data-stu-id="71b0f-104">5.0 RC2</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="71b0f-105">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="71b0f-105">Old behavior</span></span>

<span data-ttu-id="71b0f-106">Un `JSObjectReference` peut être obtenu à partir d’un appel JavaScript Interop via `IJSRuntime` .</span><span class="sxs-lookup"><span data-stu-id="71b0f-106">A `JSObjectReference` can be obtained from a JavaScript interop call via `IJSRuntime`.</span></span> <span data-ttu-id="71b0f-107">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="71b0f-107">For example:</span></span>

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<JSObjectReference>(...);
```

#### <a name="new-behavior"></a><span data-ttu-id="71b0f-108">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="71b0f-108">New behavior</span></span>

<span data-ttu-id="71b0f-109">`JSObjectReference` utilise le modificateur d’accès [interne](../../../../docs/csharp/language-reference/keywords/internal.md) .</span><span class="sxs-lookup"><span data-stu-id="71b0f-109">`JSObjectReference` uses the [internal](../../../../docs/csharp/language-reference/keywords/internal.md) access modifier.</span></span> <span data-ttu-id="71b0f-110">L' `public` `IJSObjectReference` interface doit être utilisée à la place.</span><span class="sxs-lookup"><span data-stu-id="71b0f-110">The `public` `IJSObjectReference` interface must be used instead.</span></span> <span data-ttu-id="71b0f-111">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="71b0f-111">For example:</span></span>

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<IJSObjectReference>(...);
```

<span data-ttu-id="71b0f-112">`JSInProcessObjectReference` était également marqué comme `internal` et a été remplacé par `IJSInProcessObjectReference` .</span><span class="sxs-lookup"><span data-stu-id="71b0f-112">`JSInProcessObjectReference` was also marked as `internal` and was replaced by `IJSInProcessObjectReference`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="71b0f-113">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="71b0f-113">Reason for change</span></span>

<span data-ttu-id="71b0f-114">La modification rend la fonctionnalité d’interopérabilité JavaScript plus cohérente avec d’autres modèles dans éblouissant.</span><span class="sxs-lookup"><span data-stu-id="71b0f-114">The change makes the JavaScript interop feature more consistent with other patterns within Blazor.</span></span> <span data-ttu-id="71b0f-115">`IJSObjectReference` est analogue à `IJSRuntime` dans le sens où il a un objectif similaire et possède des méthodes et des extensions similaires.</span><span class="sxs-lookup"><span data-stu-id="71b0f-115">`IJSObjectReference` is analogous to `IJSRuntime` in that it serves a similar purpose and has similar methods and extensions.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="71b0f-116">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="71b0f-116">Recommended action</span></span>

<span data-ttu-id="71b0f-117">Remplacez les occurrences de `JSObjectReference` et de `JSInProcessObjectReference` par `IJSObjectReference` et `IJSInProcessObjectReference` , respectivement.</span><span class="sxs-lookup"><span data-stu-id="71b0f-117">Replace occurrences of `JSObjectReference` and `JSInProcessObjectReference` with `IJSObjectReference` and `IJSInProcessObjectReference`, respectively.</span></span>

#### <a name="category"></a><span data-ttu-id="71b0f-118">Category</span><span class="sxs-lookup"><span data-stu-id="71b0f-118">Category</span></span>

<span data-ttu-id="71b0f-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="71b0f-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="71b0f-120">API affectées</span><span class="sxs-lookup"><span data-stu-id="71b0f-120">Affected APIs</span></span>

- `Microsoft.JSInterop.JSObjectReference`
- `Microsoft.JSInterop.JSInProcessObjectReference`

<!--

#### Affected APIs

- `T:Microsoft.JSInterop.JSObjectReference`
- `T:Microsoft.JSInterop.JSInProcessObjectReference`

-->

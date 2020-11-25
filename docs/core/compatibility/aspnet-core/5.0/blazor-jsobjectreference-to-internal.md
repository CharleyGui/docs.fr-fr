---
title: 'Modification avec rupture : les types JSObjectReference et JSInProcessObjectReference sont devenus internes'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 intitulé « éblouissant » : JSObjectReference et JSInProcessObjectReference types ont changé en interne'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 43a66d204f8309dc5afc57d099b2201c477cc3ad
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760971"
---
# <a name="blazor-jsobjectreference-and-jsinprocessobjectreference-types-changed-to-internal"></a><span data-ttu-id="7d534-103">Éblouissant : les types JSObjectReference et JSInProcessObjectReference sont devenus internes</span><span class="sxs-lookup"><span data-stu-id="7d534-103">Blazor: JSObjectReference and JSInProcessObjectReference types changed to internal</span></span>

<span data-ttu-id="7d534-104">Les nouveaux `Microsoft.JSInterop.JSObjectReference` `Microsoft.JSInterop.JSInProcessObjectReference` types et introduits dans ASP.net Core 5,0 RC1 ont été marqués comme `internal` .</span><span class="sxs-lookup"><span data-stu-id="7d534-104">The new `Microsoft.JSInterop.JSObjectReference` and `Microsoft.JSInterop.JSInProcessObjectReference` types introduced in ASP.NET Core 5.0 RC1 have been marked as `internal`.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="7d534-105">Version introduite</span><span class="sxs-lookup"><span data-stu-id="7d534-105">Version introduced</span></span>

<span data-ttu-id="7d534-106">5,0 RC2</span><span class="sxs-lookup"><span data-stu-id="7d534-106">5.0 RC2</span></span>

## <a name="old-behavior"></a><span data-ttu-id="7d534-107">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="7d534-107">Old behavior</span></span>

<span data-ttu-id="7d534-108">Un `JSObjectReference` peut être obtenu à partir d’un appel JavaScript Interop via `IJSRuntime` .</span><span class="sxs-lookup"><span data-stu-id="7d534-108">A `JSObjectReference` can be obtained from a JavaScript interop call via `IJSRuntime`.</span></span> <span data-ttu-id="7d534-109">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="7d534-109">For example:</span></span>

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<JSObjectReference>(...);
```

## <a name="new-behavior"></a><span data-ttu-id="7d534-110">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="7d534-110">New behavior</span></span>

<span data-ttu-id="7d534-111">`JSObjectReference` utilise le modificateur d’accès [interne](../../../../csharp/language-reference/keywords/internal.md) .</span><span class="sxs-lookup"><span data-stu-id="7d534-111">`JSObjectReference` uses the [internal](../../../../csharp/language-reference/keywords/internal.md) access modifier.</span></span> <span data-ttu-id="7d534-112">L' `public` `IJSObjectReference` interface doit être utilisée à la place.</span><span class="sxs-lookup"><span data-stu-id="7d534-112">The `public` `IJSObjectReference` interface must be used instead.</span></span> <span data-ttu-id="7d534-113">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="7d534-113">For example:</span></span>

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<IJSObjectReference>(...);
```

<span data-ttu-id="7d534-114">`JSInProcessObjectReference` était également marqué comme `internal` et a été remplacé par `IJSInProcessObjectReference` .</span><span class="sxs-lookup"><span data-stu-id="7d534-114">`JSInProcessObjectReference` was also marked as `internal` and was replaced by `IJSInProcessObjectReference`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="7d534-115">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="7d534-115">Reason for change</span></span>

<span data-ttu-id="7d534-116">La modification rend la fonctionnalité d’interopérabilité JavaScript plus cohérente avec d’autres modèles dans éblouissant.</span><span class="sxs-lookup"><span data-stu-id="7d534-116">The change makes the JavaScript interop feature more consistent with other patterns within Blazor.</span></span> <span data-ttu-id="7d534-117">`IJSObjectReference` est analogue à `IJSRuntime` dans le sens où il a un objectif similaire et possède des méthodes et des extensions similaires.</span><span class="sxs-lookup"><span data-stu-id="7d534-117">`IJSObjectReference` is analogous to `IJSRuntime` in that it serves a similar purpose and has similar methods and extensions.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="7d534-118">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="7d534-118">Recommended action</span></span>

<span data-ttu-id="7d534-119">Remplacez les occurrences de `JSObjectReference` et de `JSInProcessObjectReference` par `IJSObjectReference` et `IJSInProcessObjectReference` , respectivement.</span><span class="sxs-lookup"><span data-stu-id="7d534-119">Replace occurrences of `JSObjectReference` and `JSInProcessObjectReference` with `IJSObjectReference` and `IJSInProcessObjectReference`, respectively.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="7d534-120">API affectées</span><span class="sxs-lookup"><span data-stu-id="7d534-120">Affected APIs</span></span>

- `Microsoft.JSInterop.JSObjectReference`
- `Microsoft.JSInterop.JSInProcessObjectReference`

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.JSInterop.JSObjectReference`
- `T:Microsoft.JSInterop.JSInProcessObjectReference`

-->

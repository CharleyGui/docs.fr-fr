---
title: 'Modification avec rupture : éblouissant : espace blanc non significatif tronqué des composants au moment de la compilation'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 intitulé « éblouissant » : espace blanc non significatif tronqué des composants au moment de la compilation'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 92a961bb377bedd27b793c77d4be31ce52179ee2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761220"
---
# <a name="blazor-insignificant-whitespace-trimmed-from-components-at-compile-time"></a><span data-ttu-id="2afd3-103">Éblouissante : espace blanc non significatif tronqué des composants au moment de la compilation</span><span class="sxs-lookup"><span data-stu-id="2afd3-103">Blazor: Insignificant whitespace trimmed from components at compile time</span></span>

<span data-ttu-id="2afd3-104">À compter de ASP.NET Core 5,0 Preview 7, le compilateur Razor omet les espaces blancs non significatifs dans les composants éblouissants (fichiers *. Razor* ) au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="2afd3-104">Starting with ASP.NET Core 5.0 Preview 7, the Razor compiler omits insignificant whitespace in Blazor components (*.razor* files) at compile time.</span></span> <span data-ttu-id="2afd3-105">Pour plus d’informations, consultez émettre [dotnet/aspnetcore # 23568](https://github.com/dotnet/aspnetcore/issues/23568).</span><span class="sxs-lookup"><span data-stu-id="2afd3-105">For discussion, see issue [dotnet/aspnetcore#23568](https://github.com/dotnet/aspnetcore/issues/23568).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="2afd3-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="2afd3-106">Version introduced</span></span>

<span data-ttu-id="2afd3-107">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="2afd3-107">5.0 Preview 7</span></span>

## <a name="old-behavior"></a><span data-ttu-id="2afd3-108">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="2afd3-108">Old behavior</span></span>

<span data-ttu-id="2afd3-109">Dans les versions 3. x du serveur éblouissant et du webassembly éblouissant, l’espace blanc est respecté dans le code source d’un composant.</span><span class="sxs-lookup"><span data-stu-id="2afd3-109">In 3.x versions of Blazor Server and Blazor WebAssembly, whitespace is honored in a component's source code.</span></span> <span data-ttu-id="2afd3-110">Les nœuds de texte avec espaces blancs sont rendus dans le Document Object Model du navigateur (DOM), même s’il n’y a aucun effet visuel.</span><span class="sxs-lookup"><span data-stu-id="2afd3-110">Whitespace-only text nodes render in the browser's Document Object Model (DOM) even when there's no visual effect.</span></span>

<span data-ttu-id="2afd3-111">Considérez le code du composant éblouissant suivant :</span><span class="sxs-lookup"><span data-stu-id="2afd3-111">Consider the following Blazor component code:</span></span>

```razor
<ul>
    @foreach (var item in Items)
    {
        <li>
            @item.Text
        </li>
    }
</ul>
```

<span data-ttu-id="2afd3-112">L’exemple précédent restitue deux nœuds d’espace blanc :</span><span class="sxs-lookup"><span data-stu-id="2afd3-112">The preceding example renders two whitespace nodes:</span></span>

* <span data-ttu-id="2afd3-113">En dehors du `@foreach` bloc de code.</span><span class="sxs-lookup"><span data-stu-id="2afd3-113">Outside of the `@foreach` code block.</span></span>
* <span data-ttu-id="2afd3-114">Autour de l' `<li>` élément.</span><span class="sxs-lookup"><span data-stu-id="2afd3-114">Around the `<li>` element.</span></span>
* <span data-ttu-id="2afd3-115">Autour de la `@item.Text` sortie.</span><span class="sxs-lookup"><span data-stu-id="2afd3-115">Around the `@item.Text` output.</span></span>

<span data-ttu-id="2afd3-116">Une liste contenant 100 éléments génère des nœuds 402 espaces blancs.</span><span class="sxs-lookup"><span data-stu-id="2afd3-116">A list containing 100 items results in 402 whitespace nodes.</span></span> <span data-ttu-id="2afd3-117">Il s’agit de la moitié de tous les nœuds rendus, même si aucun des nœuds d’espace blanc n’affecte visuellement la sortie rendue.</span><span class="sxs-lookup"><span data-stu-id="2afd3-117">That's over half of all nodes rendered, even though none of the whitespace nodes visually affect the rendered output.</span></span>

<span data-ttu-id="2afd3-118">Lors du rendu de code HTML statique pour les composants, les espaces à l’intérieur d’une balise n’ont pas été conservés.</span><span class="sxs-lookup"><span data-stu-id="2afd3-118">When rendering static HTML for components, whitespace inside a tag wasn't preserved.</span></span> <span data-ttu-id="2afd3-119">Par exemple, affichez la source du composant suivant :</span><span class="sxs-lookup"><span data-stu-id="2afd3-119">For example, view the source of the following component:</span></span>

```razor
<foo        bar="baz"     />
```

<span data-ttu-id="2afd3-120">Les espaces blancs ne sont pas conservés.</span><span class="sxs-lookup"><span data-stu-id="2afd3-120">Whitespace isn't preserved.</span></span> <span data-ttu-id="2afd3-121">La sortie prérendue est la suivante :</span><span class="sxs-lookup"><span data-stu-id="2afd3-121">The pre-rendered output is:</span></span>

```razor
<foo bar="baz" />
```

## <a name="new-behavior"></a><span data-ttu-id="2afd3-122">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="2afd3-122">New behavior</span></span>

<span data-ttu-id="2afd3-123">Sauf `@preservewhitespace` si la directive est utilisée avec la valeur `true` , les nœuds d’espace blanc sont supprimés s’ils :</span><span class="sxs-lookup"><span data-stu-id="2afd3-123">Unless the `@preservewhitespace` directive is used with value `true`, whitespace nodes are removed if they:</span></span>

* <span data-ttu-id="2afd3-124">Sont de début ou de fin dans un élément.</span><span class="sxs-lookup"><span data-stu-id="2afd3-124">Are leading or trailing within an element.</span></span>
* <span data-ttu-id="2afd3-125">Sont de début ou de fin dans un `RenderFragment` paramètre.</span><span class="sxs-lookup"><span data-stu-id="2afd3-125">Are leading or trailing within a `RenderFragment` parameter.</span></span> <span data-ttu-id="2afd3-126">Par exemple, le contenu enfant est passé à un autre composant.</span><span class="sxs-lookup"><span data-stu-id="2afd3-126">For example, child content being passed to another component.</span></span>
* <span data-ttu-id="2afd3-127">Précédez ou suivez un bloc de code C# tel que `@if` et `@foreach` .</span><span class="sxs-lookup"><span data-stu-id="2afd3-127">Precede or follow a C# code block such as `@if` and `@foreach`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="2afd3-128">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="2afd3-128">Reason for change</span></span>

<span data-ttu-id="2afd3-129">L’objectif de éblouissant dans ASP.NET Core 5,0 est d’améliorer les performances de rendu et de comparaison.</span><span class="sxs-lookup"><span data-stu-id="2afd3-129">A goal for Blazor in ASP.NET Core 5.0 is to improve the performance of rendering and diffing.</span></span> <span data-ttu-id="2afd3-130">Les nœuds d’arbre d’espace blanc non significatifs consommaient jusqu’à 40% du temps de rendu dans les tests d’évaluation.</span><span class="sxs-lookup"><span data-stu-id="2afd3-130">Insignificant whitespace tree nodes consumed up to 40 percent of the rendering time in benchmarks.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="2afd3-131">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="2afd3-131">Recommended action</span></span>

<span data-ttu-id="2afd3-132">Dans la plupart des cas, la disposition visuelle du composant rendu n’est pas affectée.</span><span class="sxs-lookup"><span data-stu-id="2afd3-132">In most cases, the visual layout of the rendered component is unaffected.</span></span> <span data-ttu-id="2afd3-133">Toutefois, la suppression de l’espace blanc peut affecter la sortie rendue lors de l’utilisation d’une règle CSS telle que `white-space: pre` .</span><span class="sxs-lookup"><span data-stu-id="2afd3-133">However, the whitespace removal might affect the rendered output when using a CSS rule like `white-space: pre`.</span></span> <span data-ttu-id="2afd3-134">Pour désactiver cette optimisation des performances et conserver l’espace blanc, effectuez l’une des actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="2afd3-134">To disable this performance optimization and preserve the whitespace, take one of the following actions:</span></span>

* <span data-ttu-id="2afd3-135">Ajoutez la `@preservewhitespace true` directive en haut du fichier *. Razor* pour appliquer la préférence à un composant spécifique.</span><span class="sxs-lookup"><span data-stu-id="2afd3-135">Add the `@preservewhitespace true` directive at the top of the *.razor* file to apply the preference to a specific component.</span></span>
* <span data-ttu-id="2afd3-136">Ajoutez la `@preservewhitespace true` directive à l’intérieur d’un fichier *_Imports. Razor* pour appliquer la préférence à un sous-répertoire ou à l’ensemble du projet.</span><span class="sxs-lookup"><span data-stu-id="2afd3-136">Add the `@preservewhitespace true` directive inside an *_Imports.razor* file to apply the preference to an entire subdirectory or the entire project.</span></span>

<span data-ttu-id="2afd3-137">Dans la plupart des cas, aucune action n’est requise, car les applications continuent de se comporter normalement (mais plus rapidement).</span><span class="sxs-lookup"><span data-stu-id="2afd3-137">In most cases, no action is required, as applications will typically continue to behave normally (but faster).</span></span> <span data-ttu-id="2afd3-138">Si la suppression des espaces blancs provoque des problèmes pour un composant particulier, utilisez `@preservewhitespace true` dans ce composant pour désactiver cette optimisation.</span><span class="sxs-lookup"><span data-stu-id="2afd3-138">If the whitespace stripping causes any problems for a particular component, use `@preservewhitespace true` in that component to disable this optimization.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="2afd3-139">API affectées</span><span class="sxs-lookup"><span data-stu-id="2afd3-139">Affected APIs</span></span>

<span data-ttu-id="2afd3-140">None</span><span class="sxs-lookup"><span data-stu-id="2afd3-140">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->

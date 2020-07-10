---
ms.openlocfilehash: ca369c4e3f78648c6e8e0bcb5d54711d3009a769
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174259"
---
### <a name="blazor-insignificant-whitespace-trimmed-from-components-at-compile-time"></a><span data-ttu-id="1a620-101">Éblouissante : espace blanc non significatif tronqué des composants au moment de la compilation</span><span class="sxs-lookup"><span data-stu-id="1a620-101">Blazor: Insignificant whitespace trimmed from components at compile time</span></span>

<span data-ttu-id="1a620-102">À compter de ASP.NET Core 5,0 Preview 7, le compilateur Razor omet les espaces blancs non significatifs dans les composants éblouissants (fichiers *. Razor* ) au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="1a620-102">Starting with ASP.NET Core 5.0 Preview 7, the Razor compiler omits insignificant whitespace in Blazor components (*.razor* files) at compile time.</span></span> <span data-ttu-id="1a620-103">Pour plus d’informations, consultez émettre [dotnet/aspnetcore # 23568](https://github.com/dotnet/aspnetcore/issues/23568).</span><span class="sxs-lookup"><span data-stu-id="1a620-103">For discussion, see issue [dotnet/aspnetcore#23568](https://github.com/dotnet/aspnetcore/issues/23568).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1a620-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="1a620-104">Version introduced</span></span>

<span data-ttu-id="1a620-105">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="1a620-105">5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="1a620-106">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="1a620-106">Old behavior</span></span>

<span data-ttu-id="1a620-107">Dans les versions 3. x du serveur éblouissant et du webassembly éblouissant, l’espace blanc est respecté dans le code source d’un composant.</span><span class="sxs-lookup"><span data-stu-id="1a620-107">In 3.x versions of Blazor Server and Blazor WebAssembly, whitespace is honored in a component's source code.</span></span> <span data-ttu-id="1a620-108">Les nœuds de texte avec espaces blancs sont rendus dans le Document Object Model du navigateur (DOM), même s’il n’y a aucun effet visuel.</span><span class="sxs-lookup"><span data-stu-id="1a620-108">Whitespace-only text nodes render in the browser's Document Object Model (DOM) even when there's no visual effect.</span></span>

<span data-ttu-id="1a620-109">Considérez le code du composant éblouissant suivant :</span><span class="sxs-lookup"><span data-stu-id="1a620-109">Consider the following Blazor component code:</span></span>

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

<span data-ttu-id="1a620-110">L’exemple précédent restitue deux nœuds d’espace blanc :</span><span class="sxs-lookup"><span data-stu-id="1a620-110">The preceding example renders two whitespace nodes:</span></span>

* <span data-ttu-id="1a620-111">En dehors du `@foreach` bloc de code.</span><span class="sxs-lookup"><span data-stu-id="1a620-111">Outside of the `@foreach` code block.</span></span>
* <span data-ttu-id="1a620-112">Autour de l' `<li>` élément.</span><span class="sxs-lookup"><span data-stu-id="1a620-112">Around the `<li>` element.</span></span>
* <span data-ttu-id="1a620-113">Autour de la `@item.Text` sortie.</span><span class="sxs-lookup"><span data-stu-id="1a620-113">Around the `@item.Text` output.</span></span>

<span data-ttu-id="1a620-114">Une liste contenant 100 éléments génère des nœuds 402 espaces blancs.</span><span class="sxs-lookup"><span data-stu-id="1a620-114">A list containing 100 items results in 402 whitespace nodes.</span></span> <span data-ttu-id="1a620-115">Il s’agit de la moitié de tous les nœuds rendus, même si aucun des nœuds d’espace blanc n’affecte visuellement la sortie rendue.</span><span class="sxs-lookup"><span data-stu-id="1a620-115">That's over half of all nodes rendered, even though none of the whitespace nodes visually affect the rendered output.</span></span>

<span data-ttu-id="1a620-116">Lors du rendu de code HTML statique pour les composants, les espaces à l’intérieur d’une balise n’ont pas été conservés.</span><span class="sxs-lookup"><span data-stu-id="1a620-116">When rendering static HTML for components, whitespace inside a tag wasn't preserved.</span></span> <span data-ttu-id="1a620-117">Par exemple, affichez la source du composant suivant :</span><span class="sxs-lookup"><span data-stu-id="1a620-117">For example, view the source of the following component:</span></span>

```razor
<foo        bar="baz"     />
```

<span data-ttu-id="1a620-118">Les espaces blancs ne sont pas conservés.</span><span class="sxs-lookup"><span data-stu-id="1a620-118">Whitespace isn't preserved.</span></span> <span data-ttu-id="1a620-119">La sortie prérendue est la suivante :</span><span class="sxs-lookup"><span data-stu-id="1a620-119">The pre-rendered output is:</span></span>

```razor
<foo bar="baz" />
```

#### <a name="new-behavior"></a><span data-ttu-id="1a620-120">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="1a620-120">New behavior</span></span>

<span data-ttu-id="1a620-121">Sauf `@preservewhitespace` si la directive est utilisée avec la valeur `true` , les nœuds d’espace blanc sont supprimés s’ils :</span><span class="sxs-lookup"><span data-stu-id="1a620-121">Unless the `@preservewhitespace` directive is used with value `true`, whitespace nodes are removed if they:</span></span>

* <span data-ttu-id="1a620-122">Sont de début ou de fin dans un élément.</span><span class="sxs-lookup"><span data-stu-id="1a620-122">Are leading or trailing within an element.</span></span>
* <span data-ttu-id="1a620-123">Sont de début ou de fin dans un `RenderFragment` paramètre.</span><span class="sxs-lookup"><span data-stu-id="1a620-123">Are leading or trailing within a `RenderFragment` parameter.</span></span> <span data-ttu-id="1a620-124">Par exemple, le contenu enfant est passé à un autre composant.</span><span class="sxs-lookup"><span data-stu-id="1a620-124">For example, child content being passed to another component.</span></span>
* <span data-ttu-id="1a620-125">Précédez ou suivez un bloc de code C# tel que `@if` et `@foreach` .</span><span class="sxs-lookup"><span data-stu-id="1a620-125">Precede or follow a C# code block such as `@if` and `@foreach`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1a620-126">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="1a620-126">Reason for change</span></span>

<span data-ttu-id="1a620-127">L’objectif de éblouissant dans ASP.NET Core 5,0 est d’améliorer les performances de rendu et de comparaison.</span><span class="sxs-lookup"><span data-stu-id="1a620-127">A goal for Blazor in ASP.NET Core 5.0 is to improve the performance of rendering and diffing.</span></span> <span data-ttu-id="1a620-128">Les nœuds d’arbre d’espace blanc non significatifs consommaient jusqu’à 40% du temps de rendu dans les tests d’évaluation.</span><span class="sxs-lookup"><span data-stu-id="1a620-128">Insignificant whitespace tree nodes consumed up to 40 percent of the rendering time in benchmarks.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1a620-129">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="1a620-129">Recommended action</span></span>

<span data-ttu-id="1a620-130">Dans la plupart des cas, la disposition visuelle du composant rendu n’est pas affectée.</span><span class="sxs-lookup"><span data-stu-id="1a620-130">In most cases, the visual layout of the rendered component is unaffected.</span></span> <span data-ttu-id="1a620-131">Toutefois, la suppression de l’espace blanc peut affecter la sortie rendue lors de l’utilisation d’une règle CSS telle que `white-space: pre` .</span><span class="sxs-lookup"><span data-stu-id="1a620-131">However, the whitespace removal might affect the rendered output when using a CSS rule like `white-space: pre`.</span></span> <span data-ttu-id="1a620-132">Pour désactiver cette optimisation des performances et conserver l’espace blanc, effectuez l’une des actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="1a620-132">To disable this performance optimization and preserve the whitespace, take one of the following actions:</span></span>

* <span data-ttu-id="1a620-133">Ajoutez la `@preservewhitespace true` directive en haut du fichier *. Razor* pour appliquer la préférence à un composant spécifique.</span><span class="sxs-lookup"><span data-stu-id="1a620-133">Add the `@preservewhitespace true` directive at the top of the *.razor* file to apply the preference to a specific component.</span></span>
* <span data-ttu-id="1a620-134">Ajoutez la `@preservewhitespace true` directive à l’intérieur d’un fichier *_Imports. Razor* pour appliquer la préférence à un sous-répertoire ou à l’ensemble du projet.</span><span class="sxs-lookup"><span data-stu-id="1a620-134">Add the `@preservewhitespace true` directive inside an *_Imports.razor* file to apply the preference to an entire subdirectory or the entire project.</span></span>

<span data-ttu-id="1a620-135">Dans la plupart des cas, aucune action n’est requise, car les applications continuent de se comporter normalement (mais plus rapidement).</span><span class="sxs-lookup"><span data-stu-id="1a620-135">In most cases, no action is required, as applications will typically continue to behave normally (but faster).</span></span> <span data-ttu-id="1a620-136">Si la suppression des espaces blancs provoque des problèmes pour un composant particulier, utilisez `@preservewhitespace true` dans ce composant pour désactiver cette optimisation.</span><span class="sxs-lookup"><span data-stu-id="1a620-136">If the whitespace stripping causes any problems for a particular component, use `@preservewhitespace true` in that component to disable this optimization.</span></span>

#### <a name="category"></a><span data-ttu-id="1a620-137">Catégorie</span><span class="sxs-lookup"><span data-stu-id="1a620-137">Category</span></span>

<span data-ttu-id="1a620-138">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1a620-138">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1a620-139">API affectées</span><span class="sxs-lookup"><span data-stu-id="1a620-139">Affected APIs</span></span>

<span data-ttu-id="1a620-140">Aucun</span><span class="sxs-lookup"><span data-stu-id="1a620-140">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->

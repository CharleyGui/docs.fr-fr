---
title: 'Modification avec rupture : éblouissant : les champs publics ReadOnly RenderTreeFrame sont devenus des propriétés'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 intitulée éblouissant : les champs publics ReadOnly RenderTreeFrame sont devenus des propriétés'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: e9da9c538cc0a8ed4f138ef64ece0c7d144f28d3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760843"
---
# <a name="blazor-rendertreeframe-readonly-public-fields-have-become-properties"></a><span data-ttu-id="3c4f9-103">Éblouissant : les champs publics ReadOnly RenderTreeFrame sont devenus des propriétés</span><span class="sxs-lookup"><span data-stu-id="3c4f9-103">Blazor: RenderTreeFrame readonly public fields have become properties</span></span>

<span data-ttu-id="3c4f9-104">Dans ASP.NET Core 3,0 et 3,1, la <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame> structure expose différents `readonly public` champs, notamment <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.FrameType> , <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.Sequence> et d’autres.</span><span class="sxs-lookup"><span data-stu-id="3c4f9-104">In ASP.NET Core 3.0 and 3.1, the <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame> struct exposed various `readonly public` fields, including <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.FrameType>, <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.Sequence>, and others.</span></span> <span data-ttu-id="3c4f9-105">Dans ASP.NET Core version 5,0 RC1 et les versions ultérieures, tous les `readonly public` champs sont modifiés en `readonly public` Propriétés.</span><span class="sxs-lookup"><span data-stu-id="3c4f9-105">In ASP.NET Core 5.0 RC1 and later versions, all the `readonly public` fields changed to `readonly public` properties.</span></span>

<span data-ttu-id="3c4f9-106">Cette modification n’affecte pas de nombreux développeurs, car :</span><span class="sxs-lookup"><span data-stu-id="3c4f9-106">This change won't affect many developers because:</span></span>

* <span data-ttu-id="3c4f9-107">Toute application ou bibliothèque qui utilise simplement des `.razor` fichiers (ou même des <xref:Microsoft.AspNetCore.Components.Rendering.RenderTreeBuilder> appels manuels) pour définir ses composants ne référence pas directement ce type.</span><span class="sxs-lookup"><span data-stu-id="3c4f9-107">Any app or library that simply uses `.razor` files (or even manual <xref:Microsoft.AspNetCore.Components.Rendering.RenderTreeBuilder> calls) to define its components wouldn't be referencing this type directly.</span></span>
* <span data-ttu-id="3c4f9-108">Le `RenderTreeFrame` type lui-même est considéré comme un détail d’implémentation, non destiné à être utilisé en dehors de l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="3c4f9-108">The `RenderTreeFrame` type itself is regarded as an implementation detail, not intended for use outside of the framework.</span></span> <span data-ttu-id="3c4f9-109">ASP.NET Core 3,0 et versions ultérieures incluent un analyseur qui émet des avertissements du compilateur si le type est utilisé directement.</span><span class="sxs-lookup"><span data-stu-id="3c4f9-109">ASP.NET Core 3.0 and later includes an analyzer that issues compiler warnings if the type is being used directly.</span></span>
* <span data-ttu-id="3c4f9-110">Même si vous référencez `RenderTreeFrame` directement, cette modification est une rupture binaire, mais pas une rupture de source.</span><span class="sxs-lookup"><span data-stu-id="3c4f9-110">Even if you reference `RenderTreeFrame` directly, this change is binary-breaking but not source-breaking.</span></span> <span data-ttu-id="3c4f9-111">Autrement dit, votre code source existant se compilera et se comportera correctement.</span><span class="sxs-lookup"><span data-stu-id="3c4f9-111">That is, your existing source code will compile and behave properly.</span></span> <span data-ttu-id="3c4f9-112">Vous ne rencontrerez un problème que si vous compilez par rapport à un Framework .NET Core 3. x et que vous exécutez ensuite ces fichiers binaires sur .NET 5,0 RC1 et Framework ultérieur.</span><span class="sxs-lookup"><span data-stu-id="3c4f9-112">You'll only encounter an issue if compiling against a .NET Core 3.x framework and then running those binaries against the .NET 5.0 RC1 and later framework.</span></span>

<span data-ttu-id="3c4f9-113">Pour plus d’informations, consultez GitHub issue [dotnet/aspnetcore # 25727](https://github.com/dotnet/aspnetcore/issues/25727).</span><span class="sxs-lookup"><span data-stu-id="3c4f9-113">For discussion, see GitHub issue [dotnet/aspnetcore#25727](https://github.com/dotnet/aspnetcore/issues/25727).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="3c4f9-114">Version introduite</span><span class="sxs-lookup"><span data-stu-id="3c4f9-114">Version introduced</span></span>

<span data-ttu-id="3c4f9-115">5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="3c4f9-115">5.0 RC1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="3c4f9-116">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="3c4f9-116">Old behavior</span></span>

<span data-ttu-id="3c4f9-117">Les membres publics sur `RenderTreeFrame` sont définis en tant que champs.</span><span class="sxs-lookup"><span data-stu-id="3c4f9-117">Public members on `RenderTreeFrame` are defined as fields.</span></span> <span data-ttu-id="3c4f9-118">Par exemple : `renderTreeFrame.Sequence` et `renderTreeFrame.ElementName`.</span><span class="sxs-lookup"><span data-stu-id="3c4f9-118">For example, `renderTreeFrame.Sequence` and `renderTreeFrame.ElementName`.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="3c4f9-119">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="3c4f9-119">New behavior</span></span>

<span data-ttu-id="3c4f9-120">Les membres publics sur `RenderTreeFrame` sont définis en tant que propriétés portant le même nom qu’avant.</span><span class="sxs-lookup"><span data-stu-id="3c4f9-120">Public members on `RenderTreeFrame` are defined as properties with the same names as before.</span></span> <span data-ttu-id="3c4f9-121">Par exemple : `renderTreeFrame.Sequence` et `renderTreeFrame.ElementName`.</span><span class="sxs-lookup"><span data-stu-id="3c4f9-121">For example, `renderTreeFrame.Sequence` and `renderTreeFrame.ElementName`.</span></span>

<span data-ttu-id="3c4f9-122">Si un code précompilé ancien n’a pas été recompilé depuis cette modification, il peut lever une exception similaire à *MissingFieldException : champ introuvable : « Microsoft. AspNetCore. Components. RenderTree. RenderTreeFrame. Frame »*.</span><span class="sxs-lookup"><span data-stu-id="3c4f9-122">If older precompiled code hasn't been recompiled since this change, it may throw an exception similar to *MissingFieldException: Field not found: 'Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.FrameType'*.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="3c4f9-123">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="3c4f9-123">Reason for change</span></span>

<span data-ttu-id="3c4f9-124">Cette modification était nécessaire pour implémenter des améliorations de performances à fort impact dans le rendu des composants éblouissants dans ASP.NET Core 5,0.</span><span class="sxs-lookup"><span data-stu-id="3c4f9-124">This change was necessary to implement high-impact performance improvements in Blazor component rendering in ASP.NET Core 5.0.</span></span> <span data-ttu-id="3c4f9-125">Les mêmes niveaux de sécurité et d’encapsulation sont conservés.</span><span class="sxs-lookup"><span data-stu-id="3c4f9-125">The same levels of safety and encapsulation are maintained.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="3c4f9-126">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="3c4f9-126">Recommended action</span></span>

<span data-ttu-id="3c4f9-127">La plupart des développeurs éblouissants ne sont pas affectés par cette modification.</span><span class="sxs-lookup"><span data-stu-id="3c4f9-127">Most Blazor developers are unaffected by this change.</span></span> <span data-ttu-id="3c4f9-128">La modification est plus susceptible d’affecter les auteurs de bibliothèque et de package, mais uniquement dans de rares cas.</span><span class="sxs-lookup"><span data-stu-id="3c4f9-128">The change is more likely to affect library and package authors, but only in rare cases.</span></span> <span data-ttu-id="3c4f9-129">Plus précisément, si vous développez :</span><span class="sxs-lookup"><span data-stu-id="3c4f9-129">Specifically, if you're developing:</span></span>

* <span data-ttu-id="3c4f9-130">Une application et l’utilisation de ASP.NET Core 3. x ou la mise à niveau vers 5,0 RC1 ou version ultérieure, vous n’avez pas besoin de modifier votre propre code.</span><span class="sxs-lookup"><span data-stu-id="3c4f9-130">An app and using ASP.NET Core 3.x or upgrading to 5.0 RC1 or later, you don't need to change your own code.</span></span> <span data-ttu-id="3c4f9-131">Toutefois, si vous dépendez d’une bibliothèque mise à niveau pour tenir compte de cette modification, vous devez effectuer une mise à jour vers une version plus récente de cette bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="3c4f9-131">However, if you depend on a library that upgraded to account for this change, then you need to update to a newer version of that library.</span></span>
* <span data-ttu-id="3c4f9-132">Une bibliothèque et souhaitez prendre en charge uniquement ASP.NET Core 5,0 RC1 ou une version ultérieure, aucune action n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="3c4f9-132">A library and want to support only ASP.NET Core 5.0 RC1 or later, no action is needed.</span></span> <span data-ttu-id="3c4f9-133">Assurez-vous simplement que votre fichier projet déclare une `<TargetFramework>` valeur `net5.0` ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="3c4f9-133">Just ensure that your project file declares a `<TargetFramework>` value of `net5.0` or a later version.</span></span>
* <span data-ttu-id="3c4f9-134">Une bibliothèque et souhaitez prendre en charge les ASP.NET Core 3. x *et* 5,0, déterminez si votre code lit les `RenderTreeFrame` membres.</span><span class="sxs-lookup"><span data-stu-id="3c4f9-134">A library and want to support both ASP.NET Core 3.x *and* 5.0, determine whether your code reads any `RenderTreeFrame` members.</span></span> <span data-ttu-id="3c4f9-135">Par exemple, l’évaluation de `someRenderTreeFrame.FrameType` .</span><span class="sxs-lookup"><span data-stu-id="3c4f9-135">For example, evaluating `someRenderTreeFrame.FrameType`.</span></span>
  * <span data-ttu-id="3c4f9-136">La plupart des bibliothèques ne lisent pas `RenderTreeFrame` les membres, y compris les bibliothèques qui contiennent des `.razor` composants.</span><span class="sxs-lookup"><span data-stu-id="3c4f9-136">Most libraries won't read `RenderTreeFrame` members, including libraries that contain `.razor` components.</span></span> <span data-ttu-id="3c4f9-137">Dans ce cas, aucune action n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="3c4f9-137">In this case, no action is needed.</span></span>
  * <span data-ttu-id="3c4f9-138">Toutefois, si votre bibliothèque le fait, vous devez disposer de plusieurs cibles pour prendre en charge `netstandard2.1` et `net5.0` .</span><span class="sxs-lookup"><span data-stu-id="3c4f9-138">However, if your library does that, you'll need to multi-target to support both `netstandard2.1` and `net5.0`.</span></span> <span data-ttu-id="3c4f9-139">Appliquez les modifications suivantes dans votre fichier projet :</span><span class="sxs-lookup"><span data-stu-id="3c4f9-139">Apply the following changes in your project file:</span></span>
    * <span data-ttu-id="3c4f9-140">Remplacez l' `<TargetFramework>` élément existant par `<TargetFrameworks>netstandard2.0;net5.0</TargetFrameworks>` .</span><span class="sxs-lookup"><span data-stu-id="3c4f9-140">Replace the existing `<TargetFramework>` element with `<TargetFrameworks>netstandard2.0;net5.0</TargetFrameworks>`.</span></span>
    * <span data-ttu-id="3c4f9-141">Utilisez une `Microsoft.AspNetCore.Components` référence de package conditionnel pour prendre en compte les deux versions que vous souhaitez prendre en charge.</span><span class="sxs-lookup"><span data-stu-id="3c4f9-141">Use a conditional `Microsoft.AspNetCore.Components` package reference to account for both versions you wish to support.</span></span> <span data-ttu-id="3c4f9-142">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="3c4f9-142">For example:</span></span>

        ```xml
        <PackageReference Include="Microsoft.AspNetCore.Components" Version="3.0.0" Condition="'$(TargetFramework)' == 'netstandard2.0'" />
        <PackageReference Include="Microsoft.AspNetCore.Components" Version="5.0.0-rc.1.*" Condition="'$(TargetFramework)' != 'netstandard2.0'" />
        ```

<span data-ttu-id="3c4f9-143">Pour plus d’informations, consultez ce [diff illustrant la façon dont @jsakamoto la `Toolbelt.Blazor.HeadElement` bibliothèque a déjà été mise à niveau](https://github.com/jsakamoto/Toolbelt.Blazor.HeadElement/commit/090df430ba725f9420d412753db8104e8c32bf51).</span><span class="sxs-lookup"><span data-stu-id="3c4f9-143">For further clarification, see this [diff showing how @jsakamoto already upgraded the `Toolbelt.Blazor.HeadElement` library](https://github.com/jsakamoto/Toolbelt.Blazor.HeadElement/commit/090df430ba725f9420d412753db8104e8c32bf51).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="3c4f9-144">API affectées</span><span class="sxs-lookup"><span data-stu-id="3c4f9-144">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame`

-->

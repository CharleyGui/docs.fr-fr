---
title: Indications de conception de composants F#
description: 'Découvrez les instructions relatives à l’écriture de composants F # destinés à être consommés par d’autres appelants.'
ms.date: 05/14/2018
ms.openlocfilehash: 24be2a422c97b9334f749e3d9dfcccd0feec219b
ms.sourcegitcommit: e395fabeeea5c705d243d246fa64446839ac85b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2021
ms.locfileid: "97856105"
---
# <a name="f-component-design-guidelines"></a><span data-ttu-id="9fabd-103">Indications de conception de composants F#</span><span class="sxs-lookup"><span data-stu-id="9fabd-103">F# component design guidelines</span></span>

<span data-ttu-id="9fabd-104">Ce document est un ensemble d’instructions de conception de composants pour la programmation F #, basée sur les instructions de conception de composant F #, v14, Microsoft Research et une version qui a été organisée et gérée à l’origine par la Fondation de logiciel F #.</span><span class="sxs-lookup"><span data-stu-id="9fabd-104">This document is a set of component design guidelines for F# programming, based on the F# Component Design Guidelines, v14, Microsoft Research, and a version that was originally curated and maintained by the F# Software Foundation.</span></span>

<span data-ttu-id="9fabd-105">Ce document suppose que vous êtes familiarisé avec la programmation F #.</span><span class="sxs-lookup"><span data-stu-id="9fabd-105">This document assumes you are familiar with F# programming.</span></span> <span data-ttu-id="9fabd-106">Un grand Merci à la communauté F # pour leurs contributions et des commentaires utiles sur les différentes versions de ce guide.</span><span class="sxs-lookup"><span data-stu-id="9fabd-106">Many thanks to the F# community for their contributions and helpful feedback on various versions of this guide.</span></span>

## <a name="overview"></a><span data-ttu-id="9fabd-107">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="9fabd-107">Overview</span></span>

<span data-ttu-id="9fabd-108">Ce document examine certains des problèmes liés à la conception et au codage des composants F #.</span><span class="sxs-lookup"><span data-stu-id="9fabd-108">This document looks at some of the issues related to F# component design and coding.</span></span> <span data-ttu-id="9fabd-109">Un composant peut désigner l’un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="9fabd-109">A component can mean any of the following:</span></span>

* <span data-ttu-id="9fabd-110">Couche dans votre projet F # qui a des consommateurs externes dans ce projet.</span><span class="sxs-lookup"><span data-stu-id="9fabd-110">A layer in your F# project that has external consumers within that project.</span></span>
* <span data-ttu-id="9fabd-111">Bibliothèque destinée à être consommée par du code F # dans les limites d’assembly.</span><span class="sxs-lookup"><span data-stu-id="9fabd-111">A library intended for consumption by F# code across assembly boundaries.</span></span>
* <span data-ttu-id="9fabd-112">Bibliothèque destinée à être consommée par n’importe quel langage .NET au-delà des limites de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="9fabd-112">A library intended for consumption by any .NET language across assembly boundaries.</span></span>
* <span data-ttu-id="9fabd-113">Bibliothèque destinée à être distribuée via un référentiel de packages, tel que [NuGet](https://nuget.org).</span><span class="sxs-lookup"><span data-stu-id="9fabd-113">A library intended for distribution via a package repository, such as [NuGet](https://nuget.org).</span></span>

<span data-ttu-id="9fabd-114">Les techniques décrites dans cet article suivent les [cinq principes du bon code F #](index.md#five-principles-of-good-f-code)et, par conséquent, utilisent à la fois la programmation fonctionnelle et la programmation d’objets, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="9fabd-114">Techniques described in this article follow the [Five principles of good F# code](index.md#five-principles-of-good-f-code), and thus utilize both functional and object programming as appropriate.</span></span>

<span data-ttu-id="9fabd-115">Quelle que soit la méthodologie, le concepteur de composants et de bibliothèques rencontre un certain nombre de problèmes pratiques et prosaic quand il tente de concevoir une API qui est plus facilement utilisable par les développeurs.</span><span class="sxs-lookup"><span data-stu-id="9fabd-115">Regardless of the methodology, the component and library designer faces a number of practical and prosaic issues when trying to craft an API that is most easily usable by developers.</span></span> <span data-ttu-id="9fabd-116">L’application conscientious des [instructions de conception de la bibliothèque .net](../../standard/design-guidelines/index.md) vous dirigera vers la création d’un ensemble cohérent d’API qui sont agréables à consommer.</span><span class="sxs-lookup"><span data-stu-id="9fabd-116">Conscientious application of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md) will steer you towards creating a consistent set of APIs that are pleasant to consume.</span></span>

## <a name="general-guidelines"></a><span data-ttu-id="9fabd-117">Recommandations générales</span><span class="sxs-lookup"><span data-stu-id="9fabd-117">General guidelines</span></span>

<span data-ttu-id="9fabd-118">Il existe quelques recommandations universelles qui s’appliquent aux bibliothèques F #, quel que soit le public visé pour la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="9fabd-118">There are a few universal guidelines that apply to F# libraries, regardless of the intended audience for the library.</span></span>

### <a name="learn-the-net-library-design-guidelines"></a><span data-ttu-id="9fabd-119">Découvrez les instructions de conception de la bibliothèque .NET</span><span class="sxs-lookup"><span data-stu-id="9fabd-119">Learn the .NET Library Design Guidelines</span></span>

<span data-ttu-id="9fabd-120">Quel que soit le type de code F # que vous utilisez, il est utile d’avoir une connaissance pratique des [instructions de conception de la bibliothèque .net](../../standard/design-guidelines/index.md).</span><span class="sxs-lookup"><span data-stu-id="9fabd-120">Regardless of the kind of F# coding you are doing, it is valuable to have a working knowledge of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="9fabd-121">La plupart des autres programmeurs F # et .NET sont familiarisés avec ces instructions et s’attendent à ce que le code .NET soit conforme.</span><span class="sxs-lookup"><span data-stu-id="9fabd-121">Most other F# and .NET programmers will be familiar with these guidelines, and expect .NET code to conform to them.</span></span>

<span data-ttu-id="9fabd-122">Les instructions de conception de la bibliothèque .NET fournissent des indications générales sur l’affectation de noms, la conception des classes et des interfaces, la conception des membres (propriétés, méthodes, événements, etc.) et bien plus encore, et constituent un premier point de référence utile pour un large éventail de conseils en matière de conception.</span><span class="sxs-lookup"><span data-stu-id="9fabd-122">The .NET Library Design Guidelines provide general guidance regarding naming, designing classes and interfaces, member design (properties, methods, events, etc.) and more, and are a useful first point of reference for a variety of design guidance.</span></span>

### <a name="add-xml-documentation-comments-to-your-code"></a><span data-ttu-id="9fabd-123">Ajouter des commentaires de documentation XML à votre code</span><span class="sxs-lookup"><span data-stu-id="9fabd-123">Add XML documentation comments to your code</span></span>

<span data-ttu-id="9fabd-124">La documentation XML sur les API publiques permet de s’assurer que les utilisateurs peuvent obtenir des fonctionnalités IntelliSense et d’info-and Express exceptionnelles lors de l’utilisation de ces types et membres, et activer la génération de fichiers de documentation pour la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="9fabd-124">XML documentation on public APIs ensures that users can get great Intellisense and Quickinfo when using these types and members, and enable building documentation files for the library.</span></span> <span data-ttu-id="9fabd-125">Consultez la [documentation XML](../language-reference/xml-documentation.md) sur les différentes balises XML qui peuvent être utilisées pour le balisage supplémentaire dans les commentaires xmlDoc par l’employé.</span><span class="sxs-lookup"><span data-stu-id="9fabd-125">See the [XML Documentation](../language-reference/xml-documentation.md) about various xml tags that can be used for additional markup within xmldoc comments.</span></span>

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo: otherPoint:Point -> float
```

<span data-ttu-id="9fabd-126">Vous pouvez utiliser les commentaires XML de forme abrégée ( `/// comment` ) ou les commentaires XML standard ( `///<summary>comment</summary>` ).</span><span class="sxs-lookup"><span data-stu-id="9fabd-126">You can use either the short form XML comments (`/// comment`), or standard XML comments (`///<summary>comment</summary>`).</span></span>

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a><span data-ttu-id="9fabd-127">Envisagez d’utiliser des fichiers de signature explicites (. FSI) pour les API de bibliothèque et de composant stables</span><span class="sxs-lookup"><span data-stu-id="9fabd-127">Consider using explicit signature files (.fsi) for stable library and component APIs</span></span>

<span data-ttu-id="9fabd-128">L’utilisation de fichiers de signatures explicites dans une bibliothèque F # fournit un résumé succinct de l’API publique, qui vous permet de vous assurer que vous connaissez la surface publique complète de votre bibliothèque et fournit une séparation nette entre la documentation publique et les détails de l’implémentation interne.</span><span class="sxs-lookup"><span data-stu-id="9fabd-128">Using explicit signatures files in an F# library provides a succinct summary of public API, which helps to ensure that you know the full public surface of your library, and provides a clean separation between public documentation and internal implementation details.</span></span> <span data-ttu-id="9fabd-129">Les fichiers de signature ajoutent un frottement à la modification de l’API publique, en exigeant que les modifications soient apportées à la fois dans les fichiers d’implémentation et de signature.</span><span class="sxs-lookup"><span data-stu-id="9fabd-129">Signature files add friction to changing the public API, by requiring changes to be made in both the implementation and signature files.</span></span> <span data-ttu-id="9fabd-130">Par conséquent, les fichiers de signature ne doivent généralement être introduits que lorsqu’une API est devenue solidifiée et n’est plus censée changer de manière significative.</span><span class="sxs-lookup"><span data-stu-id="9fabd-130">As a result, signature files should typically only be introduced when an API has become solidified and is no longer expected to change significantly.</span></span>

### <a name="always-follow-best-practices-for-using-strings-in-net"></a><span data-ttu-id="9fabd-131">Suivre toujours les meilleures pratiques pour l’utilisation de chaînes dans .NET</span><span class="sxs-lookup"><span data-stu-id="9fabd-131">Always follow best practices for using strings in .NET</span></span>

<span data-ttu-id="9fabd-132">Suivez [les meilleures pratiques pour l’utilisation de chaînes dans l’aide de .net](../../standard/base-types/best-practices-strings.md) .</span><span class="sxs-lookup"><span data-stu-id="9fabd-132">Follow [Best Practices for Using Strings in .NET](../../standard/base-types/best-practices-strings.md) guidance.</span></span> <span data-ttu-id="9fabd-133">En particulier, indiquez toujours explicitement l' *intention culturelle* dans la conversion et la comparaison des chaînes (le cas échéant).</span><span class="sxs-lookup"><span data-stu-id="9fabd-133">In particular, always explicitly state *cultural intent* in the conversion and comparison of strings (where applicable).</span></span>

## <a name="guidelines-for-f-facing-libraries"></a><span data-ttu-id="9fabd-134">Instructions pour les bibliothèques en F #</span><span class="sxs-lookup"><span data-stu-id="9fabd-134">Guidelines for F#-facing libraries</span></span>

<span data-ttu-id="9fabd-135">Cette section présente les recommandations pour le développement de bibliothèques F # publiques. autrement dit, les bibliothèques exposent des API publiques qui sont destinées à être consommées par les développeurs F #.</span><span class="sxs-lookup"><span data-stu-id="9fabd-135">This section presents recommendations for developing public F#-facing libraries; that is, libraries exposing public APIs that are intended to be consumed by F# developers.</span></span> <span data-ttu-id="9fabd-136">Il existe une variété de recommandations de conception de bibliothèque applicables spécifiquement à F #.</span><span class="sxs-lookup"><span data-stu-id="9fabd-136">There are a variety of library-design recommendations applicable specifically to F#.</span></span> <span data-ttu-id="9fabd-137">En l’absence des recommandations spécifiques qui suivent, les règles de conception de la bibliothèque .NET sont des conseils de secours.</span><span class="sxs-lookup"><span data-stu-id="9fabd-137">In the absence of the specific recommendations that follow, the .NET Library Design Guidelines are the fallback guidance.</span></span>

### <a name="naming-conventions"></a><span data-ttu-id="9fabd-138">Conventions d’affectation de noms</span><span class="sxs-lookup"><span data-stu-id="9fabd-138">Naming conventions</span></span>

#### <a name="use-net-naming-and-capitalization-conventions"></a><span data-ttu-id="9fabd-139">Utiliser les conventions de nommage et de mise en majuscules de .NET</span><span class="sxs-lookup"><span data-stu-id="9fabd-139">Use .NET naming and capitalization conventions</span></span>

<span data-ttu-id="9fabd-140">Le tableau suivant suit les conventions de nommage et de mise en majuscules de .NET.</span><span class="sxs-lookup"><span data-stu-id="9fabd-140">The following table follows .NET naming and capitalization conventions.</span></span> <span data-ttu-id="9fabd-141">Il y a de petites additions pour inclure également des constructions F #.</span><span class="sxs-lookup"><span data-stu-id="9fabd-141">There are small additions to also include F# constructs.</span></span>

| <span data-ttu-id="9fabd-142">Construction</span><span class="sxs-lookup"><span data-stu-id="9fabd-142">Construct</span></span> | <span data-ttu-id="9fabd-143">Cas</span><span class="sxs-lookup"><span data-stu-id="9fabd-143">Case</span></span> | <span data-ttu-id="9fabd-144">Élément</span><span class="sxs-lookup"><span data-stu-id="9fabd-144">Part</span></span> | <span data-ttu-id="9fabd-145">Exemples</span><span class="sxs-lookup"><span data-stu-id="9fabd-145">Examples</span></span> | <span data-ttu-id="9fabd-146">Notes</span><span class="sxs-lookup"><span data-stu-id="9fabd-146">Notes</span></span> |
|-----------|------|------|----------|-------|
| <span data-ttu-id="9fabd-147">Types concrets</span><span class="sxs-lookup"><span data-stu-id="9fabd-147">Concrete types</span></span> | <span data-ttu-id="9fabd-148">Casse Pascal</span><span class="sxs-lookup"><span data-stu-id="9fabd-148">PascalCase</span></span> | <span data-ttu-id="9fabd-149">Substantif/adjectif</span><span class="sxs-lookup"><span data-stu-id="9fabd-149">Noun/ adjective</span></span> | <span data-ttu-id="9fabd-150">Liste, double, complexe</span><span class="sxs-lookup"><span data-stu-id="9fabd-150">List, Double, Complex</span></span> | <span data-ttu-id="9fabd-151">Les types concrets sont les structs, les classes, les énumérations, les délégués, les enregistrements et les unions.</span><span class="sxs-lookup"><span data-stu-id="9fabd-151">Concrete types are structs, classes, enumerations, delegates, records, and unions.</span></span> <span data-ttu-id="9fabd-152">Bien que les noms de types soient généralement en minuscules dans OCaml, F # a adopté le schéma de nommage .NET pour les types.</span><span class="sxs-lookup"><span data-stu-id="9fabd-152">Though type names are traditionally lowercase in OCaml, F# has adopted the .NET naming scheme for types.</span></span>
| <span data-ttu-id="9fabd-153">DLL</span><span class="sxs-lookup"><span data-stu-id="9fabd-153">DLLs</span></span>           | <span data-ttu-id="9fabd-154">Casse Pascal</span><span class="sxs-lookup"><span data-stu-id="9fabd-154">PascalCase</span></span> |                 | <span data-ttu-id="9fabd-155">Fabrikam.Core.dll</span><span class="sxs-lookup"><span data-stu-id="9fabd-155">Fabrikam.Core.dll</span></span> |  |
| <span data-ttu-id="9fabd-156">Étiquettes d’Union</span><span class="sxs-lookup"><span data-stu-id="9fabd-156">Union tags</span></span>     | <span data-ttu-id="9fabd-157">Casse Pascal</span><span class="sxs-lookup"><span data-stu-id="9fabd-157">PascalCase</span></span> | <span data-ttu-id="9fabd-158">Nom</span><span class="sxs-lookup"><span data-stu-id="9fabd-158">Noun</span></span> | <span data-ttu-id="9fabd-159">Some, ajouter, réussite</span><span class="sxs-lookup"><span data-stu-id="9fabd-159">Some, Add, Success</span></span> | <span data-ttu-id="9fabd-160">N’utilisez pas de préfixe dans les API publiques.</span><span class="sxs-lookup"><span data-stu-id="9fabd-160">Do not use a prefix in public APIs.</span></span> <span data-ttu-id="9fabd-161">Si vous le souhaitez, vous pouvez utiliser un préfixe en interne, par exemple `type Teams = TAlpha | TBeta | TDelta.`</span><span class="sxs-lookup"><span data-stu-id="9fabd-161">Optionally use a prefix when internal, such as `type Teams = TAlpha | TBeta | TDelta.`</span></span> |
| <span data-ttu-id="9fabd-162">Événement</span><span class="sxs-lookup"><span data-stu-id="9fabd-162">Event</span></span>          | <span data-ttu-id="9fabd-163">Casse Pascal</span><span class="sxs-lookup"><span data-stu-id="9fabd-163">PascalCase</span></span> | <span data-ttu-id="9fabd-164">Verbe</span><span class="sxs-lookup"><span data-stu-id="9fabd-164">Verb</span></span> | <span data-ttu-id="9fabd-165">ValueChanged/ValueChanging</span><span class="sxs-lookup"><span data-stu-id="9fabd-165">ValueChanged / ValueChanging</span></span> |  |
| <span data-ttu-id="9fabd-166">Exceptions</span><span class="sxs-lookup"><span data-stu-id="9fabd-166">Exceptions</span></span>     | <span data-ttu-id="9fabd-167">Casse Pascal</span><span class="sxs-lookup"><span data-stu-id="9fabd-167">PascalCase</span></span> |      | <span data-ttu-id="9fabd-168">WebException</span><span class="sxs-lookup"><span data-stu-id="9fabd-168">WebException</span></span> | <span data-ttu-id="9fabd-169">Le nom doit se terminer par « exception ».</span><span class="sxs-lookup"><span data-stu-id="9fabd-169">Name should end with "Exception".</span></span> |
| <span data-ttu-id="9fabd-170">Champ</span><span class="sxs-lookup"><span data-stu-id="9fabd-170">Field</span></span>          | <span data-ttu-id="9fabd-171">Casse Pascal</span><span class="sxs-lookup"><span data-stu-id="9fabd-171">PascalCase</span></span> | <span data-ttu-id="9fabd-172">Nom</span><span class="sxs-lookup"><span data-stu-id="9fabd-172">Noun</span></span> | <span data-ttu-id="9fabd-173">CurrentName</span><span class="sxs-lookup"><span data-stu-id="9fabd-173">CurrentName</span></span>  | |
| <span data-ttu-id="9fabd-174">Types interface</span><span class="sxs-lookup"><span data-stu-id="9fabd-174">Interface types</span></span> |  <span data-ttu-id="9fabd-175">Casse Pascal</span><span class="sxs-lookup"><span data-stu-id="9fabd-175">PascalCase</span></span> | <span data-ttu-id="9fabd-176">Substantif/adjectif</span><span class="sxs-lookup"><span data-stu-id="9fabd-176">Noun/ adjective</span></span> | <span data-ttu-id="9fabd-177">IDisposable</span><span class="sxs-lookup"><span data-stu-id="9fabd-177">IDisposable</span></span> | <span data-ttu-id="9fabd-178">Le nom doit commencer par « I ».</span><span class="sxs-lookup"><span data-stu-id="9fabd-178">Name should start with "I".</span></span> |
| <span data-ttu-id="9fabd-179">Méthode</span><span class="sxs-lookup"><span data-stu-id="9fabd-179">Method</span></span> |  <span data-ttu-id="9fabd-180">Casse Pascal</span><span class="sxs-lookup"><span data-stu-id="9fabd-180">PascalCase</span></span> |  <span data-ttu-id="9fabd-181">Verbe</span><span class="sxs-lookup"><span data-stu-id="9fabd-181">Verb</span></span> | <span data-ttu-id="9fabd-182">ToString</span><span class="sxs-lookup"><span data-stu-id="9fabd-182">ToString</span></span> | |
| <span data-ttu-id="9fabd-183">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="9fabd-183">Namespace</span></span> | <span data-ttu-id="9fabd-184">Casse Pascal</span><span class="sxs-lookup"><span data-stu-id="9fabd-184">PascalCase</span></span> | | <span data-ttu-id="9fabd-185">Microsoft. FSharp. Core</span><span class="sxs-lookup"><span data-stu-id="9fabd-185">Microsoft.FSharp.Core</span></span> | <span data-ttu-id="9fabd-186">Utilisez généralement `<Organization>.<Technology>[.<Subnamespace>]` , bien que supprimer l’organisation si la technologie est indépendante de l’organisation.</span><span class="sxs-lookup"><span data-stu-id="9fabd-186">Generally use `<Organization>.<Technology>[.<Subnamespace>]`, though drop the organization if the technology is independent of organization.</span></span> |
| <span data-ttu-id="9fabd-187">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9fabd-187">Parameters</span></span> | <span data-ttu-id="9fabd-188">La casse mixte</span><span class="sxs-lookup"><span data-stu-id="9fabd-188">camelCase</span></span> | <span data-ttu-id="9fabd-189">Nom</span><span class="sxs-lookup"><span data-stu-id="9fabd-189">Noun</span></span> |  <span data-ttu-id="9fabd-190">typeName, Transform, plage</span><span class="sxs-lookup"><span data-stu-id="9fabd-190">typeName, transform, range</span></span> | |
| <span data-ttu-id="9fabd-191">valeurs Let (Internal)</span><span class="sxs-lookup"><span data-stu-id="9fabd-191">let values (internal)</span></span> | <span data-ttu-id="9fabd-192">La casse mixte ou casse Pascal</span><span class="sxs-lookup"><span data-stu-id="9fabd-192">camelCase or PascalCase</span></span> | <span data-ttu-id="9fabd-193">Substantif/verbe</span><span class="sxs-lookup"><span data-stu-id="9fabd-193">Noun/ verb</span></span> |  <span data-ttu-id="9fabd-194">getValue, myTable</span><span class="sxs-lookup"><span data-stu-id="9fabd-194">getValue, myTable</span></span> |
| <span data-ttu-id="9fabd-195">valeurs Let (externe)</span><span class="sxs-lookup"><span data-stu-id="9fabd-195">let values (external)</span></span> | <span data-ttu-id="9fabd-196">La casse mixte ou casse Pascal</span><span class="sxs-lookup"><span data-stu-id="9fabd-196">camelCase or PascalCase</span></span> | <span data-ttu-id="9fabd-197">Substantif/verbe</span><span class="sxs-lookup"><span data-stu-id="9fabd-197">Noun/verb</span></span>  | <span data-ttu-id="9fabd-198">List. map, dates. Today</span><span class="sxs-lookup"><span data-stu-id="9fabd-198">List.map, Dates.Today</span></span> | <span data-ttu-id="9fabd-199">les valeurs à liaison limitée sont souvent publiques lorsque vous suivez les modèles de conception fonctionnelle traditionnels.</span><span class="sxs-lookup"><span data-stu-id="9fabd-199">let-bound values are often public when following traditional functional design patterns.</span></span> <span data-ttu-id="9fabd-200">Toutefois, utilisez généralement casse Pascal quand l’identificateur peut être utilisé à partir d’autres langages .NET.</span><span class="sxs-lookup"><span data-stu-id="9fabd-200">However, generally use PascalCase when the identifier can be used from other .NET languages.</span></span> |
| <span data-ttu-id="9fabd-201">Propriété</span><span class="sxs-lookup"><span data-stu-id="9fabd-201">Property</span></span>  | <span data-ttu-id="9fabd-202">Casse Pascal</span><span class="sxs-lookup"><span data-stu-id="9fabd-202">PascalCase</span></span>  | <span data-ttu-id="9fabd-203">Substantif/adjectif</span><span class="sxs-lookup"><span data-stu-id="9fabd-203">Noun/ adjective</span></span>  | <span data-ttu-id="9fabd-204">IsEndOfFile, BackColor</span><span class="sxs-lookup"><span data-stu-id="9fabd-204">IsEndOfFile, BackColor</span></span>  | <span data-ttu-id="9fabd-205">Les propriétés booléennes utilisent généralement et peuvent et doivent être positives, comme dans IsEndOfFile, et non IsNotEndOfFile.</span><span class="sxs-lookup"><span data-stu-id="9fabd-205">Boolean properties generally use Is and Can and should be affirmative, as in IsEndOfFile, not IsNotEndOfFile.</span></span>

#### <a name="avoid-abbreviations"></a><span data-ttu-id="9fabd-206">Éviter les abréviations</span><span class="sxs-lookup"><span data-stu-id="9fabd-206">Avoid abbreviations</span></span>

<span data-ttu-id="9fabd-207">Les instructions .NET découragent l’utilisation des abréviations (par exemple, « utiliser `OnButtonClick` plutôt que `OnBtnClick` »).</span><span class="sxs-lookup"><span data-stu-id="9fabd-207">The .NET guidelines discourage the use of abbreviations (for example, "use `OnButtonClick` rather than `OnBtnClick`").</span></span> <span data-ttu-id="9fabd-208">Les abréviations courantes, telles que `Async` pour « asynchrone », sont tolérées.</span><span class="sxs-lookup"><span data-stu-id="9fabd-208">Common abbreviations, such as `Async` for "Asynchronous", are tolerated.</span></span> <span data-ttu-id="9fabd-209">Cette instruction est parfois ignorée pour la programmation fonctionnelle. par exemple, `List.iter` utilise une abréviation pour « Iterate ».</span><span class="sxs-lookup"><span data-stu-id="9fabd-209">This guideline is sometimes ignored for functional programming; for example, `List.iter` uses an abbreviation for "iterate".</span></span> <span data-ttu-id="9fabd-210">Pour cette raison, l’utilisation d’abréviations tend à être tolérée à un degré supérieur dans la programmation F # en F #, mais doit toujours être évitée dans la conception du composant public.</span><span class="sxs-lookup"><span data-stu-id="9fabd-210">For this reason, using abbreviations tends to be tolerated to a greater degree in F#-to-F# programming, but should still generally be avoided in public component design.</span></span>

#### <a name="avoid-casing-name-collisions"></a><span data-ttu-id="9fabd-211">Éviter les collisions de nom de casse</span><span class="sxs-lookup"><span data-stu-id="9fabd-211">Avoid casing name collisions</span></span>

<span data-ttu-id="9fabd-212">Les instructions .NET indiquent que la casse seule ne peut pas être utilisée pour lever l’ambiguïté des collisions de noms, car certaines langues clientes (par exemple, Visual Basic) ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="9fabd-212">The .NET guidelines say that casing alone cannot be used to disambiguate name collisions, since some client languages (for example, Visual Basic) are case-insensitive.</span></span>

#### <a name="use-acronyms-where-appropriate"></a><span data-ttu-id="9fabd-213">Utiliser des acronymes quand cela est approprié</span><span class="sxs-lookup"><span data-stu-id="9fabd-213">Use acronyms where appropriate</span></span>

<span data-ttu-id="9fabd-214">Les acronymes tels que XML ne sont pas des abréviations et sont largement utilisés dans les bibliothèques .NET dans une forme non capitalisée (XML).</span><span class="sxs-lookup"><span data-stu-id="9fabd-214">Acronyms such as XML are not abbreviations and are widely used in .NET libraries in uncapitalized form (Xml).</span></span> <span data-ttu-id="9fabd-215">Seuls les acronymes bien connus et largement reconnus doivent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="9fabd-215">Only well-known, widely recognized acronyms should be used.</span></span>

#### <a name="use-pascalcase-for-generic-parameter-names"></a><span data-ttu-id="9fabd-216">Utiliser casse Pascal pour les noms de paramètres génériques</span><span class="sxs-lookup"><span data-stu-id="9fabd-216">Use PascalCase for generic parameter names</span></span>

<span data-ttu-id="9fabd-217">Utilisez casse Pascal pour les noms de paramètres génériques dans les API publiques, y compris pour les bibliothèques en F #.</span><span class="sxs-lookup"><span data-stu-id="9fabd-217">Do use PascalCase for generic parameter names in public APIs, including for F#-facing libraries.</span></span> <span data-ttu-id="9fabd-218">En particulier, utilisez des noms comme `T` , `U` , `T1` , `T2` pour les paramètres génériques arbitraires, et quand des noms spécifiques sont significatifs, alors pour les bibliothèques en F #, utilisez des noms comme `Key` , `Value` , `Arg` (mais pas par exemple `TKey` ).</span><span class="sxs-lookup"><span data-stu-id="9fabd-218">In particular, use names like `T`, `U`, `T1`, `T2` for arbitrary generic parameters, and when specific names make sense, then for F#-facing libraries use names like `Key`, `Value`, `Arg` (but not for example, `TKey`).</span></span>

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a><span data-ttu-id="9fabd-219">Utilisez casse Pascal ou la casse mixte pour les fonctions et valeurs publiques dans les modules F #</span><span class="sxs-lookup"><span data-stu-id="9fabd-219">Use either PascalCase or camelCase for public functions and values in F# modules</span></span>

<span data-ttu-id="9fabd-220">La casse mixte est utilisé pour les fonctions publiques qui sont conçues pour être utilisées non qualifiées (par exemple, `invalidArg` ) et pour les « fonctions de collection standard » (par exemple, List. Map).</span><span class="sxs-lookup"><span data-stu-id="9fabd-220">camelCase is used for public functions that are designed to be used unqualified (for example, `invalidArg`), and for the "standard collection functions" (for example, List.map).</span></span> <span data-ttu-id="9fabd-221">Dans ces deux cas, les noms de fonctions agissent comme des mots clés dans le langage.</span><span class="sxs-lookup"><span data-stu-id="9fabd-221">In both these cases, the function names act much like keywords in the language.</span></span>

### <a name="object-type-and-module-design"></a><span data-ttu-id="9fabd-222">Conception d’un objet, d’un type et d’un module</span><span class="sxs-lookup"><span data-stu-id="9fabd-222">Object, Type, and Module design</span></span>

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a><span data-ttu-id="9fabd-223">Utiliser des espaces de noms ou des modules pour contenir vos types et modules</span><span class="sxs-lookup"><span data-stu-id="9fabd-223">Use namespaces or modules to contain your types and modules</span></span>

<span data-ttu-id="9fabd-224">Chaque fichier F # dans un composant doit commencer par une déclaration d’espace de noms ou une déclaration de module.</span><span class="sxs-lookup"><span data-stu-id="9fabd-224">Each F# file in a component should begin with either a namespace declaration or a module declaration.</span></span>

```fsharp
namespace Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
     ...

module CommonOperations =
    ...
```

<span data-ttu-id="9fabd-225">or</span><span class="sxs-lookup"><span data-stu-id="9fabd-225">or</span></span>

```fsharp
module Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
    ...

module CommonOperations =
    ...
```

<span data-ttu-id="9fabd-226">Les différences entre l’utilisation de modules et d’espaces de noms pour organiser le code au niveau supérieur sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="9fabd-226">The differences between using modules and namespaces to organize code at the top level are as follows:</span></span>

* <span data-ttu-id="9fabd-227">Les espaces de noms peuvent s’étendre sur plusieurs fichiers</span><span class="sxs-lookup"><span data-stu-id="9fabd-227">Namespaces can span multiple files</span></span>
* <span data-ttu-id="9fabd-228">Les espaces de noms ne peuvent pas contenir de fonctions F #, sauf s’ils se trouvent dans un module interne</span><span class="sxs-lookup"><span data-stu-id="9fabd-228">Namespaces cannot contain F# functions unless they are within an inner module</span></span>
* <span data-ttu-id="9fabd-229">Le code d’un module donné doit être contenu dans un seul fichier</span><span class="sxs-lookup"><span data-stu-id="9fabd-229">The code for any given module must be contained within a single file</span></span>
* <span data-ttu-id="9fabd-230">Les modules de niveau supérieur peuvent contenir des fonctions F # sans nécessiter de module interne</span><span class="sxs-lookup"><span data-stu-id="9fabd-230">Top-level modules can contain F# functions without the need for an inner module</span></span>

<span data-ttu-id="9fabd-231">Le choix entre un espace de noms ou un module de niveau supérieur affecte la forme compilée du code et, par conséquent, affecte la vue d’autres langages .NET si votre API est finalement consommée en dehors du code F #.</span><span class="sxs-lookup"><span data-stu-id="9fabd-231">The choice between a top-level namespace or module affects the compiled form of the code, and thus will affect the view from other .NET languages should your API eventually be consumed outside of F# code.</span></span>

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a><span data-ttu-id="9fabd-232">Utiliser des méthodes et des propriétés pour des opérations intrinsèques à des types d’objet</span><span class="sxs-lookup"><span data-stu-id="9fabd-232">Use methods and properties for operations intrinsic to object types</span></span>

<span data-ttu-id="9fabd-233">Lorsque vous utilisez des objets, il est préférable de s’assurer que les fonctionnalités consommables sont implémentées en tant que méthodes et propriétés sur ce type.</span><span class="sxs-lookup"><span data-stu-id="9fabd-233">When working with objects, it is best to ensure that consumable functionality is implemented as methods and properties on that type.</span></span>

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

<span data-ttu-id="9fabd-234">La majeure partie des fonctionnalités d’un membre donné ne doit pas nécessairement être implémentée dans ce membre, mais l’élément consommable de cette fonctionnalité doit être.</span><span class="sxs-lookup"><span data-stu-id="9fabd-234">The bulk of functionality for a given member need not necessarily be implemented in that member, but the consumable piece of that functionality should be.</span></span>

#### <a name="use-classes-to-encapsulate-mutable-state"></a><span data-ttu-id="9fabd-235">Utiliser des classes pour encapsuler un État mutable</span><span class="sxs-lookup"><span data-stu-id="9fabd-235">Use classes to encapsulate mutable state</span></span>

<span data-ttu-id="9fabd-236">En F #, cette opération ne doit être effectuée que si cet État n’est pas déjà encapsulé par une autre construction de langage, telle qu’une fermeture, une expression de séquence ou un calcul asynchrone.</span><span class="sxs-lookup"><span data-stu-id="9fabd-236">In F#, this only needs to be done where that state is not already encapsulated by another language construct, such as a closure, sequence expression, or asynchronous computation.</span></span>

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a><span data-ttu-id="9fabd-237">Utiliser des interfaces pour regrouper des opérations connexes</span><span class="sxs-lookup"><span data-stu-id="9fabd-237">Use interfaces to group related operations</span></span>

<span data-ttu-id="9fabd-238">Utilisez les types d’interface pour représenter un ensemble d’opérations.</span><span class="sxs-lookup"><span data-stu-id="9fabd-238">Use interface types to represent a set of operations.</span></span> <span data-ttu-id="9fabd-239">Cela est préférable à d’autres options, telles que des tuples de fonctions ou des enregistrements de fonctions.</span><span class="sxs-lookup"><span data-stu-id="9fabd-239">This is preferred to other options, such as tuples of functions or records of functions.</span></span>

```fsharp
type Serializer =
    abstract Serialize<'T> : preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T> : preserveRefEq: bool -> pickle: string -> 'T
```

<span data-ttu-id="9fabd-240">Dans la préférence :</span><span class="sxs-lookup"><span data-stu-id="9fabd-240">In preference to:</span></span>

```fsharp
type Serializer<'T> = {
    Serialize: bool -> 'T -> string
    Deserialize: bool -> string -> 'T
}
```

<span data-ttu-id="9fabd-241">Les interfaces sont des concepts de première classe dans .NET, que vous pouvez utiliser pour obtenir ce que les functors vous procurent normalement.</span><span class="sxs-lookup"><span data-stu-id="9fabd-241">Interfaces are first-class concepts in .NET, which you can use to achieve what Functors would normally give you.</span></span> <span data-ttu-id="9fabd-242">En outre, ils peuvent être utilisés pour encoder les types existentiel dans votre programme, ce qui ne peut pas être le signe des fonctions.</span><span class="sxs-lookup"><span data-stu-id="9fabd-242">Additionally, they can be used to encode existential types into your program, which records of functions cannot.</span></span>

#### <a name="use-a-module-to-group-functions-that-act-on-collections"></a><span data-ttu-id="9fabd-243">Utiliser un module pour regrouper les fonctions qui agissent sur les collections</span><span class="sxs-lookup"><span data-stu-id="9fabd-243">Use a module to group functions that act on collections</span></span>

<span data-ttu-id="9fabd-244">Lorsque vous définissez un type de collection, envisagez de fournir un ensemble standard d’opérations comme `CollectionType.map` et `CollectionType.iter` ) pour les nouveaux types de collections.</span><span class="sxs-lookup"><span data-stu-id="9fabd-244">When you define a collection type, consider providing a standard set of operations like `CollectionType.map` and `CollectionType.iter`) for new collection types.</span></span>

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

<span data-ttu-id="9fabd-245">Si vous incluez un tel module, suivez les conventions d’affectation de noms standard pour les fonctions qui se trouvent dans FSharp. Core.</span><span class="sxs-lookup"><span data-stu-id="9fabd-245">If you include such a module, follow the standard naming conventions for functions found in FSharp.Core.</span></span>

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a><span data-ttu-id="9fabd-246">Utilisez un module pour regrouper des fonctions pour les fonctions canoniques courantes, en particulier dans les bibliothèques mathématiques et DSL</span><span class="sxs-lookup"><span data-stu-id="9fabd-246">Use a module to group functions for common, canonical functions, especially in math and DSL libraries</span></span>

<span data-ttu-id="9fabd-247">Par exemple, `Microsoft.FSharp.Core.Operators` est une collection ouverte automatiquement de fonctions de niveau supérieur (comme `abs` et `sin` ) fournies par FSharp.Core.dll.</span><span class="sxs-lookup"><span data-stu-id="9fabd-247">For example, `Microsoft.FSharp.Core.Operators` is an automatically opened collection of top-level functions (like `abs` and `sin`) provided by FSharp.Core.dll.</span></span>

<span data-ttu-id="9fabd-248">De même, une bibliothèque de statistiques peut inclure un module avec des fonctions `erf` et `erfc` , où ce module est conçu pour être ouvert de manière explicite ou automatique.</span><span class="sxs-lookup"><span data-stu-id="9fabd-248">Likewise, a statistics library might include a module with functions `erf` and `erfc`, where this module is designed to be explicitly or automatically opened.</span></span>

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a><span data-ttu-id="9fabd-249">Envisagez d’utiliser RequireQualifiedAccess et d’appliquer avec précaution les attributs AutoOpen</span><span class="sxs-lookup"><span data-stu-id="9fabd-249">Consider using RequireQualifiedAccess and carefully apply AutoOpen attributes</span></span>

<span data-ttu-id="9fabd-250">L’ajout `[<RequireQualifiedAccess>]` de l’attribut à un module indique que le module ne peut pas être ouvert et que les références aux éléments du module requièrent un accès qualifié explicite.</span><span class="sxs-lookup"><span data-stu-id="9fabd-250">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="9fabd-251">Par exemple, le `Microsoft.FSharp.Collections.List` module a cet attribut.</span><span class="sxs-lookup"><span data-stu-id="9fabd-251">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="9fabd-252">Cela est utile lorsque les fonctions et valeurs du module ont des noms qui sont susceptibles d’entrer en conflit avec des noms dans d’autres modules.</span><span class="sxs-lookup"><span data-stu-id="9fabd-252">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="9fabd-253">La nécessité d’un accès qualifié peut augmenter la maintenabilité à long terme et la évolutivité d’une bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="9fabd-253">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

<span data-ttu-id="9fabd-254">L’ajout `[<AutoOpen>]` de l’attribut à un module signifie que le module s’ouvre lorsque l’espace de noms conteneur est ouvert.</span><span class="sxs-lookup"><span data-stu-id="9fabd-254">Adding the `[<AutoOpen>]` attribute to a module means the module will be opened when the containing namespace is opened.</span></span> <span data-ttu-id="9fabd-255">L' `[<AutoOpen>]` attribut peut également être appliqué à un assembly pour indiquer un module qui s’ouvre automatiquement lorsque l’assembly est référencé.</span><span class="sxs-lookup"><span data-stu-id="9fabd-255">The `[<AutoOpen>]` attribute may also be applied to an assembly to indicate a module that is automatically opened when the assembly is referenced.</span></span>

<span data-ttu-id="9fabd-256">Par exemple, une bibliothèque de statistiques **MathsHeaven. Statistics** peut contenir des `module MathsHeaven.Statistics.Operators` fonctions contenantes `erf` et `erfc` .</span><span class="sxs-lookup"><span data-stu-id="9fabd-256">For example, a statistics library **MathsHeaven.Statistics** might contain a `module MathsHeaven.Statistics.Operators` containing functions `erf` and `erfc`.</span></span> <span data-ttu-id="9fabd-257">Il est raisonnable de marquer ce module comme `[<AutoOpen>]` .</span><span class="sxs-lookup"><span data-stu-id="9fabd-257">It is reasonable to mark this module as `[<AutoOpen>]`.</span></span> <span data-ttu-id="9fabd-258">Cela `open MathsHeaven.Statistics` permet également d’ouvrir ce module et de placer les noms `erf` et l' `erfc` étendue.</span><span class="sxs-lookup"><span data-stu-id="9fabd-258">This means `open MathsHeaven.Statistics` will also open this module and bring the names `erf` and `erfc` into scope.</span></span> <span data-ttu-id="9fabd-259">Une autre bonne utilisation de `[<AutoOpen>]` est pour les modules contenant des méthodes d’extension.</span><span class="sxs-lookup"><span data-stu-id="9fabd-259">Another good use of `[<AutoOpen>]` is for modules containing extension methods.</span></span>

<span data-ttu-id="9fabd-260">`[<AutoOpen>]`La surutilisation des déclencheurs à des espaces de noms pollués, et l’attribut doit être utilisé avec précaution.</span><span class="sxs-lookup"><span data-stu-id="9fabd-260">Overuse of `[<AutoOpen>]` leads to polluted namespaces, and the attribute should be used with care.</span></span> <span data-ttu-id="9fabd-261">Pour des bibliothèques spécifiques dans des domaines spécifiques, l’utilisation judicieuse de `[<AutoOpen>]` peut aboutir à une meilleure convivialité.</span><span class="sxs-lookup"><span data-stu-id="9fabd-261">For specific libraries in specific domains, judicious use of `[<AutoOpen>]` can lead to better usability.</span></span>

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a><span data-ttu-id="9fabd-262">Envisagez de définir des membres d’opérateur sur des classes pour lesquelles l’utilisation d’opérateurs connus est appropriée</span><span class="sxs-lookup"><span data-stu-id="9fabd-262">Consider defining operator members on classes where using well-known operators is appropriate</span></span>

<span data-ttu-id="9fabd-263">Parfois, les classes sont utilisées pour modéliser des constructions mathématiques telles que des vecteurs.</span><span class="sxs-lookup"><span data-stu-id="9fabd-263">Sometimes classes are used to model mathematical constructs such as Vectors.</span></span> <span data-ttu-id="9fabd-264">Lorsque le domaine modélisé a des opérateurs connus, il est utile de les définir en tant que membres intrinsèques à la classe.</span><span class="sxs-lookup"><span data-stu-id="9fabd-264">When the domain being modeled has well-known operators, defining them as members intrinsic to the class is helpful.</span></span>

```fsharp
type Vector(x: float) =

    member v.X = x

    static member (*) (vector: Vector, scalar: float) = Vector(vector.X * scalar)

    static member (+) (vector1: Vector, vector2: Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

<span data-ttu-id="9fabd-265">Ce guide correspond aux instructions .NET générales pour ces types.</span><span class="sxs-lookup"><span data-stu-id="9fabd-265">This guidance corresponds to general .NET guidance for these types.</span></span> <span data-ttu-id="9fabd-266">Toutefois, il peut également être important dans le codage F #, car cela permet d’utiliser ces types conjointement avec les fonctions et les méthodes F # avec des contraintes de membre, telles que List. sumBy.</span><span class="sxs-lookup"><span data-stu-id="9fabd-266">However, it can be additionally important in F# coding as this allows these types to be used in conjunction with F# functions and methods with member constraints, such as List.sumBy.</span></span>

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a><span data-ttu-id="9fabd-267">Envisagez d’utiliser CompiledName pour fournir un. Nom convivial NET pour les autres consommateurs de langage .NET</span><span class="sxs-lookup"><span data-stu-id="9fabd-267">Consider using CompiledName to provide a .NET-friendly name for other .NET language consumers</span></span>

<span data-ttu-id="9fabd-268">Parfois, vous souhaiterez peut-être nommer un élément dans un style pour les consommateurs F # (par exemple, un membre statique en minuscules afin qu’il apparaisse comme s’il s’agissait d’une fonction liée à un module), mais avec un style différent pour le nom lorsqu’il est compilé dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="9fabd-268">Sometimes you may wish to name something in one style for F# consumers (such as a static member in lower case so that it appears as if it were a module-bound function), but have a different style for the name when it is compiled into an assembly.</span></span> <span data-ttu-id="9fabd-269">Vous pouvez utiliser l' `[<CompiledName>]` attribut pour fournir un style différent pour le code non F # consommant l’assembly.</span><span class="sxs-lookup"><span data-stu-id="9fabd-269">You can use the `[<CompiledName>]` attribute to provide a different style for non F# code consuming the assembly.</span></span>

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

<span data-ttu-id="9fabd-270">À l’aide de `[<CompiledName>]` , vous pouvez utiliser des conventions d’affectation de noms .net pour les consommateurs non F # de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="9fabd-270">By using `[<CompiledName>]`, you can use .NET naming conventions for non F# consumers of the assembly.</span></span>

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a><span data-ttu-id="9fabd-271">Utilisez la surcharge de méthode pour les fonctions membres, si cela fournit une API plus simple</span><span class="sxs-lookup"><span data-stu-id="9fabd-271">Use method overloading for member functions, if doing so provides a simpler API</span></span>

<span data-ttu-id="9fabd-272">La surcharge de méthode est un outil puissant pour simplifier une API qui peut avoir besoin d’effectuer des fonctionnalités similaires, mais avec des options ou des arguments différents.</span><span class="sxs-lookup"><span data-stu-id="9fabd-272">Method overloading is a powerful tool for simplifying an API that may need to perform similar functionality, but with different options or arguments.</span></span>

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

<span data-ttu-id="9fabd-273">En F #, il est plus courant de surcharger le nombre d’arguments que les types d’arguments.</span><span class="sxs-lookup"><span data-stu-id="9fabd-273">In F#, it is more common to overload on number of arguments rather than types of arguments.</span></span>

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="9fabd-274">Masquer les représentations des types d’enregistrement et d’Union si la conception de ces types est susceptible d’évoluer</span><span class="sxs-lookup"><span data-stu-id="9fabd-274">Hide the representations of record and union types if the design of these types is likely to evolve</span></span>

<span data-ttu-id="9fabd-275">Évitez de révéler des représentations concrètes d’objets.</span><span class="sxs-lookup"><span data-stu-id="9fabd-275">Avoid revealing concrete representations of objects.</span></span> <span data-ttu-id="9fabd-276">Par exemple, la représentation concrète des <xref:System.DateTime> valeurs n’est pas révélée par l’API externe publique de la conception de la bibliothèque .net.</span><span class="sxs-lookup"><span data-stu-id="9fabd-276">For example, the concrete representation of <xref:System.DateTime> values is not revealed by the external, public API of the .NET library design.</span></span> <span data-ttu-id="9fabd-277">Au moment de l’exécution, le Common Language Runtime connaît l’implémentation validée qui sera utilisée tout au long de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="9fabd-277">At run time, the Common Language Runtime knows the committed implementation that will be used throughout execution.</span></span> <span data-ttu-id="9fabd-278">Toutefois, le code compilé ne récupère pas lui-même les dépendances sur la représentation concrète.</span><span class="sxs-lookup"><span data-stu-id="9fabd-278">However, compiled code doesn't itself pick up dependencies on the concrete representation.</span></span>

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a><span data-ttu-id="9fabd-279">Éviter l’utilisation de l’héritage d’implémentation pour l’extensibilité</span><span class="sxs-lookup"><span data-stu-id="9fabd-279">Avoid the use of implementation inheritance for extensibility</span></span>

<span data-ttu-id="9fabd-280">En F #, l’héritage d’implémentation est rarement utilisé.</span><span class="sxs-lookup"><span data-stu-id="9fabd-280">In F#, implementation inheritance is rarely used.</span></span> <span data-ttu-id="9fabd-281">En outre, les hiérarchies d’héritage sont souvent complexes et difficiles à modifier lorsque de nouvelles exigences arrivent.</span><span class="sxs-lookup"><span data-stu-id="9fabd-281">Furthermore, inheritance hierarchies are often complex and difficult to change when new requirements arrive.</span></span> <span data-ttu-id="9fabd-282">L’implémentation de l’héritage existe toujours en F # à des fins de compatibilité et de rares cas où il s’agit de la meilleure solution à un problème, mais d’autres techniques doivent être recherchées dans vos programmes F # lors de la conception du polymorphisme, comme l’implémentation de l’interface.</span><span class="sxs-lookup"><span data-stu-id="9fabd-282">Inheritance implementation still exists in F# for compatibility and rare cases where it is the best solution to a problem, but alternative techniques should be sought in your F# programs when designing for polymorphism, such as interface implementation.</span></span>

### <a name="function-and-member-signatures"></a><span data-ttu-id="9fabd-283">Signatures des fonctions et des membres</span><span class="sxs-lookup"><span data-stu-id="9fabd-283">Function and member signatures</span></span>

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a><span data-ttu-id="9fabd-284">Utiliser des tuples pour les valeurs de retour lors du retour d’un petit nombre de valeurs non liées multiples</span><span class="sxs-lookup"><span data-stu-id="9fabd-284">Use tuples for return values when returning a small number of multiple unrelated values</span></span>

<span data-ttu-id="9fabd-285">Voici un bon exemple d’utilisation d’un tuple dans un type de retour :</span><span class="sxs-lookup"><span data-stu-id="9fabd-285">Here is a good example of using a tuple in a return type:</span></span>

```fsharp
val divrem: BigInteger -> BigInteger -> BigInteger * BigInteger
```

<span data-ttu-id="9fabd-286">Pour les types de retour contenant de nombreux composants, ou où les composants sont associés à une seule entité identifiable, envisagez d’utiliser un type nommé au lieu d’un tuple.</span><span class="sxs-lookup"><span data-stu-id="9fabd-286">For return types containing many components, or where the components are related to a single identifiable entity, consider using a named type instead of a tuple.</span></span>

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a><span data-ttu-id="9fabd-287">Utilisation `Async<T>` pour la programmation asynchrone aux limites de l’API F #</span><span class="sxs-lookup"><span data-stu-id="9fabd-287">Use `Async<T>` for async programming at F# API boundaries</span></span>

<span data-ttu-id="9fabd-288">S’il existe une opération synchrone correspondante nommée `Operation` qui retourne un `T` , alors l’opération asynchrone doit être nommée `AsyncOperation` si elle retourne `Async<T>` ou `OperationAsync` si elle retourne `Task<T>` .</span><span class="sxs-lookup"><span data-stu-id="9fabd-288">If there is a corresponding synchronous operation named `Operation` that returns a `T`, then the async operation should be named `AsyncOperation` if it returns `Async<T>` or `OperationAsync` if it returns `Task<T>`.</span></span> <span data-ttu-id="9fabd-289">Pour les types .NET couramment utilisés qui exposent des méthodes Begin/End, envisagez `Async.FromBeginEnd` d’utiliser pour écrire des méthodes d’extension en tant que façade pour fournir le modèle de programmation F # Async à ces API .net.</span><span class="sxs-lookup"><span data-stu-id="9fabd-289">For commonly used .NET types that expose Begin/End methods, consider using `Async.FromBeginEnd` to write extension methods as a façade to provide the F# async programming model to those .NET APIs.</span></span>

```fsharp
type SomeType =
    member this.Compute(x:int): int =
        ...
    member this.AsyncCompute(x:int): Async<int> =
        ...

type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        ...
```

### <a name="exceptions"></a><span data-ttu-id="9fabd-290">Exceptions</span><span class="sxs-lookup"><span data-stu-id="9fabd-290">Exceptions</span></span>

<span data-ttu-id="9fabd-291">Consultez [gestion des erreurs](conventions.md#error-management) pour en savoir plus sur l’utilisation appropriée des exceptions, des résultats et des options.</span><span class="sxs-lookup"><span data-stu-id="9fabd-291">See [Error Management](conventions.md#error-management) to learn about appropriate use of exceptions, results, and options.</span></span>

### <a name="extension-members"></a><span data-ttu-id="9fabd-292">Membres d’extension</span><span class="sxs-lookup"><span data-stu-id="9fabd-292">Extension Members</span></span>

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a><span data-ttu-id="9fabd-293">Appliquez avec soin les membres d’extension F # dans les composants F #-to-F #</span><span class="sxs-lookup"><span data-stu-id="9fabd-293">Carefully apply F# extension members in F#-to-F# components</span></span>

<span data-ttu-id="9fabd-294">En général, les membres d’extension F # doivent être utilisés uniquement pour les opérations qui se trouvent dans la fermeture des opérations intrinsèques associées à un type dans la majorité de ses modes d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="9fabd-294">F# extension members should generally only be used for operations that are in the closure of intrinsic operations associated with a type in the majority of its modes of use.</span></span> <span data-ttu-id="9fabd-295">Une utilisation courante consiste à fournir des API qui sont plus idiomatique à F # pour divers types .NET :</span><span class="sxs-lookup"><span data-stu-id="9fabd-295">One common use is to provide APIs that are more idiomatic to F# for various .NET types:</span></span>

```fsharp
type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        Async.FromBeginEnd(this.BeginReceive, this.EndReceive)

type System.Collections.Generic.IDictionary<'Key,'Value> with
    member this.TryGet key =
        let ok, v = this.TryGetValue key
        if ok then Some v else None
```

### <a name="union-types"></a><span data-ttu-id="9fabd-296">Types d’Union</span><span class="sxs-lookup"><span data-stu-id="9fabd-296">Union Types</span></span>

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a><span data-ttu-id="9fabd-297">Utiliser des unions discriminées plutôt que des hiérarchies de classes pour les données structurées en arborescence</span><span class="sxs-lookup"><span data-stu-id="9fabd-297">Use discriminated unions instead of class hierarchies for tree-structured data</span></span>

<span data-ttu-id="9fabd-298">Les structures de type arborescence sont définies de manière récursive.</span><span class="sxs-lookup"><span data-stu-id="9fabd-298">Tree-like structures are recursively defined.</span></span> <span data-ttu-id="9fabd-299">Cela est délicat avec l’héritage, mais élégant avec des unions discriminées.</span><span class="sxs-lookup"><span data-stu-id="9fabd-299">This is awkward with inheritance, but elegant with Discriminated Unions.</span></span>

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

<span data-ttu-id="9fabd-300">Le fait de représenter des données d’arborescence avec des unions discriminées vous permet également de tirer parti de l’exhaustivité dans les critères spéciaux.</span><span class="sxs-lookup"><span data-stu-id="9fabd-300">Representing tree-like data with Discriminated Unions also allows you to benefit from exhaustiveness in pattern matching.</span></span>

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a><span data-ttu-id="9fabd-301">Utilisez `[<RequireQualifiedAccess>]` sur les types d’Union dont les noms de cas ne sont pas suffisamment uniques</span><span class="sxs-lookup"><span data-stu-id="9fabd-301">Use `[<RequireQualifiedAccess>]` on union types whose case names are not sufficiently unique</span></span>

<span data-ttu-id="9fabd-302">Vous pouvez vous trouver dans un domaine où le même nom est le meilleur nom pour différents éléments, tels que les cas d’union discriminée.</span><span class="sxs-lookup"><span data-stu-id="9fabd-302">You may find yourself in a domain where the same name is the best name for different things, such as Discriminated Union cases.</span></span> <span data-ttu-id="9fabd-303">Vous pouvez utiliser `[<RequireQualifiedAccess>]` pour lever l’ambiguïté des noms de cas afin d’éviter de déclencher des erreurs confuses en raison de l’occultation en fonction de l’ordre des `open` instructions.</span><span class="sxs-lookup"><span data-stu-id="9fabd-303">You can use `[<RequireQualifiedAccess>]` to disambiguate case names in order to avoid triggering confusing errors due to shadowing dependent on the ordering of `open` statements</span></span>

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="9fabd-304">Masquer les représentations des unions discriminées pour les API compatibles binaires si la conception de ces types est susceptible d’évoluer</span><span class="sxs-lookup"><span data-stu-id="9fabd-304">Hide the representations of discriminated unions for binary compatible APIs if the design of these types is likely to evolve</span></span>

<span data-ttu-id="9fabd-305">Les types unions reposent sur les formulaires de critères spéciaux F # pour un modèle de programmation succinct.</span><span class="sxs-lookup"><span data-stu-id="9fabd-305">Unions types rely on F# pattern-matching forms for a succinct programming model.</span></span> <span data-ttu-id="9fabd-306">Comme mentionné précédemment, vous devez éviter de révéler des représentations de données concrètes si la conception de ces types est susceptible d’évoluer.</span><span class="sxs-lookup"><span data-stu-id="9fabd-306">As mentioned previously, you should avoid revealing concrete data representations if the design of these types is likely to evolve.</span></span>

<span data-ttu-id="9fabd-307">Par exemple, la représentation d’une union discriminée peut être masquée à l’aide d’une déclaration privée ou interne, ou à l’aide d’un fichier de signature.</span><span class="sxs-lookup"><span data-stu-id="9fabd-307">For example, the representation of a discriminated union can be hidden using a private or internal declaration, or by using a signature file.</span></span>

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

<span data-ttu-id="9fabd-308">Si vous révélez des unions discriminées de façon non discriminatoire, il peut s’avérer difficile de créer une version de votre bibliothèque sans rompre le code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9fabd-308">If you reveal discriminated unions indiscriminately, you may find it hard to version your library without breaking user code.</span></span> <span data-ttu-id="9fabd-309">Au lieu de cela, envisagez de révéler un ou plusieurs modèles actifs afin d’autoriser les critères spéciaux sur les valeurs de votre type.</span><span class="sxs-lookup"><span data-stu-id="9fabd-309">Instead, consider revealing one or more active patterns to permit pattern matching over values of your type.</span></span>

<span data-ttu-id="9fabd-310">Les modèles actifs fournissent un autre moyen de fournir aux consommateurs F # des critères spéciaux tout en évitant d’exposer directement les types d’Union F #.</span><span class="sxs-lookup"><span data-stu-id="9fabd-310">Active patterns provide an alternate way to provide F# consumers with pattern matching while avoiding exposing F# Union Types directly.</span></span>

### <a name="inline-functions-and-member-constraints"></a><span data-ttu-id="9fabd-311">Fonctions inline et contraintes de membre</span><span class="sxs-lookup"><span data-stu-id="9fabd-311">Inline Functions and Member Constraints</span></span>

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a><span data-ttu-id="9fabd-312">Définir des algorithmes numériques génériques à l’aide de fonctions inline avec des contraintes de membre implicites et des types génériques résolus statiquement</span><span class="sxs-lookup"><span data-stu-id="9fabd-312">Define generic numeric algorithms using inline functions with implied member constraints and statically resolved generic types</span></span>

<span data-ttu-id="9fabd-313">Les contraintes de membre arithmétiques et les contraintes de comparaison F # sont une norme pour la programmation F #.</span><span class="sxs-lookup"><span data-stu-id="9fabd-313">Arithmetic member constraints and F# comparison constraints are a standard for F# programming.</span></span> <span data-ttu-id="9fabd-314">Considérons par exemple le code suivant :</span><span class="sxs-lookup"><span data-stu-id="9fabd-314">For example, consider the following code:</span></span>

```fsharp
let inline highestCommonFactor a b =
    let rec loop a b =
        if a = LanguagePrimitives.GenericZero<_> then b
        elif a < b then loop a (b - a)
        else loop (a - b) b
    loop a b
```

<span data-ttu-id="9fabd-315">Le type de cette fonction est le suivant :</span><span class="sxs-lookup"><span data-stu-id="9fabd-315">The type of this function is as follows:</span></span>

```fsharp
val inline highestCommonFactor : ^T -> ^T -> ^T
                when ^T : (static member Zero : ^T)
                and ^T : (static member ( - ) : ^T * ^T -> ^T)
                and ^T : equality
                and ^T : comparison
```

<span data-ttu-id="9fabd-316">Il s’agit d’une fonction appropriée pour une API publique dans une bibliothèque mathématique.</span><span class="sxs-lookup"><span data-stu-id="9fabd-316">This is a suitable function for a public API in a mathematical library.</span></span>

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a><span data-ttu-id="9fabd-317">Évitez d’utiliser des contraintes de membre pour simuler des classes de type et des types de canard</span><span class="sxs-lookup"><span data-stu-id="9fabd-317">Avoid using member constraints to simulate type classes and duck typing</span></span>

<span data-ttu-id="9fabd-318">Il est possible de simuler un « typage de canard » à l’aide de contraintes de membre F #.</span><span class="sxs-lookup"><span data-stu-id="9fabd-318">It is possible to simulate "duck typing" using F# member constraints.</span></span> <span data-ttu-id="9fabd-319">Toutefois, les membres qui l’utilisent ne doivent pas en général être utilisés dans les conceptions de bibliothèque F # vers F #.</span><span class="sxs-lookup"><span data-stu-id="9fabd-319">However, members that make use of this should not in general be used in F#-to-F# library designs.</span></span> <span data-ttu-id="9fabd-320">Cela est dû au fait que les conceptions de bibliothèques basées sur des contraintes implicites inconnues ou non standard ont tendance à amener le code utilisateur à devenir rigide et à être lié à un modèle d’infrastructure particulier.</span><span class="sxs-lookup"><span data-stu-id="9fabd-320">This is because library designs based on unfamiliar or non-standard implicit constraints tend to cause user code to become inflexible and tied to one particular framework pattern.</span></span>

<span data-ttu-id="9fabd-321">En outre, il y a de fortes chances pour que l’utilisation intensive de contraintes de membre de cette manière puisse entraîner des temps de compilation très longs.</span><span class="sxs-lookup"><span data-stu-id="9fabd-321">Additionally, there is a good chance that heavy use of member constraints in this manner can result in very long compile times.</span></span>

### <a name="operator-definitions"></a><span data-ttu-id="9fabd-322">Définitions d’opérateur</span><span class="sxs-lookup"><span data-stu-id="9fabd-322">Operator Definitions</span></span>

#### <a name="avoid-defining-custom-symbolic-operators"></a><span data-ttu-id="9fabd-323">Évitez de définir des opérateurs symboliques personnalisés</span><span class="sxs-lookup"><span data-stu-id="9fabd-323">Avoid defining custom symbolic operators</span></span>

<span data-ttu-id="9fabd-324">Les opérateurs personnalisés sont essentiels dans certaines situations et sont des appareils notations très utiles dans un grand corps de code d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="9fabd-324">Custom operators are essential in some situations and are highly useful notational devices within a large body of implementation code.</span></span> <span data-ttu-id="9fabd-325">Pour les nouveaux utilisateurs d’une bibliothèque, les fonctions nommées sont souvent plus faciles à utiliser.</span><span class="sxs-lookup"><span data-stu-id="9fabd-325">For new users of a library, named functions are often easier to use.</span></span> <span data-ttu-id="9fabd-326">En outre, les opérateurs symboliques personnalisés peuvent être difficiles à documenter et les utilisateurs trouvent qu’il est plus difficile de rechercher de l’aide sur les opérateurs, en raison des limitations existantes de l’IDE et des moteurs de recherche.</span><span class="sxs-lookup"><span data-stu-id="9fabd-326">In addition, custom symbolic operators can be hard to document, and users find it more difficult to look up help on operators, due to existing limitations in IDE and search engines.</span></span>

<span data-ttu-id="9fabd-327">Par conséquent, il est préférable de publier vos fonctionnalités en tant que fonctions et membres nommés, et d’exposer en outre des opérateurs pour cette fonctionnalité uniquement si les avantages en notation compensent la documentation et le coût cognitif de leur utilisation.</span><span class="sxs-lookup"><span data-stu-id="9fabd-327">As a result, it is best to publish your functionality as named functions and members, and additionally expose operators for this functionality only if the notational benefits outweigh the documentation and cognitive cost of having them.</span></span>

### <a name="units-of-measure"></a><span data-ttu-id="9fabd-328">Unités de mesure</span><span class="sxs-lookup"><span data-stu-id="9fabd-328">Units of Measure</span></span>

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a><span data-ttu-id="9fabd-329">Utiliser avec soin les unités de mesure pour la sécurité de type ajoutée dans le code F #</span><span class="sxs-lookup"><span data-stu-id="9fabd-329">Carefully use units of measure for added type safety in F# code</span></span>

<span data-ttu-id="9fabd-330">Les informations de saisie supplémentaires pour les unités de mesure sont effacées lorsqu’elles sont affichées par d’autres langages .NET.</span><span class="sxs-lookup"><span data-stu-id="9fabd-330">Additional typing information for units of measure is erased when viewed by other .NET languages.</span></span> <span data-ttu-id="9fabd-331">N’oubliez pas que les composants, les outils et la réflexion .NET voient les types-sans unités.</span><span class="sxs-lookup"><span data-stu-id="9fabd-331">Be aware that .NET components, tools, and reflection will see types-sans-units.</span></span> <span data-ttu-id="9fabd-332">Par exemple, les consommateurs C# verront `float` plutôt que `float<kg>` .</span><span class="sxs-lookup"><span data-stu-id="9fabd-332">For example, C# consumers will see `float` rather than `float<kg>`.</span></span>

### <a name="type-abbreviations"></a><span data-ttu-id="9fabd-333">Abréviations de types</span><span class="sxs-lookup"><span data-stu-id="9fabd-333">Type Abbreviations</span></span>

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a><span data-ttu-id="9fabd-334">Utilisez avec soin les abréviations de type pour simplifier le code F #</span><span class="sxs-lookup"><span data-stu-id="9fabd-334">Carefully use type abbreviations to simplify F# code</span></span>

<span data-ttu-id="9fabd-335">Les composants, les outils et la réflexion .NET ne voient pas les noms abrégés pour les types.</span><span class="sxs-lookup"><span data-stu-id="9fabd-335">.NET components, tools, and reflection will not see abbreviated names for types.</span></span> <span data-ttu-id="9fabd-336">Une utilisation significative des abréviations de type peut également rendre un domaine plus complexe qu’il ne l’est, ce qui peut dérouter les consommateurs.</span><span class="sxs-lookup"><span data-stu-id="9fabd-336">Significant usage of type abbreviations can also make a domain appear more complex than it actually is, which could confuse consumers.</span></span>

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a><span data-ttu-id="9fabd-337">Évitez les abréviations de type pour les types publics dont les membres et les propriétés doivent être intrinsèquement différents de ceux disponibles sur le type en cours d’abréviation</span><span class="sxs-lookup"><span data-stu-id="9fabd-337">Avoid type abbreviations for public types whose members and properties should be intrinsically different to those available on the type being abbreviated</span></span>

<span data-ttu-id="9fabd-338">Dans ce cas, le type en cours d’abréviation révèle trop d’informations sur la représentation du type réel en cours de définition.</span><span class="sxs-lookup"><span data-stu-id="9fabd-338">In this case, the type being abbreviated reveals too much about the representation of the actual type being defined.</span></span> <span data-ttu-id="9fabd-339">Envisagez plutôt d’encapsuler l’abréviation dans un type de classe ou une union discriminée à cas unique (ou, lorsque les performances sont essentielles, envisagez d’utiliser un type struct pour encapsuler l’abréviation).</span><span class="sxs-lookup"><span data-stu-id="9fabd-339">Instead, consider wrapping the abbreviation in a class type or a single-case discriminated union (or, when performance is essential, consider using a struct type to wrap the abbreviation).</span></span>

<span data-ttu-id="9fabd-340">Par exemple, il est tentant de définir un mappage multiple comme un cas spécial d’une carte F #, par exemple :</span><span class="sxs-lookup"><span data-stu-id="9fabd-340">For example, it is tempting to define a multi-map as a special case of an F# map, for example:</span></span>

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

<span data-ttu-id="9fabd-341">Toutefois, les opérations logiques de pointage sur ce type ne sont pas les mêmes que les opérations sur une carte, par exemple, il est raisonnable que le mappage d’opérateur de recherche. [clé] retourne la liste vide si la clé n’est pas dans le dictionnaire, au lieu de lever une exception.</span><span class="sxs-lookup"><span data-stu-id="9fabd-341">However, the logical dot-notation operations on this type are not the same as the operations on a Map – for example, it is reasonable that the lookup operator map.[key] return the empty list if the key is not in the dictionary, rather than raising an exception.</span></span>

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="9fabd-342">Instructions pour les bibliothèques à utiliser à partir d’autres langages .NET</span><span class="sxs-lookup"><span data-stu-id="9fabd-342">Guidelines for libraries for Use from other .NET Languages</span></span>

<span data-ttu-id="9fabd-343">Lorsque vous concevez des bibliothèques à utiliser à partir d’autres langages .NET, il est important de respecter les règles de conception de la [bibliothèque .net](../../standard/design-guidelines/index.md).</span><span class="sxs-lookup"><span data-stu-id="9fabd-343">When designing libraries for use from other .NET languages, it is important to adhere to the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="9fabd-344">Dans ce document, ces bibliothèques sont étiquetées en tant que bibliothèques .NET vanille, par opposition aux bibliothèques F # qui utilisent des constructions F # sans restriction.</span><span class="sxs-lookup"><span data-stu-id="9fabd-344">In this document, these libraries are labeled as vanilla .NET libraries, as opposed to F#-facing libraries that use F# constructs without restriction.</span></span> <span data-ttu-id="9fabd-345">La conception de bibliothèques .NET vanille signifie que les API familières et idiomatique sont cohérentes avec le reste du .NET Framework en minimisant l’utilisation des constructions spécifiques à F # dans l’API publique.</span><span class="sxs-lookup"><span data-stu-id="9fabd-345">Designing vanilla .NET libraries means providing familiar and idiomatic APIs consistent with the rest of the .NET Framework by minimizing the use of F#-specific constructs in the public API.</span></span> <span data-ttu-id="9fabd-346">Les règles sont décrites dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="9fabd-346">The rules are explained in the following sections.</span></span>

### <a name="namespace-and-type-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="9fabd-347">Conception de l’espace de noms et du type (pour les bibliothèques à utiliser à partir d’autres langages .NET)</span><span class="sxs-lookup"><span data-stu-id="9fabd-347">Namespace and Type design (for libraries for use from other .NET Languages)</span></span>

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a><span data-ttu-id="9fabd-348">Appliquer les conventions d’affectation de noms .NET à l’API publique de vos composants</span><span class="sxs-lookup"><span data-stu-id="9fabd-348">Apply the .NET naming conventions to the public API of your components</span></span>

<span data-ttu-id="9fabd-349">Portez une attention particulière à l’utilisation des noms abrégés et des recommandations en matière de mise en majuscules .NET.</span><span class="sxs-lookup"><span data-stu-id="9fabd-349">Pay special attention to the use of abbreviated names and the .NET capitalization guidelines.</span></span>

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a><span data-ttu-id="9fabd-350">Utilisez les espaces de noms, les types et les membres comme structure d’organisation principale de vos composants</span><span class="sxs-lookup"><span data-stu-id="9fabd-350">Use namespaces, types, and members as the primary organizational structure for your components</span></span>

<span data-ttu-id="9fabd-351">Tous les fichiers contenant des fonctionnalités publiques doivent commencer par une `namespace` déclaration, et les seules entités publiques dans les espaces de noms doivent être des types.</span><span class="sxs-lookup"><span data-stu-id="9fabd-351">All files containing public functionality should begin with a `namespace` declaration, and the only public-facing entities in namespaces should be types.</span></span> <span data-ttu-id="9fabd-352">N’utilisez pas de modules F #.</span><span class="sxs-lookup"><span data-stu-id="9fabd-352">Do not use F# modules.</span></span>

<span data-ttu-id="9fabd-353">Utilisez des modules non publics pour stocker le code d’implémentation, les types d’utilitaire et les fonctions utilitaires.</span><span class="sxs-lookup"><span data-stu-id="9fabd-353">Use non-public modules to hold implementation code, utility types, and utility functions.</span></span>

<span data-ttu-id="9fabd-354">Les types statiques doivent être préférés aux modules, car ils permettent une évolution future de l’API afin d’utiliser la surcharge et d’autres concepts de conception de l’API .NET qui ne peuvent pas être utilisés dans les modules F #.</span><span class="sxs-lookup"><span data-stu-id="9fabd-354">Static types should be preferred over modules, as they allow for future evolution of the API to use overloading and other .NET API design concepts that may not be used within F# modules.</span></span>

<span data-ttu-id="9fabd-355">Par exemple, à la place de l’API publique suivante :</span><span class="sxs-lookup"><span data-stu-id="9fabd-355">For example, in place of the following public API:</span></span>

```fsharp
module Fabrikam

module Utilities =
    let Name = "Bob"
    let Add2 x y = x + y
    let Add3 x y z = x + y + z
```

<span data-ttu-id="9fabd-356">À la place :</span><span class="sxs-lookup"><span data-stu-id="9fabd-356">Consider instead:</span></span>

```fsharp
namespace Fabrikam

[<AbstractClass; Sealed>]
type Utilities =
    static member Name = "Bob"
    static member Add(x,y) = x + y
    static member Add(x,y,z) = x + y + z
```

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a><span data-ttu-id="9fabd-357">Utilisez les types d’enregistrements F # dans les API .NET vanille Si la conception des types ne évoluera pas</span><span class="sxs-lookup"><span data-stu-id="9fabd-357">Use F# record types in vanilla .NET APIs if the design of the types won't evolve</span></span>

<span data-ttu-id="9fabd-358">Les types d’enregistrements F # sont compilés en une classe .NET simple.</span><span class="sxs-lookup"><span data-stu-id="9fabd-358">F# record types compile to a simple .NET class.</span></span> <span data-ttu-id="9fabd-359">Celles-ci conviennent pour certains types simples et stables dans les API.</span><span class="sxs-lookup"><span data-stu-id="9fabd-359">These are suitable for some simple, stable types in APIs.</span></span> <span data-ttu-id="9fabd-360">Envisagez `[<NoEquality>]` d’utiliser les `[<NoComparison>]` attributs et pour supprimer la génération automatique des interfaces.</span><span class="sxs-lookup"><span data-stu-id="9fabd-360">Consider using the `[<NoEquality>]` and `[<NoComparison>]` attributes to suppress the automatic generation of interfaces.</span></span> <span data-ttu-id="9fabd-361">Évitez également d’utiliser des champs d’enregistrement mutables dans des API .NET vanille, car celles-ci exposent un champ public.</span><span class="sxs-lookup"><span data-stu-id="9fabd-361">Also avoid using mutable record fields in vanilla .NET APIs as these expose a public field.</span></span> <span data-ttu-id="9fabd-362">Déterminez toujours si une classe fournirait une option plus flexible pour l’évolution future de l’API.</span><span class="sxs-lookup"><span data-stu-id="9fabd-362">Always consider whether a class would provide a more flexible option for future evolution of the API.</span></span>

<span data-ttu-id="9fabd-363">Par exemple, le code F # suivant expose l’API publique à un consommateur C# :</span><span class="sxs-lookup"><span data-stu-id="9fabd-363">For example, the following F# code exposes the public API to a C# consumer:</span></span>

<span data-ttu-id="9fabd-364">F# :</span><span class="sxs-lookup"><span data-stu-id="9fabd-364">F#:</span></span>

```fsharp
[<NoEquality; NoComparison>]
type MyRecord =
    { FirstThing: int
        SecondThing: string }
```

<span data-ttu-id="9fabd-365">C# :</span><span class="sxs-lookup"><span data-stu-id="9fabd-365">C#:</span></span>

```csharp
public sealed class MyRecord
{
    public MyRecord(int firstThing, string secondThing);
    public int FirstThing { get; }
    public string SecondThing { get; }
}
```

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a><span data-ttu-id="9fabd-366">Masquer la représentation des types d’Union F # dans les API .NET vanille</span><span class="sxs-lookup"><span data-stu-id="9fabd-366">Hide the representation of F# union types in vanilla .NET APIs</span></span>

<span data-ttu-id="9fabd-367">Les types d’Union f # ne sont généralement pas utilisés dans les limites d’un composant, même pour le codage F # en F #.</span><span class="sxs-lookup"><span data-stu-id="9fabd-367">F# union types are not commonly used across component boundaries, even for F#-to-F# coding.</span></span> <span data-ttu-id="9fabd-368">Ils constituent un excellent dispositif d’implémentation lorsqu’ils sont utilisés en interne dans les composants et les bibliothèques.</span><span class="sxs-lookup"><span data-stu-id="9fabd-368">They are an excellent implementation device when used internally within components and libraries.</span></span>

<span data-ttu-id="9fabd-369">Lors de la conception d’une API .NET vanille, pensez à masquer la représentation d’un type d’Union à l’aide d’une déclaration privée ou d’un fichier de signature.</span><span class="sxs-lookup"><span data-stu-id="9fabd-369">When designing a vanilla .NET API, consider hiding the representation of a union type by using either a private declaration or a signature file.</span></span>

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

<span data-ttu-id="9fabd-370">Vous pouvez également augmenter les types qui utilisent une représentation d’Union en interne avec des membres pour fournir un souhaité. API .net.</span><span class="sxs-lookup"><span data-stu-id="9fabd-370">You may also augment types that use a union representation internally with members to provide a desired .NET-facing API.</span></span>

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True

    /// A public member for use from C#
    member x.Evaluate =
        match x with
        | And(a,b) -> a.Evaluate && b.Evaluate
        | Not a -> not a.Evaluate
        | True -> true

    /// A public member for use from C#
    static member CreateAnd(a,b) = And(a,b)
```

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a><span data-ttu-id="9fabd-371">Concevoir une interface utilisateur graphique et d’autres composants à l’aide des modèles de conception de l’infrastructure</span><span class="sxs-lookup"><span data-stu-id="9fabd-371">Design GUI and other components using the design patterns of the framework</span></span>

<span data-ttu-id="9fabd-372">Il existe de nombreuses infrastructures différentes disponibles dans .NET, comme WinForms, WPF et ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9fabd-372">There are many different frameworks available within .NET, such as WinForms, WPF, and ASP.NET.</span></span> <span data-ttu-id="9fabd-373">Les conventions de nommage et de conception de chaque doivent être utilisées si vous concevez des composants à utiliser dans ces infrastructures.</span><span class="sxs-lookup"><span data-stu-id="9fabd-373">Naming and design conventions for each should be used if you are designing components for use in these frameworks.</span></span> <span data-ttu-id="9fabd-374">Par exemple, pour la programmation WPF, adoptez des modèles de conception WPF pour les classes que vous concevez.</span><span class="sxs-lookup"><span data-stu-id="9fabd-374">For example, for WPF programming, adopt WPF design patterns for the classes you are designing.</span></span> <span data-ttu-id="9fabd-375">Pour les modèles dans la programmation de l’interface utilisateur, utilisez des modèles de conception tels que les événements et les collections basées sur les notifications, tels que ceux qui se trouvent dans <xref:System.Collections.ObjectModel> .</span><span class="sxs-lookup"><span data-stu-id="9fabd-375">For models in user interface programming, use design patterns such as events and notification-based collections such as those found in <xref:System.Collections.ObjectModel>.</span></span>

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="9fabd-376">Conception d’objets et de membres (pour les bibliothèques à utiliser à partir d’autres langages .NET)</span><span class="sxs-lookup"><span data-stu-id="9fabd-376">Object and Member design (for libraries for use from other .NET Languages)</span></span>

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a><span data-ttu-id="9fabd-377">Utiliser l’attribut CLIEvent pour exposer des événements .NET</span><span class="sxs-lookup"><span data-stu-id="9fabd-377">Use the CLIEvent attribute to expose .NET events</span></span>

<span data-ttu-id="9fabd-378">Construit un `DelegateEvent` avec un type délégué .net spécifique qui prend un objet et `EventArgs` (plutôt qu’un `Event` , qui utilise simplement le `FSharpHandler` type par défaut) afin que les événements soient publiés de la manière familière vers d’autres langages .net.</span><span class="sxs-lookup"><span data-stu-id="9fabd-378">Construct a `DelegateEvent` with a specific .NET delegate type that takes an object and `EventArgs` (rather than an `Event`, which just uses the `FSharpHandler` type by default) so that the events are published in the familiar way to other .NET languages.</span></span>

```fsharp
type MyBadType() =
    let myEv = new Event<int>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish

type MyEventArgs(x: int) =
    inherit System.EventArgs()
    member this.X = x

    /// A type in a component designed for use from other .NET languages
type MyGoodType() =
    let myEv = new DelegateEvent<EventHandler<MyEventArgs>>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish
```

#### <a name="expose-asynchronous-operations-as-methods-that-return-net-tasks"></a><span data-ttu-id="9fabd-379">Exposer des opérations asynchrones en tant que méthodes qui retournent des tâches .NET</span><span class="sxs-lookup"><span data-stu-id="9fabd-379">Expose asynchronous operations as methods that return .NET tasks</span></span>

<span data-ttu-id="9fabd-380">Les tâches sont utilisées dans .NET pour représenter des calculs asynchrones actifs.</span><span class="sxs-lookup"><span data-stu-id="9fabd-380">Tasks are used in .NET to represent active asynchronous computations.</span></span> <span data-ttu-id="9fabd-381">Les tâches sont en général moins compositionnels que `Async<T>` les objets F #, car elles représentent des tâches « déjà en cours d’exécution » et ne peuvent pas être composées de la même façon que pour effectuer une composition parallèle, ou qui masquent la propagation des signaux d’annulation et d’autres paramètres contextuels.</span><span class="sxs-lookup"><span data-stu-id="9fabd-381">Tasks are in general less compositional than F# `Async<T>` objects, since they represent "already executing" tasks and can't be composed together in ways that perform parallel composition, or which hide the propagation of cancellation signals and other contextual parameters.</span></span>

<span data-ttu-id="9fabd-382">Toutefois, malgré cela, les méthodes qui retournent des tâches sont la représentation standard de la programmation asynchrone sur .NET.</span><span class="sxs-lookup"><span data-stu-id="9fabd-382">However, despite this, methods that return Tasks are the standard representation of asynchronous programming on .NET.</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int): Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

<span data-ttu-id="9fabd-383">Vous souhaiterez souvent également accepter un jeton d’annulation explicite :</span><span class="sxs-lookup"><span data-stu-id="9fabd-383">You will frequently also want to accept an explicit cancellation token:</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x: int): Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a><span data-ttu-id="9fabd-384">Utiliser les types délégués .NET au lieu des types de fonctions F #</span><span class="sxs-lookup"><span data-stu-id="9fabd-384">Use .NET delegate types instead of F# function types</span></span>

<span data-ttu-id="9fabd-385">Ici « types de fonction F # » sont des types « flèche » comme `int -> int` .</span><span class="sxs-lookup"><span data-stu-id="9fabd-385">Here "F# function types" mean "arrow" types like `int -> int`.</span></span>

<span data-ttu-id="9fabd-386">Au lieu de :</span><span class="sxs-lookup"><span data-stu-id="9fabd-386">Instead of this:</span></span>

```fsharp
member this.Transform(f: int->int) =
    ...
```

<span data-ttu-id="9fabd-387">Procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="9fabd-387">Do this:</span></span>

```fsharp
member this.Transform(f: Func<int,int>) =
    ...
```

<span data-ttu-id="9fabd-388">Le type de fonction F # apparaît comme `class FSharpFunc<T,U>` pour d’autres langages .net et est moins adapté aux fonctionnalités de langage et aux outils qui comprennent les types délégués.</span><span class="sxs-lookup"><span data-stu-id="9fabd-388">The F# function type appears as `class FSharpFunc<T,U>` to other .NET languages, and is less suitable for language features and tooling that understands delegate types.</span></span> <span data-ttu-id="9fabd-389">Lors de la création d’une méthode d’ordre supérieur ciblant .NET Framework 3,5 ou une version ultérieure, les `System.Func` `System.Action` délégués et sont les API appropriées à publier pour permettre aux développeurs .net d’utiliser ces API à des fins de faible frottement.</span><span class="sxs-lookup"><span data-stu-id="9fabd-389">When authoring a higher-order method targeting .NET Framework 3.5 or higher, the `System.Func` and `System.Action` delegates are the right APIs to publish to enable .NET developers to consume these APIs in a low-friction manner.</span></span> <span data-ttu-id="9fabd-390">(Lorsque vous ciblez .NET Framework 2,0, les types délégués définis par le système sont plus limités ; envisagez d’utiliser des types délégués prédéfinis tels que `System.Converter<T,U>` ou définissant un type délégué spécifique.)</span><span class="sxs-lookup"><span data-stu-id="9fabd-390">(When targeting .NET Framework 2.0, the system-defined delegate types are more limited; consider using predefined delegate types such as `System.Converter<T,U>` or defining a specific delegate type.)</span></span>

<span data-ttu-id="9fabd-391">À l’inverse, les délégués .NET ne sont pas naturels pour les bibliothèques F # (consultez la section suivante sur les bibliothèques en F #).</span><span class="sxs-lookup"><span data-stu-id="9fabd-391">On the flip side, .NET delegates are not natural for F#-facing libraries (see the next Section on F#-facing libraries).</span></span> <span data-ttu-id="9fabd-392">Par conséquent, une stratégie d’implémentation courante lors du développement de méthodes d’ordre supérieur pour des bibliothèques .NET vanille consiste à créer toute l’implémentation à l’aide de types de fonction F #, puis à créer l’API publique à l’aide de délégués comme une façade fine au-dessus de l’implémentation réelle de F #.</span><span class="sxs-lookup"><span data-stu-id="9fabd-392">As a result, a common implementation strategy when developing higher-order methods for vanilla .NET libraries is to author all the implementation using F# function types, and then create the public API using delegates as a thin façade atop the actual F# implementation.</span></span>

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a><span data-ttu-id="9fabd-393">Utilisez le modèle TryGetValue au lieu de retourner des valeurs d’option F #, et préférer la surcharge de méthode pour prendre des valeurs d’option F # comme arguments</span><span class="sxs-lookup"><span data-stu-id="9fabd-393">Use the TryGetValue pattern instead of returning F# option values, and prefer method overloading to taking F# option values as arguments</span></span>

<span data-ttu-id="9fabd-394">Les modèles courants d’utilisation pour le type d’option F # dans les API sont mieux implémentés dans les API .NET vanille à l’aide des techniques de conception .NET standard.</span><span class="sxs-lookup"><span data-stu-id="9fabd-394">Common patterns of use for the F# option type in APIs are better implemented in vanilla .NET APIs using standard .NET design techniques.</span></span> <span data-ttu-id="9fabd-395">Au lieu de retourner une valeur d’option F #, envisagez d’utiliser le type de retour bool plus un paramètre out comme dans le modèle « TryGetValue ».</span><span class="sxs-lookup"><span data-stu-id="9fabd-395">Instead of returning an F# option value, consider using the bool return type plus an out parameter as in the "TryGetValue" pattern.</span></span> <span data-ttu-id="9fabd-396">Et au lieu de prendre des valeurs d’option F # comme paramètres, envisagez d’utiliser la surcharge de méthode ou des arguments facultatifs.</span><span class="sxs-lookup"><span data-stu-id="9fabd-396">And instead of taking F# option values as parameters, consider using method overloading or optional arguments.</span></span>

```fsharp
member this.ReturnOption() = Some 3

member this.ReturnBoolAndOut(outVal: byref<int>) =
    outVal <- 3
    true

member this.ParamOption(x: int, y: int option) =
    match y with
    | Some y2 -> x + y2
    | None -> x

member this.ParamOverload(x: int) = x

member this.ParamOverload(x: int, y: int) = x + y
```

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a><span data-ttu-id="9fabd-397">Utiliser les types d’interfaces de collection .NET IEnumerable \<T\> et IDictionary \<Key,Value\> pour les paramètres et les valeurs de retour</span><span class="sxs-lookup"><span data-stu-id="9fabd-397">Use the .NET collection interface types IEnumerable\<T\> and IDictionary\<Key,Value\> for parameters and return values</span></span>

<span data-ttu-id="9fabd-398">Évitez l’utilisation de types de collections concrets tels que les tableaux .NET `T[]` , les types F # `list<T>` , `Map<Key,Value>` et `Set<T>` , ainsi que les types de collections concrètes .NET tels que `Dictionary<Key,Value>` .</span><span class="sxs-lookup"><span data-stu-id="9fabd-398">Avoid the use of concrete collection types such as .NET arrays `T[]`, F# types `list<T>`, `Map<Key,Value>` and `Set<T>`, and .NET concrete collection types such as `Dictionary<Key,Value>`.</span></span> <span data-ttu-id="9fabd-399">Les règles de conception de la bibliothèque .NET ont de bons conseils quant à l’utilisation de différents types de collections comme `IEnumerable<T>` .</span><span class="sxs-lookup"><span data-stu-id="9fabd-399">The .NET Library Design Guidelines have good advice regarding when to use various collection types like `IEnumerable<T>`.</span></span> <span data-ttu-id="9fabd-400">Certaines utilisation de tableaux ( `T[]` ) sont acceptables dans certains cas, pour des raisons de performances.</span><span class="sxs-lookup"><span data-stu-id="9fabd-400">Some use of arrays (`T[]`) is acceptable in some circumstances, on performance grounds.</span></span> <span data-ttu-id="9fabd-401">Notez surtout qu’il `seq<T>` s’agit simplement de l’alias F # pour `IEnumerable<T>` , et donc seq est souvent un type approprié pour une API .net vanille.</span><span class="sxs-lookup"><span data-stu-id="9fabd-401">Note especially that `seq<T>` is just the F# alias for `IEnumerable<T>`, and thus seq is often an appropriate type for a vanilla .NET API.</span></span>

<span data-ttu-id="9fabd-402">Au lieu de listes F # :</span><span class="sxs-lookup"><span data-stu-id="9fabd-402">Instead of F# lists:</span></span>

```fsharp
member this.PrintNames(names: string list) =
    ...
```

<span data-ttu-id="9fabd-403">Utilisez des séquences F # :</span><span class="sxs-lookup"><span data-stu-id="9fabd-403">Use F# sequences:</span></span>

```fsharp
member this.PrintNames(names: seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a><span data-ttu-id="9fabd-404">Utilisez le type d’unité comme seul type d’entrée d’une méthode pour définir une méthode de zéro argument ou comme type de retour unique pour définir une méthode qui retourne une valeur void</span><span class="sxs-lookup"><span data-stu-id="9fabd-404">Use the unit type as the only input type of a method to define a zero-argument method, or as the only return type to define a void-returning method</span></span>

<span data-ttu-id="9fabd-405">Évitez les autres utilisations du type d’unité.</span><span class="sxs-lookup"><span data-stu-id="9fabd-405">Avoid other uses of the unit type.</span></span> <span data-ttu-id="9fabd-406">Ils sont corrects :</span><span class="sxs-lookup"><span data-stu-id="9fabd-406">These are good:</span></span>

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x: int) = ()
```

<span data-ttu-id="9fabd-407">Ceci est incorrect :</span><span class="sxs-lookup"><span data-stu-id="9fabd-407">This is bad:</span></span>

```fsharp
member this.WrongUnit( x: unit, z: int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a><span data-ttu-id="9fabd-408">Rechercher les valeurs NULL sur les limites de l’API .NET vanille</span><span class="sxs-lookup"><span data-stu-id="9fabd-408">Check for null values on vanilla .NET API boundaries</span></span>

<span data-ttu-id="9fabd-409">Le code d’implémentation F # a tendance à avoir moins de valeurs NULL, en raison de modèles de conception immuables et de restrictions sur l’utilisation de littéraux NULL pour les types F #.</span><span class="sxs-lookup"><span data-stu-id="9fabd-409">F# implementation code tends to have fewer null values, due to immutable design patterns and restrictions on use of null literals for F# types.</span></span> <span data-ttu-id="9fabd-410">D’autres langages .NET utilisent souvent la valeur null de manière plus fréquente.</span><span class="sxs-lookup"><span data-stu-id="9fabd-410">Other .NET languages often use null as a value much more frequently.</span></span> <span data-ttu-id="9fabd-411">Pour cette raison, le code F # qui expose une API .NET vanille doit vérifier les paramètres pour la valeur null au niveau de la limite de l’API et éviter que ces valeurs circulent plus profondément dans le code d’implémentation F #.</span><span class="sxs-lookup"><span data-stu-id="9fabd-411">Because of this, F# code that is exposing a vanilla .NET API should check parameters for null at the API boundary, and prevent these values from flowing deeper into the F# implementation code.</span></span> <span data-ttu-id="9fabd-412">La `isNull` fonction ou le modèle correspondant au `null` modèle peut être utilisé.</span><span class="sxs-lookup"><span data-stu-id="9fabd-412">The `isNull` function or pattern matching on the `null` pattern can be used.</span></span>

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a><span data-ttu-id="9fabd-413">Évitez d’utiliser des tuples comme valeurs de retour</span><span class="sxs-lookup"><span data-stu-id="9fabd-413">Avoid using tuples as return values</span></span>

<span data-ttu-id="9fabd-414">Au lieu de cela, préférez retourner un type nommé contenant les données agrégées, ou utiliser des paramètres out pour retourner plusieurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="9fabd-414">Instead, prefer returning a named type holding the aggregate data, or using out parameters to return multiple values.</span></span> <span data-ttu-id="9fabd-415">Bien que les tuples et les tuples de struct existent dans .NET (y compris la prise en charge du langage C# pour les tuples de struct), ils ne fournissent pas le plus souvent l’API idéale et attendue pour les développeurs .NET.</span><span class="sxs-lookup"><span data-stu-id="9fabd-415">Although tuples and struct tuples exist in .NET (including C# language support for struct tuples), they will most often not provide the ideal and expected API for .NET developers.</span></span>

#### <a name="avoid-the-use-of-currying-of-parameters"></a><span data-ttu-id="9fabd-416">Éviter l’utilisation de la curryfication des paramètres</span><span class="sxs-lookup"><span data-stu-id="9fabd-416">Avoid the use of currying of parameters</span></span>

<span data-ttu-id="9fabd-417">Utilisez plutôt des conventions d’appel .NET `Method(arg1,arg2,…,argN)` .</span><span class="sxs-lookup"><span data-stu-id="9fabd-417">Instead, use .NET calling conventions `Method(arg1,arg2,…,argN)`.</span></span>

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

<span data-ttu-id="9fabd-418">Conseil : Si vous concevez des bibliothèques en vue d’une utilisation à partir de n’importe quel langage .NET, il n’y a pas de substitut pour effectuer des tâches expérimentales C# et Visual Basic programmation pour vous assurer que vos bibliothèques ne sont pas correctes dans ces langues.</span><span class="sxs-lookup"><span data-stu-id="9fabd-418">Tip: If you're designing libraries for use from any .NET language, then there's no substitute for actually doing some experimental C# and Visual Basic programming to ensure that your libraries "feel right" from these languages.</span></span> <span data-ttu-id="9fabd-419">Vous pouvez également utiliser des outils tels que .NET Reflector et l’Explorateur d’objets de Visual Studio pour vous assurer que les bibliothèques et leur documentation s’affichent comme prévu pour les développeurs.</span><span class="sxs-lookup"><span data-stu-id="9fabd-419">You can also use tools such as .NET Reflector and the Visual Studio Object Browser to ensure that libraries and their documentation appear as expected to developers.</span></span>

## <a name="appendix"></a><span data-ttu-id="9fabd-420">Annexe</span><span class="sxs-lookup"><span data-stu-id="9fabd-420">Appendix</span></span>

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a><span data-ttu-id="9fabd-421">Exemple de bout en bout de la conception de code F # pour une utilisation par d’autres langages .NET</span><span class="sxs-lookup"><span data-stu-id="9fabd-421">End-to-end example of designing F# code for use by other .NET languages</span></span>

<span data-ttu-id="9fabd-422">Considérons la classe suivante :</span><span class="sxs-lookup"><span data-stu-id="9fabd-422">Consider the following class:</span></span>

```fsharp
open System

type Point1(angle,radius) =
    new() = Point1(angle=0.0, radius=0.0)
    member x.Angle = angle
    member x.Radius = radius
    member x.Stretch(l) = Point1(angle=x.Angle, radius=x.Radius * l)
    member x.Warp(f) = Point1(angle=f(x.Angle), radius=x.Radius)
    static member Circle(n) =
        [ for i in 1..n -> Point1(angle=2.0*Math.PI/float(n), radius=1.0) ]
```

<span data-ttu-id="9fabd-423">Le type F # inféré de cette classe est le suivant :</span><span class="sxs-lookup"><span data-stu-id="9fabd-423">The inferred F# type of this class is as follows:</span></span>

```fsharp
type Point1 =
    new : unit -> Point1
    new : angle:double * radius:double -> Point1
    static member Circle : n:int -> Point1 list
    member Stretch : l:double -> Point1
    member Warp : f:(double -> double) -> Point1
    member Angle : double
    member Radius : double
```

<span data-ttu-id="9fabd-424">Voyons comment ce type F # apparaît pour un programmeur qui utilise un autre langage .NET.</span><span class="sxs-lookup"><span data-stu-id="9fabd-424">Let's take a look at how this F# type appears to a programmer using another .NET language.</span></span> <span data-ttu-id="9fabd-425">Par exemple, la « signature » C# approximative est la suivante :</span><span class="sxs-lookup"><span data-stu-id="9fabd-425">For example, the approximate C# "signature" is as follows:</span></span>

```csharp
// C# signature for the unadjusted Point1 class
public class Point1
{
    public Point1();

    public Point1(double angle, double radius);

    public static Microsoft.FSharp.Collections.List<Point1> Circle(int count);

    public Point1 Stretch(double factor);

    public Point1 Warp(Microsoft.FSharp.Core.FastFunc<double,double> transform);

    public double Angle { get; }

    public double Radius { get; }
}
```

<span data-ttu-id="9fabd-426">Il y a quelques points importants à noter sur la façon dont F # représente les constructions ici.</span><span class="sxs-lookup"><span data-stu-id="9fabd-426">There are some important points to notice about how F# represents constructs here.</span></span> <span data-ttu-id="9fabd-427">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="9fabd-427">For example:</span></span>

* <span data-ttu-id="9fabd-428">Les métadonnées telles que les noms d’arguments ont été conservées.</span><span class="sxs-lookup"><span data-stu-id="9fabd-428">Metadata such as argument names has been preserved.</span></span>

* <span data-ttu-id="9fabd-429">Les méthodes F # qui acceptent deux arguments deviennent des méthodes C# qui acceptent deux arguments.</span><span class="sxs-lookup"><span data-stu-id="9fabd-429">F# methods that take two arguments become C# methods that take two arguments.</span></span>

* <span data-ttu-id="9fabd-430">Les fonctions et les listes deviennent des références aux types correspondants dans la bibliothèque F #.</span><span class="sxs-lookup"><span data-stu-id="9fabd-430">Functions and lists become references to corresponding types in the F# library.</span></span>

<span data-ttu-id="9fabd-431">Le code suivant montre comment ajuster ce code pour prendre en compte ces éléments.</span><span class="sxs-lookup"><span data-stu-id="9fabd-431">The following code shows how to adjust this code to take these things into account.</span></span>

```fsharp
namespace SuperDuperFSharpLibrary.Types

type RadialPoint(angle:double, radius:double) =

    /// Return a point at the origin
    new() = RadialPoint(angle=0.0, radius=0.0)

    /// The angle to the point, from the x-axis
    member x.Angle = angle

    /// The distance to the point, from the origin
    member x.Radius = radius

    /// Return a new point, with radius multiplied by the given factor
    member x.Stretch(factor) =
        RadialPoint(angle=angle, radius=radius * factor)

    /// Return a new point, with angle transformed by the function
    member x.Warp(transform:Func<_,_>) =
        RadialPoint(angle=transform.Invoke angle, radius=radius)

    /// Return a sequence of points describing an approximate circle using
    /// the given count of points
    static member Circle(count) =
        seq { for i in 1..count ->
                RadialPoint(angle=2.0*Math.PI/float(count), radius=1.0) }
```

<span data-ttu-id="9fabd-432">Le type F # inféré du code est le suivant :</span><span class="sxs-lookup"><span data-stu-id="9fabd-432">The inferred F# type of the code is as follows:</span></span>

```fsharp
type RadialPoint =
    new : unit -> RadialPoint
    new : angle:double * radius:double -> RadialPoint
    static member Circle : count:int -> seq<RadialPoint>
    member Stretch : factor:double -> RadialPoint
    member Warp : transform:System.Func<double,double> -> RadialPoint
    member Angle : double
    member Radius : double
```

<span data-ttu-id="9fabd-433">La signature C# est maintenant la suivante :</span><span class="sxs-lookup"><span data-stu-id="9fabd-433">The C# signature is now as follows:</span></span>

```csharp
public class RadialPoint
{
    public RadialPoint();

    public RadialPoint(double angle, double radius);

    public static System.Collections.Generic.IEnumerable<RadialPoint> Circle(int count);

    public RadialPoint Stretch(double factor);

    public RadialPoint Warp(System.Func<double,double> transform);

    public double Angle { get; }

    public double Radius { get; }
}
```

<span data-ttu-id="9fabd-434">Les correctifs effectués pour préparer ce type pour une utilisation dans le cadre d’une bibliothèque .NET vanille sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="9fabd-434">The fixes made to prepare this type for use as part of a vanilla .NET library are as follows:</span></span>

* <span data-ttu-id="9fabd-435">Plusieurs noms modifiés : `Point1` , `n` , `l` et sont `f` devenus `RadialPoint` ,, `count` `factor` et `transform` , respectivement.</span><span class="sxs-lookup"><span data-stu-id="9fabd-435">Adjusted several names: `Point1`, `n`, `l`, and `f` became `RadialPoint`, `count`, `factor`, and `transform`, respectively.</span></span>

* <span data-ttu-id="9fabd-436">Utilise un type de retour `seq<RadialPoint>` au lieu de `RadialPoint list` en modifiant une construction de liste à l’aide `[ ... ]` d’une construction de séquence à l’aide de `IEnumerable<RadialPoint>` .</span><span class="sxs-lookup"><span data-stu-id="9fabd-436">Used a return type of `seq<RadialPoint>` instead of `RadialPoint list` by changing a list construction using `[ ... ]` to a sequence construction using `IEnumerable<RadialPoint>`.</span></span>

* <span data-ttu-id="9fabd-437">Utilisé le type délégué .NET `System.Func` au lieu d’un type de fonction F #.</span><span class="sxs-lookup"><span data-stu-id="9fabd-437">Used the .NET delegate type `System.Func` instead of an F# function type.</span></span>

<span data-ttu-id="9fabd-438">Cela rend l’utilisation beaucoup plus intéressante dans le code C#.</span><span class="sxs-lookup"><span data-stu-id="9fabd-438">This makes it far nicer to consume in C# code.</span></span>

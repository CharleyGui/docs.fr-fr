---
title: What's new in C# 8.0 - C# Guide
description: Vue d’ensemble des nouvelles fonctionnalités disponibles dans C# 8.0.
ms.date: 09/20/2019
ms.openlocfilehash: 540b95beaf00c17812a3b602602504278be69b0e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429390"
---
# <a name="whats-new-in-c-80"></a><span data-ttu-id="9561f-103">Nouveautés de C# 8.0</span><span class="sxs-lookup"><span data-stu-id="9561f-103">What's new in C# 8.0</span></span>

<span data-ttu-id="9561f-104">C# 8.0 adds the following features and enhancements to the C# language:</span><span class="sxs-lookup"><span data-stu-id="9561f-104">C# 8.0 adds the following features and enhancements to the C# language:</span></span>

- [<span data-ttu-id="9561f-105">Membres ReadOnly</span><span class="sxs-lookup"><span data-stu-id="9561f-105">Readonly members</span></span>](#readonly-members)
- [<span data-ttu-id="9561f-106">Default interface methods</span><span class="sxs-lookup"><span data-stu-id="9561f-106">Default interface methods</span></span>](#default-interface-methods)
- <span data-ttu-id="9561f-107">[Amélioration des critères spéciaux](#more-patterns-in-more-places) :</span><span class="sxs-lookup"><span data-stu-id="9561f-107">[Pattern matching enhancements](#more-patterns-in-more-places):</span></span>
  - [<span data-ttu-id="9561f-108">Expressions switch</span><span class="sxs-lookup"><span data-stu-id="9561f-108">Switch expressions</span></span>](#switch-expressions)
  - [<span data-ttu-id="9561f-109">Modèles de propriétés</span><span class="sxs-lookup"><span data-stu-id="9561f-109">Property patterns</span></span>](#property-patterns)
  - [<span data-ttu-id="9561f-110">Modèles de tuples</span><span class="sxs-lookup"><span data-stu-id="9561f-110">Tuple patterns</span></span>](#tuple-patterns)
  - [<span data-ttu-id="9561f-111">Modèles positionnels</span><span class="sxs-lookup"><span data-stu-id="9561f-111">Positional patterns</span></span>](#positional-patterns)
- [<span data-ttu-id="9561f-112">Déclarations using</span><span class="sxs-lookup"><span data-stu-id="9561f-112">Using declarations</span></span>](#using-declarations)
- [<span data-ttu-id="9561f-113">Fonctions locales statiques</span><span class="sxs-lookup"><span data-stu-id="9561f-113">Static local functions</span></span>](#static-local-functions)
- [<span data-ttu-id="9561f-114">Structs ref jetables</span><span class="sxs-lookup"><span data-stu-id="9561f-114">Disposable ref structs</span></span>](#disposable-ref-structs)
- [<span data-ttu-id="9561f-115">Types de référence Nullable</span><span class="sxs-lookup"><span data-stu-id="9561f-115">Nullable reference types</span></span>](#nullable-reference-types)
- [<span data-ttu-id="9561f-116">Flux asynchrones</span><span class="sxs-lookup"><span data-stu-id="9561f-116">Asynchronous streams</span></span>](#asynchronous-streams)
- [<span data-ttu-id="9561f-117">Index et plages</span><span class="sxs-lookup"><span data-stu-id="9561f-117">Indices and ranges</span></span>](#indices-and-ranges)
- [<span data-ttu-id="9561f-118">Null-coalescing assignment</span><span class="sxs-lookup"><span data-stu-id="9561f-118">Null-coalescing assignment</span></span>](#null-coalescing-assignment)
- [<span data-ttu-id="9561f-119">Unmanaged constructed types</span><span class="sxs-lookup"><span data-stu-id="9561f-119">Unmanaged constructed types</span></span>](#unmanaged-constructed-types)
- [<span data-ttu-id="9561f-120">Stackalloc in nested expressions</span><span class="sxs-lookup"><span data-stu-id="9561f-120">Stackalloc in nested expressions</span></span>](#stackalloc-in-nested-expressions)
- [<span data-ttu-id="9561f-121">Enhancement of interpolated verbatim strings</span><span class="sxs-lookup"><span data-stu-id="9561f-121">Enhancement of interpolated verbatim strings</span></span>](#enhancement-of-interpolated-verbatim-strings)

<span data-ttu-id="9561f-122">C# 8.0 is supported on **.NET Core 3.x** and **.NET Standard 2.1**.</span><span class="sxs-lookup"><span data-stu-id="9561f-122">C# 8.0 is supported on **.NET Core 3.x** and **.NET Standard 2.1**.</span></span> <span data-ttu-id="9561f-123">For more information, see [C# language versioning](../language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="9561f-123">For more information, see [C# language versioning](../language-reference/configure-language-version.md).</span></span>

<span data-ttu-id="9561f-124">La suite de cet article décrit brièvement ces fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="9561f-124">The remainder of this article briefly describes these features.</span></span> <span data-ttu-id="9561f-125">Lorsque des articles détaillés sont disponibles, des liens vers ces tutoriels et vues d’ensemble sont indiqués.</span><span class="sxs-lookup"><span data-stu-id="9561f-125">Where in-depth articles are available, links to those tutorials and overviews are provided.</span></span> <span data-ttu-id="9561f-126">Vous pouvez explorer ces fonctionnalités dans votre environnement à l’aide de l’outil global `dotnet try` :</span><span class="sxs-lookup"><span data-stu-id="9561f-126">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="9561f-127">Installez l’outil global [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup).</span><span class="sxs-lookup"><span data-stu-id="9561f-127">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="9561f-128">Clonez le référentiel [dotnet/try-samples](https://github.com/dotnet/try-samples).</span><span class="sxs-lookup"><span data-stu-id="9561f-128">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="9561f-129">Définissez le répertoire actuel sur le sous-répertoire *csharp8* pour le référentiel *try-samples*.</span><span class="sxs-lookup"><span data-stu-id="9561f-129">Set the current directory to the *csharp8* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="9561f-130">Exécutez `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="9561f-130">Run `dotnet try`.</span></span>

## <a name="readonly-members"></a><span data-ttu-id="9561f-131">Membres ReadOnly</span><span class="sxs-lookup"><span data-stu-id="9561f-131">Readonly members</span></span>

<span data-ttu-id="9561f-132">You can apply the `readonly` modifier to members of a struct.</span><span class="sxs-lookup"><span data-stu-id="9561f-132">You can apply the `readonly` modifier to members of a struct.</span></span> <span data-ttu-id="9561f-133">It indicates that the member doesn't modify state.</span><span class="sxs-lookup"><span data-stu-id="9561f-133">It indicates that the member doesn't modify state.</span></span> <span data-ttu-id="9561f-134">C’est plus précis que d’appliquer le modificateur `readonly` à une déclaration `struct`.</span><span class="sxs-lookup"><span data-stu-id="9561f-134">It's more granular than applying the `readonly` modifier to a `struct` declaration.</span></span>  <span data-ttu-id="9561f-135">Examinons le struct mutable suivant :</span><span class="sxs-lookup"><span data-stu-id="9561f-135">Consider the following mutable struct:</span></span>

```csharp
public struct Point
{
    public double X { get; set; }
    public double Y { get; set; }
    public double Distance => Math.Sqrt(X * X + Y * Y);

    public override string ToString() =>
        $"({X}, {Y}) is {Distance} from the origin";
}
```

<span data-ttu-id="9561f-136">Like most structs, the `ToString()` method doesn't modify state.</span><span class="sxs-lookup"><span data-stu-id="9561f-136">Like most structs, the `ToString()` method doesn't modify state.</span></span> <span data-ttu-id="9561f-137">Vous pouvez indiquer cela en ajoutant le modificateur `readonly` à la déclaration de `ToString()` :</span><span class="sxs-lookup"><span data-stu-id="9561f-137">You could indicate that by adding the `readonly` modifier to the declaration of `ToString()`:</span></span>

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

<span data-ttu-id="9561f-138">The preceding change generates a compiler warning, because `ToString` accesses the `Distance` property, which isn't marked `readonly`:</span><span class="sxs-lookup"><span data-stu-id="9561f-138">The preceding change generates a compiler warning, because `ToString` accesses the `Distance` property, which isn't marked `readonly`:</span></span>

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

<span data-ttu-id="9561f-139">Le compilateur vous avertit lorsqu’il a besoin de créer une copie défensive.</span><span class="sxs-lookup"><span data-stu-id="9561f-139">The compiler warns you when it needs to create a defensive copy.</span></span>  <span data-ttu-id="9561f-140">The `Distance` property doesn't change state, so you can fix this warning by adding the `readonly` modifier to the declaration:</span><span class="sxs-lookup"><span data-stu-id="9561f-140">The `Distance` property doesn't change state, so you can fix this warning by adding the `readonly` modifier to the declaration:</span></span>

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

<span data-ttu-id="9561f-141">Notice that the `readonly` modifier is necessary on a read-only property.</span><span class="sxs-lookup"><span data-stu-id="9561f-141">Notice that the `readonly` modifier is necessary on a read-only property.</span></span> <span data-ttu-id="9561f-142">The compiler doesn't assume `get` accessors don't modify state; you must declare `readonly` explicitly.</span><span class="sxs-lookup"><span data-stu-id="9561f-142">The compiler doesn't assume `get` accessors don't modify state; you must declare `readonly` explicitly.</span></span> <span data-ttu-id="9561f-143">Auto-implemented properties are an exception; the compiler will treat all auto-implemented getters as readonly, so here there's no need to add the `readonly` modifier to the `X` and `Y` properties.</span><span class="sxs-lookup"><span data-stu-id="9561f-143">Auto-implemented properties are an exception; the compiler will treat all auto-implemented getters as readonly, so here there's no need to add the `readonly` modifier to the `X` and `Y` properties.</span></span>

<span data-ttu-id="9561f-144">The compiler does enforce the rule that `readonly` members don't modify state.</span><span class="sxs-lookup"><span data-stu-id="9561f-144">The compiler does enforce the rule that `readonly` members don't modify state.</span></span> <span data-ttu-id="9561f-145">The following method won't compile unless you remove the `readonly` modifier:</span><span class="sxs-lookup"><span data-stu-id="9561f-145">The following method won't compile unless you remove the `readonly` modifier:</span></span>

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

<span data-ttu-id="9561f-146">Cette fonctionnalité vous permet de spécifier votre intention de conception, afin que le compilateur puisse l’appliquer et procéder à des optimisations basées sur cette intention.</span><span class="sxs-lookup"><span data-stu-id="9561f-146">This feature lets you specify your design intent so the compiler can enforce it, and make optimizations based on that intent.</span></span> <span data-ttu-id="9561f-147">You can learn more about readonly members in the language reference article on [`readonly`](../language-reference/keywords/readonly.md#readonly-member-examples).</span><span class="sxs-lookup"><span data-stu-id="9561f-147">You can learn more about readonly members in the language reference article on [`readonly`](../language-reference/keywords/readonly.md#readonly-member-examples).</span></span>

## <a name="default-interface-methods"></a><span data-ttu-id="9561f-148">Méthodes d’interface par défaut</span><span class="sxs-lookup"><span data-stu-id="9561f-148">Default interface methods</span></span>

<span data-ttu-id="9561f-149">Vous pouvez désormais ajouter des membres aux interfaces et fournir une implémentation pour ces membres.</span><span class="sxs-lookup"><span data-stu-id="9561f-149">You can now add members to interfaces and provide an implementation for those members.</span></span> <span data-ttu-id="9561f-150">Cette fonctionnalité de langage permet aux auteurs d’API d’ajouter des méthodes à une interface dans les versions ultérieures sans pour autant nuire à la compatibilité des binaires ou des sources avec les implémentations existantes de cette interface.</span><span class="sxs-lookup"><span data-stu-id="9561f-150">This language feature enables API authors to add methods to an interface in later versions without breaking source or binary compatibility with existing implementations of that interface.</span></span> <span data-ttu-id="9561f-151">Les implémentations existantes *héritent* de l’implémentation par défaut.</span><span class="sxs-lookup"><span data-stu-id="9561f-151">Existing implementations *inherit* the default implementation.</span></span> <span data-ttu-id="9561f-152">Cette fonctionnalité permet également à C# d’interagir avec les API ciblant Android ou Swift, qui prennent en charge des fonctionnalités similaires.</span><span class="sxs-lookup"><span data-stu-id="9561f-152">This feature also enables C# to interoperate with APIs that target Android or Swift, which support similar features.</span></span> <span data-ttu-id="9561f-153">Default interface methods also enable scenarios similar to a "traits" language feature.</span><span class="sxs-lookup"><span data-stu-id="9561f-153">Default interface methods also enable scenarios similar to a "traits" language feature.</span></span>

<span data-ttu-id="9561f-154">Default interface methods affects many scenarios and language elements.</span><span class="sxs-lookup"><span data-stu-id="9561f-154">Default interface methods affects many scenarios and language elements.</span></span> <span data-ttu-id="9561f-155">Ce premier tutoriel couvre [la mise à jour d’une interface à l’aide d’implémentations par défaut](../tutorials/default-interface-methods-versions.md).</span><span class="sxs-lookup"><span data-stu-id="9561f-155">Our first tutorial covers [updating an interface with default implementations](../tutorials/default-interface-methods-versions.md).</span></span> <span data-ttu-id="9561f-156">D’autres tutoriels et mises à jour de référence seront disponibles avant le lancement général.</span><span class="sxs-lookup"><span data-stu-id="9561f-156">Other tutorials and reference updates are coming in time for general release.</span></span>

## <a name="more-patterns-in-more-places"></a><span data-ttu-id="9561f-157">Ajout de modèles à différents endroits</span><span class="sxs-lookup"><span data-stu-id="9561f-157">More patterns in more places</span></span>

<span data-ttu-id="9561f-158">Les **critères spéciaux** offrent des outils permettant de produire des fonctionnalités dépendantes de la forme sur des types de données liés mais différents.</span><span class="sxs-lookup"><span data-stu-id="9561f-158">**Pattern matching** gives tools to provide shape-dependent functionality across related but different kinds of data.</span></span> <span data-ttu-id="9561f-159">C# 7.0 a introduit la syntaxe des modèles de type et des modèles de constantes avec l’expression [`is`](../language-reference/keywords/is.md) et l’instruction [`switch`](../language-reference/keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="9561f-159">C# 7.0 introduced syntax for type patterns and constant patterns by using the [`is`](../language-reference/keywords/is.md) expression and the [`switch`](../language-reference/keywords/switch.md) statement.</span></span> <span data-ttu-id="9561f-160">Ces fonctionnalités représentaient les premières étapes provisoires de prise en charge de paradigmes de programmation distinguant données et fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="9561f-160">These features represented the first tentative steps toward supporting programming paradigms where data and functionality live apart.</span></span> <span data-ttu-id="9561f-161">Face à la transition du secteur vers de nouveaux microservices et autres architectures cloud, d’autres outils sont nécessaires pour le langage.</span><span class="sxs-lookup"><span data-stu-id="9561f-161">As the industry moves toward more microservices and other cloud-based architectures, other language tools are needed.</span></span>

<span data-ttu-id="9561f-162">C# 8.0 développe ce vocabulaire en offrant la possibilité d’utiliser d’autres expressions de modèle à davantage d’endroits dans le code.</span><span class="sxs-lookup"><span data-stu-id="9561f-162">C# 8.0 expands this vocabulary so you can use more pattern expressions in more places in your code.</span></span> <span data-ttu-id="9561f-163">Étudiez ces fonctionnalités si vos données et vos fonctionnalités sont séparées.</span><span class="sxs-lookup"><span data-stu-id="9561f-163">Consider these features when your data and functionality are separate.</span></span> <span data-ttu-id="9561f-164">Les critères spéciaux peuvent être intéressants si vos algorithmes dépendent d’un fait autre que le type de runtime d’un objet.</span><span class="sxs-lookup"><span data-stu-id="9561f-164">Consider pattern matching when your algorithms depend on a fact other than the runtime type of an object.</span></span> <span data-ttu-id="9561f-165">Ces techniques représentent un autre moyen d’exprimer des conceptions.</span><span class="sxs-lookup"><span data-stu-id="9561f-165">These techniques provide another way to express designs.</span></span>

<span data-ttu-id="9561f-166">En plus des nouveaux modèles en de nouveaux endroits, C# 8.0 ajoute des **modèles récursifs**.</span><span class="sxs-lookup"><span data-stu-id="9561f-166">In addition to new patterns in new places, C# 8.0 adds **recursive patterns**.</span></span> <span data-ttu-id="9561f-167">Le résultat d’une expression de modèle est une expression.</span><span class="sxs-lookup"><span data-stu-id="9561f-167">The result of any pattern expression is an expression.</span></span> <span data-ttu-id="9561f-168">Un modèle récursif constitue simplement une expression de modèle appliquée à la sortie d’une autre expression de modèle.</span><span class="sxs-lookup"><span data-stu-id="9561f-168">A recursive pattern is simply a pattern expression applied to the output of another pattern expression.</span></span>

### <a name="switch-expressions"></a><span data-ttu-id="9561f-169">Expressions switch</span><span class="sxs-lookup"><span data-stu-id="9561f-169">Switch expressions</span></span>

<span data-ttu-id="9561f-170">Souvent, une instruction [`switch`](../language-reference/keywords/switch.md) produit une valeur dans chacun de ses blocs `case`.</span><span class="sxs-lookup"><span data-stu-id="9561f-170">Often, a [`switch`](../language-reference/keywords/switch.md) statement produces a value in each of its `case` blocks.</span></span> <span data-ttu-id="9561f-171">**Les expressions switch** permettent d’utiliser une syntaxe d’expression plus concise,</span><span class="sxs-lookup"><span data-stu-id="9561f-171">**Switch expressions** enable you to use more concise expression syntax.</span></span> <span data-ttu-id="9561f-172">comprenant moins de mots clés `case` et `break` répétitifs et moins d’accolades.</span><span class="sxs-lookup"><span data-stu-id="9561f-172">There are fewer repetitive `case` and `break` keywords, and fewer curly braces.</span></span>  <span data-ttu-id="9561f-173">Prenons par exemple l’enum suivant, qui liste les couleurs de l’arc-en-ciel :</span><span class="sxs-lookup"><span data-stu-id="9561f-173">As an example, consider the following enum that lists the colors of the rainbow:</span></span>

```csharp
public enum Rainbow
{
    Red,
    Orange,
    Yellow,
    Green,
    Blue,
    Indigo,
    Violet
}
```

<span data-ttu-id="9561f-174">Si votre application a défini un type `RGBColor` construit à partir des composants `R`, `G` et `B`, vous pouvez convertir une valeur `Rainbow` en valeurs RVB avec la méthode suivante, qui contient une expression switch :</span><span class="sxs-lookup"><span data-stu-id="9561f-174">If your application defined an `RGBColor` type that is constructed from the `R`, `G` and `B` components, you could convert a `Rainbow` value to its RGB values using the following method containing a switch expression:</span></span>

```csharp
public static RGBColor FromRainbow(Rainbow colorBand) =>
    colorBand switch
    {
        Rainbow.Red    => new RGBColor(0xFF, 0x00, 0x00),
        Rainbow.Orange => new RGBColor(0xFF, 0x7F, 0x00),
        Rainbow.Yellow => new RGBColor(0xFF, 0xFF, 0x00),
        Rainbow.Green  => new RGBColor(0x00, 0xFF, 0x00),
        Rainbow.Blue   => new RGBColor(0x00, 0x00, 0xFF),
        Rainbow.Indigo => new RGBColor(0x4B, 0x00, 0x82),
        Rainbow.Violet => new RGBColor(0x94, 0x00, 0xD3),
        _              => throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand)),
    };
```

<span data-ttu-id="9561f-175">Plusieurs améliorations ont ici été apportées à la syntaxe :</span><span class="sxs-lookup"><span data-stu-id="9561f-175">There are several syntax improvements here:</span></span>

- <span data-ttu-id="9561f-176">La variable se situe avant le mot clé `switch`.</span><span class="sxs-lookup"><span data-stu-id="9561f-176">The variable comes before the `switch` keyword.</span></span> <span data-ttu-id="9561f-177">Ce nouvel ordre permet de distinguer visuellement l’expression switch de l’instruction switch.</span><span class="sxs-lookup"><span data-stu-id="9561f-177">The different order makes it visually easy to distinguish the switch expression from the switch statement.</span></span>
- <span data-ttu-id="9561f-178">Les éléments `case` et `:` sont remplacés par `=>`,</span><span class="sxs-lookup"><span data-stu-id="9561f-178">The `case` and `:` elements are replaced with `=>`.</span></span> <span data-ttu-id="9561f-179">plus concis et plus intuitif.</span><span class="sxs-lookup"><span data-stu-id="9561f-179">It's more concise and intuitive.</span></span>
- <span data-ttu-id="9561f-180">Le cas `default` est remplacé par un discard `_`.</span><span class="sxs-lookup"><span data-stu-id="9561f-180">The `default` case is replaced with a `_` discard.</span></span>
- <span data-ttu-id="9561f-181">Les corps sont des expressions et non des instructions.</span><span class="sxs-lookup"><span data-stu-id="9561f-181">The bodies are expressions, not statements.</span></span>

<span data-ttu-id="9561f-182">Comparez cela avec le code équivalent utilisant l’instruction `switch` classique :</span><span class="sxs-lookup"><span data-stu-id="9561f-182">Contrast that with the equivalent code using the classic `switch` statement:</span></span>

```csharp
public static RGBColor FromRainbowClassic(Rainbow colorBand)
{
    switch (colorBand)
    {
        case Rainbow.Red:
            return new RGBColor(0xFF, 0x00, 0x00);
        case Rainbow.Orange:
            return new RGBColor(0xFF, 0x7F, 0x00);
        case Rainbow.Yellow:
            return new RGBColor(0xFF, 0xFF, 0x00);
        case Rainbow.Green:
            return new RGBColor(0x00, 0xFF, 0x00);
        case Rainbow.Blue:
            return new RGBColor(0x00, 0x00, 0xFF);
        case Rainbow.Indigo:
            return new RGBColor(0x4B, 0x00, 0x82);
        case Rainbow.Violet:
            return new RGBColor(0x94, 0x00, 0xD3);
        default:
            throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand));
    };
}
```

### <a name="property-patterns"></a><span data-ttu-id="9561f-183">Modèles de propriétés</span><span class="sxs-lookup"><span data-stu-id="9561f-183">Property patterns</span></span>

<span data-ttu-id="9561f-184">Le **modèle de propriété** permet de faire correspondre les propriétés de l’objet examiné.</span><span class="sxs-lookup"><span data-stu-id="9561f-184">The **property pattern** enables you to match on properties of the object examined.</span></span> <span data-ttu-id="9561f-185">Prenons un site d’e-commerce qui doit calculer les taxes sur les ventes en fonction de l’adresse de l’acheteur.</span><span class="sxs-lookup"><span data-stu-id="9561f-185">Consider an eCommerce site that must compute sales tax based on the buyer's address.</span></span> <span data-ttu-id="9561f-186">That computation isn't a core responsibility of an `Address` class.</span><span class="sxs-lookup"><span data-stu-id="9561f-186">That computation isn't a core responsibility of an `Address` class.</span></span> <span data-ttu-id="9561f-187">Il changera au fil du temps, probablement plus souvent que n’évoluera le format de l’adresse.</span><span class="sxs-lookup"><span data-stu-id="9561f-187">It will change over time, likely more often than address format changes.</span></span> <span data-ttu-id="9561f-188">Le montant des taxes sur les ventes varie selon la propriété `State` de l’adresse.</span><span class="sxs-lookup"><span data-stu-id="9561f-188">The amount of sales tax depends on the `State` property of the address.</span></span> <span data-ttu-id="9561f-189">La méthode suivante utilise le modèle de propriété pour calculer les taxes sur les ventes à partir de l’adresse et du prix :</span><span class="sxs-lookup"><span data-stu-id="9561f-189">The following method uses the property pattern to compute the sales tax from the address and the price:</span></span>

```csharp
public static decimal ComputeSalesTax(Address location, decimal salePrice) =>
    location switch
    {
        { State: "WA" } => salePrice * 0.06M,
        { State: "MN" } => salePrice * 0.75M,
        { State: "MI" } => salePrice * 0.05M,
        // other cases removed for brevity...
        _ => 0M
    };
```

<span data-ttu-id="9561f-190">Les critères spéciaux offrent une syntaxe concise pour exprimer cet algorithme.</span><span class="sxs-lookup"><span data-stu-id="9561f-190">Pattern matching creates a concise syntax for expressing this algorithm.</span></span>

### <a name="tuple-patterns"></a><span data-ttu-id="9561f-191">Modèles de tuples</span><span class="sxs-lookup"><span data-stu-id="9561f-191">Tuple patterns</span></span>

<span data-ttu-id="9561f-192">Certains algorithmes dépendent de plusieurs entrées.</span><span class="sxs-lookup"><span data-stu-id="9561f-192">Some algorithms depend on multiple inputs.</span></span> <span data-ttu-id="9561f-193">Les **modèles de tuples** permettent de basculer des unes aux autres en fonction de plusieurs valeurs exprimées sous forme de [tuple](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="9561f-193">**Tuple patterns** allow you to switch based on multiple values expressed as a [tuple](../tuples.md).</span></span>  <span data-ttu-id="9561f-194">Le code suivant montre une expression switch pour le jeu *Pierre-papier-ciseaux* :</span><span class="sxs-lookup"><span data-stu-id="9561f-194">The following code shows a switch expression for the game *rock, paper, scissors*:</span></span>

```csharp
public static string RockPaperScissors(string first, string second)
    => (first, second) switch
    {
        ("rock", "paper") => "rock is covered by paper. Paper wins.",
        ("rock", "scissors") => "rock breaks scissors. Rock wins.",
        ("paper", "rock") => "paper covers rock. Paper wins.",
        ("paper", "scissors") => "paper is cut by scissors. Scissors wins.",
        ("scissors", "rock") => "scissors is broken by rock. Rock wins.",
        ("scissors", "paper") => "scissors cuts paper. Scissors wins.",
        (_, _) => "tie"
    };
```

<span data-ttu-id="9561f-195">Les messages indiquent le vainqueur.</span><span class="sxs-lookup"><span data-stu-id="9561f-195">The messages indicate the winner.</span></span> <span data-ttu-id="9561f-196">Le cas discard représente les trois combinaisons pour les égalités, ou d’autres entrées de texte.</span><span class="sxs-lookup"><span data-stu-id="9561f-196">The discard case represents the three combinations for ties, or other text inputs.</span></span>

### <a name="positional-patterns"></a><span data-ttu-id="9561f-197">Modèles positionnels</span><span class="sxs-lookup"><span data-stu-id="9561f-197">Positional patterns</span></span>

<span data-ttu-id="9561f-198">Certains types comportent une méthode `Deconstruct` qui décompose ses propriétés en variables discrètes.</span><span class="sxs-lookup"><span data-stu-id="9561f-198">Some types include a `Deconstruct` method that deconstructs its properties into discrete variables.</span></span> <span data-ttu-id="9561f-199">Lorsqu’une méthode `Deconstruct` est accessible, il est possible d’utiliser des **modèles positionnels** pour inspecter les propriétés de l’objet et de se servir de ces dernières pour un modèle.</span><span class="sxs-lookup"><span data-stu-id="9561f-199">When a `Deconstruct` method is accessible, you can use **positional patterns** to inspect properties of the object and use those properties for a pattern.</span></span>  <span data-ttu-id="9561f-200">Considérez la classe `Point` suivante, dont la méthode `Deconstruct` sert à créer des variables discrètes pour `X` et `Y` :</span><span class="sxs-lookup"><span data-stu-id="9561f-200">Consider the following `Point` class that includes a `Deconstruct` method to create discrete variables for `X` and `Y`:</span></span>

```csharp
public class Point
{
    public int X { get; }
    public int Y { get; }

    public Point(int x, int y) => (X, Y) = (x, y);

    public void Deconstruct(out int x, out int y) =>
        (x, y) = (X, Y);
}
```

<span data-ttu-id="9561f-201">De plus, envisagez l’énumération suivante qui représente diverses positions d’un quadrant :</span><span class="sxs-lookup"><span data-stu-id="9561f-201">Additionally, consider the following enum that represents various positions of a quadrant:</span></span>

```csharp
public enum Quadrant
{
    Unknown,
    Origin,
    One,
    Two,
    Three,
    Four,
    OnBorder
}
```

<span data-ttu-id="9561f-202">La méthode suivante utilise le **modèle positionnel** pour extraire les valeurs de `x` et de `y`.</span><span class="sxs-lookup"><span data-stu-id="9561f-202">The following method uses the **positional pattern** to extract the values of `x` and `y`.</span></span> <span data-ttu-id="9561f-203">Ensuite, elle utilise une clause `when` pour déterminer le `Quadrant` du point :</span><span class="sxs-lookup"><span data-stu-id="9561f-203">Then, it uses a `when` clause to determine the `Quadrant` of the point:</span></span>

```csharp
static Quadrant GetQuadrant(Point point) => point switch
{
    (0, 0) => Quadrant.Origin,
    var (x, y) when x > 0 && y > 0 => Quadrant.One,
    var (x, y) when x < 0 && y > 0 => Quadrant.Two,
    var (x, y) when x < 0 && y < 0 => Quadrant.Three,
    var (x, y) when x > 0 && y < 0 => Quadrant.Four,
    var (_, _) => Quadrant.OnBorder,
    _ => Quadrant.Unknown
};
```

<span data-ttu-id="9561f-204">Le modèle discard dans le switch précédent indique une correspondance lorsque soit `x`, soit `y` est égal à 0, mais pas les deux.</span><span class="sxs-lookup"><span data-stu-id="9561f-204">The discard pattern in the preceding switch matches when either `x` or `y` is 0, but not both.</span></span> <span data-ttu-id="9561f-205">Une expression switch doit produire une valeur ou,</span><span class="sxs-lookup"><span data-stu-id="9561f-205">A switch expression must either produce a value or throw an exception.</span></span> <span data-ttu-id="9561f-206">si aucun des cas ne correspond, lever une exception.</span><span class="sxs-lookup"><span data-stu-id="9561f-206">If none of the cases match, the switch expression throws an exception.</span></span> <span data-ttu-id="9561f-207">The compiler generates a warning for you if you don't cover all possible cases in your switch expression.</span><span class="sxs-lookup"><span data-stu-id="9561f-207">The compiler generates a warning for you if you don't cover all possible cases in your switch expression.</span></span>

<span data-ttu-id="9561f-208">Vous pouvez explorer des techniques de critères spéciaux dans ce [tutoriel avancé sur les critères spéciaux](../tutorials/pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="9561f-208">You can explore pattern matching techniques in this [advanced tutorial on pattern matching](../tutorials/pattern-matching.md).</span></span>

## <a name="using-declarations"></a><span data-ttu-id="9561f-209">Déclarations using</span><span class="sxs-lookup"><span data-stu-id="9561f-209">Using declarations</span></span>

<span data-ttu-id="9561f-210">Une **déclaration using** est une déclaration de variable précédée par le mot clé `using`.</span><span class="sxs-lookup"><span data-stu-id="9561f-210">A **using declaration** is a variable declaration preceded by the `using` keyword.</span></span> <span data-ttu-id="9561f-211">Elle indique au compilateur que la variable déclarée doit être supprimée à la fin de la portée englobante.</span><span class="sxs-lookup"><span data-stu-id="9561f-211">It tells the compiler that the variable being declared should be disposed at the end of the enclosing scope.</span></span> <span data-ttu-id="9561f-212">Prenons par exemple le code suivant, qui écrit un fichier texte :</span><span class="sxs-lookup"><span data-stu-id="9561f-212">For example, consider the following code that writes a text file:</span></span>

```csharp
static int WriteLinesToFile(IEnumerable<string> lines)
{
    using var file = new System.IO.StreamWriter("WriteLines2.txt");
    // Notice how we declare skippedLines after the using statement.
    int skippedLines = 0;
    foreach (string line in lines)
    {
        if (!line.Contains("Second"))
        {
            file.WriteLine(line);
        }
        else
        {
            skippedLines++;
        }
    }
    // Notice how skippedLines is in scope here.
    return skippedLines;
    // file is disposed here
}
```

<span data-ttu-id="9561f-213">Dans l’exemple précédent, le fichier est supprimé une fois l’accolade fermante de la méthode atteinte.</span><span class="sxs-lookup"><span data-stu-id="9561f-213">In the preceding example, the file is disposed when the closing brace for the method is reached.</span></span> <span data-ttu-id="9561f-214">C’est la fin de la portée dans laquelle `file` est déclaré.</span><span class="sxs-lookup"><span data-stu-id="9561f-214">That's the end of the scope in which `file` is declared.</span></span> <span data-ttu-id="9561f-215">Le code précédent équivaut au suivant, qui utilise [l’instruction using](../language-reference/keywords/using-statement.md) classique :</span><span class="sxs-lookup"><span data-stu-id="9561f-215">The preceding code is equivalent to the following code that uses the classic [using statement](../language-reference/keywords/using-statement.md):</span></span>

```csharp
static int WriteLinesToFile(IEnumerable<string> lines)
{
    // We must declare the variable outside of the using block
    // so that it is in scope to be returned.
    int skippedLines = 0;
    using (var file = new System.IO.StreamWriter("WriteLines2.txt"))
    {
        foreach (string line in lines)
        {
            if (!line.Contains("Second"))
            {
                file.WriteLine(line);
            }
            else
            {
                skippedLines++;
            }
        }
    } // file is disposed here
    return skippedLines;
}
```

<span data-ttu-id="9561f-216">Dans l’exemple précédent, le fichier est supprimé une fois l’accolade fermante associée à l’instruction `using` atteinte.</span><span class="sxs-lookup"><span data-stu-id="9561f-216">In the preceding example, the file is disposed when the closing brace associated with the `using` statement is reached.</span></span>

<span data-ttu-id="9561f-217">Dans les deux cas, le compilateur génère l’appel à `Dispose()`.</span><span class="sxs-lookup"><span data-stu-id="9561f-217">In both cases, the compiler generates the call to `Dispose()`.</span></span> <span data-ttu-id="9561f-218">The compiler generates an error if the expression in the `using` statement isn't disposable.</span><span class="sxs-lookup"><span data-stu-id="9561f-218">The compiler generates an error if the expression in the `using` statement isn't disposable.</span></span>

## <a name="static-local-functions"></a><span data-ttu-id="9561f-219">Fonctions locales statiques</span><span class="sxs-lookup"><span data-stu-id="9561f-219">Static local functions</span></span>

<span data-ttu-id="9561f-220">Il est maintenant possible d’ajouter le modificateur `static` à des fonctions locales pour éviter qu’elles ne capturent (fassent référence à) des variables au sein de la portée englobante.</span><span class="sxs-lookup"><span data-stu-id="9561f-220">You can now add the `static` modifier to local functions to ensure that local function doesn't capture (reference) any variables from the enclosing scope.</span></span> <span data-ttu-id="9561f-221">Cela génère `CS8421`, « A static local function can’t contain a reference to \< variable> ».</span><span class="sxs-lookup"><span data-stu-id="9561f-221">Doing so generates `CS8421`, "A static local function can't contain a reference to \<variable>."</span></span> 

<span data-ttu-id="9561f-222">Prenons le code suivant.</span><span class="sxs-lookup"><span data-stu-id="9561f-222">Consider the following code.</span></span> <span data-ttu-id="9561f-223">La fonction locale `LocalFunction` accède à la variable `y`, déclarée dans la portée englobante (la méthode `M`).</span><span class="sxs-lookup"><span data-stu-id="9561f-223">The local function `LocalFunction` accesses the variable `y`, declared in the enclosing scope (the method `M`).</span></span> <span data-ttu-id="9561f-224">Par conséquent, `LocalFunction` ne peut pas être déclarée avec le modificateur `static` :</span><span class="sxs-lookup"><span data-stu-id="9561f-224">Therefore, `LocalFunction` can't be declared with the `static` modifier:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="9561f-225">Le code suivant contient une fonction locale statique.</span><span class="sxs-lookup"><span data-stu-id="9561f-225">The following code contains a static local function.</span></span> <span data-ttu-id="9561f-226">Elle peut être statique, car elle n’accède à aucune variable dans la portée englobante :</span><span class="sxs-lookup"><span data-stu-id="9561f-226">It can be static because it doesn't access any variables in the enclosing scope:</span></span>

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a><span data-ttu-id="9561f-227">Structs ref jetables</span><span class="sxs-lookup"><span data-stu-id="9561f-227">Disposable ref structs</span></span>

<span data-ttu-id="9561f-228">A `struct` declared with the `ref` modifier may not implement any interfaces and so can't implement <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="9561f-228">A `struct` declared with the `ref` modifier may not implement any interfaces and so can't implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="9561f-229">Par conséquent, pour qu’un `ref struct` soit supprimable, il doit avoir une méthode `void Dispose()` accessible.</span><span class="sxs-lookup"><span data-stu-id="9561f-229">Therefore, to enable a `ref struct` to be disposed, it must have an accessible `void Dispose()` method.</span></span> <span data-ttu-id="9561f-230">This feature also applies to `readonly ref struct` declarations.</span><span class="sxs-lookup"><span data-stu-id="9561f-230">This feature also applies to `readonly ref struct` declarations.</span></span>

## <a name="nullable-reference-types"></a><span data-ttu-id="9561f-231">Types références Nullables</span><span class="sxs-lookup"><span data-stu-id="9561f-231">Nullable reference types</span></span>

<span data-ttu-id="9561f-232">Dans un contexte d’annotation Nullable, toute variable d’un type référence est considérée comme un **type référence n'acceptant pas la valeur Null**.</span><span class="sxs-lookup"><span data-stu-id="9561f-232">Inside a nullable annotation context, any variable of a reference type is considered to be a **nonnullable reference type**.</span></span> <span data-ttu-id="9561f-233">Si vous souhaitez indiquer qu’une variable peut être Null, ajoutez `?` au nom de type pour la déclarer comme **type référence Nullable**.</span><span class="sxs-lookup"><span data-stu-id="9561f-233">If you want to indicate that a variable may be null, you must append the type name with the `?` to declare the variable as a **nullable reference type**.</span></span>

<span data-ttu-id="9561f-234">Avec les types références n'acceptant pas la valeur Null, le compilateur utilise l’analyse de flux pour que les variables locales soient initialisées à une valeur non Null une fois déclarées.</span><span class="sxs-lookup"><span data-stu-id="9561f-234">For nonnullable reference types, the compiler uses flow analysis to ensure that local variables are initialized to a non-null value when declared.</span></span> <span data-ttu-id="9561f-235">Les champs doivent être initialisés à la construction.</span><span class="sxs-lookup"><span data-stu-id="9561f-235">Fields must be initialized during construction.</span></span> <span data-ttu-id="9561f-236">The compiler generates a warning if the variable isn't set by a call to any of the available constructors or by an initializer.</span><span class="sxs-lookup"><span data-stu-id="9561f-236">The compiler generates a warning if the variable isn't set by a call to any of the available constructors or by an initializer.</span></span> <span data-ttu-id="9561f-237">Par ailleurs, les types références n’acceptant pas la valeur Null ne peuvent pas avoir de valeur pouvant être Null.</span><span class="sxs-lookup"><span data-stu-id="9561f-237">Furthermore, nonnullable reference types can't be assigned a value that could be null.</span></span>

<span data-ttu-id="9561f-238">Les types références Nullables font l’objet d’aucun contrôle visant à vérifier qu’ils ne sont pas affectés ou initialisées sur Null.</span><span class="sxs-lookup"><span data-stu-id="9561f-238">Nullable reference types aren't checked to ensure they aren't assigned or initialized to null.</span></span> <span data-ttu-id="9561f-239">Toutefois, le compilateur utilise l’analyse de flux pour comparer à Null toutes les variables d’un type référence Nullable avant d’y accéder ou de lui affecter un type référence n’acceptant pas la valeur Null.</span><span class="sxs-lookup"><span data-stu-id="9561f-239">However, the compiler uses flow analysis to ensure that any variable of a nullable reference type is checked against null before it's accessed or assigned to a nonnullable reference type.</span></span>

<span data-ttu-id="9561f-240">Plus d’informations sur la fonctionnalité, voir la vue d’ensemble des [types références Nullables](../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="9561f-240">You can learn more about the feature in the overview of [nullable reference types](../nullable-references.md).</span></span> <span data-ttu-id="9561f-241">Essayez par vous-même dans une nouvelle application avec ce [tutoriel des types références Nullables](../tutorials/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="9561f-241">Try it yourself in a new application in this [nullable reference types tutorial](../tutorials/nullable-reference-types.md).</span></span> <span data-ttu-id="9561f-242">Pour plus d’informations sur le processus de migration d’un codebase dans l’objectif d’utiliser des types références Nullables, voir le [tutoriel Migrer une application pour utiliser des types références Nullables](../tutorials/upgrade-to-nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="9561f-242">Learn about the steps to migrate an existing codebase to make use of nullable reference types in the [migrating an application to use nullable reference types tutorial](../tutorials/upgrade-to-nullable-references.md).</span></span>

## <a name="asynchronous-streams"></a><span data-ttu-id="9561f-243">Flux asynchrones</span><span class="sxs-lookup"><span data-stu-id="9561f-243">Asynchronous streams</span></span>

<span data-ttu-id="9561f-244">À partir de C# 8.0, il est possible de créer et de consommer des flux de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="9561f-244">Starting with C# 8.0, you can create and consume streams asynchronously.</span></span> <span data-ttu-id="9561f-245">Une méthode qui retourne un flux asynchrone comporte trois propriétés :</span><span class="sxs-lookup"><span data-stu-id="9561f-245">A method that returns an asynchronous stream has three properties:</span></span>

1. <span data-ttu-id="9561f-246">Elle est déclarée avec le modificateur `async`.</span><span class="sxs-lookup"><span data-stu-id="9561f-246">It's declared with the `async` modifier.</span></span>
1. <span data-ttu-id="9561f-247">Elle retourne un <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="9561f-247">It returns an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span>
1. <span data-ttu-id="9561f-248">La méthode contient des instructions `yield return` pour retourner des éléments consécutifs dans le flux asynchrone.</span><span class="sxs-lookup"><span data-stu-id="9561f-248">The method contains `yield return` statements to return successive elements in the asynchronous stream.</span></span>

<span data-ttu-id="9561f-249">Pour pouvoir consommer un flux asynchrone, il faut ajouter le mot clé `await` avant le mot clé `foreach` au moment d’énumérer les éléments du flux.</span><span class="sxs-lookup"><span data-stu-id="9561f-249">Consuming an asynchronous stream requires you to add the `await` keyword before the `foreach` keyword when you enumerate the elements of the stream.</span></span> <span data-ttu-id="9561f-250">Le mot clé `await` exige que la méthode qui énumère le flux asynchrone soit déclarée avec le modificateur `async` et retourne un type autorisé pour une méthode `async`,</span><span class="sxs-lookup"><span data-stu-id="9561f-250">Adding the `await` keyword requires the method that enumerates the asynchronous stream to be declared with the `async` modifier and to return a type allowed for an `async` method.</span></span> <span data-ttu-id="9561f-251">soit en général <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="9561f-251">Typically that means returning a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="9561f-252">Il peut également s’agir de <xref:System.Threading.Tasks.ValueTask> ou <xref:System.Threading.Tasks.ValueTask%601>.</span><span class="sxs-lookup"><span data-stu-id="9561f-252">It can also be a <xref:System.Threading.Tasks.ValueTask> or <xref:System.Threading.Tasks.ValueTask%601>.</span></span> <span data-ttu-id="9561f-253">Une méthode peut consommer et produire un flux asynchrone ; elle retournerait alors un <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="9561f-253">A method can both consume and produce an asynchronous stream, which means it would return an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span> <span data-ttu-id="9561f-254">Le code suivant génère une séquence de 0 à 19, en attendant 100 ms entre chaque nombre :</span><span class="sxs-lookup"><span data-stu-id="9561f-254">The following code generates a sequence from 0 to 19, waiting 100 ms between generating each number:</span></span>

```csharp
public static async System.Collections.Generic.IAsyncEnumerable<int> GenerateSequence()
{
    for (int i = 0; i < 20; i++)
    {
        await Task.Delay(100);
        yield return i;
    }
}
```

<span data-ttu-id="9561f-255">Pour énumérer la séquence, on utilise l’instruction `await foreach` :</span><span class="sxs-lookup"><span data-stu-id="9561f-255">You would enumerate the sequence using the `await foreach` statement:</span></span>

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

<span data-ttu-id="9561f-256">Vous pouvez essayer par vous-même les flux asynchrones dans notre tutoriel [Créer et consommer des flux asynchrones](../tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="9561f-256">You can try asynchronous streams yourself in our tutorial on [creating and consuming async streams](../tutorials/generate-consume-asynchronous-stream.md).</span></span>

## <a name="indices-and-ranges"></a><span data-ttu-id="9561f-257">Index et plages</span><span class="sxs-lookup"><span data-stu-id="9561f-257">Indices and ranges</span></span>

<span data-ttu-id="9561f-258">Indices and ranges provide a succinct syntax for accessing single elements or ranges in a sequence.</span><span class="sxs-lookup"><span data-stu-id="9561f-258">Indices and ranges provide a succinct syntax for accessing single elements or ranges in a sequence.</span></span>

<span data-ttu-id="9561f-259">This language support relies on two new types, and two new operators:</span><span class="sxs-lookup"><span data-stu-id="9561f-259">This language support relies on two new types, and two new operators:</span></span>

- <span data-ttu-id="9561f-260"><xref:System.Index?displayProperty=nameWithType> représente un index au sein d’une séquence.</span><span class="sxs-lookup"><span data-stu-id="9561f-260"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="9561f-261">The index from end operator `^`, which specifies that an index is relative to the end of the sequence.</span><span class="sxs-lookup"><span data-stu-id="9561f-261">The index from end operator `^`, which specifies that an index is relative to the end of the sequence.</span></span>
- <span data-ttu-id="9561f-262"><xref:System.Range?displayProperty=nameWithType> représente une sous-plage d’une séquence.</span><span class="sxs-lookup"><span data-stu-id="9561f-262"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="9561f-263">The range operator `..`, which specifies the start and end of a range as its operands.</span><span class="sxs-lookup"><span data-stu-id="9561f-263">The range operator `..`, which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="9561f-264">Commençons par les règles concernant les index.</span><span class="sxs-lookup"><span data-stu-id="9561f-264">Let's start with the rules for indexes.</span></span> <span data-ttu-id="9561f-265">Prenons pour exemple un tableau `sequence`.</span><span class="sxs-lookup"><span data-stu-id="9561f-265">Consider an array `sequence`.</span></span> <span data-ttu-id="9561f-266">L’index `0` est identique à l’index `sequence[0]`.</span><span class="sxs-lookup"><span data-stu-id="9561f-266">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="9561f-267">L’index `^0` est identique à l’index `sequence[sequence.Length]`.</span><span class="sxs-lookup"><span data-stu-id="9561f-267">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="9561f-268">Notez que `sequence[^0]` lève une exception, tout comme `sequence[sequence.Length]`.</span><span class="sxs-lookup"><span data-stu-id="9561f-268">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="9561f-269">Pour n’importe quel nombre `n`, l’index `^n` est identique à l’index `sequence.Length - n`.</span><span class="sxs-lookup"><span data-stu-id="9561f-269">For any number `n`, the index `^n` is the same as `sequence.Length - n`.</span></span>

<span data-ttu-id="9561f-270">Une plage spécifie son *début* et sa *fin*.</span><span class="sxs-lookup"><span data-stu-id="9561f-270">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="9561f-271">The start of the range is inclusive, but the end of the range is exclusive, meaning the *start* is included in the range but the *end* isn't included in the range.</span><span class="sxs-lookup"><span data-stu-id="9561f-271">The start of the range is inclusive, but the end of the range is exclusive, meaning the *start* is included in the range but the *end* isn't included in the range.</span></span> <span data-ttu-id="9561f-272">La plage `[0..^0]` représente la plage dans son intégralité, tout comme `[0..sequence.Length]` représente la plage entière.</span><span class="sxs-lookup"><span data-stu-id="9561f-272">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span>

<span data-ttu-id="9561f-273">Prenons quelques exemples.</span><span class="sxs-lookup"><span data-stu-id="9561f-273">Let's look at a few examples.</span></span> <span data-ttu-id="9561f-274">Examinez le tableau suivant, annoté avec son index à partir du début et de la fin :</span><span class="sxs-lookup"><span data-stu-id="9561f-274">Consider the following array, annotated with its index from the start and from the end:</span></span>

```csharp
var words = new string[]
{
                // index from start    index from end
    "The",      // 0                   ^9
    "quick",    // 1                   ^8
    "brown",    // 2                   ^7
    "fox",      // 3                   ^6
    "jumped",   // 4                   ^5
    "over",     // 5                   ^4
    "the",      // 6                   ^3
    "lazy",     // 7                   ^2
    "dog"       // 8                   ^1
};              // 9 (or words.Length) ^0
```

<span data-ttu-id="9561f-275">Vous pouvez récupérer le dernier mot avec l’index `^1` :</span><span class="sxs-lookup"><span data-stu-id="9561f-275">You can retrieve the last word with the `^1` index:</span></span>

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

<span data-ttu-id="9561f-276">Le code suivant crée une sous-plage qui comporte les mots « quick », « brown » et « fox »</span><span class="sxs-lookup"><span data-stu-id="9561f-276">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="9561f-277">et va de `words[1]` à `words[3]`.</span><span class="sxs-lookup"><span data-stu-id="9561f-277">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="9561f-278">L’élément `words[4]` n’est pas dans la plage.</span><span class="sxs-lookup"><span data-stu-id="9561f-278">The element `words[4]` isn't in the range.</span></span>

```csharp
var quickBrownFox = words[1..4];
```

<span data-ttu-id="9561f-279">Le code suivant crée une sous-plage qui comporte « lazy » et « dog »</span><span class="sxs-lookup"><span data-stu-id="9561f-279">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="9561f-280">et comprend `words[^2]` et `words[^1]`.</span><span class="sxs-lookup"><span data-stu-id="9561f-280">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="9561f-281">The end index `words[^0]` isn't included:</span><span class="sxs-lookup"><span data-stu-id="9561f-281">The end index `words[^0]` isn't included:</span></span>

```csharp
var lazyDog = words[^2..^0];
```

<span data-ttu-id="9561f-282">Les exemples suivants créent des plages ouvertes au début, à la fin ou les deux :</span><span class="sxs-lookup"><span data-stu-id="9561f-282">The following examples create ranges that are open ended for the start, end, or both:</span></span>

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

<span data-ttu-id="9561f-283">Vous pouvez également déclarer des plages comme variables :</span><span class="sxs-lookup"><span data-stu-id="9561f-283">You can also declare ranges as variables:</span></span>

```csharp
Range phrase = 1..4;
```

<span data-ttu-id="9561f-284">La plage peut ensuite être utilisée à l’intérieur des caractères `[` et `]` :</span><span class="sxs-lookup"><span data-stu-id="9561f-284">The range can then be used inside the `[` and `]` characters:</span></span>

```csharp
var text = words[phrase];
```

<span data-ttu-id="9561f-285">Not only arrays support indices and ranges.</span><span class="sxs-lookup"><span data-stu-id="9561f-285">Not only arrays support indices and ranges.</span></span> <span data-ttu-id="9561f-286">You also can use indices and ranges with [string](../language-reference/builtin-types/reference-types.md#the-string-type), <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="9561f-286">You also can use indices and ranges with [string](../language-reference/builtin-types/reference-types.md#the-string-type), <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="9561f-287">For more information, see [Type support for indices and ranges](../tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).</span><span class="sxs-lookup"><span data-stu-id="9561f-287">For more information, see [Type support for indices and ranges](../tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).</span></span>

<span data-ttu-id="9561f-288">Pour explorer davantage les index et les plages, consultez le tutoriel sur [les index et les plages](../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="9561f-288">You can explore more about indices and ranges in the tutorial on [indices and ranges](../tutorials/ranges-indexes.md).</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="9561f-289">Null-coalescing assignment</span><span class="sxs-lookup"><span data-stu-id="9561f-289">Null-coalescing assignment</span></span>

<span data-ttu-id="9561f-290">C# 8.0 introduces the null-coalescing assignment operator `??=`.</span><span class="sxs-lookup"><span data-stu-id="9561f-290">C# 8.0 introduces the null-coalescing assignment operator `??=`.</span></span> <span data-ttu-id="9561f-291">You can use the `??=` operator to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span><span class="sxs-lookup"><span data-stu-id="9561f-291">You can use the `??=` operator to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span>

```csharp
List<int> numbers = null;
int? i = null;

numbers ??= new List<int>();
numbers.Add(i ??= 17);
numbers.Add(i ??= 20);

Console.WriteLine(string.Join(" ", numbers));  // output: 17 17
Console.WriteLine(i);  // output: 17
```

<span data-ttu-id="9561f-292">For more information, see the [?? and ??= operators](../language-reference/operators/null-coalescing-operator.md) article.</span><span class="sxs-lookup"><span data-stu-id="9561f-292">For more information, see the [?? and ??= operators](../language-reference/operators/null-coalescing-operator.md) article.</span></span>

## <a name="unmanaged-constructed-types"></a><span data-ttu-id="9561f-293">Unmanaged constructed types</span><span class="sxs-lookup"><span data-stu-id="9561f-293">Unmanaged constructed types</span></span>

<span data-ttu-id="9561f-294">In C# 7.3 and earlier, a constructed type (a type that includes at least one type argument) can't be an [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="9561f-294">In C# 7.3 and earlier, a constructed type (a type that includes at least one type argument) can't be an [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="9561f-295">Starting with C# 8.0, a constructed value type is unmanaged if it contains fields of unmanaged types only.</span><span class="sxs-lookup"><span data-stu-id="9561f-295">Starting with C# 8.0, a constructed value type is unmanaged if it contains fields of unmanaged types only.</span></span>

<span data-ttu-id="9561f-296">For example, given the following definition of the generic `Coords<T>` type:</span><span class="sxs-lookup"><span data-stu-id="9561f-296">For example, given the following definition of the generic `Coords<T>` type:</span></span>

```csharp
public struct Coords<T>
{
    public T X;
    public T Y;
}
```

<span data-ttu-id="9561f-297">the `Coords<int>` type is an unmanaged type in C# 8.0 and later.</span><span class="sxs-lookup"><span data-stu-id="9561f-297">the `Coords<int>` type is an unmanaged type in C# 8.0 and later.</span></span> <span data-ttu-id="9561f-298">Like for any unmanaged type, you can create a pointer to a variable of this type or [allocate a block of memory on the stack](../language-reference/operators/stackalloc.md) for instances of this type:</span><span class="sxs-lookup"><span data-stu-id="9561f-298">Like for any unmanaged type, you can create a pointer to a variable of this type or [allocate a block of memory on the stack](../language-reference/operators/stackalloc.md) for instances of this type:</span></span>

```csharp
Span<Coords<int>> coordinates = stackalloc[]
{
    new Coords<int> { X = 0, Y = 0 },
    new Coords<int> { X = 0, Y = 3 },
    new Coords<int> { X = 4, Y = 0 }
};
```

<span data-ttu-id="9561f-299">For more information, see [Unmanaged types](../language-reference/builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="9561f-299">For more information, see [Unmanaged types](../language-reference/builtin-types/unmanaged-types.md).</span></span>

## <a name="stackalloc-in-nested-expressions"></a><span data-ttu-id="9561f-300">Stackalloc in nested expressions</span><span class="sxs-lookup"><span data-stu-id="9561f-300">Stackalloc in nested expressions</span></span>

<span data-ttu-id="9561f-301">Starting with C# 8.0, if the result of a [stackalloc](../language-reference/operators/stackalloc.md) expression is of the <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> type, you can use the `stackalloc` expression in other expressions:</span><span class="sxs-lookup"><span data-stu-id="9561f-301">Starting with C# 8.0, if the result of a [stackalloc](../language-reference/operators/stackalloc.md) expression is of the <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> type, you can use the `stackalloc` expression in other expressions:</span></span>

```csharp
Span<int> numbers = stackalloc[] { 1, 2, 3, 4, 5, 6 };
var ind = numbers.IndexOfAny(stackalloc[] { 2, 4, 6 ,8 });
Console.WriteLine(ind);  // output: 1
```

## <a name="enhancement-of-interpolated-verbatim-strings"></a><span data-ttu-id="9561f-302">Enhancement of interpolated verbatim strings</span><span class="sxs-lookup"><span data-stu-id="9561f-302">Enhancement of interpolated verbatim strings</span></span>

<span data-ttu-id="9561f-303">Order of the `$` and `@` tokens in [interpolated](../language-reference/tokens/interpolated.md) verbatim strings can be any: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span><span class="sxs-lookup"><span data-stu-id="9561f-303">Order of the `$` and `@` tokens in [interpolated](../language-reference/tokens/interpolated.md) verbatim strings can be any: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span> <span data-ttu-id="9561f-304">In earlier C# versions, the `$` token must appear before the `@` token.</span><span class="sxs-lookup"><span data-stu-id="9561f-304">In earlier C# versions, the `$` token must appear before the `@` token.</span></span>

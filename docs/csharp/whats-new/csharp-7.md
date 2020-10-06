---
title: Nouveautés de C# 7.0 | Guide C#
description: Découvrez les nouvelles fonctionnalités disponibles dans la version 7.0 du langage C#.
ms.date: 10/02/2020
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: 774bf9860d929d725f3a2bda4a52bc75ae3921fe
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91755822"
---
# <a name="whats-new-in-c-70-through-c-73"></a><span data-ttu-id="edd6d-103">Nouveautés de C# 7,0 par C# 7,3</span><span class="sxs-lookup"><span data-stu-id="edd6d-103">What's new in C# 7.0 through C# 7.3</span></span>

<span data-ttu-id="edd6d-104">C# 7,0 à C# 7,3 a apporté un certain nombre de fonctionnalités et des améliorations incrémentielles à votre expérience de développement avec C#.</span><span class="sxs-lookup"><span data-stu-id="edd6d-104">C# 7.0 through C# 7.3 brought a number of features and incremental improvements to your development experience with C#.</span></span> <span data-ttu-id="edd6d-105">Cet article fournit une vue d’ensemble des nouvelles fonctionnalités de langage et des options du compilateur.</span><span class="sxs-lookup"><span data-stu-id="edd6d-105">This article provides an overview of the new language features and compiler options.</span></span> <span data-ttu-id="edd6d-106">Les descriptions décrivent le comportement de C# 7,3, qui est la version la plus récente prise en charge pour les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="edd6d-106">The descriptions describe the behavior for C# 7.3, which is the most recent version supported for .NET Framework-based applications.</span></span>

<span data-ttu-id="edd6d-107">L’élément de configuration de sélection de la [version de langage](../language-reference/configure-language-version.md) a été ajouté avec C# 7,1, ce qui vous permet de spécifier la version du langage du compilateur dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="edd6d-107">The [language version selection](../language-reference/configure-language-version.md) configuration element was added with C# 7.1, which enables you to specify the compiler language version in your project file.</span></span>

<span data-ttu-id="edd6d-108">C# 7.0-7.3 ajoute ces fonctionnalités et thèmes au langage C# :</span><span class="sxs-lookup"><span data-stu-id="edd6d-108">C# 7.0-7.3 adds these features and themes to the C# language:</span></span>

- [<span data-ttu-id="edd6d-109">Tuples et éléments ignorés</span><span class="sxs-lookup"><span data-stu-id="edd6d-109">Tuples and discards</span></span>](#tuples-and-discards)
  - <span data-ttu-id="edd6d-110">Vous pouvez créer des types légers et sans nom qui contiennent plusieurs champs publics.</span><span class="sxs-lookup"><span data-stu-id="edd6d-110">You can create lightweight, unnamed types that contain multiple public fields.</span></span> <span data-ttu-id="edd6d-111">Les compilateurs et les outils de l’IDE comprennent la sémantique de ces types.</span><span class="sxs-lookup"><span data-stu-id="edd6d-111">Compilers and IDE tools understand the semantics of these types.</span></span>
  - <span data-ttu-id="edd6d-112">Les éléments ignorés sont les variables temporaires en écriture seule utilisées dans les attributions quand vous ne vous souciez pas de la valeur assignée.</span><span class="sxs-lookup"><span data-stu-id="edd6d-112">Discards are temporary, write-only variables used in assignments when you don't care about the value assigned.</span></span> <span data-ttu-id="edd6d-113">Ils s’avèrent utiles lors de la déconstruction de tuples et de types définis par l’utilisateur, ainsi que lors de l’appel de méthodes avec des paramètres `out`.</span><span class="sxs-lookup"><span data-stu-id="edd6d-113">They're most useful when deconstructing tuples and user-defined types, as well as when calling methods with `out` parameters.</span></span>
- [<span data-ttu-id="edd6d-114">Critères spéciaux</span><span class="sxs-lookup"><span data-stu-id="edd6d-114">Pattern Matching</span></span>](#pattern-matching)
  - <span data-ttu-id="edd6d-115">Vous pouvez créer une logique de branchement basée sur des types arbitraires et les valeurs des membres de ces types.</span><span class="sxs-lookup"><span data-stu-id="edd6d-115">You can create branching logic based on arbitrary types and values of the members of those types.</span></span>
- [<span data-ttu-id="edd6d-116">`async``Main`méthode</span><span class="sxs-lookup"><span data-stu-id="edd6d-116">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="edd6d-117">Le point d’entrée pour une application peut avoir le modificateur `async`.</span><span class="sxs-lookup"><span data-stu-id="edd6d-117">The entry point for an application can have the `async` modifier.</span></span>
- [<span data-ttu-id="edd6d-118">Fonctions locales</span><span class="sxs-lookup"><span data-stu-id="edd6d-118">Local Functions</span></span>](#local-functions)
  - <span data-ttu-id="edd6d-119">Vous pouvez imbriquer des fonctions dans d’autres fonctions afin de limiter leur portée et leur visibilité.</span><span class="sxs-lookup"><span data-stu-id="edd6d-119">You can nest functions inside other functions to limit their scope and visibility.</span></span>
- [<span data-ttu-id="edd6d-120">Autres membres expression-bodied</span><span class="sxs-lookup"><span data-stu-id="edd6d-120">More expression-bodied members</span></span>](#more-expression-bodied-members)
  - <span data-ttu-id="edd6d-121">La liste des membres pouvant être créés à l’aide d’expressions s’est allongée.</span><span class="sxs-lookup"><span data-stu-id="edd6d-121">The list of members that can be authored using expressions has grown.</span></span>
- [<span data-ttu-id="edd6d-122">`throw` Manifestations</span><span class="sxs-lookup"><span data-stu-id="edd6d-122">`throw` Expressions</span></span>](#throw-expressions)
  - <span data-ttu-id="edd6d-123">Vous pouvez lever des exceptions dans les constructions de code qui n’étaient pas autorisées auparavant, car `throw` était une instruction.</span><span class="sxs-lookup"><span data-stu-id="edd6d-123">You can throw exceptions in code constructs that previously weren't allowed because `throw` was a statement.</span></span>
- [<span data-ttu-id="edd6d-124">`default` expressions littérales</span><span class="sxs-lookup"><span data-stu-id="edd6d-124">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="edd6d-125">Vous pouvez utiliser des expressions littérales default dans les expressions de valeur par défaut quand le type cible peut être inféré.</span><span class="sxs-lookup"><span data-stu-id="edd6d-125">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
- [<span data-ttu-id="edd6d-126">Améliorations de la syntaxe littérale numérique</span><span class="sxs-lookup"><span data-stu-id="edd6d-126">Numeric literal syntax improvements</span></span>](#numeric-literal-syntax-improvements)
  - <span data-ttu-id="edd6d-127">De nouveaux jetons améliorent la lisibilité des constantes numériques.</span><span class="sxs-lookup"><span data-stu-id="edd6d-127">New tokens improve readability for numeric constants.</span></span>
- [<span data-ttu-id="edd6d-128">`out` variables</span><span class="sxs-lookup"><span data-stu-id="edd6d-128">`out` variables</span></span>](#out-variables)
  - <span data-ttu-id="edd6d-129">Vous pouvez déclarer des valeurs `out` inline comme arguments de la méthode dans laquelle elles sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="edd6d-129">You can declare `out` values inline as arguments to the method where they're used.</span></span>
- [<span data-ttu-id="edd6d-130">Arguments nommés non placés en position de fin</span><span class="sxs-lookup"><span data-stu-id="edd6d-130">Non-trailing named arguments</span></span>](#non-trailing-named-arguments)
  - <span data-ttu-id="edd6d-131">Les arguments nommés peuvent être suivis par des arguments de position.</span><span class="sxs-lookup"><span data-stu-id="edd6d-131">Named arguments can be followed by positional arguments.</span></span>
- [<span data-ttu-id="edd6d-132">`private protected` modificateur d’accès</span><span class="sxs-lookup"><span data-stu-id="edd6d-132">`private protected` access modifier</span></span>](#private-protected-access-modifier)
  - <span data-ttu-id="edd6d-133">Le modificateur d’accès `private protected` active l’accès pour les classes dérivées dans le même assembly.</span><span class="sxs-lookup"><span data-stu-id="edd6d-133">The `private protected` access modifier enables access for derived classes in the same assembly.</span></span>
- [<span data-ttu-id="edd6d-134">Résolution de surcharge améliorée</span><span class="sxs-lookup"><span data-stu-id="edd6d-134">Improved overload resolution</span></span>](#improved-overload-resolution)
  - <span data-ttu-id="edd6d-135">Nouvelles règles pour résoudre l’ambiguïté de résolution de surcharge.</span><span class="sxs-lookup"><span data-stu-id="edd6d-135">New rules to resolve overload resolution ambiguity.</span></span>
- [<span data-ttu-id="edd6d-136">Techniques d’écriture de code safe et efficace</span><span class="sxs-lookup"><span data-stu-id="edd6d-136">Techniques for writing safe efficient code</span></span>](#safe-efficient-code-enhancements)
  - <span data-ttu-id="edd6d-137">Une combinaison des améliorations de la syntaxe qui permettent d’utiliser les types valeur avec la sémantique de référence.</span><span class="sxs-lookup"><span data-stu-id="edd6d-137">A combination of syntax improvements that enable working with value types using reference semantics.</span></span>

<span data-ttu-id="edd6d-138">Enfin, le compilateur a de nouvelles options :</span><span class="sxs-lookup"><span data-stu-id="edd6d-138">Finally, the compiler has new options:</span></span>

- <span data-ttu-id="edd6d-139">`-refout` et `-refonly` qui contrôlent la génération de l' [assembly de référence](#reference-assembly-generation).</span><span class="sxs-lookup"><span data-stu-id="edd6d-139">`-refout` and `-refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>
- <span data-ttu-id="edd6d-140">`-publicsign` pour activer la signature d’assemblys Open Source Software (OSS).</span><span class="sxs-lookup"><span data-stu-id="edd6d-140">`-publicsign` to enable Open Source Software (OSS) signing of assemblies.</span></span>
- <span data-ttu-id="edd6d-141">`-pathmap` pour fournir un mappage des répertoires sources.</span><span class="sxs-lookup"><span data-stu-id="edd6d-141">`-pathmap` to provide a mapping for source directories.</span></span>

<span data-ttu-id="edd6d-142">Le reste de cet article présente une vue d’ensemble de chaque fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="edd6d-142">The remainder of this article provides an overview of each feature.</span></span> <span data-ttu-id="edd6d-143">Pour chaque fonctionnalité, vous apprendrez le raisonnement sous-jacent et la syntaxe.</span><span class="sxs-lookup"><span data-stu-id="edd6d-143">For each feature, you'll learn the reasoning behind it and the syntax.</span></span> <span data-ttu-id="edd6d-144">Vous pouvez explorer ces fonctionnalités dans votre environnement à l’aide de l’outil global `dotnet try` :</span><span class="sxs-lookup"><span data-stu-id="edd6d-144">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="edd6d-145">Installez l’outil global [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup).</span><span class="sxs-lookup"><span data-stu-id="edd6d-145">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="edd6d-146">Clonez le référentiel [dotnet/try-samples](https://github.com/dotnet/try-samples).</span><span class="sxs-lookup"><span data-stu-id="edd6d-146">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="edd6d-147">Définissez le répertoire actuel sur le sous-répertoire *csharp7* pour le référentiel *try-samples*.</span><span class="sxs-lookup"><span data-stu-id="edd6d-147">Set the current directory to the *csharp7* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="edd6d-148">Exécutez `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="edd6d-148">Run `dotnet try`.</span></span>

## <a name="tuples-and-discards"></a><span data-ttu-id="edd6d-149">Tuples et éléments ignorés</span><span class="sxs-lookup"><span data-stu-id="edd6d-149">Tuples and discards</span></span>

<span data-ttu-id="edd6d-150">C# fournit une syntaxe complète pour les classes et les structs, utilisée pour expliquer l’intention de votre conception.</span><span class="sxs-lookup"><span data-stu-id="edd6d-150">C# provides a rich syntax for classes and structs that is used to explain your design intent.</span></span> <span data-ttu-id="edd6d-151">Cependant, cette syntaxe complète nécessite parfois un travail supplémentaire avec peu d’avantages.</span><span class="sxs-lookup"><span data-stu-id="edd6d-151">But sometimes that rich syntax requires extra work with minimal benefit.</span></span> <span data-ttu-id="edd6d-152">Vous pouvez souvent écrire des méthodes qui nécessitent une structure simple contenant plusieurs éléments de données.</span><span class="sxs-lookup"><span data-stu-id="edd6d-152">You may often write methods that need a simple structure containing more than one data element.</span></span> <span data-ttu-id="edd6d-153">Pour prendre en charge ces scénarios, des *tuples* ont été ajoutées à C#.</span><span class="sxs-lookup"><span data-stu-id="edd6d-153">To support these scenarios *tuples* were added to C#.</span></span> <span data-ttu-id="edd6d-154">Les tuples sont des structures de données légères contenant plusieurs champs pour représenter les membres de données.</span><span class="sxs-lookup"><span data-stu-id="edd6d-154">Tuples are lightweight data structures that contain multiple fields to represent the data members.</span></span> <span data-ttu-id="edd6d-155">Les champs ne sont pas validés et vous ne pouvez pas définir vos propres méthodes.</span><span class="sxs-lookup"><span data-stu-id="edd6d-155">The fields aren't validated, and you can't define your own methods.</span></span> <span data-ttu-id="edd6d-156">Les types de tuple C# prennent en charge `==` et `!=` .</span><span class="sxs-lookup"><span data-stu-id="edd6d-156">C# tuple types support `==` and `!=`.</span></span> <span data-ttu-id="edd6d-157">Pour plus d’informations, consultez</span><span class="sxs-lookup"><span data-stu-id="edd6d-157">For more information.</span></span>

> [!NOTE]
> <span data-ttu-id="edd6d-158">Les tuples étaient disponibles avant C# 7.0, mais ils n’étaient pas efficaces et n’avaient aucune prise en charge du langage.</span><span class="sxs-lookup"><span data-stu-id="edd6d-158">Tuples were available before C# 7.0, but they were inefficient and had no language support.</span></span> <span data-ttu-id="edd6d-159">Cela signifiait que les éléments tuples pouvaient uniquement être référencés comme `Item1`, `Item2`, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="edd6d-159">This meant that tuple elements could only be referenced as `Item1`, `Item2` and so on.</span></span> <span data-ttu-id="edd6d-160">C# 7.0 introduit la prise en charge du langage pour les tuples, ce qui permet d’utiliser des noms sémantiques pour les champs d’un tuple avec de nouveaux types tuple plus efficaces.</span><span class="sxs-lookup"><span data-stu-id="edd6d-160">C# 7.0 introduces language support for tuples, which enables semantic names for the fields of a tuple using new, more efficient tuple types.</span></span>

<span data-ttu-id="edd6d-161">Vous pouvez créer un tuple en assignant une valeur à chaque membre et éventuellement, en fournissant des noms sémantiques à chacun des membres du tuple :</span><span class="sxs-lookup"><span data-stu-id="edd6d-161">You can create a tuple by assigning a value to each member, and optionally providing semantic names to each of the members of the tuple:</span></span>

[!code-csharp[NamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#NamedTuple "Named tuple")]

<span data-ttu-id="edd6d-162">Le tuple `namedLetters` contient des champs appelés `Alpha` et `Beta`.</span><span class="sxs-lookup"><span data-stu-id="edd6d-162">The `namedLetters` tuple contains fields referred to as `Alpha` and `Beta`.</span></span> <span data-ttu-id="edd6d-163">Ces noms existent uniquement au moment de la compilation et ne sont pas conservés, par exemple lors de l’inspection du tuple à l’aide de la réflexion au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="edd6d-163">Those names exist only at compile time and aren't preserved, for example when inspecting the tuple using reflection at run time.</span></span>

<span data-ttu-id="edd6d-164">Dans une assignation de tuple, vous pouvez également spécifier les noms des champs dans la partie droite :</span><span class="sxs-lookup"><span data-stu-id="edd6d-164">In a tuple assignment, you can also specify the names of the fields on the right-hand side of the assignment:</span></span>

[!code-csharp[ImplicitNamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#ImplicitNamedTuple "Implicitly named tuple")]

<span data-ttu-id="edd6d-165">Dans certains cas, vous pouvez souhaiter décompresser les membres d’un tuple qui ont été retournés à partir d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="edd6d-165">There may be times when you want to unpackage the members of a tuple that were returned from a method.</span></span>  <span data-ttu-id="edd6d-166">Pour ce faire, déclarez des variables distinctes pour chacune des valeurs dans le tuple.</span><span class="sxs-lookup"><span data-stu-id="edd6d-166">You can do that by declaring separate variables for each of the values in the tuple.</span></span> <span data-ttu-id="edd6d-167">Cette décompression est appelée *déconstruction* du tuple :</span><span class="sxs-lookup"><span data-stu-id="edd6d-167">This unpackaging is called *deconstructing* the tuple:</span></span>

[!code-csharp[CallingWithDeconstructor](~/samples/snippets/csharp/new-in-7/program.cs#CallingWithDeconstructor "Deconstructing a tuple")]

<span data-ttu-id="edd6d-168">Vous pouvez également fournir une déconstruction similaire pour tout type dans le .NET.</span><span class="sxs-lookup"><span data-stu-id="edd6d-168">You can also provide a similar deconstruction for any type in .NET.</span></span> <span data-ttu-id="edd6d-169">Vous écrivez une méthode `Deconstruct` en tant que membre de la classe.</span><span class="sxs-lookup"><span data-stu-id="edd6d-169">You write a `Deconstruct` method as a member of the class.</span></span> <span data-ttu-id="edd6d-170">Cette méthode `Deconstruct` fournit un ensemble d’arguments `out` pour chacune des propriétés que vous voulez extraire.</span><span class="sxs-lookup"><span data-stu-id="edd6d-170">That `Deconstruct` method provides a set of `out` arguments for each of the properties you want to extract.</span></span> <span data-ttu-id="edd6d-171">Prenons la classe `Point` suivante qui fournit une méthode de déconstructeur qui extrait les coordonnées `X` et `Y` :</span><span class="sxs-lookup"><span data-stu-id="edd6d-171">Consider this `Point` class that provides a deconstructor method that extracts the `X` and `Y` coordinates:</span></span>

[!code-csharp[PointWithDeconstruction](~/samples/snippets/csharp/new-in-7/point.cs#PointWithDeconstruction "Point with deconstruction method")]

<span data-ttu-id="edd6d-172">Vous pouvez extraire les champs individuels en affectant un `Point` à un tuple :</span><span class="sxs-lookup"><span data-stu-id="edd6d-172">You can extract the individual fields by assigning a `Point` to a tuple:</span></span>

[!code-csharp[DeconstructPoint](~/samples/snippets/csharp/new-in-7/program.cs#DeconstructPoint "Deconstruct a point")]

<span data-ttu-id="edd6d-173">Bien souvent, lorsque vous initialisez un tuple, les variables utilisées pour le côté droit de l’assignation sont les mêmes que les noms que vous souhaitez pour les éléments de tuple : les noms des éléments de tuple peuvent être déduits à partir des variables utilisées pour initialiser le tuple :</span><span class="sxs-lookup"><span data-stu-id="edd6d-173">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements: The names of tuple elements can be inferred from the variables used to initialize the tuple:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="edd6d-174">Pour plus d’informations sur cette fonctionnalité, consultez l’article [types de tuples](../language-reference/builtin-types/value-tuples.md) .</span><span class="sxs-lookup"><span data-stu-id="edd6d-174">You can learn more about this feature in the [Tuple types](../language-reference/builtin-types/value-tuples.md) article.</span></span>

<span data-ttu-id="edd6d-175">Souvent, lors de la déconstruction d’un tuple ou de l’appel d’une méthode avec des paramètres `out`, vous devez définir une variable dont la valeur ne vous importe pas et que vous ne prévoyez pas d’utiliser.</span><span class="sxs-lookup"><span data-stu-id="edd6d-175">Often when deconstructing a tuple or calling a method with `out` parameters, you're forced to define a variable whose value you don't care about and don't intend to use.</span></span> <span data-ttu-id="edd6d-176">C# ajoute la prise en charge des *éléments ignorés* pour gérer ce scénario.</span><span class="sxs-lookup"><span data-stu-id="edd6d-176">C# adds support for *discards* to handle this scenario.</span></span> <span data-ttu-id="edd6d-177">Un élément ignoré est une variable en écriture seule dont le nom est `_` (caractère de soulignement) ; vous pouvez assigner toutes les valeurs que vous souhaitez ignorer à la variable unique.</span><span class="sxs-lookup"><span data-stu-id="edd6d-177">A discard is a write-only variable whose name is `_` (the underscore character); you can assign all of the values that you intend to discard to the single variable.</span></span> <span data-ttu-id="edd6d-178">Un élément ignoré est semblable à une variable non assignée ; en dehors de l’instruction d’assignation, l’élément ignoré ne peut pas être utilisé dans le code.</span><span class="sxs-lookup"><span data-stu-id="edd6d-178">A discard is like an unassigned variable; apart from the assignment statement, the discard can't be used in code.</span></span>

<span data-ttu-id="edd6d-179">Les éléments ignorés sont pris en charge dans les scénarios suivants :</span><span class="sxs-lookup"><span data-stu-id="edd6d-179">Discards are supported in the following scenarios:</span></span>

- <span data-ttu-id="edd6d-180">Lors de la déconstruction de tuples ou de types définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="edd6d-180">When deconstructing tuples or user-defined types.</span></span>
- <span data-ttu-id="edd6d-181">Lors d’appels à des méthodes avec des paramètres [out](../language-reference/keywords/out-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="edd6d-181">When calling methods with [out](../language-reference/keywords/out-parameter-modifier.md) parameters.</span></span>
- <span data-ttu-id="edd6d-182">Dans une opération de critères spéciaux avec les instructions [is](../language-reference/keywords/is.md) et [switch](../language-reference/keywords/switch.md).</span><span class="sxs-lookup"><span data-stu-id="edd6d-182">In a pattern matching operation with the [is](../language-reference/keywords/is.md) and [switch](../language-reference/keywords/switch.md) statements.</span></span>
- <span data-ttu-id="edd6d-183">Comme un identificateur autonome quand vous voulez explicitement identifier la valeur d’une assignation comme un élément ignoré.</span><span class="sxs-lookup"><span data-stu-id="edd6d-183">As a standalone identifier when you want to explicitly identify the value of an assignment as a discard.</span></span>

<span data-ttu-id="edd6d-184">L’exemple suivant définit une méthode `QueryCityDataForYears` qui retourne un tuple à 6 composants qui contient des données pour une ville au cours de deux années différentes.</span><span class="sxs-lookup"><span data-stu-id="edd6d-184">The following example defines a `QueryCityDataForYears` method that returns a 6-tuple that contains data for a city for two different years.</span></span> <span data-ttu-id="edd6d-185">L’appel de méthode dans l’exemple s’intéresse uniquement à deux valeurs de population retournées par la méthode et traite par conséquent les valeurs restantes dans le tuple comme des éléments ignorés lors de la déconstruction du tuple.</span><span class="sxs-lookup"><span data-stu-id="edd6d-185">The method call in the example is concerned only with the two population values returned by the method and so treats the remaining values in the tuple as discards when it deconstructs the tuple.</span></span>

[!code-csharp[Tuple-discard](~/samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

<span data-ttu-id="edd6d-186">Pour plus d’informations, consultez [Éléments ignorés](../discards.md).</span><span class="sxs-lookup"><span data-stu-id="edd6d-186">For more information, see [Discards](../discards.md).</span></span>

## <a name="pattern-matching"></a><span data-ttu-id="edd6d-187">Critères spéciaux</span><span class="sxs-lookup"><span data-stu-id="edd6d-187">Pattern matching</span></span>

<span data-ttu-id="edd6d-188">Les *critères spéciaux* sont un ensemble de fonctionnalités qui permettent de nouvelles façons d’exprimer le contrôle du workflow dans votre code.</span><span class="sxs-lookup"><span data-stu-id="edd6d-188">*Pattern matching* is a set of features that enable new ways to express control flow in your code.</span></span> <span data-ttu-id="edd6d-189">Vous pouvez tester des variables pour leur type, leurs valeurs ou les valeurs de leurs propriétés.</span><span class="sxs-lookup"><span data-stu-id="edd6d-189">You can test variables for their type, values or the values of their properties.</span></span> <span data-ttu-id="edd6d-190">Ces techniques créent un flot de code plus lisible.</span><span class="sxs-lookup"><span data-stu-id="edd6d-190">These techniques create more readable code flow.</span></span>

<span data-ttu-id="edd6d-191">Les critères spéciaux prennent en charge les expressions `is` et les expressions `switch`.</span><span class="sxs-lookup"><span data-stu-id="edd6d-191">Pattern matching supports `is` expressions and `switch` expressions.</span></span> <span data-ttu-id="edd6d-192">L’une ou l’autre permettent d’inspecter un objet et ses propriétés afin de déterminer s’il correspond au modèle recherché.</span><span class="sxs-lookup"><span data-stu-id="edd6d-192">Each enables inspecting an object and its properties to determine if that object satisfies the sought pattern.</span></span> <span data-ttu-id="edd6d-193">Vous utilisez le mot clé `when` pour spécifier des règles supplémentaires pour le modèle.</span><span class="sxs-lookup"><span data-stu-id="edd6d-193">You use the `when` keyword to specify additional rules to the pattern.</span></span>

<span data-ttu-id="edd6d-194">L' `is` expression de modèle étend l' [ `is` opérateur](../language-reference/keywords/is.md#pattern-matching-with-is) familier pour interroger un objet sur son type et assigner le résultat dans une instruction.</span><span class="sxs-lookup"><span data-stu-id="edd6d-194">The `is` pattern expression extends the familiar [`is` operator](../language-reference/keywords/is.md#pattern-matching-with-is) to query an object about its type and assign the result in one instruction.</span></span> <span data-ttu-id="edd6d-195">Le code suivant vérifie si une variable est un `int`, et si tel est le cas, il l’ajoute à la somme actuelle :</span><span class="sxs-lookup"><span data-stu-id="edd6d-195">The following code checks if a variable is an `int`, and if so, adds it to the current sum:</span></span>

```csharp
if (input is int count)
    sum += count;
```

<span data-ttu-id="edd6d-196">Le petit exemple précédent illustre les améliorations apportées à l’expression `is`.</span><span class="sxs-lookup"><span data-stu-id="edd6d-196">The preceding small example demonstrates the enhancements to the `is` expression.</span></span> <span data-ttu-id="edd6d-197">Vous pouvez tester par rapport à des types valeur, ainsi que des types référence, et vous pouvez assigner le résultat de réussite à une nouvelle variable du type correct.</span><span class="sxs-lookup"><span data-stu-id="edd6d-197">You can test against value types as well as reference types, and you can assign the successful result to a new variable of the correct type.</span></span>

<span data-ttu-id="edd6d-198">L’expression de correspondance switch a une syntaxe familière, basée sur l’instruction `switch` qui fait déjà partie du langage C#.</span><span class="sxs-lookup"><span data-stu-id="edd6d-198">The switch match expression has a familiar syntax, based on the `switch` statement already part of the C# language.</span></span> <span data-ttu-id="edd6d-199">L’instruction switch mise à jour a plusieurs nouvelles constructions :</span><span class="sxs-lookup"><span data-stu-id="edd6d-199">The updated switch statement has several new constructs:</span></span>

- <span data-ttu-id="edd6d-200">Le type directeur d’une expression `switch` n’est plus limité aux types intégraux, aux types `Enum`, `string` ou à un type nullable correspondant à l’un de ces types.</span><span class="sxs-lookup"><span data-stu-id="edd6d-200">The governing type of a `switch` expression is no longer restricted to integral types, `Enum` types, `string`, or a nullable type corresponding to one of those types.</span></span> <span data-ttu-id="edd6d-201">Vous pouvez utiliser n’importe quel type.</span><span class="sxs-lookup"><span data-stu-id="edd6d-201">Any type may be used.</span></span>
- <span data-ttu-id="edd6d-202">Vous pouvez tester le type de l’expression `switch` dans chaque étiquette `case`.</span><span class="sxs-lookup"><span data-stu-id="edd6d-202">You can test the type of the `switch` expression in each `case` label.</span></span> <span data-ttu-id="edd6d-203">Comme avec l’expression `is`, vous pouvez assigner une nouvelle variable à ce type.</span><span class="sxs-lookup"><span data-stu-id="edd6d-203">As with the `is` expression, you may assign a new variable to that type.</span></span>
- <span data-ttu-id="edd6d-204">Vous pouvez ajouter une clause `when` pour tester encore les conditions sur cette variable.</span><span class="sxs-lookup"><span data-stu-id="edd6d-204">You may add a `when` clause to further test conditions on that variable.</span></span>
- <span data-ttu-id="edd6d-205">L’ordre des étiquettes `case` est à présent important.</span><span class="sxs-lookup"><span data-stu-id="edd6d-205">The order of `case` labels is now important.</span></span> <span data-ttu-id="edd6d-206">La première branche à faire correspondre est exécutée ; les autres sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="edd6d-206">The first branch to match is executed; others are skipped.</span></span>

<span data-ttu-id="edd6d-207">Le code suivant illustre ces nouvelles fonctionnalités :</span><span class="sxs-lookup"><span data-stu-id="edd6d-207">The following code demonstrates these new features:</span></span>

```csharp
public static int SumPositiveNumbers(IEnumerable<object> sequence)
{
    int sum = 0;
    foreach (var i in sequence)
    {
        switch (i)
        {
            case 0:
                break;
            case IEnumerable<int> childSequence:
            {
                foreach(var item in childSequence)
                    sum += (item > 0) ? item : 0;
                break;
            }
            case int n when n > 0:
                sum += n;
                break;
            case null:
                throw new NullReferenceException("Null found in sequence");
            default:
                throw new InvalidOperationException("Unrecognized type");
        }
    }
    return sum;
}
```

- <span data-ttu-id="edd6d-208">`case 0:` est le modèle de constante classique.</span><span class="sxs-lookup"><span data-stu-id="edd6d-208">`case 0:` is the familiar constant pattern.</span></span>
- <span data-ttu-id="edd6d-209">`case IEnumerable<int> childSequence:` est un modèle de type.</span><span class="sxs-lookup"><span data-stu-id="edd6d-209">`case IEnumerable<int> childSequence:` is a type pattern.</span></span>
- <span data-ttu-id="edd6d-210">`case int n when n > 0:` est un modèle de type avec une autre condition `when`.</span><span class="sxs-lookup"><span data-stu-id="edd6d-210">`case int n when n > 0:` is a type pattern with an additional `when` condition.</span></span>
- <span data-ttu-id="edd6d-211">`case null:` est le modèle null.</span><span class="sxs-lookup"><span data-stu-id="edd6d-211">`case null:` is the null pattern.</span></span>
- <span data-ttu-id="edd6d-212">`default:` est le cas par défaut classique.</span><span class="sxs-lookup"><span data-stu-id="edd6d-212">`default:` is the familiar default case.</span></span>

<span data-ttu-id="edd6d-213">À compter de C# 7.1, l’expression de modèle de `is` et du modèle de type `switch` peut avoir le type d’un paramètre de type générique,</span><span class="sxs-lookup"><span data-stu-id="edd6d-213">Beginning with C# 7.1, the pattern expression for `is` and the `switch` type pattern may have the type of a generic type parameter.</span></span> <span data-ttu-id="edd6d-214">ce qui peut se révéler particulièrement utile pour vérifier des types potentiellement `struct` ou `class` tout en évitant le boxing.</span><span class="sxs-lookup"><span data-stu-id="edd6d-214">This can be most useful when checking types that may be either `struct` or `class` types, and you want to avoid boxing.</span></span>

<span data-ttu-id="edd6d-215">Pour plus d’informations sur les critères spéciaux, consultez [Critères spéciaux en C#](../pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="edd6d-215">You can learn more about pattern matching in [Pattern Matching in C#](../pattern-matching.md).</span></span>

## <a name="async-main"></a><span data-ttu-id="edd6d-216">Async main</span><span class="sxs-lookup"><span data-stu-id="edd6d-216">Async main</span></span>

<span data-ttu-id="edd6d-217">Une méthode *async main* vous permet d’utiliser `await` dans votre méthode `Main`.</span><span class="sxs-lookup"><span data-stu-id="edd6d-217">An *async main* method enables you to use `await` in your `Main` method.</span></span> <span data-ttu-id="edd6d-218">Auparavant, vous deviez écrire :</span><span class="sxs-lookup"><span data-stu-id="edd6d-218">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="edd6d-219">Vous pouvez désormais écrire :</span><span class="sxs-lookup"><span data-stu-id="edd6d-219">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="edd6d-220">Si votre programme ne retourne pas de code de sortie, vous pouvez déclarer une méthode `Main` qui retourne une <xref:System.Threading.Tasks.Task> :</span><span class="sxs-lookup"><span data-stu-id="edd6d-220">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="edd6d-221">Pour plus d’informations, voir l’article [async main](../programming-guide/main-and-command-args/index.md) du guide de programmation.</span><span class="sxs-lookup"><span data-stu-id="edd6d-221">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) article in the programming guide.</span></span>

## <a name="local-functions"></a><span data-ttu-id="edd6d-222">Fonctions locales</span><span class="sxs-lookup"><span data-stu-id="edd6d-222">Local functions</span></span>

<span data-ttu-id="edd6d-223">De nombreuses conceptions pour les classes incluent des méthodes qui sont appelées à partir d’un seul emplacement.</span><span class="sxs-lookup"><span data-stu-id="edd6d-223">Many designs for classes include methods that are called from only one location.</span></span> <span data-ttu-id="edd6d-224">Ces méthodes privées supplémentaires maintiennent chaque méthode réduite et focalisée.</span><span class="sxs-lookup"><span data-stu-id="edd6d-224">These additional private methods keep each method small and focused.</span></span> <span data-ttu-id="edd6d-225">Les *fonctions locales* vous permettent d’utiliser des méthodes dans le contexte d’une autre méthode.</span><span class="sxs-lookup"><span data-stu-id="edd6d-225">*Local functions* enable you to  methods inside the context of another method.</span></span> <span data-ttu-id="edd6d-226">Il est ainsi plus facile pour les lecteurs de la classe de voir que la méthode locale est appelée uniquement à partir du contexte dans lequel elle a été déclarée.</span><span class="sxs-lookup"><span data-stu-id="edd6d-226">Local functions make it easier for readers of the class to see that the local method is only called from the context in which it is declared.</span></span>

<span data-ttu-id="edd6d-227">Il existe deux cas d’utilisation courants pour les fonctions locales : les méthodes iterator publiques et les méthodes async publiques.</span><span class="sxs-lookup"><span data-stu-id="edd6d-227">There are two common use cases for local functions: public iterator methods and public async methods.</span></span> <span data-ttu-id="edd6d-228">Ces deux types de méthodes génèrent du code qui signale les erreurs plus tard que ce qu’attendent les programmeurs.</span><span class="sxs-lookup"><span data-stu-id="edd6d-228">Both types of methods generate code that reports errors later than programmers might expect.</span></span> <span data-ttu-id="edd6d-229">Dans les méthodes iterator, toute exception est observée uniquement lors de l’appel de code qui énumère la séquence retournée.</span><span class="sxs-lookup"><span data-stu-id="edd6d-229">In iterator methods, any exceptions are observed only when calling code that enumerates the returned sequence.</span></span> <span data-ttu-id="edd6d-230">Dans les méthodes async, toute exception est observée uniquement quand le `Task` retourné est attendu.</span><span class="sxs-lookup"><span data-stu-id="edd6d-230">In async methods, any exceptions are only observed when the returned `Task` is awaited.</span></span> <span data-ttu-id="edd6d-231">L’exemple suivant illustre la séparation entre la validation de paramètres et l’implémentation de l’itérateur à l’aide d’une fonction locale :</span><span class="sxs-lookup"><span data-stu-id="edd6d-231">The following example demonstrates separating parameter validation from the iterator implementation using a local function:</span></span>

[!code-csharp[22_IteratorMethodLocal](~/samples/snippets/csharp/new-in-7/Iterator.cs#IteratorMethodLocal "Iterator method with local function")]

<span data-ttu-id="edd6d-232">Il est possible d’utiliser la même technique avec les méthodes `async` pour garantir que les exceptions résultant de la validation d’argument sont levées avant le début de la tâche asynchrone :</span><span class="sxs-lookup"><span data-stu-id="edd6d-232">The same technique can be employed with `async` methods to ensure that exceptions arising from argument validation are thrown before the asynchronous work begins:</span></span>

[!code-csharp[TaskExample](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

<span data-ttu-id="edd6d-233">Cette syntaxe est maintenant prise en charge :</span><span class="sxs-lookup"><span data-stu-id="edd6d-233">This syntax is now supported:</span></span>

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

<span data-ttu-id="edd6d-234">L’attribut `SomeThingAboutFieldAttribute` est appliqué au champ de stockage généré par le compilateur pour `SomeProperty`.</span><span class="sxs-lookup"><span data-stu-id="edd6d-234">The attribute `SomeThingAboutFieldAttribute` is applied to the compiler generated backing field for `SomeProperty`.</span></span> <span data-ttu-id="edd6d-235">Pour plus d’informations, consultez les [attributs](../programming-guide/concepts/attributes/index.md) dans le guide de programmation C#.</span><span class="sxs-lookup"><span data-stu-id="edd6d-235">For more information, see [attributes](../programming-guide/concepts/attributes/index.md) in the C# programming guide.</span></span>

> [!NOTE]
> <span data-ttu-id="edd6d-236">Certaines des conceptions prises en charge par les fonctions locales peuvent également être accomplies à l’aide d' *expressions lambda*.</span><span class="sxs-lookup"><span data-stu-id="edd6d-236">Some of the designs that are supported by local functions can also be accomplished using *lambda expressions*.</span></span> <span data-ttu-id="edd6d-237">Pour plus d’informations, consultez [fonctions locales et expressions lambda](../programming-guide/classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions).</span><span class="sxs-lookup"><span data-stu-id="edd6d-237">For more information, see [Local functions vs. lambda expressions](../programming-guide/classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions).</span></span>

## <a name="more-expression-bodied-members"></a><span data-ttu-id="edd6d-238">Autres membres expression-bodied</span><span class="sxs-lookup"><span data-stu-id="edd6d-238">More expression-bodied members</span></span>

<span data-ttu-id="edd6d-239">C# 6 a introduit les [membres expression-bodied](csharp-6.md#expression-bodied-function-members) pour les fonctions membres, ainsi que des propriétés en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="edd6d-239">C# 6 introduced [expression-bodied members](csharp-6.md#expression-bodied-function-members) for member functions, and read-only properties.</span></span> <span data-ttu-id="edd6d-240">C# 7.0 développe les membres autorisés pouvant être implémentés comme expressions.</span><span class="sxs-lookup"><span data-stu-id="edd6d-240">C# 7.0 expands the allowed members that can be implemented as expressions.</span></span> <span data-ttu-id="edd6d-241">Dans C# 7.0, vous pouvez implémenter des *constructeurs*, des *finaliseurs* ainsi que des accesseurs `get` et `set` sur des *propriétés* et des *indexeurs*.</span><span class="sxs-lookup"><span data-stu-id="edd6d-241">In C# 7.0, you can implement *constructors*, *finalizers*, and `get` and `set` accessors on *properties* and *indexers*.</span></span> <span data-ttu-id="edd6d-242">Le code suivant présente des exemples de chaque élément :</span><span class="sxs-lookup"><span data-stu-id="edd6d-242">The following code shows examples of each:</span></span>

[!code-csharp[ExpressionBodiedMembers](~/samples/snippets/csharp/new-in-7/expressionmembers.cs#ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> <span data-ttu-id="edd6d-243">Cet exemple n’a pas besoin de finaliseur, mais il est présenté pour illustrer la syntaxe.</span><span class="sxs-lookup"><span data-stu-id="edd6d-243">This example does not need a finalizer, but it is shown to demonstrate the syntax.</span></span> <span data-ttu-id="edd6d-244">Vous ne devez implémenter un finaliseur dans votre classe que si cela est nécessaire pour libérer des ressources non managées.</span><span class="sxs-lookup"><span data-stu-id="edd6d-244">You should not implement a finalizer in your class unless it is necessary to  release unmanaged resources.</span></span> <span data-ttu-id="edd6d-245">Vous devez également envisager d’utiliser la classe <xref:System.Runtime.InteropServices.SafeHandle> au lieu de gérer directement les ressources non managées.</span><span class="sxs-lookup"><span data-stu-id="edd6d-245">You should also consider using the <xref:System.Runtime.InteropServices.SafeHandle> class instead of managing unmanaged resources directly.</span></span>

<span data-ttu-id="edd6d-246">Ces nouveaux emplacements pour les membres expression-bodied représentent une étape importante pour le langage C# : ces fonctionnalités ont été implémentées par des membres de la communauté travaillant sur le projet open source [Roslyn](https://github.com/dotnet/Roslyn).</span><span class="sxs-lookup"><span data-stu-id="edd6d-246">These new locations for expression-bodied members represent an important milestone for the C# language: These features were implemented by community members working on the open-source [Roslyn](https://github.com/dotnet/Roslyn) project.</span></span>

<span data-ttu-id="edd6d-247">La modification d’une méthode en un membre expression-bodied est une [modification compatible binaire](version-update-considerations.md#binary-compatible-changes).</span><span class="sxs-lookup"><span data-stu-id="edd6d-247">Changing a method to an expression bodied member is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

## <a name="throw-expressions"></a><span data-ttu-id="edd6d-248">Expressions throw</span><span class="sxs-lookup"><span data-stu-id="edd6d-248">Throw expressions</span></span>

<span data-ttu-id="edd6d-249">En C#, `throw` a toujours été une instruction.</span><span class="sxs-lookup"><span data-stu-id="edd6d-249">In C#, `throw` has always been a statement.</span></span> <span data-ttu-id="edd6d-250">Étant donné que `throw` est une instruction, et non pas une expression, certaines constructions C# ne pouvaient pas l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="edd6d-250">Because `throw` is a statement, not an expression, there were C# constructs where you couldn't use it.</span></span> <span data-ttu-id="edd6d-251">Il s’agit notamment des expressions conditionnelles, des expressions de fusion null, ainsi que de certaines expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="edd6d-251">These included conditional expressions, null coalescing expressions, and some lambda expressions.</span></span> <span data-ttu-id="edd6d-252">L’ajout de membres expression-bodied ajoute des emplacements supplémentaires où les expressions `throw` seraient utiles.</span><span class="sxs-lookup"><span data-stu-id="edd6d-252">The addition of expression-bodied members adds more locations where `throw` expressions would be useful.</span></span> <span data-ttu-id="edd6d-253">Afin que vous puissiez écrire l’une de ces constructions, C# 7,0 introduit des [*expressions Throw*](../language-reference/keywords/throw.md#the-throw-expression).</span><span class="sxs-lookup"><span data-stu-id="edd6d-253">So that you can write any of these constructs, C# 7.0 introduces [*throw expressions*](../language-reference/keywords/throw.md#the-throw-expression).</span></span>

<span data-ttu-id="edd6d-254">Cet ajout facilite l’écriture de code davantage basé sur des expressions.</span><span class="sxs-lookup"><span data-stu-id="edd6d-254">This addition makes it easier to write more expression-based code.</span></span> <span data-ttu-id="edd6d-255">Vous n’avez pas besoin d’instructions supplémentaires pour la vérification des erreurs.</span><span class="sxs-lookup"><span data-stu-id="edd6d-255">You don't need additional statements for error checking.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="edd6d-256">Expressions littérales par défaut</span><span class="sxs-lookup"><span data-stu-id="edd6d-256">Default literal expressions</span></span>

<span data-ttu-id="edd6d-257">Les expressions littérales par défaut sont une amélioration des expressions de valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="edd6d-257">Default literal expressions are an enhancement to default value expressions.</span></span> <span data-ttu-id="edd6d-258">Ces expressions initialisent une variable à la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="edd6d-258">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="edd6d-259">Vous deviez écrire auparavant :</span><span class="sxs-lookup"><span data-stu-id="edd6d-259">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="edd6d-260">Vous pouvez désormais omettre le type du côté droit de l’initialisation :</span><span class="sxs-lookup"><span data-stu-id="edd6d-260">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="edd6d-261">Pour plus d’informations, voir la section [littéral par défaut](../language-reference/operators/default.md#default-literal) de l’article [opérateur par défaut](../language-reference/operators/default.md).</span><span class="sxs-lookup"><span data-stu-id="edd6d-261">For more information, see the [default literal](../language-reference/operators/default.md#default-literal) section of the [default operator](../language-reference/operators/default.md) article.</span></span>

## <a name="numeric-literal-syntax-improvements"></a><span data-ttu-id="edd6d-262">Améliorations de la syntaxe littérale numérique</span><span class="sxs-lookup"><span data-stu-id="edd6d-262">Numeric literal syntax improvements</span></span>

<span data-ttu-id="edd6d-263">La mauvaise interprétation de constantes numériques peut rendre plus difficile la compréhension du code quand il est lu pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="edd6d-263">Misreading numeric constants can make it harder to understand code when reading it for the first time.</span></span> <span data-ttu-id="edd6d-264">Les masques de bits ou d’autres valeurs symboliques sont source de méprise.</span><span class="sxs-lookup"><span data-stu-id="edd6d-264">Bit masks or other symbolic values are prone to misunderstanding.</span></span> <span data-ttu-id="edd6d-265">C# 7.0 comprend deux nouvelles fonctionnalités permettant d’écrire des nombres de la manière la plus lisible pour l’utilisation prévue : les *littéraux binaires* et les *séparateurs de chiffres*.</span><span class="sxs-lookup"><span data-stu-id="edd6d-265">C# 7.0 includes two new features to write numbers in the most readable fashion for the intended use: *binary literals*, and *digit separators*.</span></span>

<span data-ttu-id="edd6d-266">Dans les cas où vous créez des masques de bits chaque fois qu’une représentation binaire d’un nombre rend le code plus lisible, écrivez ce nombre au format binaire :</span><span class="sxs-lookup"><span data-stu-id="edd6d-266">For those times when you're creating bit masks, or whenever a binary representation of a number makes the most readable code, write that number in binary:</span></span>

[!code-csharp[ThousandSeparators](~/samples/snippets/csharp/new-in-7/Program.cs#ThousandSeparators "Thousands separators")]

<span data-ttu-id="edd6d-267">Le `0b` au début de la constante indique que le nombre est écrit sous la forme d’un nombre binaire.</span><span class="sxs-lookup"><span data-stu-id="edd6d-267">The `0b` at the beginning of the constant indicates that the number is written as a binary number.</span></span> <span data-ttu-id="edd6d-268">Les nombres binaires peuvent être longs. il est donc souvent plus facile de voir les modèles binaires en introduisant le `_` sous forme de séparateur numérique, comme indiqué dans la constante binaire de l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="edd6d-268">Binary numbers can get long, so it's often easier to see the bit patterns by introducing the `_` as a digit separator, as shown in the binary constant in the preceding example.</span></span> <span data-ttu-id="edd6d-269">Le séparateur de chiffres peut apparaître n’importe où dans la constante.</span><span class="sxs-lookup"><span data-stu-id="edd6d-269">The digit separator can appear anywhere in the constant.</span></span> <span data-ttu-id="edd6d-270">Pour les nombres de base 10, il est courant de l’utiliser comme séparateur des milliers.</span><span class="sxs-lookup"><span data-stu-id="edd6d-270">For base 10 numbers, it is common to use it as a thousands separator.</span></span> <span data-ttu-id="edd6d-271">Les littéraux numériques hexadécimaux et binaires peuvent commencer par un `_` :</span><span class="sxs-lookup"><span data-stu-id="edd6d-271">Hex and binary numeric literals may begin with an `_`:</span></span>

[!code-csharp[LargeIntegers](~/samples/snippets/csharp/new-in-7/Program.cs#LargeIntegers "Large integer")]

<span data-ttu-id="edd6d-272">Il est possible d’utiliser le séparateur de chiffres également avec les types `decimal`, `float` et `double` :</span><span class="sxs-lookup"><span data-stu-id="edd6d-272">The digit separator can be used with `decimal`, `float`, and `double` types as well:</span></span>

[!code-csharp[OtherConstants](~/samples/snippets/csharp/new-in-7/Program.cs#OtherConstants "non-integral constants")]

<span data-ttu-id="edd6d-273">Globalement, vous pouvez déclarer des constantes numériques avec beaucoup plus de lisibilité.</span><span class="sxs-lookup"><span data-stu-id="edd6d-273">Taken together, you can declare numeric constants with much more readability.</span></span>

## <a name="out-variables"></a><span data-ttu-id="edd6d-274">Variables `out`</span><span class="sxs-lookup"><span data-stu-id="edd6d-274">`out` variables</span></span>

<span data-ttu-id="edd6d-275">La syntaxe existante qui prend en charge les `out` paramètres a été améliorée en C# 7.</span><span class="sxs-lookup"><span data-stu-id="edd6d-275">The existing syntax that supports `out` parameters has been improved in C# 7.</span></span> <span data-ttu-id="edd6d-276">Vous pouvez désormais déclarer des variables `out` dans la liste d’arguments d’un appel de méthode, au lieu d’écrire une instruction de déclaration distincte :</span><span class="sxs-lookup"><span data-stu-id="edd6d-276">You can now declare `out` variables in the argument list of a method call, rather than writing a separate declaration statement:</span></span>

[!code-csharp[OutVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVariableDeclarations "Out variable declarations")]

<span data-ttu-id="edd6d-277">Vous pouvez spécifier le type de la `out` variable pour plus de clarté, comme indiqué dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="edd6d-277">You may want to specify the type of the `out` variable for clarity, as shown in the preceding example.</span></span> <span data-ttu-id="edd6d-278">Toutefois, le langage prend en charge l’utilisation d’une variable locale implicitement typée :</span><span class="sxs-lookup"><span data-stu-id="edd6d-278">However, the language does support using an implicitly typed local variable:</span></span>

[!code-csharp[OutVarVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVarVariableDeclarations "Implicitly typed Out variable")]

- <span data-ttu-id="edd6d-279">Le code est plus facile à lire.</span><span class="sxs-lookup"><span data-stu-id="edd6d-279">The code is easier to read.</span></span>
  - <span data-ttu-id="edd6d-280">Vous déclarez la variable out là où vous l’utilisez, et non sur une ligne de code précédente.</span><span class="sxs-lookup"><span data-stu-id="edd6d-280">You declare the out variable where you use it, not on a preceding line of code.</span></span>
- <span data-ttu-id="edd6d-281">Il n’est pas nécessaire d’assigner une valeur initiale.</span><span class="sxs-lookup"><span data-stu-id="edd6d-281">No need to assign an initial value.</span></span>
  - <span data-ttu-id="edd6d-282">En déclarant la variable `out` à l’endroit où elle est utilisée dans un appel de méthode, vous ne pouvez pas l’utiliser accidentellement avant qu’elle soit assignée.</span><span class="sxs-lookup"><span data-stu-id="edd6d-282">By declaring the `out` variable where it's used in a method call, you can't accidentally use it before it is assigned.</span></span>

<span data-ttu-id="edd6d-283">La syntaxe ajoutée dans C# 7.0 pour autoriser les déclarations variables `out` a été étendue pour inclure des initialiseurs de champ, des initialiseurs de propriété, des initialiseurs de constructeur et des clauses de requête.</span><span class="sxs-lookup"><span data-stu-id="edd6d-283">The syntax added in C# 7.0 to allow `out` variable declarations has been extended to include field initializers, property initializers, constructor initializers, and query clauses.</span></span> <span data-ttu-id="edd6d-284">Il permet d’écrire un code tel que l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="edd6d-284">It enables code such as the following example:</span></span>

```csharp
public class B
{
   public B(int i, out int j)
   {
      j = i;
   }
}

public class D : B
{
   public D(int i) : base(i, out var j)
   {
      Console.WriteLine($"The value of 'j' is {j}");
   }
}
```

## <a name="non-trailing-named-arguments"></a><span data-ttu-id="edd6d-285">Arguments nommés non placés en position de fin</span><span class="sxs-lookup"><span data-stu-id="edd6d-285">Non-trailing named arguments</span></span>

<span data-ttu-id="edd6d-286">Les appels de méthode peuvent désormais utiliser des arguments nommés qui précèdent les arguments de position quand ces arguments nommés se trouvent dans les positions appropriées.</span><span class="sxs-lookup"><span data-stu-id="edd6d-286">Method calls may now use named arguments that precede positional arguments when those named arguments are in the correct positions.</span></span> <span data-ttu-id="edd6d-287">Pour plus d’informations, consultez [arguments nommés et facultatifs](../programming-guide/classes-and-structs/named-and-optional-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="edd6d-287">For more information, see [Named and optional arguments](../programming-guide/classes-and-structs/named-and-optional-arguments.md).</span></span>

## <a name="private-protected-access-modifier"></a><span data-ttu-id="edd6d-288">*private protected* (modificateur d’accès)</span><span class="sxs-lookup"><span data-stu-id="edd6d-288">*private protected* access modifier</span></span>

<span data-ttu-id="edd6d-289">Enfin, un nouveau modificateur d’accès composé, `private protected`, indique qu’un membre est accessible à la classe globale ou aux classes dérivées déclarées dans le même assembly.</span><span class="sxs-lookup"><span data-stu-id="edd6d-289">A new compound access modifier: `private protected` indicates that a member may be accessed by containing class or derived classes that are declared in the same assembly.</span></span> <span data-ttu-id="edd6d-290">Alors que `protected internal` autorise l’accès par des classes dérivées ou qui se trouvent dans le même assembly, `private protected` limite l’accès aux types dérivés déclarés dans le même assembly.</span><span class="sxs-lookup"><span data-stu-id="edd6d-290">While `protected internal` allows access by derived classes or classes that are in the same assembly, `private protected` limits access to derived types declared in the same assembly.</span></span>

<span data-ttu-id="edd6d-291">Pour plus d’informations, consultez [modificateurs d’accès](../language-reference/keywords/access-modifiers.md) dans la référence du langage.</span><span class="sxs-lookup"><span data-stu-id="edd6d-291">For more information, see [access modifiers](../language-reference/keywords/access-modifiers.md) in the language reference.</span></span>

## <a name="improved-overload-candidates"></a><span data-ttu-id="edd6d-292">Candidats de surcharge améliorés</span><span class="sxs-lookup"><span data-stu-id="edd6d-292">Improved overload candidates</span></span>

<span data-ttu-id="edd6d-293">Dans chaque version, les règles de résolution de surcharge ont été mises à jour pour résoudre les situations où des appels de méthode ambigus sont face à un choix « évident ».</span><span class="sxs-lookup"><span data-stu-id="edd6d-293">In every release, the overload resolution rules get updated to address situations where ambiguous method invocations have an "obvious" choice.</span></span> <span data-ttu-id="edd6d-294">Cette version ajoute trois nouvelles règles pour aider le compilateur à opter pour le choix évident :</span><span class="sxs-lookup"><span data-stu-id="edd6d-294">This release adds three new rules to help the compiler pick the obvious choice:</span></span>

1. <span data-ttu-id="edd6d-295">Lorsqu’un groupe de méthodes contient à la fois une instance et des membres statiques, le compilateur ignore les membres de l’instance si la méthode a été appelée sans récepteur d’instance ou contexte.</span><span class="sxs-lookup"><span data-stu-id="edd6d-295">When a method group contains both instance and static members, the compiler discards the instance members if the method was invoked without an instance receiver or context.</span></span> <span data-ttu-id="edd6d-296">Le compilateur ignore les membres statiques si la méthode a été appelée avec un récepteur d’instance.</span><span class="sxs-lookup"><span data-stu-id="edd6d-296">The compiler discards the static members if the method was invoked with an instance receiver.</span></span> <span data-ttu-id="edd6d-297">Lorsqu’il n’existe aucun récepteur, le compilateur inclut uniquement les membres statiques dans un contexte statique, sinon, à la fois les membres statiques et les membres de l’instance.</span><span class="sxs-lookup"><span data-stu-id="edd6d-297">When there is no receiver, the compiler includes only static members in a static context, otherwise both static and instance members.</span></span> <span data-ttu-id="edd6d-298">Lorsque le récepteur représente de façon ambiguë une instance ou un type, le compilateur inclut les deux éléments.</span><span class="sxs-lookup"><span data-stu-id="edd6d-298">When the receiver is ambiguously an instance or type, the compiler includes both.</span></span> <span data-ttu-id="edd6d-299">Un contexte statique, où un récepteur d’instance `this` implicite ne peut pas être utilisé, inclut le corps des membres où aucun `this` n’est défini, par exemple des membres statiques, ainsi que chaque endroit où `this` ne peut pas être utilisé, par exemple les initialiseurs de champ et les initialiseurs de constructeur.</span><span class="sxs-lookup"><span data-stu-id="edd6d-299">A static context, where an implicit `this` instance receiver cannot be used, includes the body of members where no `this` is defined, such as static members, as well as places where `this` cannot be used, such as field initializers and constructor-initializers.</span></span>
1. <span data-ttu-id="edd6d-300">Lorsqu’un groupe de méthodes contient certaines méthodes génériques dont les arguments de type ne répondent pas à leurs contraintes, ces membres sont supprimés de l’ensemble de candidats.</span><span class="sxs-lookup"><span data-stu-id="edd6d-300">When a method group contains some generic methods whose type arguments do not satisfy their constraints, these members are removed from the candidate set.</span></span>
1. <span data-ttu-id="edd6d-301">Pour une conversion de groupe de méthodes, les méthodes candidates dont le type de retour ne correspond pas à celui du délégué sont supprimées de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="edd6d-301">For a method group conversion, candidate methods whose return type doesn't match up with the delegate's return type are removed from the set.</span></span>

<span data-ttu-id="edd6d-302">Vous ne remarquerez que cette modification car vous trouverez moins d’erreurs de compilateur pour les surcharges de méthode ambiguës si vous savez quelle méthode est la meilleure.</span><span class="sxs-lookup"><span data-stu-id="edd6d-302">You'll only notice this change because you'll find fewer compiler errors for ambiguous method overloads when you are sure which method is better.</span></span>

## <a name="enabling-more-efficient-safe-code"></a><span data-ttu-id="edd6d-303">Code sécurisé plus performant</span><span class="sxs-lookup"><span data-stu-id="edd6d-303">Enabling more efficient safe code</span></span>

<span data-ttu-id="edd6d-304">Vous devez être en mesure d’écrire en toute sécurité un code C# ainsi performant qu’un code non sécurisé.</span><span class="sxs-lookup"><span data-stu-id="edd6d-304">You should be able to write C# code safely that performs as well as unsafe code.</span></span> <span data-ttu-id="edd6d-305">Le code sécurisé évite les classes d’erreurs, par exemple les dépassements de mémoire tampon, les pointeurs perdus et d’autres erreurs d’accès à la mémoire.</span><span class="sxs-lookup"><span data-stu-id="edd6d-305">Safe code avoids classes of errors, such as buffer overruns, stray pointers, and other memory access errors.</span></span> <span data-ttu-id="edd6d-306">Ces nouvelles fonctionnalités étendent les fonctionnalités de code sécurisé vérifiables.</span><span class="sxs-lookup"><span data-stu-id="edd6d-306">These new features expand the capabilities of verifiable safe code.</span></span> <span data-ttu-id="edd6d-307">Efforcez-vous d’utiliser plus de constructions sécurisées pour écrire votre code.</span><span class="sxs-lookup"><span data-stu-id="edd6d-307">Strive to write more of your code using safe constructs.</span></span> <span data-ttu-id="edd6d-308">Ces fonctionnalités facilitent cette écriture.</span><span class="sxs-lookup"><span data-stu-id="edd6d-308">These features make that easier.</span></span>

<span data-ttu-id="edd6d-309">Les nouvelles fonctionnalités suivantes prennent en charge le thème de meilleures performances pour le code sécurisé :</span><span class="sxs-lookup"><span data-stu-id="edd6d-309">The following new features support the theme of better performance for safe code:</span></span>

- <span data-ttu-id="edd6d-310">Vous pouvez accéder à des champs fixes sans épinglage.</span><span class="sxs-lookup"><span data-stu-id="edd6d-310">You can access fixed fields without pinning.</span></span>
- <span data-ttu-id="edd6d-311">Vous pouvez réaffecter des variables locales `ref`.</span><span class="sxs-lookup"><span data-stu-id="edd6d-311">You can reassign `ref` local variables.</span></span>
- <span data-ttu-id="edd6d-312">Vous pouvez utiliser des initialiseurs sur les tableaux `stackalloc`.</span><span class="sxs-lookup"><span data-stu-id="edd6d-312">You can use initializers on `stackalloc` arrays.</span></span>
- <span data-ttu-id="edd6d-313">Vous pouvez utiliser des instructions `fixed` avec tout type prenant en charge un modèle.</span><span class="sxs-lookup"><span data-stu-id="edd6d-313">You can use `fixed` statements with any type that supports a pattern.</span></span>
- <span data-ttu-id="edd6d-314">Vous pouvez utiliser des contraintes génériques supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="edd6d-314">You can use additional generic constraints.</span></span>
- <span data-ttu-id="edd6d-315">Le modificateur `in` sur les paramètres pour spécifier qu’un argument est passé par référence, mais pas modifié par la méthode appelée.</span><span class="sxs-lookup"><span data-stu-id="edd6d-315">The `in` modifier on parameters, to specify that an argument is passed by reference but not modified by the called method.</span></span> <span data-ttu-id="edd6d-316">L’ajout du modificateur `in` à un argument est une [modification compatible avec la source](version-update-considerations.md#source-compatible-changes).</span><span class="sxs-lookup"><span data-stu-id="edd6d-316">Adding the `in` modifier to an argument is a [source compatible change](version-update-considerations.md#source-compatible-changes).</span></span>
- <span data-ttu-id="edd6d-317">Le modificateur `ref readonly` sur les retours de méthode pour indiquer qu’une méthode retourne sa valeur par référence, mais n’autorise pas les écritures sur cet objet.</span><span class="sxs-lookup"><span data-stu-id="edd6d-317">The `ref readonly` modifier on method returns, to indicate that a method returns its value by reference but doesn't allow writes to that object.</span></span> <span data-ttu-id="edd6d-318">L’ajout du modificateur `ref readonly` est une [modification compatible avec la source](version-update-considerations.md#source-compatible-changes), si une valeur est assignée au retour.</span><span class="sxs-lookup"><span data-stu-id="edd6d-318">Adding the `ref readonly` modifier is a [source compatible change](version-update-considerations.md#source-compatible-changes), if the return is assigned to a value.</span></span> <span data-ttu-id="edd6d-319">Le fait d’ajouter le modificateur `readonly` à une instruction de retour `ref` existante représente une [modification incompatible](version-update-considerations.md#incompatible-changes).</span><span class="sxs-lookup"><span data-stu-id="edd6d-319">Adding the `readonly` modifier to an existing `ref` return statement is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="edd6d-320">Cela nécessite que les appelants mettent à jour de la déclaration de variables locales `ref` pour inclure le modificateur `readonly`.</span><span class="sxs-lookup"><span data-stu-id="edd6d-320">It requires callers to update the declaration of `ref` local variables to include the `readonly` modifier.</span></span>
- <span data-ttu-id="edd6d-321">La déclaration `readonly struct` pour indiquer qu’un struct est immuable et doit être passé comme un paramètre `in` aux méthodes de ses membres.</span><span class="sxs-lookup"><span data-stu-id="edd6d-321">The `readonly struct` declaration, to indicate that a struct is immutable and should be passed as an `in` parameter to its member methods.</span></span> <span data-ttu-id="edd6d-322">L’ajout du modificateur `readonly` à une déclaration struct existante est une [modification compatible binaire](version-update-considerations.md#binary-compatible-changes).</span><span class="sxs-lookup"><span data-stu-id="edd6d-322">Adding the `readonly` modifier to an existing struct declaration is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>
- <span data-ttu-id="edd6d-323">La déclaration `ref struct` pour indiquer qu’un type struct accède directement à la mémoire managée et doit toujours être alloué par la pile.</span><span class="sxs-lookup"><span data-stu-id="edd6d-323">The `ref struct` declaration, to indicate that a struct type accesses managed memory directly and must always be stack allocated.</span></span> <span data-ttu-id="edd6d-324">L’ajout du modificateur `ref` à une déclaration `struct` existante est une [modification incompatible](version-update-considerations.md#incompatible-changes).</span><span class="sxs-lookup"><span data-stu-id="edd6d-324">Adding the `ref` modifier to an existing `struct` declaration is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="edd6d-325">Un `ref struct` ne peut pas être membre d’une classe ou utilisé dans d’autres emplacements où il pourrait être alloué sur le tas.</span><span class="sxs-lookup"><span data-stu-id="edd6d-325">A `ref struct` cannot be a member of a class or used in other locations where it may be allocated on the heap.</span></span>

<span data-ttu-id="edd6d-326">Pour plus d’informations sur toutes ces modifications, voir [Écrire du code safe et efficace](../write-safe-efficient-code.md).</span><span class="sxs-lookup"><span data-stu-id="edd6d-326">You can read more about all these changes in [Write safe efficient code](../write-safe-efficient-code.md).</span></span>

### <a name="ref-locals-and-returns"></a><span data-ttu-id="edd6d-327">Variables locales et retours ref</span><span class="sxs-lookup"><span data-stu-id="edd6d-327">Ref locals and returns</span></span>

<span data-ttu-id="edd6d-328">Cette fonctionnalité active les algorithmes qui utilisent et retournent des références à des variables définies ailleurs.</span><span class="sxs-lookup"><span data-stu-id="edd6d-328">This feature enables algorithms that use and return references to variables defined elsewhere.</span></span> <span data-ttu-id="edd6d-329">C’est le cas, par exemple, lors de la recherche d’un emplacement unique comportant certaines caractéristiques dans une matrice de grande taille.</span><span class="sxs-lookup"><span data-stu-id="edd6d-329">One example is working with large matrices, and finding a single location with certain characteristics.</span></span> <span data-ttu-id="edd6d-330">La méthode suivante retourne une **référence** à ce stockage dans la matrice :</span><span class="sxs-lookup"><span data-stu-id="edd6d-330">The following method returns a **reference** to that storage in the matrix:</span></span>

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

<span data-ttu-id="edd6d-331">Vous pouvez déclarer la valeur de retour en tant que `ref` et modifier cette valeur dans la matrice, comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="edd6d-331">You can declare the return value as a `ref` and modify that value in the matrix, as shown in the following code:</span></span>

[!code-csharp[AssignRefReturn](~/samples/snippets/csharp/new-in-7/Program.cs#AssignRefReturn "Assign ref return")]

<span data-ttu-id="edd6d-332">Le langage C# a plusieurs règles qui vous protègent contre une mauvaise utilisation des variables locales et des retours `ref` :</span><span class="sxs-lookup"><span data-stu-id="edd6d-332">The C# language has several rules that protect you from misusing the `ref` locals and returns:</span></span>

- <span data-ttu-id="edd6d-333">Vous devez ajouter le mot clé `ref` à la signature de méthode et à toutes les instructions `return` dans une méthode.</span><span class="sxs-lookup"><span data-stu-id="edd6d-333">You must add the `ref` keyword to the method signature and to all `return` statements in a method.</span></span>
  - <span data-ttu-id="edd6d-334">Cela permet de clarifier le retour par référence tout au long de la méthode.</span><span class="sxs-lookup"><span data-stu-id="edd6d-334">That makes it clear the method returns by reference throughout the method.</span></span>
- <span data-ttu-id="edd6d-335">Un `ref return` peut être assigné à une variable de la valeur ou à une variable `ref`.</span><span class="sxs-lookup"><span data-stu-id="edd6d-335">A `ref return` may be assigned to a value variable, or a `ref` variable.</span></span>
  - <span data-ttu-id="edd6d-336">L’appelant contrôle si la valeur de retour est copiée ou non.</span><span class="sxs-lookup"><span data-stu-id="edd6d-336">The caller controls whether the return value is copied or not.</span></span> <span data-ttu-id="edd6d-337">L’omission du modificateur `ref` lors de l’assignation de la valeur de retour indique que l’appelant souhaite une copie de la valeur, pas une référence au stockage.</span><span class="sxs-lookup"><span data-stu-id="edd6d-337">Omitting the `ref` modifier when assigning the return value indicates that the caller wants a copy of the value, not a reference to the storage.</span></span>
- <span data-ttu-id="edd6d-338">Vous ne pouvez pas affecter une valeur de retour de méthode standard à une variable locale `ref`.</span><span class="sxs-lookup"><span data-stu-id="edd6d-338">You can't assign a standard method return value to a `ref` local variable.</span></span>
  - <span data-ttu-id="edd6d-339">Cela rejette les instructions telles que `ref int i = sequence.Count();`.</span><span class="sxs-lookup"><span data-stu-id="edd6d-339">That disallows statements like `ref int i = sequence.Count();`</span></span>
- <span data-ttu-id="edd6d-340">Vous ne pouvez pas retourner un `ref` à une variable dont la durée de vie ne s’étend pas au-delà de l’exécution de la méthode.</span><span class="sxs-lookup"><span data-stu-id="edd6d-340">You can't return a `ref` to a variable whose lifetime doesn't extend beyond the execution of the method.</span></span>
  - <span data-ttu-id="edd6d-341">Cela signifie que vous ne pouvez pas retourner une référence à une variable locale ni une variable avec une étendue similaire.</span><span class="sxs-lookup"><span data-stu-id="edd6d-341">That means you can't return a reference to a local variable or a variable with a similar scope.</span></span>
- <span data-ttu-id="edd6d-342">Les variables locales et les retours `ref` ne peuvent pas être utilisés avec les méthodes Async.</span><span class="sxs-lookup"><span data-stu-id="edd6d-342">`ref` locals and returns can't be used with async methods.</span></span>
  - <span data-ttu-id="edd6d-343">Le compilateur ne peut pas savoir si la variable référencée a été définie à sa valeur finale quand la méthode Async est retournée.</span><span class="sxs-lookup"><span data-stu-id="edd6d-343">The compiler can't know if the referenced variable has been set to its final value when the async method returns.</span></span>

<span data-ttu-id="edd6d-344">L’ajout de variables locales ref et de retours ref permet d’utiliser des algorithmes qui sont plus efficaces en évitant la copie de valeurs, ou d’effectuer plusieurs fois des opérations de déréférencement.</span><span class="sxs-lookup"><span data-stu-id="edd6d-344">The addition of ref locals and ref returns enables algorithms that are more efficient by avoiding copying values, or performing dereferencing operations multiple times.</span></span>

<span data-ttu-id="edd6d-345">L’ajout de `ref` à la valeur de retour est une [modification compatible avec la source](version-update-considerations.md#source-compatible-changes).</span><span class="sxs-lookup"><span data-stu-id="edd6d-345">Adding `ref` to the return value is a [source compatible change](version-update-considerations.md#source-compatible-changes).</span></span> <span data-ttu-id="edd6d-346">Le code existant est compilé, mais la valeur de retour référencée est copiée lorsqu’elle est assignée.</span><span class="sxs-lookup"><span data-stu-id="edd6d-346">Existing code compiles, but the ref return value is copied when assigned.</span></span> <span data-ttu-id="edd6d-347">Les appelants doivent mettre à jour le stockage pour la valeur de retour sur une variable locale `ref` afin de stocker la valeur de retour en tant que référence.</span><span class="sxs-lookup"><span data-stu-id="edd6d-347">Callers must update the storage for the return value to a `ref` local variable to store the return as a reference.</span></span>

<span data-ttu-id="edd6d-348">Désormais, les variables locales `ref` peuvent être réassignées pour faire référence à d’autres instances, après avoir été initialisées.</span><span class="sxs-lookup"><span data-stu-id="edd6d-348">Now, `ref` locals may be reassigned to refer to different instances after being initialized.</span></span> <span data-ttu-id="edd6d-349">Le code suivant effectue maintenant une compilation :</span><span class="sxs-lookup"><span data-stu-id="edd6d-349">The following code now compiles:</span></span>

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

<span data-ttu-id="edd6d-350">Pour plus d’informations, consultez l’article sur les [ `ref` retours et les `ref` variables locales](../programming-guide/classes-and-structs/ref-returns.md), ainsi que l’article sur [`foreach`](../language-reference/keywords/foreach-in.md) .</span><span class="sxs-lookup"><span data-stu-id="edd6d-350">For more information, see the article on [`ref` returns and `ref` locals](../programming-guide/classes-and-structs/ref-returns.md), and the article on [`foreach`](../language-reference/keywords/foreach-in.md).</span></span>

<span data-ttu-id="edd6d-351">Pour plus d'informations, voir l’article [ref, mot clé](../language-reference/keywords/ref.md).</span><span class="sxs-lookup"><span data-stu-id="edd6d-351">For more information, see the [ref keyword](../language-reference/keywords/ref.md) article.</span></span>

### <a name="conditional-ref-expressions"></a><span data-ttu-id="edd6d-352">Expressions `ref` conditionnelles</span><span class="sxs-lookup"><span data-stu-id="edd6d-352">Conditional `ref` expressions</span></span>

<span data-ttu-id="edd6d-353">Enfin, l’expression conditionnelle peut produire comme résultat une référence plutôt qu’une valeur.</span><span class="sxs-lookup"><span data-stu-id="edd6d-353">Finally, the conditional expression may produce a ref result instead of a value result.</span></span> <span data-ttu-id="edd6d-354">Prenons par exemple la ligne suivante, qui récupère une référence au premier élément dans un des deux tableaux :</span><span class="sxs-lookup"><span data-stu-id="edd6d-354">For example, you would write the following to retrieve a reference to the first element in one of two arrays:</span></span>

```csharp
ref var r = ref (arr != null ? ref arr[0] : ref otherArr[0]);
```

<span data-ttu-id="edd6d-355">La variable `r` est une référence à la première valeur de `arr` ou `otherArr`.</span><span class="sxs-lookup"><span data-stu-id="edd6d-355">The variable `r` is a reference to the first value in either `arr` or `otherArr`.</span></span>

<span data-ttu-id="edd6d-356">Pour plus d’informations, voir [Opérateur conditionnel (?:)](../language-reference/operators/conditional-operator.md) dans la référence sur le langage.</span><span class="sxs-lookup"><span data-stu-id="edd6d-356">For more information, see [conditional operator (?:)](../language-reference/operators/conditional-operator.md) in the language reference.</span></span>

### <a name="in-parameter-modifier"></a><span data-ttu-id="edd6d-357">`in` modificateur de paramètre</span><span class="sxs-lookup"><span data-stu-id="edd6d-357">`in` parameter modifier</span></span>

<span data-ttu-id="edd6d-358">Le `in` mot clé complète les mots clés REF et out existants pour passer des arguments par référence.</span><span class="sxs-lookup"><span data-stu-id="edd6d-358">The `in` keyword complements the existing ref and out keywords to pass arguments by reference.</span></span> <span data-ttu-id="edd6d-359">Le mot clé `in` spécifie que l’argument doit être passé par référence, mais la méthode appelée ne modifie pas la valeur.</span><span class="sxs-lookup"><span data-stu-id="edd6d-359">The `in` keyword specifies passing the argument by reference, but the called method doesn't modify the value.</span></span>

<span data-ttu-id="edd6d-360">Vous pouvez déclarer des surcharges qui passent par valeur ou par référence ReadOnly, comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="edd6d-360">You may declare overloads that pass by value or by readonly reference, as shown in the following code:</span></span>

```csharp
static void M(S arg);
static void M(in S arg);
```

<span data-ttu-id="edd6d-361">La valeur par valeur (tout d’abord dans l’exemple précédent) est meilleure que la version de référence par ReadOnly.</span><span class="sxs-lookup"><span data-stu-id="edd6d-361">The by value (first in the preceding example) overload is better than the by readonly reference version.</span></span> <span data-ttu-id="edd6d-362">Pour appeler la version avec l’argument de référence en lecture seule, vous devez inclure le modificateur `in` lors de l’appel de la méthode.</span><span class="sxs-lookup"><span data-stu-id="edd6d-362">To call the version with the readonly reference argument, you must include the `in` modifier when calling the method.</span></span>

<span data-ttu-id="edd6d-363">Pour plus d’informations, consultez l’article sur le [ `in` modificateur de paramètre](../language-reference/keywords/in-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="edd6d-363">For more information, see the article on the [`in` parameter modifier](../language-reference/keywords/in-parameter-modifier.md).</span></span>

### <a name="more-types-support-the-fixed-statement"></a><span data-ttu-id="edd6d-364">D’autres types prennent en charge l’instruction `fixed`</span><span class="sxs-lookup"><span data-stu-id="edd6d-364">More types support the `fixed` statement</span></span>

<span data-ttu-id="edd6d-365">L’instruction `fixed` prenait en charge un ensemble limité de types.</span><span class="sxs-lookup"><span data-stu-id="edd6d-365">The `fixed` statement supported a limited set of types.</span></span> <span data-ttu-id="edd6d-366">À partir de C# 7.3, tout type contenant une méthode `GetPinnableReference()` qui retourne `ref T` ou `ref readonly T` peut être `fixed`.</span><span class="sxs-lookup"><span data-stu-id="edd6d-366">Starting with C# 7.3, any type that contains a `GetPinnableReference()` method that returns a `ref T` or `ref readonly T` may be `fixed`.</span></span> <span data-ttu-id="edd6d-367">L’ajout de cette fonctionnalité signifie que `fixed` peut être utilisé avec <xref:System.Span%601?displayProperty=nameWithType> et des types connexes.</span><span class="sxs-lookup"><span data-stu-id="edd6d-367">Adding this feature means that `fixed` can be used with <xref:System.Span%601?displayProperty=nameWithType> and related types.</span></span>

<span data-ttu-id="edd6d-368">Pour plus d’informations, consultez l’article sur les [ `fixed` instructions](../language-reference/keywords/fixed-statement.md) dans la référence du langage.</span><span class="sxs-lookup"><span data-stu-id="edd6d-368">For more information, see the [`fixed` statement](../language-reference/keywords/fixed-statement.md) article in the language reference.</span></span>

### <a name="indexing-fixed-fields-does-not-require-pinning"></a><span data-ttu-id="edd6d-369">L’indexation des champs `fixed` ne nécessite aucun épinglage</span><span class="sxs-lookup"><span data-stu-id="edd6d-369">Indexing `fixed` fields does not require pinning</span></span>

<span data-ttu-id="edd6d-370">Prenons le struct suivant :</span><span class="sxs-lookup"><span data-stu-id="edd6d-370">Consider this struct:</span></span>

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

<span data-ttu-id="edd6d-371">Dans les versions antérieures de C#, vous deviez épingler une variable pour accéder à un des entiers faisant partie de `myFixedField`.</span><span class="sxs-lookup"><span data-stu-id="edd6d-371">In earlier versions of C#, you needed to pin a variable to access one of the integers that are part of `myFixedField`.</span></span> <span data-ttu-id="edd6d-372">À présent, le code suivant se compile sans épingler la variable `p` à l’intérieur d’une instruction `fixed` distincte :</span><span class="sxs-lookup"><span data-stu-id="edd6d-372">Now, the following code compiles without pinning the variable `p` inside a separate `fixed` statement:</span></span>

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        int p = s.myFixedField[5];
    }
}
```

<span data-ttu-id="edd6d-373">La variable `p` accède à un élément dans `myFixedField`.</span><span class="sxs-lookup"><span data-stu-id="edd6d-373">The variable `p` accesses one element in `myFixedField`.</span></span> <span data-ttu-id="edd6d-374">Vous n’avez pas besoin de déclarer une variable `int*` distincte.</span><span class="sxs-lookup"><span data-stu-id="edd6d-374">You don't need to declare a separate `int*` variable.</span></span> <span data-ttu-id="edd6d-375">Vous avez toujours besoin d’un `unsafe` contexte.</span><span class="sxs-lookup"><span data-stu-id="edd6d-375">You still need an `unsafe` context.</span></span> <span data-ttu-id="edd6d-376">Dans les versions antérieures de C#, vous devez déclarer un second pointeur fixe :</span><span class="sxs-lookup"><span data-stu-id="edd6d-376">In earlier versions of C#, you need to declare a second fixed pointer:</span></span>

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        fixed (int* ptr = s.myFixedField)
        {
            int p = ptr[5];
        }
    }
}
```

<span data-ttu-id="edd6d-377">Pour plus d’informations, consultez l’article sur l' [ `fixed` instruction](../language-reference/keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="edd6d-377">For more information, see the article on the [`fixed` statement](../language-reference/keywords/fixed-statement.md).</span></span>

### <a name="stackalloc-arrays-support-initializers"></a><span data-ttu-id="edd6d-378">Les tableaux `stackalloc` prennent en charge les initialiseurs</span><span class="sxs-lookup"><span data-stu-id="edd6d-378">`stackalloc` arrays support initializers</span></span>

<span data-ttu-id="edd6d-379">Vous avez été en mesure de spécifier les valeurs des éléments dans un tableau lors de son initialisation :</span><span class="sxs-lookup"><span data-stu-id="edd6d-379">You've been able to specify the values for elements in an array when you initialize it:</span></span>

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

<span data-ttu-id="edd6d-380">Maintenant, la même syntaxe peut être appliquée aux tableaux déclarés avec `stackalloc` :</span><span class="sxs-lookup"><span data-stu-id="edd6d-380">Now, that same syntax can be applied to arrays that are declared with `stackalloc`:</span></span>

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

<span data-ttu-id="edd6d-381">Pour plus d’informations, consultez l’article relatif à l' [ `stackalloc` opérateur](../language-reference/operators/stackalloc.md) .</span><span class="sxs-lookup"><span data-stu-id="edd6d-381">For more information, see the [`stackalloc` operator](../language-reference/operators/stackalloc.md) article.</span></span>

### <a name="enhanced-generic-constraints"></a><span data-ttu-id="edd6d-382">Contraintes génériques améliorées</span><span class="sxs-lookup"><span data-stu-id="edd6d-382">Enhanced generic constraints</span></span>

<span data-ttu-id="edd6d-383">Vous pouvez maintenant spécifier le type <xref:System.Enum?displayProperty=nameWithType> ou <xref:System.Delegate?displayProperty=nameWithType> en tant que contraintes de classe de base pour un paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="edd6d-383">You can now specify the type <xref:System.Enum?displayProperty=nameWithType> or <xref:System.Delegate?displayProperty=nameWithType> as base class constraints for a type parameter.</span></span>

<span data-ttu-id="edd6d-384">Vous pouvez également utiliser la nouvelle `unmanaged` contrainte pour spécifier qu’un paramètre de type doit être un [type non managé](../language-reference/builtin-types/unmanaged-types.md)qui n’accepte pas les valeurs NULL.</span><span class="sxs-lookup"><span data-stu-id="edd6d-384">You can also use the new `unmanaged` constraint, to specify that a type parameter must be a non-nullable [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span></span>

<span data-ttu-id="edd6d-385">Pour plus d’informations, consultez les articles sur les contraintes et contraintes [ `where` génériques](../language-reference/keywords/where-generic-type-constraint.md) [sur les paramètres de type](../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="edd6d-385">For more information, see the articles on [`where` generic constraints](../language-reference/keywords/where-generic-type-constraint.md) and [constraints on type parameters](../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="edd6d-386">L’ajout de ces contraintes aux types existants est une [modification incompatible](version-update-considerations.md#incompatible-changes).</span><span class="sxs-lookup"><span data-stu-id="edd6d-386">Adding these constraints to existing types is an [incompatible change](version-update-considerations.md#incompatible-changes).</span></span> <span data-ttu-id="edd6d-387">Les types génériques fermés peuvent ne plus respecter ces nouvelles contraintes.</span><span class="sxs-lookup"><span data-stu-id="edd6d-387">Closed generic types may no longer meet these new constraints.</span></span>

### <a name="generalized-async-return-types"></a><span data-ttu-id="edd6d-388">Types de retour async généralisés</span><span class="sxs-lookup"><span data-stu-id="edd6d-388">Generalized async return types</span></span>

<span data-ttu-id="edd6d-389">Le retour d’un objet `Task` à partir de méthodes async peut introduire des goulots d’étranglement au niveau des performances dans certains chemins.</span><span class="sxs-lookup"><span data-stu-id="edd6d-389">Returning a `Task` object from async methods can introduce performance bottlenecks in certain paths.</span></span> <span data-ttu-id="edd6d-390">`Task` est un type référence. Si vous l’utilisez, vous allouez donc un objet.</span><span class="sxs-lookup"><span data-stu-id="edd6d-390">`Task` is a reference type, so using it means allocating an object.</span></span> <span data-ttu-id="edd6d-391">Dans les cas où une méthode déclarée avec le modificateur `async` retourne un résultat mis en cache, ou si elle s’exécute de manière synchrone, le coût en termes de temps induit par les allocations supplémentaires peut s’avérer significatif dans les sections de code critiques pour les performances.</span><span class="sxs-lookup"><span data-stu-id="edd6d-391">In cases where a method declared with the `async` modifier returns a cached result, or completes synchronously, the extra allocations can become a significant time cost in performance critical sections of code.</span></span> <span data-ttu-id="edd6d-392">Cela peut devenir coûteux si ces allocations se produisent dans des boucles serrées.</span><span class="sxs-lookup"><span data-stu-id="edd6d-392">It can become costly if those allocations occur in tight loops.</span></span>

<span data-ttu-id="edd6d-393">La nouvelle fonctionnalité du langage signifie que les types de retour des méthodes async ne se limitent pas à `Task`, `Task<T>` et `void`.</span><span class="sxs-lookup"><span data-stu-id="edd6d-393">The new language feature means that async method return types aren't limited to `Task`, `Task<T>`, and `void`.</span></span> <span data-ttu-id="edd6d-394">Le type retourné doit toujours correspondre au modèle async, ce qui signifie qu’une méthode `GetAwaiter` doit être accessible.</span><span class="sxs-lookup"><span data-stu-id="edd6d-394">The returned type must still satisfy the async pattern, meaning a `GetAwaiter` method must be accessible.</span></span> <span data-ttu-id="edd6d-395">En guise d’exemple concret, le `ValueTask` type a été ajouté à .net pour utiliser cette nouvelle fonctionnalité de langage :</span><span class="sxs-lookup"><span data-stu-id="edd6d-395">As one concrete example, the `ValueTask` type has been added to .NET to make use of this new language feature:</span></span>

[!code-csharp[UsingValueTask](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#UsingValueTask "Using ValueTask")]

> [!NOTE]
> <span data-ttu-id="edd6d-396">Vous devez ajouter le package NuGet [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) > pour pouvoir utiliser le <xref:System.Threading.Tasks.ValueTask%601> type.</span><span class="sxs-lookup"><span data-stu-id="edd6d-396">You need to add the NuGet package [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) > in order to use the <xref:System.Threading.Tasks.ValueTask%601> type.</span></span>

<span data-ttu-id="edd6d-397">Cette amélioration s’avère particulièrement utile pour les auteurs de bibliothèques afin d’éviter d’allouer un `Task` dans le code critique pour les performances.</span><span class="sxs-lookup"><span data-stu-id="edd6d-397">This enhancement is most useful for library authors to avoid allocating a `Task` in performance critical code.</span></span>

## <a name="new-compiler-options"></a><span data-ttu-id="edd6d-398">Nouvelles options du compilateur</span><span class="sxs-lookup"><span data-stu-id="edd6d-398">New compiler options</span></span>

<span data-ttu-id="edd6d-399">De nouvelles options du compilateur prennent en charge la nouvelle build et les scénarios DevOps pour les programmes C#.</span><span class="sxs-lookup"><span data-stu-id="edd6d-399">New compiler options support new build and DevOps scenarios for C# programs.</span></span>

### <a name="reference-assembly-generation"></a><span data-ttu-id="edd6d-400">Génération d’assemblys de références</span><span class="sxs-lookup"><span data-stu-id="edd6d-400">Reference assembly generation</span></span>

<span data-ttu-id="edd6d-401">Il existe deux nouvelles options de compilateur qui génèrent des *assemblys de référence uniquement*: [-REFOUT](../language-reference/compiler-options/refout-compiler-option.md) et [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="edd6d-401">There are two new compiler options that generate *reference-only assemblies*: [-refout](../language-reference/compiler-options/refout-compiler-option.md) and [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="edd6d-402">Les articles en lien décrivent plus en détail ces options et les assemblys de références.</span><span class="sxs-lookup"><span data-stu-id="edd6d-402">The linked articles explain these options and reference assemblies in more detail.</span></span>

### <a name="public-or-open-source-signing"></a><span data-ttu-id="edd6d-403">Signature publique ou Open Source</span><span class="sxs-lookup"><span data-stu-id="edd6d-403">Public or Open Source signing</span></span>

<span data-ttu-id="edd6d-404">L’option du compilateur `-publicsign` indique au compilateur de signer l’assembly à l’aide d’une clé publique.</span><span class="sxs-lookup"><span data-stu-id="edd6d-404">The `-publicsign` compiler option instructs the compiler to sign the assembly using a public key.</span></span> <span data-ttu-id="edd6d-405">L’assembly est marqué comme étant signé, mais la signature provient de la clé publique.</span><span class="sxs-lookup"><span data-stu-id="edd6d-405">The assembly is marked as signed, but the signature is taken from the public key.</span></span> <span data-ttu-id="edd6d-406">Cette option vous permet de générer des assemblys signés à partir de projets open source à l’aide d’une clé publique.</span><span class="sxs-lookup"><span data-stu-id="edd6d-406">This option enables you to build signed assemblies from open-source projects using a public key.</span></span>

<span data-ttu-id="edd6d-407">Pour plus d’informations, consultez l’article [Option du compilateur -publicsign](../language-reference/compiler-options/publicsign-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="edd6d-407">For more information, see the [-publicsign compiler option](../language-reference/compiler-options/publicsign-compiler-option.md) article.</span></span>

### <a name="pathmap"></a><span data-ttu-id="edd6d-408">pathmap</span><span class="sxs-lookup"><span data-stu-id="edd6d-408">pathmap</span></span>

<span data-ttu-id="edd6d-409">L’option du compilateur `-pathmap` indique au compilateur de remplacer les chemins sources de l’environnement de build par des chemins sources mappés.</span><span class="sxs-lookup"><span data-stu-id="edd6d-409">The `-pathmap` compiler option instructs the compiler to replace source paths from the build environment with mapped source paths.</span></span> <span data-ttu-id="edd6d-410">L’option `-pathmap` contrôle le chemin source écrit par le compilateur vers les fichiers PDB ou pour <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span><span class="sxs-lookup"><span data-stu-id="edd6d-410">The `-pathmap` option controls the source path written by the compiler to PDB files or for the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute>.</span></span>

<span data-ttu-id="edd6d-411">Pour plus d’informations, consultez l’article [Option du compilateur -pathmap](../language-reference/compiler-options/pathmap-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="edd6d-411">For more information, see the [-pathmap compiler option](../language-reference/compiler-options/pathmap-compiler-option.md) article.</span></span>

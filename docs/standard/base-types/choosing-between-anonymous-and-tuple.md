---
title: Choix entre les types de tuples et anonymes
description: Découvrez quand il est approprié de choisir entre les types anonymes et le type de Tuple.
author: IEvangelist
ms.author: dapine
ms.date: 07/01/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 9c186133a639faf187c89d872856d860a20f5a2d
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174216"
---
# <a name="choosing-between-anonymous-and-tuple-types"></a><span data-ttu-id="ee1b1-103">Choix entre les types de tuples et anonymes</span><span class="sxs-lookup"><span data-stu-id="ee1b1-103">Choosing between anonymous and tuple types</span></span>

<span data-ttu-id="ee1b1-104">Le choix du type approprié implique la prise en compte de l’utilisation, des performances et des compromis par rapport aux autres types.</span><span class="sxs-lookup"><span data-stu-id="ee1b1-104">Choosing the appropriate type involves considering its usability, performance, and tradeoffs compared to other types.</span></span> <span data-ttu-id="ee1b1-105">Les types anonymes sont disponibles depuis C# 3,0, tandis que <xref:System.Tuple%602?displayProperty=nameWithType> les types génériques ont été introduits avec .NET Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="ee1b1-105">Anonymous types have been available since C# 3.0, while generic <xref:System.Tuple%602?displayProperty=nameWithType> types were introduced with .NET Framework 4.0.</span></span> <span data-ttu-id="ee1b1-106">Dans la mesure où de nouvelles options ont été introduites avec la prise en charge du niveau de langage, comme, <xref:System.ValueTuple%602?displayProperty=nameWithType> qui, comme son nom l’indique, fournit un type de valeur avec la flexibilité des types anonymes.</span><span class="sxs-lookup"><span data-stu-id="ee1b1-106">Since then new options have been introduced with language level support, such as <xref:System.ValueTuple%602?displayProperty=nameWithType> - which as the name implies, provide a value type with the flexibility of anonymous types.</span></span> <span data-ttu-id="ee1b1-107">Dans cet article, vous découvrirez quand il est approprié de choisir un type par rapport à l’autre.</span><span class="sxs-lookup"><span data-stu-id="ee1b1-107">In this article, you'll learn when it's appropriate to choose one type over the other.</span></span>

## <a name="usability-and-functionality"></a><span data-ttu-id="ee1b1-108">Convivialité et fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="ee1b1-108">Usability and functionality</span></span>

<span data-ttu-id="ee1b1-109">Les types anonymes ont été introduits dans C# 3,0 avec des expressions LINQ (Language-Integrated Query).</span><span class="sxs-lookup"><span data-stu-id="ee1b1-109">Anonymous types were introduced in C# 3.0 with Language-Integrated Query (LINQ) expressions.</span></span> <span data-ttu-id="ee1b1-110">Avec LINQ, les développeurs projetent souvent les résultats de requêtes dans des types anonymes qui contiennent quelques propriétés Select des objets avec lesquels ils travaillent.</span><span class="sxs-lookup"><span data-stu-id="ee1b1-110">With LINQ, developers often project results from queries into anonymous types that hold a few select properties from the objects they're working with.</span></span> <span data-ttu-id="ee1b1-111">Prenons l’exemple suivant, qui instancie un tableau d' <xref:System.DateTime> objets, et itère au sein de ce projet dans un type anonyme avec deux propriétés.</span><span class="sxs-lookup"><span data-stu-id="ee1b1-111">Consider the following example, that instantiates an array of <xref:System.DateTime> objects, and iterates through them projecting into an anonymous type with two properties.</span></span>

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var anonymous in
             dates.Select(
                 date => new { Formatted = $"{date:MMM dd, yyyy hh:mm zzz}", date.Ticks }))
{
    Console.WriteLine($"Ticks: {anonymous.Ticks}, formatted: {anonymous.Formatted}");
}
```

<span data-ttu-id="ee1b1-112">Les types anonymes sont instanciés à l’aide de l' [`new`](../../csharp/language-reference/operators/new-operator.md) opérateur, et les noms et types de propriétés sont déduits de la déclaration.</span><span class="sxs-lookup"><span data-stu-id="ee1b1-112">Anonymous types are instantiated by using the [`new`](../../csharp/language-reference/operators/new-operator.md) operator, and the property names and types are inferred from the declaration.</span></span> <span data-ttu-id="ee1b1-113">Si au moins deux initialiseurs d’objets anonymes dans le même assembly spécifient une séquence de propriétés qui sont dans le même ordre et qui ont les mêmes noms et types, le compilateur traite les objets comme des instances du même type.</span><span class="sxs-lookup"><span data-stu-id="ee1b1-113">If two or more anonymous object initializers in the same assembly specify a sequence of properties that are in the same order and that have the same names and types, the compiler treats the objects as instances of the same type.</span></span> <span data-ttu-id="ee1b1-114">Elles partagent les mêmes informations de type générées par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="ee1b1-114">They share the same compiler-generated type information.</span></span>

<span data-ttu-id="ee1b1-115">L’extrait de code C# précédent projette un type anonyme avec deux propriétés, de la même façon que la classe C# générée par le compilateur suivante :</span><span class="sxs-lookup"><span data-stu-id="ee1b1-115">The previous C# snippet projects an anonymous type with two properties, much like the following compiler-generated C# class:</span></span>

```csharp
internal sealed class f__AnonymousType0
{
    public string Formatted { get; }
    public long Ticks { get; }

    public f__AnonymousType0(string formatted, long ticks)
    {
        Formatted = formatted;
        Ticks = ticks;
    }
}
```

<span data-ttu-id="ee1b1-116">Pour plus d’informations, consultez [types anonymes](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="ee1b1-116">For more information, see [anonymous types](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span> <span data-ttu-id="ee1b1-117">Les mêmes fonctionnalités existent avec les tuples lors de la projection dans des requêtes LINQ, vous pouvez sélectionner des propriétés dans des tuples.</span><span class="sxs-lookup"><span data-stu-id="ee1b1-117">The same functionality exists with tuples when projecting into LINQ queries, you can select properties into tuples.</span></span> <span data-ttu-id="ee1b1-118">Ces tuples passent par la requête, tout comme les types anonymes.</span><span class="sxs-lookup"><span data-stu-id="ee1b1-118">These tuples flow through the query, just as anonymous types would.</span></span> <span data-ttu-id="ee1b1-119">À présent, considérez l’exemple suivant à l’aide de `System.Tuple<string, long>` .</span><span class="sxs-lookup"><span data-stu-id="ee1b1-119">Now consider the following example using the `System.Tuple<string, long>`.</span></span>

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var tuple in
            dates.Select(
                date => new Tuple<string, long>($"{date:MMM dd, yyyy hh:mm zzz}", date.Ticks)))
{
    Console.WriteLine($"Ticks: {tuple.Item2}, formatted: {tuple.Item1}");
}
```

<span data-ttu-id="ee1b1-120">Avec <xref:System.Tuple%602?displayProperty=nameWithType> , l’instance expose des propriétés d’élément numérotées, telles que `Item1` et `Item2` .</span><span class="sxs-lookup"><span data-stu-id="ee1b1-120">With the <xref:System.Tuple%602?displayProperty=nameWithType>, the instance exposes numbered item properties, such as `Item1`, and `Item2`.</span></span> <span data-ttu-id="ee1b1-121">Ces noms de propriété peuvent compliquer la compréhension de l’objectif des valeurs de propriété, car le nom de propriété fournit uniquement l’ordinal.</span><span class="sxs-lookup"><span data-stu-id="ee1b1-121">These property names can make it more difficult to understand the intent of the property values, as the property name only provides the ordinal.</span></span> <span data-ttu-id="ee1b1-122">En outre, les `System.Tuple` types sont des `class` types référence.</span><span class="sxs-lookup"><span data-stu-id="ee1b1-122">Furthermore, the `System.Tuple` types are reference `class` types.</span></span> <span data-ttu-id="ee1b1-123"><xref:System.ValueTuple%602?displayProperty=nameWithType>Toutefois, est un type valeur `struct` .</span><span class="sxs-lookup"><span data-stu-id="ee1b1-123">The <xref:System.ValueTuple%602?displayProperty=nameWithType> however, is a value `struct` type.</span></span> <span data-ttu-id="ee1b1-124">L’extrait de code C# suivant utilise `ValueTuple<string, long>` pour projeter dans.</span><span class="sxs-lookup"><span data-stu-id="ee1b1-124">The following C# snippet, uses `ValueTuple<string, long>` to project into.</span></span> <span data-ttu-id="ee1b1-125">Dans ce cas, elle est assignée à l’aide d’une syntaxe littérale.</span><span class="sxs-lookup"><span data-stu-id="ee1b1-125">In doing so, it assigns using a literal syntax.</span></span>

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var (formatted, ticks) in
            dates.Select(
                date => (Formatted: $"{date:MMM dd, yyyy at hh:mm zzz}", date.Ticks)))
{
    Console.WriteLine($"Ticks: {ticks}, formatted: {formatted}");
}
```

<span data-ttu-id="ee1b1-126">Pour plus d’informations sur les tuples, consultez [types de tuples (référence C#)](../../csharp/language-reference/builtin-types/value-tuples.md) ou [tuples (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/tuples.md).</span><span class="sxs-lookup"><span data-stu-id="ee1b1-126">For more information about tuples, see [Tuple types (C# reference)](../../csharp/language-reference/builtin-types/value-tuples.md) or [Tuples (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/tuples.md).</span></span>

<span data-ttu-id="ee1b1-127">Les exemples précédents sont tous des équivalents fonctionnels, toutefois, leur utilisation et leurs implémentations sous-jacentes présentent de légères différences.</span><span class="sxs-lookup"><span data-stu-id="ee1b1-127">The previous examples are all functionally equivalent, however; there are slight differences in their usability and their underlying implementations.</span></span>

## <a name="tradeoffs"></a><span data-ttu-id="ee1b1-128">Compromis</span><span class="sxs-lookup"><span data-stu-id="ee1b1-128">Tradeoffs</span></span>

<span data-ttu-id="ee1b1-129">Vous souhaiterez peut-être toujours utiliser <xref:System.ValueTuple> <xref:System.Tuple> les types plus ou anonymes, mais il existe des compromis à prendre en compte.</span><span class="sxs-lookup"><span data-stu-id="ee1b1-129">You might want to always use <xref:System.ValueTuple> over <xref:System.Tuple>, and anonymous types, but there are tradeoffs you should consider.</span></span> <span data-ttu-id="ee1b1-130">Les <xref:System.ValueTuple> types sont mutables, alors que <xref:System.Tuple> ceux-ci sont en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="ee1b1-130">The <xref:System.ValueTuple> types are mutable, whereas <xref:System.Tuple> are read-only.</span></span> <span data-ttu-id="ee1b1-131">Les types anonymes peuvent être utilisés dans les arborescences d’expressions, contrairement aux tuples.</span><span class="sxs-lookup"><span data-stu-id="ee1b1-131">Anonymous types can be used in expression trees, while tuples cannot.</span></span> <span data-ttu-id="ee1b1-132">Le tableau suivant est une vue d’ensemble de certaines des principales différences.</span><span class="sxs-lookup"><span data-stu-id="ee1b1-132">The following table is an overview of some of the key differences.</span></span>

### <a name="key-differences"></a><span data-ttu-id="ee1b1-133">Différences clés</span><span class="sxs-lookup"><span data-stu-id="ee1b1-133">Key differences</span></span>

| <span data-ttu-id="ee1b1-134">Nom</span><span class="sxs-lookup"><span data-stu-id="ee1b1-134">Name</span></span>                     | <span data-ttu-id="ee1b1-135">Modificateur d’accès </span><span class="sxs-lookup"><span data-stu-id="ee1b1-135">Access modifier</span></span> | <span data-ttu-id="ee1b1-136">Type</span><span class="sxs-lookup"><span data-stu-id="ee1b1-136">Type</span></span>     | <span data-ttu-id="ee1b1-137">Nom du membre personnalisé</span><span class="sxs-lookup"><span data-stu-id="ee1b1-137">Custom member name</span></span> | <span data-ttu-id="ee1b1-138">Prise en charge de la déconstruction</span><span class="sxs-lookup"><span data-stu-id="ee1b1-138">Deconstruction support</span></span> | <span data-ttu-id="ee1b1-139">Prise en charge de l’arborescence d’expressions</span><span class="sxs-lookup"><span data-stu-id="ee1b1-139">Expression tree support</span></span> |
|--------------------------|-----------------|----------|----------------------|------------------------|-------------------------|
| <span data-ttu-id="ee1b1-140">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="ee1b1-140">Anonymous types</span></span>          | `internal`      | `class`  | <span data-ttu-id="ee1b1-141">✔️</span><span class="sxs-lookup"><span data-stu-id="ee1b1-141">✔️</span></span>                   | ❌                     | <span data-ttu-id="ee1b1-142">✔️</span><span class="sxs-lookup"><span data-stu-id="ee1b1-142">✔️</span></span>                     |
| <xref:System.Tuple>      | `public`        | `class`  | ❌                   | ❌                     | <span data-ttu-id="ee1b1-143">✔️</span><span class="sxs-lookup"><span data-stu-id="ee1b1-143">✔️</span></span>                     |
| <xref:System.ValueTuple> | `public`        | `struct` | <span data-ttu-id="ee1b1-144">✔️</span><span class="sxs-lookup"><span data-stu-id="ee1b1-144">✔️</span></span>                   | <span data-ttu-id="ee1b1-145">✔️</span><span class="sxs-lookup"><span data-stu-id="ee1b1-145">✔️</span></span>                     | ❌                     |

### <a name="serialization"></a><span data-ttu-id="ee1b1-146">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="ee1b1-146">Serialization</span></span>

<span data-ttu-id="ee1b1-147">Un point important à prendre en compte lors du choix d’un type est qu’il doit ou non être sérialisé.</span><span class="sxs-lookup"><span data-stu-id="ee1b1-147">One important consideration when choosing a type, is whether or not it will need to be serialized.</span></span> <span data-ttu-id="ee1b1-148">La sérialisation correspond au processus de conversion de l'état d'un objet en un formulaire persistant ou transportable.</span><span class="sxs-lookup"><span data-stu-id="ee1b1-148">Serialization is the process of converting the state of an object into a form that can be persisted or transported.</span></span> <span data-ttu-id="ee1b1-149">Pour plus d’informations, consultez [sérialisation](../../csharp/programming-guide/concepts/serialization/index.md).</span><span class="sxs-lookup"><span data-stu-id="ee1b1-149">For more information, see [serialization](../../csharp/programming-guide/concepts/serialization/index.md).</span></span> <span data-ttu-id="ee1b1-150">Lorsque la sérialisation est importante, la création d’un ou d’un `class` `struct` est préférable sur les types anonymes ou les types de tuples.</span><span class="sxs-lookup"><span data-stu-id="ee1b1-150">When serialization is important, creating a `class` or `struct` is preferred over anonymous types or tuple types.</span></span>

## <a name="performance"></a><span data-ttu-id="ee1b1-151">Performances</span><span class="sxs-lookup"><span data-stu-id="ee1b1-151">Performance</span></span>

<span data-ttu-id="ee1b1-152">Les performances entre ces types dépendent du scénario.</span><span class="sxs-lookup"><span data-stu-id="ee1b1-152">Performance between these types depends on the scenario.</span></span> <span data-ttu-id="ee1b1-153">L’impact majeur concerne le compromis entre les allocations et la copie.</span><span class="sxs-lookup"><span data-stu-id="ee1b1-153">The major impact involves the tradeoff between allocations and copying.</span></span> <span data-ttu-id="ee1b1-154">Dans la plupart des scénarios, l’impact est faible.</span><span class="sxs-lookup"><span data-stu-id="ee1b1-154">In most scenarios, the impact is small.</span></span> <span data-ttu-id="ee1b1-155">Lorsque des impacts majeurs peuvent survenir, les mesures doivent être prises pour informer la décision.</span><span class="sxs-lookup"><span data-stu-id="ee1b1-155">When major impacts could arise, measurements should be taken to inform the decision.</span></span>

## <a name="conclusion"></a><span data-ttu-id="ee1b1-156">Conclusion</span><span class="sxs-lookup"><span data-stu-id="ee1b1-156">Conclusion</span></span>

<span data-ttu-id="ee1b1-157">En tant que développeur qui choisit entre les tuples et les types anonymes, plusieurs facteurs sont à prendre en compte.</span><span class="sxs-lookup"><span data-stu-id="ee1b1-157">As a developer choosing between tuples and anonymous types, there are several factors to consider.</span></span> <span data-ttu-id="ee1b1-158">En règle générale, si vous ne travaillez pas avec les [arborescences d’expressions](../../csharp/expression-trees.md), et que vous êtes familiarisé avec la syntaxe des tuples, choisissez alors <xref:System.ValueTuple> qu’elles fournissent un type de valeur avec la flexibilité nécessaire pour nommer les propriétés.</span><span class="sxs-lookup"><span data-stu-id="ee1b1-158">Generally speaking, if you're not working with [expression trees](../../csharp/expression-trees.md), and you're comfortable with tuple syntax then choose <xref:System.ValueTuple> as they provide a value type with the flexibility to name properties.</span></span> <span data-ttu-id="ee1b1-159">Si vous utilisez des arborescences d’expressions et que vous préférez nommer des propriétés, choisissez des types anonymes.</span><span class="sxs-lookup"><span data-stu-id="ee1b1-159">If you're working with expression trees, and you'd prefer to name properties, choose anonymous types.</span></span> <span data-ttu-id="ee1b1-160">Sinon, utilisez <xref:System.Tuple>.</span><span class="sxs-lookup"><span data-stu-id="ee1b1-160">Otherwise, use <xref:System.Tuple>.</span></span>

## <a name="see-also"></a><span data-ttu-id="ee1b1-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee1b1-161">See also</span></span>

- [<span data-ttu-id="ee1b1-162">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="ee1b1-162">Anonymous types</span></span>](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="ee1b1-163">Arborescences de l’expression</span><span class="sxs-lookup"><span data-stu-id="ee1b1-163">Expression trees</span></span>](../../csharp/expression-trees.md)
- [<span data-ttu-id="ee1b1-164">Types de tuples (référence C#)</span><span class="sxs-lookup"><span data-stu-id="ee1b1-164">Tuple types (C# reference)</span></span>](../../csharp/language-reference/builtin-types/value-tuples.md)
- [<span data-ttu-id="ee1b1-165">Tuples (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ee1b1-165">Tuples (Visual Basic)</span></span>](../../visual-basic/programming-guide/language-features/data-types/tuples.md)
- [<span data-ttu-id="ee1b1-166">Instructions de conception de types</span><span class="sxs-lookup"><span data-stu-id="ee1b1-166">Type design guidelines</span></span>](../design-guidelines/type.md)

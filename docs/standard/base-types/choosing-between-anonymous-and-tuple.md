---
title: Choix entre les types de tuples et anonymes
description: Découvrez quand il est approprié de choisir entre les types anonymes et le type de Tuple.
ms.date: 07/01/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 24ab770d709b9f3968f4c7fe4b01eb0729dbd751
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85854001"
---
# <a name="choosing-between-anonymous-and-tuple-types"></a><span data-ttu-id="c083a-103">Choix entre les types de tuples et anonymes</span><span class="sxs-lookup"><span data-stu-id="c083a-103">Choosing between anonymous and tuple types</span></span>

<span data-ttu-id="c083a-104">Le choix du type approprié implique la prise en compte de l’utilisation, des performances et des compromis par rapport aux autres types.</span><span class="sxs-lookup"><span data-stu-id="c083a-104">Choosing the appropriate type involves considering its usability, performance, and tradeoffs compared to other types.</span></span> <span data-ttu-id="c083a-105">Les types anonymes sont disponibles depuis C# 3,0, tandis que <xref:System.Tuple%602?displayProperty=nameWithType> les types génériques ont été introduits avec .NET Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="c083a-105">Anonymous types have been available since C# 3.0, while generic <xref:System.Tuple%602?displayProperty=nameWithType> types were introduced with .NET Framework 4.0.</span></span> <span data-ttu-id="c083a-106">Dans la mesure où de nouvelles options ont été introduites avec la prise en charge du niveau de langage, comme, <xref:System.ValueTuple%602?displayProperty=nameWithType> qui, comme son nom l’indique, fournit un type de valeur avec la flexibilité des types anonymes.</span><span class="sxs-lookup"><span data-stu-id="c083a-106">Since then new options have been introduced with language level support, such as <xref:System.ValueTuple%602?displayProperty=nameWithType> - which as the name implies, provide a value type with the flexibility of anonymous types.</span></span> <span data-ttu-id="c083a-107">Dans cet article, vous découvrirez quand il est approprié de choisir un type par rapport à l’autre.</span><span class="sxs-lookup"><span data-stu-id="c083a-107">In this article, you'll learn when it's appropriate to choose one type over the other.</span></span>

## <a name="usability-and-functionality"></a><span data-ttu-id="c083a-108">Convivialité et fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="c083a-108">Usability and functionality</span></span>

<span data-ttu-id="c083a-109">Les types anonymes ont été introduits dans C# 3,0 avec des expressions LINQ (Language-Integrated Query).</span><span class="sxs-lookup"><span data-stu-id="c083a-109">Anonymous types were introduced in C# 3.0 with Language-Integrated Query (LINQ) expressions.</span></span> <span data-ttu-id="c083a-110">Avec LINQ, les développeurs projetent souvent les résultats de requêtes dans des types anonymes qui contiennent quelques propriétés Select des objets avec lesquels ils travaillent.</span><span class="sxs-lookup"><span data-stu-id="c083a-110">With LINQ, developers often project results from queries into anonymous types that hold a few select properties from the objects they're working with.</span></span> <span data-ttu-id="c083a-111">Prenons l’exemple suivant, qui instancie un tableau d' <xref:System.DateTime> objets, et itère au sein de ce projet dans un type anonyme avec deux propriétés.</span><span class="sxs-lookup"><span data-stu-id="c083a-111">Consider the following example, that instantiates an array of <xref:System.DateTime> objects, and iterates through them projecting into an anonymous type with two properties.</span></span>

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

<span data-ttu-id="c083a-112">Les types anonymes sont instanciés à l’aide de l' [`new`](../../csharp/language-reference/operators/new-operator.md) opérateur, et les noms et types de propriétés sont déduits de la déclaration.</span><span class="sxs-lookup"><span data-stu-id="c083a-112">Anonymous types are instantiated by using the [`new`](../../csharp/language-reference/operators/new-operator.md) operator, and the property names and types are inferred from the declaration.</span></span> <span data-ttu-id="c083a-113">Si au moins deux initialiseurs d’objets anonymes dans le même assembly spécifient une séquence de propriétés qui sont dans le même ordre et qui ont les mêmes noms et types, le compilateur traite les objets comme des instances du même type.</span><span class="sxs-lookup"><span data-stu-id="c083a-113">If two or more anonymous object initializers in the same assembly specify a sequence of properties that are in the same order and that have the same names and types, the compiler treats the objects as instances of the same type.</span></span> <span data-ttu-id="c083a-114">Elles partagent les mêmes informations de type générées par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="c083a-114">They share the same compiler-generated type information.</span></span>

<span data-ttu-id="c083a-115">L’extrait de code C# précédent projette un type anonyme avec deux propriétés, de la même façon que la classe C# générée par le compilateur suivante :</span><span class="sxs-lookup"><span data-stu-id="c083a-115">The previous C# snippet projects an anonymous type with two properties, much like the following compiler-generated C# class:</span></span>

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

<span data-ttu-id="c083a-116">Pour plus d’informations, consultez [types anonymes](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="c083a-116">For more information, see [anonymous types](../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span> <span data-ttu-id="c083a-117">Les mêmes fonctionnalités existent avec les tuples lors de la projection dans des requêtes LINQ, vous pouvez sélectionner des propriétés dans des tuples.</span><span class="sxs-lookup"><span data-stu-id="c083a-117">The same functionality exists with tuples when projecting into LINQ queries, you can select properties into tuples.</span></span> <span data-ttu-id="c083a-118">Ces tuples passent par la requête, tout comme les types anonymes.</span><span class="sxs-lookup"><span data-stu-id="c083a-118">These tuples flow through the query, just as anonymous types would.</span></span> <span data-ttu-id="c083a-119">À présent, considérez l’exemple suivant à l’aide de `System.Tuple<string, long>` .</span><span class="sxs-lookup"><span data-stu-id="c083a-119">Now consider the following example using the `System.Tuple<string, long>`.</span></span>

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

<span data-ttu-id="c083a-120">Avec <xref:System.Tuple%602?displayProperty=nameWithType> , l’instance expose des propriétés d’élément numérotées, telles que `Item1` et `Item2` .</span><span class="sxs-lookup"><span data-stu-id="c083a-120">With the <xref:System.Tuple%602?displayProperty=nameWithType>, the instance exposes numbered item properties, such as `Item1`, and `Item2`.</span></span> <span data-ttu-id="c083a-121">Ces noms de propriété peuvent compliquer la compréhension de l’objectif des valeurs de propriété, car le nom de propriété fournit uniquement l’ordinal.</span><span class="sxs-lookup"><span data-stu-id="c083a-121">These property names can make it more difficult to understand the intent of the property values, as the property name only provides the ordinal.</span></span> <span data-ttu-id="c083a-122">En outre, les `System.Tuple` types sont des `class` types référence.</span><span class="sxs-lookup"><span data-stu-id="c083a-122">Furthermore, the `System.Tuple` types are reference `class` types.</span></span> <span data-ttu-id="c083a-123"><xref:System.ValueTuple%602?displayProperty=nameWithType>Toutefois, est un type valeur `struct` .</span><span class="sxs-lookup"><span data-stu-id="c083a-123">The <xref:System.ValueTuple%602?displayProperty=nameWithType> however, is a value `struct` type.</span></span> <span data-ttu-id="c083a-124">L’extrait de code C# suivant utilise `ValueTuple<string, long>` pour projeter dans.</span><span class="sxs-lookup"><span data-stu-id="c083a-124">The following C# snippet, uses `ValueTuple<string, long>` to project into.</span></span> <span data-ttu-id="c083a-125">Dans ce cas, elle est assignée à l’aide d’une syntaxe littérale.</span><span class="sxs-lookup"><span data-stu-id="c083a-125">In doing so, it assigns using a literal syntax.</span></span>

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

<span data-ttu-id="c083a-126">C# fournit la prise en charge linguistique des tuples avec le <xref:System.ValueTuple> type, et la sémantique pour :</span><span class="sxs-lookup"><span data-stu-id="c083a-126">C# provides language support of tuples with the <xref:System.ValueTuple> type, and semantics for:</span></span>

- [<span data-ttu-id="c083a-127">Assignation de Tuple</span><span class="sxs-lookup"><span data-stu-id="c083a-127">Tuple assignment</span></span>](../../csharp/tuples.md#assignment-and-tuples)
- <span data-ttu-id="c083a-128">[Déconstruction de tuple](../../csharp/deconstruct.md) (non limité aux tuples)</span><span class="sxs-lookup"><span data-stu-id="c083a-128">[Tuple deconstruction](../../csharp/deconstruct.md) (not limited to tuples)</span></span>
- [<span data-ttu-id="c083a-129">Vérifications de l’égalité des tuples</span><span class="sxs-lookup"><span data-stu-id="c083a-129">Tuple equality checks</span></span>](../../csharp/tuples.md#equality-and-tuples)
- [<span data-ttu-id="c083a-130">Initialiseurs de projection de tuple</span><span class="sxs-lookup"><span data-stu-id="c083a-130">Tuple projection initializers</span></span>](../../csharp/tuples.md#tuple-projection-initializers)

<span data-ttu-id="c083a-131">Les exemples précédents sont tous des équivalents fonctionnels, toutefois, leur utilisation et leurs implémentations sous-jacentes présentent de légères différences.</span><span class="sxs-lookup"><span data-stu-id="c083a-131">The previous examples are all functionally equivalent, however; there are slight differences in their usability and their underlying implementations.</span></span>

## <a name="tradeoffs"></a><span data-ttu-id="c083a-132">Compromis</span><span class="sxs-lookup"><span data-stu-id="c083a-132">Tradeoffs</span></span>

<span data-ttu-id="c083a-133">Vous souhaiterez peut-être toujours utiliser <xref:System.ValueTuple> <xref:System.Tuple> les types plus ou anonymes, mais il existe des compromis à prendre en compte.</span><span class="sxs-lookup"><span data-stu-id="c083a-133">You might want to always use <xref:System.ValueTuple> over <xref:System.Tuple>, and anonymous types, but there are tradeoffs you should consider.</span></span> <span data-ttu-id="c083a-134">Les <xref:System.ValueTuple> types sont mutables, alors que <xref:System.Tuple> ceux-ci sont en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="c083a-134">The <xref:System.ValueTuple> types are mutable, whereas <xref:System.Tuple> are read-only.</span></span> <span data-ttu-id="c083a-135">Les types anonymes peuvent être utilisés dans les arborescences d’expressions, contrairement aux tuples.</span><span class="sxs-lookup"><span data-stu-id="c083a-135">Anonymous types can be used in expression trees, while tuples cannot.</span></span> <span data-ttu-id="c083a-136">Le tableau suivant est une vue d’ensemble de certaines des principales différences.</span><span class="sxs-lookup"><span data-stu-id="c083a-136">The following table is an overview of some of the key differences.</span></span>

### <a name="key-differences"></a><span data-ttu-id="c083a-137">Différences clés</span><span class="sxs-lookup"><span data-stu-id="c083a-137">Key differences</span></span>

| <span data-ttu-id="c083a-138">Nom</span><span class="sxs-lookup"><span data-stu-id="c083a-138">Name</span></span>                     | <span data-ttu-id="c083a-139">Modificateur d’accès </span><span class="sxs-lookup"><span data-stu-id="c083a-139">Access modifier</span></span> | <span data-ttu-id="c083a-140">Type</span><span class="sxs-lookup"><span data-stu-id="c083a-140">Type</span></span>     | <span data-ttu-id="c083a-141">Nom de la propriété personnalisée</span><span class="sxs-lookup"><span data-stu-id="c083a-141">Custom property name</span></span> | <span data-ttu-id="c083a-142">Prise en charge de la déconstruction</span><span class="sxs-lookup"><span data-stu-id="c083a-142">Deconstruction support</span></span> | <span data-ttu-id="c083a-143">Prise en charge de l’arborescence d’expressions</span><span class="sxs-lookup"><span data-stu-id="c083a-143">Expression tree support</span></span> |
|--------------------------|-----------------|----------|----------------------|------------------------|-------------------------|
| <span data-ttu-id="c083a-144">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="c083a-144">Anonymous types</span></span>          | `internal`      | `class`  | <span data-ttu-id="c083a-145">✔️</span><span class="sxs-lookup"><span data-stu-id="c083a-145">✔️</span></span>                   | ❌                     | <span data-ttu-id="c083a-146">✔️</span><span class="sxs-lookup"><span data-stu-id="c083a-146">✔️</span></span>                     |
| <xref:System.Tuple>      | `public`        | `class`  | ❌                   | ❌                     | <span data-ttu-id="c083a-147">✔️</span><span class="sxs-lookup"><span data-stu-id="c083a-147">✔️</span></span>                     |
| <xref:System.ValueTuple> | `public`        | `struct` | <span data-ttu-id="c083a-148">✔️</span><span class="sxs-lookup"><span data-stu-id="c083a-148">✔️</span></span>                   | <span data-ttu-id="c083a-149">✔️</span><span class="sxs-lookup"><span data-stu-id="c083a-149">✔️</span></span>                     | ❌                     |

### <a name="serialization"></a><span data-ttu-id="c083a-150">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="c083a-150">Serialization</span></span>

<span data-ttu-id="c083a-151">Un point important à prendre en compte lors du choix d’un type est qu’il doit ou non être sérialisé.</span><span class="sxs-lookup"><span data-stu-id="c083a-151">One important consideration when choosing a type, is whether or not it will need to be serialized.</span></span> <span data-ttu-id="c083a-152">La sérialisation correspond au processus de conversion de l'état d'un objet en un formulaire persistant ou transportable.</span><span class="sxs-lookup"><span data-stu-id="c083a-152">Serialization is the process of converting the state of an object into a form that can be persisted or transported.</span></span> <span data-ttu-id="c083a-153">Pour plus d’informations, consultez [sérialisation](../../csharp/programming-guide/concepts/serialization/index.md).</span><span class="sxs-lookup"><span data-stu-id="c083a-153">For more information, see [serialization](../../csharp/programming-guide/concepts/serialization/index.md).</span></span> <span data-ttu-id="c083a-154">Lorsque la sérialisation est importante, la création d’un ou d’un `class` `struct` est préférable sur les types anonymes ou les types de tuples.</span><span class="sxs-lookup"><span data-stu-id="c083a-154">When serialization is important, creating a `class` or `struct` is preferred over anonymous types or tuple types.</span></span>

## <a name="performance"></a><span data-ttu-id="c083a-155">Performances</span><span class="sxs-lookup"><span data-stu-id="c083a-155">Performance</span></span>

<span data-ttu-id="c083a-156">Les performances entre ces types dépendent du scénario.</span><span class="sxs-lookup"><span data-stu-id="c083a-156">Performance between these types depends on the scenario.</span></span> <span data-ttu-id="c083a-157">L’impact majeur concerne le compromis entre les allocations et la copie.</span><span class="sxs-lookup"><span data-stu-id="c083a-157">The major impact involves the tradeoff between allocations and copying.</span></span> <span data-ttu-id="c083a-158">Dans la plupart des scénarios, l’impact est faible.</span><span class="sxs-lookup"><span data-stu-id="c083a-158">In most scenarios, the impact is small.</span></span> <span data-ttu-id="c083a-159">Lorsque des impacts majeurs peuvent survenir, les mesures doivent être prises pour informer la décision.</span><span class="sxs-lookup"><span data-stu-id="c083a-159">When major impacts could arise, measurements should be taken to inform the decision.</span></span>

## <a name="conclusion"></a><span data-ttu-id="c083a-160">Conclusion</span><span class="sxs-lookup"><span data-stu-id="c083a-160">Conclusion</span></span>

<span data-ttu-id="c083a-161">En tant que développeur qui choisit entre les tuples et les types anonymes, plusieurs facteurs sont à prendre en compte.</span><span class="sxs-lookup"><span data-stu-id="c083a-161">As a developer choosing between tuples and anonymous types, there are several factors to consider.</span></span> <span data-ttu-id="c083a-162">En règle générale, si vous ne travaillez pas avec les [arborescences d’expressions](../../csharp/expression-trees.md), et que vous êtes familiarisé avec la syntaxe des tuples, choisissez alors <xref:System.ValueTuple> qu’elles fournissent un type de valeur avec la flexibilité nécessaire pour nommer les propriétés.</span><span class="sxs-lookup"><span data-stu-id="c083a-162">Generally speaking, if you're not working with [expression trees](../../csharp/expression-trees.md), and you're comfortable with tuple syntax then choose <xref:System.ValueTuple> as they provide a value type with the flexibility to name properties.</span></span> <span data-ttu-id="c083a-163">Si vous utilisez des arborescences d’expressions et que vous préférez nommer des propriétés, choisissez des types anonymes.</span><span class="sxs-lookup"><span data-stu-id="c083a-163">If you're working with expression trees, and you'd prefer to name properties, choose anonymous types.</span></span> <span data-ttu-id="c083a-164">Sinon, utilisez <xref:System.Tuple>.</span><span class="sxs-lookup"><span data-stu-id="c083a-164">Otherwise, use <xref:System.Tuple>.</span></span>

## <a name="see-also"></a><span data-ttu-id="c083a-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c083a-165">See also</span></span>

- [<span data-ttu-id="c083a-166">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="c083a-166">Anonymous types</span></span>](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="c083a-167">Arborescences de l’expression</span><span class="sxs-lookup"><span data-stu-id="c083a-167">Expression trees</span></span>](../../csharp/expression-trees.md)
- [<span data-ttu-id="c083a-168">Types de tuples</span><span class="sxs-lookup"><span data-stu-id="c083a-168">Tuple types</span></span>](../../csharp/tuples.md)
- [<span data-ttu-id="c083a-169">Instructions de conception de types</span><span class="sxs-lookup"><span data-stu-id="c083a-169">Type design guidelines</span></span>](../design-guidelines/type.md)

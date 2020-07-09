---
title: Choix entre les types de tuples et anonymes
description: Découvrez quand il est approprié de choisir entre les types anonymes et le type de Tuple.
author: IEvangelist
ms.author: dapine
ms.date: 07/01/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 9140250ad1f48501bf1d2e53a1c179e6823f19cd
ms.sourcegitcommit: 4ad2f8920251f3744240c3b42a443ffbe0a46577
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/08/2020
ms.locfileid: "86100962"
---
# <a name="choosing-between-anonymous-and-tuple-types"></a>Choix entre les types de tuples et anonymes

Le choix du type approprié implique la prise en compte de l’utilisation, des performances et des compromis par rapport aux autres types. Les types anonymes sont disponibles depuis C# 3,0, tandis que <xref:System.Tuple%602?displayProperty=nameWithType> les types génériques ont été introduits avec .NET Framework 4,0. Dans la mesure où de nouvelles options ont été introduites avec la prise en charge du niveau de langage, comme, <xref:System.ValueTuple%602?displayProperty=nameWithType> qui, comme son nom l’indique, fournit un type de valeur avec la flexibilité des types anonymes. Dans cet article, vous découvrirez quand il est approprié de choisir un type par rapport à l’autre.

## <a name="usability-and-functionality"></a>Convivialité et fonctionnalités

Les types anonymes ont été introduits dans C# 3,0 avec des expressions LINQ (Language-Integrated Query). Avec LINQ, les développeurs projetent souvent les résultats de requêtes dans des types anonymes qui contiennent quelques propriétés Select des objets avec lesquels ils travaillent. Prenons l’exemple suivant, qui instancie un tableau d' <xref:System.DateTime> objets, et itère au sein de ce projet dans un type anonyme avec deux propriétés.

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

Les types anonymes sont instanciés à l’aide de l' [`new`](../../csharp/language-reference/operators/new-operator.md) opérateur, et les noms et types de propriétés sont déduits de la déclaration. Si au moins deux initialiseurs d’objets anonymes dans le même assembly spécifient une séquence de propriétés qui sont dans le même ordre et qui ont les mêmes noms et types, le compilateur traite les objets comme des instances du même type. Elles partagent les mêmes informations de type générées par le compilateur.

L’extrait de code C# précédent projette un type anonyme avec deux propriétés, de la même façon que la classe C# générée par le compilateur suivante :

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

Pour plus d’informations, consultez [types anonymes](../../csharp/programming-guide/classes-and-structs/anonymous-types.md). Les mêmes fonctionnalités existent avec les tuples lors de la projection dans des requêtes LINQ, vous pouvez sélectionner des propriétés dans des tuples. Ces tuples passent par la requête, tout comme les types anonymes. À présent, considérez l’exemple suivant à l’aide de `System.Tuple<string, long>` .

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

Avec <xref:System.Tuple%602?displayProperty=nameWithType> , l’instance expose des propriétés d’élément numérotées, telles que `Item1` et `Item2` . Ces noms de propriété peuvent compliquer la compréhension de l’objectif des valeurs de propriété, car le nom de propriété fournit uniquement l’ordinal. En outre, les `System.Tuple` types sont des `class` types référence. <xref:System.ValueTuple%602?displayProperty=nameWithType>Toutefois, est un type valeur `struct` . L’extrait de code C# suivant utilise `ValueTuple<string, long>` pour projeter dans. Dans ce cas, elle est assignée à l’aide d’une syntaxe littérale.

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

C# fournit la prise en charge linguistique des tuples avec le <xref:System.ValueTuple> type, et la sémantique pour :

- [Assignation de Tuple](../../csharp/tuples.md#assignment-and-tuples)
- [Déconstruction de tuple](../../csharp/deconstruct.md) (non limité aux tuples)
- [Vérifications de l’égalité des tuples](../../csharp/tuples.md#equality-and-tuples)
- [Initialiseurs de projection de tuple](../../csharp/tuples.md#tuple-projection-initializers)

Les exemples précédents sont tous des équivalents fonctionnels, toutefois, leur utilisation et leurs implémentations sous-jacentes présentent de légères différences.

## <a name="tradeoffs"></a>Compromis

Vous souhaiterez peut-être toujours utiliser <xref:System.ValueTuple> <xref:System.Tuple> les types plus ou anonymes, mais il existe des compromis à prendre en compte. Les <xref:System.ValueTuple> types sont mutables, alors que <xref:System.Tuple> ceux-ci sont en lecture seule. Les types anonymes peuvent être utilisés dans les arborescences d’expressions, contrairement aux tuples. Le tableau suivant est une vue d’ensemble de certaines des principales différences.

### <a name="key-differences"></a>Différences clés

| Nom                     | Modificateur d’accès  | Type     | Nom du membre personnalisé | Prise en charge de la déconstruction | Prise en charge de l’arborescence d’expressions |
|--------------------------|-----------------|----------|----------------------|------------------------|-------------------------|
| Types anonymes          | `internal`      | `class`  | ✔️                   | ❌                     | ✔️                     |
| <xref:System.Tuple>      | `public`        | `class`  | ❌                   | ❌                     | ✔️                     |
| <xref:System.ValueTuple> | `public`        | `struct` | ✔️                   | ✔️                     | ❌                     |

### <a name="serialization"></a>Sérialisation

Un point important à prendre en compte lors du choix d’un type est qu’il doit ou non être sérialisé. La sérialisation correspond au processus de conversion de l'état d'un objet en un formulaire persistant ou transportable. Pour plus d’informations, consultez [sérialisation](../../csharp/programming-guide/concepts/serialization/index.md). Lorsque la sérialisation est importante, la création d’un ou d’un `class` `struct` est préférable sur les types anonymes ou les types de tuples.

## <a name="performance"></a>Performances

Les performances entre ces types dépendent du scénario. L’impact majeur concerne le compromis entre les allocations et la copie. Dans la plupart des scénarios, l’impact est faible. Lorsque des impacts majeurs peuvent survenir, les mesures doivent être prises pour informer la décision.

## <a name="conclusion"></a>Conclusion

En tant que développeur qui choisit entre les tuples et les types anonymes, plusieurs facteurs sont à prendre en compte. En règle générale, si vous ne travaillez pas avec les [arborescences d’expressions](../../csharp/expression-trees.md), et que vous êtes familiarisé avec la syntaxe des tuples, choisissez alors <xref:System.ValueTuple> qu’elles fournissent un type de valeur avec la flexibilité nécessaire pour nommer les propriétés. Si vous utilisez des arborescences d’expressions et que vous préférez nommer des propriétés, choisissez des types anonymes. Sinon, utilisez <xref:System.Tuple>.

## <a name="see-also"></a>Voir aussi

- [Types anonymes](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [Arborescences de l’expression](../../csharp/expression-trees.md)
- [Types de tuples](../../csharp/tuples.md)
- [Instructions de conception de types](../design-guidelines/type.md)

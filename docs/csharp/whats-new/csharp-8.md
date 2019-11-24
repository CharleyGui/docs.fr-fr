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
# <a name="whats-new-in-c-80"></a>Nouveautés de C# 8.0

C# 8.0 adds the following features and enhancements to the C# language:

- [Membres ReadOnly](#readonly-members)
- [Default interface methods](#default-interface-methods)
- [Amélioration des critères spéciaux](#more-patterns-in-more-places) :
  - [Expressions switch](#switch-expressions)
  - [Modèles de propriétés](#property-patterns)
  - [Modèles de tuples](#tuple-patterns)
  - [Modèles positionnels](#positional-patterns)
- [Déclarations using](#using-declarations)
- [Fonctions locales statiques](#static-local-functions)
- [Structs ref jetables](#disposable-ref-structs)
- [Types de référence Nullable](#nullable-reference-types)
- [Flux asynchrones](#asynchronous-streams)
- [Index et plages](#indices-and-ranges)
- [Null-coalescing assignment](#null-coalescing-assignment)
- [Unmanaged constructed types](#unmanaged-constructed-types)
- [Stackalloc in nested expressions](#stackalloc-in-nested-expressions)
- [Enhancement of interpolated verbatim strings](#enhancement-of-interpolated-verbatim-strings)

C# 8.0 is supported on **.NET Core 3.x** and **.NET Standard 2.1**. For more information, see [C# language versioning](../language-reference/configure-language-version.md).

La suite de cet article décrit brièvement ces fonctionnalités. Lorsque des articles détaillés sont disponibles, des liens vers ces tutoriels et vues d’ensemble sont indiqués. Vous pouvez explorer ces fonctionnalités dans votre environnement à l’aide de l’outil global `dotnet try` :

1. Installez l’outil global [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup).
1. Clonez le référentiel [dotnet/try-samples](https://github.com/dotnet/try-samples).
1. Définissez le répertoire actuel sur le sous-répertoire *csharp8* pour le référentiel *try-samples*.
1. Exécutez `dotnet try`.

## <a name="readonly-members"></a>Membres ReadOnly

You can apply the `readonly` modifier to members of a struct. It indicates that the member doesn't modify state. C’est plus précis que d’appliquer le modificateur `readonly` à une déclaration `struct`.  Examinons le struct mutable suivant :

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

Like most structs, the `ToString()` method doesn't modify state. Vous pouvez indiquer cela en ajoutant le modificateur `readonly` à la déclaration de `ToString()` :

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

The preceding change generates a compiler warning, because `ToString` accesses the `Distance` property, which isn't marked `readonly`:

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

Le compilateur vous avertit lorsqu’il a besoin de créer une copie défensive.  The `Distance` property doesn't change state, so you can fix this warning by adding the `readonly` modifier to the declaration:

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

Notice that the `readonly` modifier is necessary on a read-only property. The compiler doesn't assume `get` accessors don't modify state; you must declare `readonly` explicitly. Auto-implemented properties are an exception; the compiler will treat all auto-implemented getters as readonly, so here there's no need to add the `readonly` modifier to the `X` and `Y` properties.

The compiler does enforce the rule that `readonly` members don't modify state. The following method won't compile unless you remove the `readonly` modifier:

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

Cette fonctionnalité vous permet de spécifier votre intention de conception, afin que le compilateur puisse l’appliquer et procéder à des optimisations basées sur cette intention. You can learn more about readonly members in the language reference article on [`readonly`](../language-reference/keywords/readonly.md#readonly-member-examples).

## <a name="default-interface-methods"></a>Méthodes d’interface par défaut

Vous pouvez désormais ajouter des membres aux interfaces et fournir une implémentation pour ces membres. Cette fonctionnalité de langage permet aux auteurs d’API d’ajouter des méthodes à une interface dans les versions ultérieures sans pour autant nuire à la compatibilité des binaires ou des sources avec les implémentations existantes de cette interface. Les implémentations existantes *héritent* de l’implémentation par défaut. Cette fonctionnalité permet également à C# d’interagir avec les API ciblant Android ou Swift, qui prennent en charge des fonctionnalités similaires. Default interface methods also enable scenarios similar to a "traits" language feature.

Default interface methods affects many scenarios and language elements. Ce premier tutoriel couvre [la mise à jour d’une interface à l’aide d’implémentations par défaut](../tutorials/default-interface-methods-versions.md). D’autres tutoriels et mises à jour de référence seront disponibles avant le lancement général.

## <a name="more-patterns-in-more-places"></a>Ajout de modèles à différents endroits

Les **critères spéciaux** offrent des outils permettant de produire des fonctionnalités dépendantes de la forme sur des types de données liés mais différents. C# 7.0 a introduit la syntaxe des modèles de type et des modèles de constantes avec l’expression [`is`](../language-reference/keywords/is.md) et l’instruction [`switch`](../language-reference/keywords/switch.md). Ces fonctionnalités représentaient les premières étapes provisoires de prise en charge de paradigmes de programmation distinguant données et fonctionnalités. Face à la transition du secteur vers de nouveaux microservices et autres architectures cloud, d’autres outils sont nécessaires pour le langage.

C# 8.0 développe ce vocabulaire en offrant la possibilité d’utiliser d’autres expressions de modèle à davantage d’endroits dans le code. Étudiez ces fonctionnalités si vos données et vos fonctionnalités sont séparées. Les critères spéciaux peuvent être intéressants si vos algorithmes dépendent d’un fait autre que le type de runtime d’un objet. Ces techniques représentent un autre moyen d’exprimer des conceptions.

En plus des nouveaux modèles en de nouveaux endroits, C# 8.0 ajoute des **modèles récursifs**. Le résultat d’une expression de modèle est une expression. Un modèle récursif constitue simplement une expression de modèle appliquée à la sortie d’une autre expression de modèle.

### <a name="switch-expressions"></a>Expressions switch

Souvent, une instruction [`switch`](../language-reference/keywords/switch.md) produit une valeur dans chacun de ses blocs `case`. **Les expressions switch** permettent d’utiliser une syntaxe d’expression plus concise, comprenant moins de mots clés `case` et `break` répétitifs et moins d’accolades.  Prenons par exemple l’enum suivant, qui liste les couleurs de l’arc-en-ciel :

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

Si votre application a défini un type `RGBColor` construit à partir des composants `R`, `G` et `B`, vous pouvez convertir une valeur `Rainbow` en valeurs RVB avec la méthode suivante, qui contient une expression switch :

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

Plusieurs améliorations ont ici été apportées à la syntaxe :

- La variable se situe avant le mot clé `switch`. Ce nouvel ordre permet de distinguer visuellement l’expression switch de l’instruction switch.
- Les éléments `case` et `:` sont remplacés par `=>`, plus concis et plus intuitif.
- Le cas `default` est remplacé par un discard `_`.
- Les corps sont des expressions et non des instructions.

Comparez cela avec le code équivalent utilisant l’instruction `switch` classique :

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

### <a name="property-patterns"></a>Modèles de propriétés

Le **modèle de propriété** permet de faire correspondre les propriétés de l’objet examiné. Prenons un site d’e-commerce qui doit calculer les taxes sur les ventes en fonction de l’adresse de l’acheteur. That computation isn't a core responsibility of an `Address` class. Il changera au fil du temps, probablement plus souvent que n’évoluera le format de l’adresse. Le montant des taxes sur les ventes varie selon la propriété `State` de l’adresse. La méthode suivante utilise le modèle de propriété pour calculer les taxes sur les ventes à partir de l’adresse et du prix :

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

Les critères spéciaux offrent une syntaxe concise pour exprimer cet algorithme.

### <a name="tuple-patterns"></a>Modèles de tuples

Certains algorithmes dépendent de plusieurs entrées. Les **modèles de tuples** permettent de basculer des unes aux autres en fonction de plusieurs valeurs exprimées sous forme de [tuple](../tuples.md).  Le code suivant montre une expression switch pour le jeu *Pierre-papier-ciseaux* :

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

Les messages indiquent le vainqueur. Le cas discard représente les trois combinaisons pour les égalités, ou d’autres entrées de texte.

### <a name="positional-patterns"></a>Modèles positionnels

Certains types comportent une méthode `Deconstruct` qui décompose ses propriétés en variables discrètes. Lorsqu’une méthode `Deconstruct` est accessible, il est possible d’utiliser des **modèles positionnels** pour inspecter les propriétés de l’objet et de se servir de ces dernières pour un modèle.  Considérez la classe `Point` suivante, dont la méthode `Deconstruct` sert à créer des variables discrètes pour `X` et `Y` :

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

De plus, envisagez l’énumération suivante qui représente diverses positions d’un quadrant :

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

La méthode suivante utilise le **modèle positionnel** pour extraire les valeurs de `x` et de `y`. Ensuite, elle utilise une clause `when` pour déterminer le `Quadrant` du point :

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

Le modèle discard dans le switch précédent indique une correspondance lorsque soit `x`, soit `y` est égal à 0, mais pas les deux. Une expression switch doit produire une valeur ou, si aucun des cas ne correspond, lever une exception. The compiler generates a warning for you if you don't cover all possible cases in your switch expression.

Vous pouvez explorer des techniques de critères spéciaux dans ce [tutoriel avancé sur les critères spéciaux](../tutorials/pattern-matching.md).

## <a name="using-declarations"></a>Déclarations using

Une **déclaration using** est une déclaration de variable précédée par le mot clé `using`. Elle indique au compilateur que la variable déclarée doit être supprimée à la fin de la portée englobante. Prenons par exemple le code suivant, qui écrit un fichier texte :

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

Dans l’exemple précédent, le fichier est supprimé une fois l’accolade fermante de la méthode atteinte. C’est la fin de la portée dans laquelle `file` est déclaré. Le code précédent équivaut au suivant, qui utilise [l’instruction using](../language-reference/keywords/using-statement.md) classique :

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

Dans l’exemple précédent, le fichier est supprimé une fois l’accolade fermante associée à l’instruction `using` atteinte.

Dans les deux cas, le compilateur génère l’appel à `Dispose()`. The compiler generates an error if the expression in the `using` statement isn't disposable.

## <a name="static-local-functions"></a>Fonctions locales statiques

Il est maintenant possible d’ajouter le modificateur `static` à des fonctions locales pour éviter qu’elles ne capturent (fassent référence à) des variables au sein de la portée englobante. Cela génère `CS8421`, « A static local function can’t contain a reference to \< variable> ». 

Prenons le code suivant. La fonction locale `LocalFunction` accède à la variable `y`, déclarée dans la portée englobante (la méthode `M`). Par conséquent, `LocalFunction` ne peut pas être déclarée avec le modificateur `static` :

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

Le code suivant contient une fonction locale statique. Elle peut être statique, car elle n’accède à aucune variable dans la portée englobante :

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a>Structs ref jetables

A `struct` declared with the `ref` modifier may not implement any interfaces and so can't implement <xref:System.IDisposable>. Par conséquent, pour qu’un `ref struct` soit supprimable, il doit avoir une méthode `void Dispose()` accessible. This feature also applies to `readonly ref struct` declarations.

## <a name="nullable-reference-types"></a>Types références Nullables

Dans un contexte d’annotation Nullable, toute variable d’un type référence est considérée comme un **type référence n'acceptant pas la valeur Null**. Si vous souhaitez indiquer qu’une variable peut être Null, ajoutez `?` au nom de type pour la déclarer comme **type référence Nullable**.

Avec les types références n'acceptant pas la valeur Null, le compilateur utilise l’analyse de flux pour que les variables locales soient initialisées à une valeur non Null une fois déclarées. Les champs doivent être initialisés à la construction. The compiler generates a warning if the variable isn't set by a call to any of the available constructors or by an initializer. Par ailleurs, les types références n’acceptant pas la valeur Null ne peuvent pas avoir de valeur pouvant être Null.

Les types références Nullables font l’objet d’aucun contrôle visant à vérifier qu’ils ne sont pas affectés ou initialisées sur Null. Toutefois, le compilateur utilise l’analyse de flux pour comparer à Null toutes les variables d’un type référence Nullable avant d’y accéder ou de lui affecter un type référence n’acceptant pas la valeur Null.

Plus d’informations sur la fonctionnalité, voir la vue d’ensemble des [types références Nullables](../nullable-references.md). Essayez par vous-même dans une nouvelle application avec ce [tutoriel des types références Nullables](../tutorials/nullable-reference-types.md). Pour plus d’informations sur le processus de migration d’un codebase dans l’objectif d’utiliser des types références Nullables, voir le [tutoriel Migrer une application pour utiliser des types références Nullables](../tutorials/upgrade-to-nullable-references.md).

## <a name="asynchronous-streams"></a>Flux asynchrones

À partir de C# 8.0, il est possible de créer et de consommer des flux de façon asynchrone. Une méthode qui retourne un flux asynchrone comporte trois propriétés :

1. Elle est déclarée avec le modificateur `async`.
1. Elle retourne un <xref:System.Collections.Generic.IAsyncEnumerable%601>.
1. La méthode contient des instructions `yield return` pour retourner des éléments consécutifs dans le flux asynchrone.

Pour pouvoir consommer un flux asynchrone, il faut ajouter le mot clé `await` avant le mot clé `foreach` au moment d’énumérer les éléments du flux. Le mot clé `await` exige que la méthode qui énumère le flux asynchrone soit déclarée avec le modificateur `async` et retourne un type autorisé pour une méthode `async`, soit en général <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>. Il peut également s’agir de <xref:System.Threading.Tasks.ValueTask> ou <xref:System.Threading.Tasks.ValueTask%601>. Une méthode peut consommer et produire un flux asynchrone ; elle retournerait alors un <xref:System.Collections.Generic.IAsyncEnumerable%601>. Le code suivant génère une séquence de 0 à 19, en attendant 100 ms entre chaque nombre :

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

Pour énumérer la séquence, on utilise l’instruction `await foreach` :

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

Vous pouvez essayer par vous-même les flux asynchrones dans notre tutoriel [Créer et consommer des flux asynchrones](../tutorials/generate-consume-asynchronous-stream.md).

## <a name="indices-and-ranges"></a>Index et plages

Indices and ranges provide a succinct syntax for accessing single elements or ranges in a sequence.

This language support relies on two new types, and two new operators:

- <xref:System.Index?displayProperty=nameWithType> représente un index au sein d’une séquence.
- The index from end operator `^`, which specifies that an index is relative to the end of the sequence.
- <xref:System.Range?displayProperty=nameWithType> représente une sous-plage d’une séquence.
- The range operator `..`, which specifies the start and end of a range as its operands.

Commençons par les règles concernant les index. Prenons pour exemple un tableau `sequence`. L’index `0` est identique à l’index `sequence[0]`. L’index `^0` est identique à l’index `sequence[sequence.Length]`. Notez que `sequence[^0]` lève une exception, tout comme `sequence[sequence.Length]`. Pour n’importe quel nombre `n`, l’index `^n` est identique à l’index `sequence.Length - n`.

Une plage spécifie son *début* et sa *fin*. The start of the range is inclusive, but the end of the range is exclusive, meaning the *start* is included in the range but the *end* isn't included in the range. La plage `[0..^0]` représente la plage dans son intégralité, tout comme `[0..sequence.Length]` représente la plage entière.

Prenons quelques exemples. Examinez le tableau suivant, annoté avec son index à partir du début et de la fin :

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

Vous pouvez récupérer le dernier mot avec l’index `^1` :

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

Le code suivant crée une sous-plage qui comporte les mots « quick », « brown » et « fox » et va de `words[1]` à `words[3]`. L’élément `words[4]` n’est pas dans la plage.

```csharp
var quickBrownFox = words[1..4];
```

Le code suivant crée une sous-plage qui comporte « lazy » et « dog » et comprend `words[^2]` et `words[^1]`. The end index `words[^0]` isn't included:

```csharp
var lazyDog = words[^2..^0];
```

Les exemples suivants créent des plages ouvertes au début, à la fin ou les deux :

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

Vous pouvez également déclarer des plages comme variables :

```csharp
Range phrase = 1..4;
```

La plage peut ensuite être utilisée à l’intérieur des caractères `[` et `]` :

```csharp
var text = words[phrase];
```

Not only arrays support indices and ranges. You also can use indices and ranges with [string](../language-reference/builtin-types/reference-types.md#the-string-type), <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>. For more information, see [Type support for indices and ranges](../tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).

Pour explorer davantage les index et les plages, consultez le tutoriel sur [les index et les plages](../tutorials/ranges-indexes.md).

## <a name="null-coalescing-assignment"></a>Null-coalescing assignment

C# 8.0 introduces the null-coalescing assignment operator `??=`. You can use the `??=` operator to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.

```csharp
List<int> numbers = null;
int? i = null;

numbers ??= new List<int>();
numbers.Add(i ??= 17);
numbers.Add(i ??= 20);

Console.WriteLine(string.Join(" ", numbers));  // output: 17 17
Console.WriteLine(i);  // output: 17
```

For more information, see the [?? and ??= operators](../language-reference/operators/null-coalescing-operator.md) article.

## <a name="unmanaged-constructed-types"></a>Unmanaged constructed types

In C# 7.3 and earlier, a constructed type (a type that includes at least one type argument) can't be an [unmanaged type](../language-reference/builtin-types/unmanaged-types.md). Starting with C# 8.0, a constructed value type is unmanaged if it contains fields of unmanaged types only.

For example, given the following definition of the generic `Coords<T>` type:

```csharp
public struct Coords<T>
{
    public T X;
    public T Y;
}
```

the `Coords<int>` type is an unmanaged type in C# 8.0 and later. Like for any unmanaged type, you can create a pointer to a variable of this type or [allocate a block of memory on the stack](../language-reference/operators/stackalloc.md) for instances of this type:

```csharp
Span<Coords<int>> coordinates = stackalloc[]
{
    new Coords<int> { X = 0, Y = 0 },
    new Coords<int> { X = 0, Y = 3 },
    new Coords<int> { X = 4, Y = 0 }
};
```

For more information, see [Unmanaged types](../language-reference/builtin-types/unmanaged-types.md).

## <a name="stackalloc-in-nested-expressions"></a>Stackalloc in nested expressions

Starting with C# 8.0, if the result of a [stackalloc](../language-reference/operators/stackalloc.md) expression is of the <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> type, you can use the `stackalloc` expression in other expressions:

```csharp
Span<int> numbers = stackalloc[] { 1, 2, 3, 4, 5, 6 };
var ind = numbers.IndexOfAny(stackalloc[] { 2, 4, 6 ,8 });
Console.WriteLine(ind);  // output: 1
```

## <a name="enhancement-of-interpolated-verbatim-strings"></a>Enhancement of interpolated verbatim strings

Order of the `$` and `@` tokens in [interpolated](../language-reference/tokens/interpolated.md) verbatim strings can be any: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings. In earlier C# versions, the `$` token must appear before the `@` token.

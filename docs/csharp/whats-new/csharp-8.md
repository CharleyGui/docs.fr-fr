---
title: Nouveautés de C# 8,0-Guide C#
description: Vue d’ensemble des nouvelles fonctionnalités disponibles dans C# 8.0.
ms.date: 04/07/2020
ms.openlocfilehash: 1d6d33a36092ba685247f894375888da278b7e6e
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434806"
---
# <a name="whats-new-in-c-80"></a>Nouveautés de C# 8.0

C# 8,0 ajoute les fonctionnalités et améliorations suivantes au langage C# :

- [Membres ReadOnly](#readonly-members)
- [Méthodes d’interface par défaut](#default-interface-methods)
- [Améliorations des critères spéciaux](#more-patterns-in-more-places):
  - [Expressions de commutateur](#switch-expressions)
  - [Modèles de propriétés](#property-patterns)
  - [Modèles de tuples](#tuple-patterns)
  - [Modèles positionnels](#positional-patterns)
- [Utilisation des déclarations](#using-declarations)
- [Fonctions locales statiques](#static-local-functions)
- [Structs ref jetables](#disposable-ref-structs)
- [Types références Nullables](#nullable-reference-types)
- [Flux asynchrones](#asynchronous-streams)
- [Supprimable asynchrone](#asynchronous-disposable)
- [Index et plages](#indices-and-ranges)
- [Assignation de fusion Null](#null-coalescing-assignment)
- [Types construits non managés](#unmanaged-constructed-types)
- [Stackalloc dans les expressions imbriquées](#stackalloc-in-nested-expressions)
- [Amélioration des chaînes textuelles interpolées](#enhancement-of-interpolated-verbatim-strings)

C# 8,0 est pris en charge sur **.net Core 3. x** et **.NET standard 2,1**. Pour plus d’informations, consultez contrôle de [version du langage C#](../language-reference/configure-language-version.md).

La suite de cet article décrit brièvement ces fonctionnalités. Lorsque des articles détaillés sont disponibles, des liens vers ces tutoriels et vues d’ensemble sont indiqués. Vous pouvez explorer ces fonctionnalités dans votre environnement à l’aide de l’outil global `dotnet try` :

1. Installez l’outil global [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup).
1. Clonez le référentiel [dotnet/try-samples](https://github.com/dotnet/try-samples).
1. Définissez le répertoire actuel sur le sous-répertoire *csharp8* pour le référentiel *try-samples*.
1. Exécutez `dotnet try`.

## <a name="readonly-members"></a>Membres ReadOnly

Vous pouvez appliquer le `readonly` modificateur aux membres d’un struct. Elle indique que le membre ne modifie pas l’État. C’est plus précis que d’appliquer le modificateur `readonly` à une déclaration `struct`.  Examinons le struct mutable suivant :

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

Comme la plupart des structs, la `ToString()` méthode ne modifie pas l’État. Vous pouvez indiquer cela en ajoutant le modificateur `readonly` à la déclaration de `ToString()` :

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

La modification précédente génère un avertissement du compilateur, car `ToString` accède à la `Distance` propriété, qui n’est pas marquée comme `readonly` suit :

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

Le compilateur vous avertit lorsqu’il a besoin de créer une copie défensive.  La `Distance` propriété ne change pas d’État. vous pouvez donc résoudre cet avertissement en ajoutant le `readonly` modificateur à la déclaration :

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

Notez que le `readonly` modificateur est nécessaire sur une propriété en lecture seule. Le compilateur ne suppose pas que les `get` accesseurs ne modifient pas l’état ; vous devez déclarer `readonly` explicitement. Les propriétés implémentées automatiquement sont une exception. le compilateur traite tous les accesseurs get implémentés automatiquement comme. `readonly` il n’est donc pas nécessaire d’ajouter le `readonly` modificateur aux `X` `Y` Propriétés et.

Le compilateur applique la règle qui `readonly` ne modifie pas l’état des membres. La méthode suivante n’est pas compilée, sauf si vous supprimez le `readonly` modificateur :

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

Cette fonctionnalité vous permet de spécifier votre intention de conception, afin que le compilateur puisse l’appliquer et procéder à des optimisations basées sur cette intention.

Pour plus d’informations, consultez la section [ `readonly` membres d’instance](../language-reference/builtin-types/struct.md#readonly-instance-members) de l’article [types de structures](../language-reference/builtin-types/struct.md) .

## <a name="default-interface-methods"></a>Méthodes d’interface par défaut

Vous pouvez désormais ajouter des membres aux interfaces et fournir une implémentation pour ces membres. Cette fonctionnalité de langage permet aux auteurs d’API d’ajouter des méthodes à une interface dans les versions ultérieures sans pour autant nuire à la compatibilité des binaires ou des sources avec les implémentations existantes de cette interface. Les implémentations existantes *héritent* de l’implémentation par défaut. Cette fonctionnalité permet également à C# d’interagir avec les API ciblant Android ou Swift, qui prennent en charge des fonctionnalités similaires. Les méthodes d’interface par défaut permettent également des scénarios semblables à une fonctionnalité de langage « traits ».

Les méthodes d’interface par défaut affectent de nombreux scénarios et éléments de langage. Ce premier tutoriel couvre [la mise à jour d’une interface à l’aide d’implémentations par défaut](../tutorials/default-interface-methods-versions.md). D’autres tutoriels et mises à jour de référence seront disponibles avant le lancement général.

## <a name="more-patterns-in-more-places"></a>Ajout de modèles à différents endroits

Les **critères spéciaux** offrent des outils permettant de produire des fonctionnalités dépendantes de la forme sur des types de données liés mais différents. C# 7,0 a introduit la syntaxe pour les modèles de type et les modèles de constante à l’aide de l' [`is`](../language-reference/keywords/is.md) expression et de l' [`switch`](../language-reference/keywords/switch.md) instruction. Ces fonctionnalités représentaient les premières étapes provisoires de prise en charge de paradigmes de programmation distinguant données et fonctionnalités. Face à la transition du secteur vers de nouveaux microservices et autres architectures cloud, d’autres outils sont nécessaires pour le langage.

C# 8.0 développe ce vocabulaire en offrant la possibilité d’utiliser d’autres expressions de modèle à davantage d’endroits dans le code. Étudiez ces fonctionnalités si vos données et vos fonctionnalités sont séparées. Les critères spéciaux peuvent être intéressants si vos algorithmes dépendent d’un fait autre que le type de runtime d’un objet. Ces techniques représentent un autre moyen d’exprimer des conceptions.

En plus des nouveaux modèles en de nouveaux endroits, C# 8.0 ajoute des **modèles récursifs**. Le résultat d’une expression de modèle est une expression. Un modèle récursif constitue simplement une expression de modèle appliquée à la sortie d’une autre expression de modèle.

### <a name="switch-expressions"></a>Expressions switch

Souvent, une [`switch`](../language-reference/keywords/switch.md) instruction produit une valeur dans chacun de ses `case` blocs. **Les expressions switch** permettent d’utiliser une syntaxe d’expression plus concise, comprenant moins de mots clés `case` et `break` répétitifs et moins d’accolades.  Prenons par exemple l’enum suivant, qui liste les couleurs de l’arc-en-ciel :

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

Le **modèle de propriété** permet de faire correspondre les propriétés de l’objet examiné. Prenons un site d’e-commerce qui doit calculer les taxes sur les ventes en fonction de l’adresse de l’acheteur. Ce calcul n’est pas une responsabilité fondamentale d’une `Address` classe. Il changera au fil du temps, probablement plus souvent que n’évoluera le format de l’adresse. Le montant des taxes sur les ventes varie selon la propriété `State` de l’adresse. La méthode suivante utilise le modèle de propriété pour calculer les taxes sur les ventes à partir de l’adresse et du prix :

```csharp
public static decimal ComputeSalesTax(Address location, decimal salePrice) =>
    location switch
    {
        { State: "WA" } => salePrice * 0.06M,
        { State: "MN" } => salePrice * 0.075M,
        { State: "MI" } => salePrice * 0.05M,
        // other cases removed for brevity...
        _ => 0M
    };
```

Les critères spéciaux offrent une syntaxe concise pour exprimer cet algorithme.

### <a name="tuple-patterns"></a>Modèles de tuples

Certains algorithmes dépendent de plusieurs entrées. Les **modèles de tuples** permettent de basculer des unes aux autres en fonction de plusieurs valeurs exprimées sous forme de [tuple](../language-reference/builtin-types/value-tuples.md).  Le code suivant montre une expression switch pour le jeu *Pierre-papier-ciseaux* :

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

Le modèle discard dans le switch précédent indique une correspondance lorsque soit `x`, soit `y` est égal à 0, mais pas les deux. Une expression switch doit produire une valeur ou, si aucun des cas ne correspond, lever une exception. Le compilateur génère un avertissement pour vous si vous ne traitez pas tous les cas possibles dans votre expression de commutateur.

Vous pouvez explorer des techniques de critères spéciaux dans ce [tutoriel avancé sur les critères spéciaux](../tutorials/pattern-matching.md).

## <a name="using-declarations"></a>Déclarations using

Une **déclaration using** est une déclaration de variable précédée par le mot clé `using`. Elle indique au compilateur que la variable déclarée doit être supprimée à la fin de la portée englobante. Prenons par exemple le code suivant, qui écrit un fichier texte :

```csharp
static int WriteLinesToFile(IEnumerable<string> lines)
{
    using var file = new System.IO.StreamWriter("WriteLines2.txt");
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
    using (var file = new System.IO.StreamWriter("WriteLines2.txt"))
    {
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
        return skippedLines;
    } // file is disposed here
}
```

Dans l’exemple précédent, le fichier est supprimé une fois l’accolade fermante associée à l’instruction `using` atteinte.

Dans les deux cas, le compilateur génère l’appel à `Dispose()`. Le compilateur génère une erreur si l’expression dans l' `using` instruction n’est pas supprimable.

## <a name="static-local-functions"></a>Fonctions locales statiques

Vous pouvez maintenant ajouter le `static` modificateur aux [fonctions locales](../programming-guide/classes-and-structs/local-functions.md) pour vous assurer que la fonction locale ne capture pas (référence) les variables de la portée englobante. Cela génère `CS8421`, « A static local function can't contain a reference to \<variable> ».

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

Un `struct` déclaré avec le `ref` modificateur ne peut pas implémenter d’interfaces et ne peut donc pas implémenter <xref:System.IDisposable> . Par conséquent, pour qu’un `ref struct` soit supprimable, il doit avoir une méthode `void Dispose()` accessible. Cette fonctionnalité s’applique également aux `readonly ref struct` déclarations.

## <a name="nullable-reference-types"></a>Types références Nullables

Dans un contexte d’annotation Nullable, toute variable d’un type référence est considérée comme un **type référence n'acceptant pas la valeur Null**. Si vous souhaitez indiquer qu’une variable peut être Null, ajoutez `?` au nom de type pour la déclarer comme **type référence Nullable**.

Avec les types références n'acceptant pas la valeur Null, le compilateur utilise l’analyse de flux pour que les variables locales soient initialisées à une valeur non Null une fois déclarées. Les champs doivent être initialisés à la construction. Le compilateur génère un avertissement si la variable n’est pas définie par un appel à l’un des constructeurs disponibles ou par un initialiseur. Par ailleurs, les types références n’acceptant pas la valeur Null ne peuvent pas avoir de valeur pouvant être Null.

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

Vous pouvez essayer par vous-même les flux asynchrones dans notre tutoriel [Créer et consommer des flux asynchrones](../tutorials/generate-consume-asynchronous-stream.md). Par défaut, les éléments de flux sont traités dans le contexte capturé. Si vous souhaitez désactiver la capture du contexte, utilisez la <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> méthode d’extension. Pour plus d’informations sur les contextes de synchronisation et la capture du contexte actuel, consultez l’article sur l' [utilisation du modèle asynchrone basé](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)sur des tâches.

## <a name="asynchronous-disposable"></a>Supprimable asynchrone

À compter de C# 8,0, le langage prend en charge les types jetables asynchrones qui implémentent l' <xref:System.IAsyncDisposable?displayProperty=nameWithType> interface. Vous utilisez l' `await using` instruction pour travailler avec un objet supprimé de manière asynchrone. Pour plus d’informations, consultez l’article [mettre en œuvre une méthode DisposeAsync](../../standard/garbage-collection/implementing-disposeasync.md) .

## <a name="indices-and-ranges"></a>Index et plages

Les index et les plages fournissent une syntaxe concise pour accéder à des éléments ou des plages uniques dans une séquence.

Cette prise en charge de langage s’appuie sur deux nouveaux types et deux nouveaux opérateurs :

- <xref:System.Index?displayProperty=nameWithType> représente un index au sein d’une séquence.
- Index de l’opérateur End `^` , qui spécifie qu’un index est relatif à la fin de la séquence.
- <xref:System.Range?displayProperty=nameWithType> représente une sous-plage d’une séquence.
- Opérateur de plage `..` , qui spécifie le début et la fin d’une plage comme opérandes.

Commençons par les règles concernant les index. Prenons pour exemple un tableau `sequence`. L’index `0` est identique à l’index `sequence[0]`. L’index `^0` est identique à l’index `sequence[sequence.Length]`. Notez que `sequence[^0]` lève une exception, tout comme `sequence[sequence.Length]`. Pour n’importe quel nombre `n`, l’index `^n` est identique à l’index `sequence.Length - n`.

Une plage spécifie son *début* et sa *fin*. Le début de la plage est compris, mais la fin de la plage est exclusive, ce qui signifie que le *début* est inclus dans la plage, mais que la *fin* n’est pas incluse dans la plage. La plage `[0..^0]` représente la plage dans son intégralité, tout comme `[0..sequence.Length]` représente la plage entière.

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

Le code suivant crée une sous-plage qui comporte « lazy » et « dog » et comprend `words[^2]` et `words[^1]`. L’index de fin `words[^0]` n’est pas inclus :

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

Non seulement les tableaux prennent en charge les index et les plages. Vous pouvez également utiliser des index et des plages avec [String](../language-reference/builtin-types/reference-types.md#the-string-type), <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601> . Pour plus d’informations, consultez [prise en charge des types d’index et de plages](../tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).

Pour explorer davantage les index et les plages, consultez le tutoriel sur [les index et les plages](../tutorials/ranges-indexes.md).

## <a name="null-coalescing-assignment"></a>Assignation de fusion Null

C# 8,0 introduit l’opérateur d’assignation de fusion Null `??=` . Vous pouvez utiliser l' `??=` opérateur pour assigner la valeur de son opérande droit à son opérande gauche uniquement si l’opérande de gauche prend la valeur `null` .

```csharp
List<int> numbers = null;
int? i = null;

numbers ??= new List<int>();
numbers.Add(i ??= 17);
numbers.Add(i ??= 20);

Console.WriteLine(string.Join(" ", numbers));  // output: 17 17
Console.WriteLine(i);  // output: 17
```

Pour plus d’informations, consultez [les = l’article Operators](../language-reference/operators/null-coalescing-operator.md) .

## <a name="unmanaged-constructed-types"></a>Types construits non managés

En C# 7,3 et versions antérieures, un type construit (un type qui comprend au moins un argument de type) ne peut pas être un [type non managé](../language-reference/builtin-types/unmanaged-types.md). À compter de C# 8,0, un type valeur construit est non managé s’il contient uniquement des champs de types non managés.

Par exemple, étant donné la définition suivante du `Coords<T>` type générique :

```csharp
public struct Coords<T>
{
    public T X;
    public T Y;
}
```

le `Coords<int>` type est un type non managé dans C# 8,0 et versions ultérieures. Comme pour tout type non managé, vous pouvez créer un pointeur vers une variable de ce type ou [allouer un bloc de mémoire sur la pile](../language-reference/operators/stackalloc.md) pour les instances de ce type :

```csharp
Span<Coords<int>> coordinates = stackalloc[]
{
    new Coords<int> { X = 0, Y = 0 },
    new Coords<int> { X = 0, Y = 3 },
    new Coords<int> { X = 4, Y = 0 }
};
```

Pour plus d’informations, consultez [types non managés](../language-reference/builtin-types/unmanaged-types.md).

## <a name="stackalloc-in-nested-expressions"></a>Stackalloc dans les expressions imbriquées

À compter de C# 8,0, si le résultat d’une expression [stackalloc](../language-reference/operators/stackalloc.md) est du <xref:System.Span%601?displayProperty=nameWithType> <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> type ou, vous pouvez utiliser l' `stackalloc` expression dans d’autres expressions :

```csharp
Span<int> numbers = stackalloc[] { 1, 2, 3, 4, 5, 6 };
var ind = numbers.IndexOfAny(stackalloc[] { 2, 4, 6, 8 });
Console.WriteLine(ind);  // output: 1
```

## <a name="enhancement-of-interpolated-verbatim-strings"></a>Amélioration des chaînes textuelles interpolées

L’ordre des `$` `@` jetons et dans les chaînes textuelles [interpolées](../language-reference/tokens/interpolated.md) peut être any : `$@"..."` et `@$"..."` sont des chaînes textuelles interpolées valides. Dans les versions antérieures de C#, le `$` jeton doit apparaître avant le `@` jeton.

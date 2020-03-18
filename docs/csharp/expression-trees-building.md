---
title: Génération d’arborescences d’expressions
description: En savoir plus sur les techniques de génération d’arborescences d’expressions.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 542754a9-7f40-4293-b299-b9f80241902c
ms.openlocfilehash: c93eb16ebf2ff66dc0162afb6841f2cadfce174e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146045"
---
# <a name="building-expression-trees"></a>Génération d’arborescences d’expressions

[Précédent -- Interprétation d’expressions](expression-trees-interpreting.md)

Toutes les arborescences d’expressions que vous avez vues jusqu’ici ont été créées par le compilateur C#. Tout ce que vous aviez à faire était de créer une expression lambda qui était assignée à une variable de type `Expression<Func<T>>` ou d’un type similaire. Ce n’est pas la seule façon de créer une arborescence d’expressions. Dans de nombreux scénarios, vous constaterez peut-être que vous devez générer une expression en mémoire au moment de l’exécution.

La génération d’arborescences d’expressions est compliquée par le fait qu’elles sont immuables. Cela signifie que vous devez générer l’arborescence à partir des feuilles jusqu’à la racine. Les API que vous utiliserez pour générer des arborescences d’expressions reflètent cet état de fait : les méthodes que vous utiliserez pour générer un nœud prennent tous ses enfants en tant qu’arguments. Examinons quelques exemples illustrant les techniques à appliquer.

## <a name="creating-nodes"></a>Création de nœuds

Commençons par quelque chose de relativement simple. Nous allons utiliser l’expression d’addition avec laquelle j’ai travaillé tout au long de ces sections :

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

Pour construire cette arborescence d’expressions, nous devons construire les nœuds terminaux.
Les nœuds terminaux étant des constantes, nous pouvons utiliser la méthode `Expression.Constant` pour créer les nœuds :

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

Ensuite, nous allons générer l’expression d’addition :

```csharp
var addition = Expression.Add(one, two);
```

Après cela, nous pouvons créer l’expression lambda :

```csharp
var lambda = Expression.Lambda(addition);
```

Cette expression lambda est très simple, car elle ne contient aucun argument.
Plus loin dans cette section, nous verrons comment mapper des arguments à des paramètres, et comment générer des expressions plus complexes.

Pour les expressions qui sont aussi simples que celle-ci, nous pouvons combiner tous les appels en une seule instruction :

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a>Génération d’une arborescence

Voilà les principes fondamentaux de génération d’une arborescence d’expressions en mémoire. Les arborescences plus complexes signifient généralement qu’il y a davantage de types de nœuds et davantage de nœuds dans l’arborescence. Examinons un autre exemple et voyons deux autres types de nœuds que vous générerez souvent lors de la création d’arborescences d’expressions : les nœuds d’argument et les nœuds d’appel de méthode.

Commençons par générer une arborescence d’expressions pour créer cette expression :

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```

Nous allons commencer par créer des expressions de paramètre pour `x` et `y` :

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

La création des expressions de multiplication et d’addition suit le modèle que nous avons déjà vu :

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

Ensuite, nous devons créer une expression d’appel de méthode pour l’appel à `Math.Sqrt`.

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

Pour finir, nous plaçons l’appel de méthode dans une expression lambda et nous veillons à définir les arguments de l’expression lambda :

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

Dans cet exemple plus complexe, vous pouvez observer quelques techniques supplémentaires dont vous aurez souvent besoin pour créer des arborescences d’expressions.

Tout d’abord, vous devez créer les objets qui représentent des variables locales ou des paramètres avant de les utiliser. Une fois que vous avez créé ces objets, vous pouvez les utiliser dans votre arborescence d’expressions partout où vous en avez besoin.

Ensuite, vous devez utiliser un sous-ensemble des API de réflexion pour créer un objet `MethodInfo` afin de pouvoir créer une arborescence d’expressions pour accéder à cette méthode. Vous devez vous limiter au sous-ensemble des API de réflexion disponibles sur la plateforme .NET Core. Là encore, ces techniques s’étendront à d’autres arborescences d’expressions.

## <a name="building-code-in-depth"></a>Code de génération en profondeur

Vous n’êtes pas limité dans ce que vous pouvez générer à l’aide de ces API. Toutefois, plus l’arborescence d’expressions que vous souhaitez générer est compliquée, plus le code est difficile à gérer et à lire.

Nous allons générer une arborescence d’expressions qui est l’équivalent de ce code :

```csharp
Func<int, int> factorialFunc = (n) =>
{
    var res = 1;
    while (n > 1)
    {
        res = res * n;
        n--;
    }
    return res;
};
```

Vous remarquerez ci-dessus que je n’ai pas généré l’arborescence d’expressions, mais simplement le délégué. À l’aide de la classe `Expression`, vous ne pouvez pas créer de lambda-instructions. Voici le code nécessaire pour générer la même fonctionnalité. Il est compliqué par le fait qu’il n’existe pas d’API pour générer une boucle `while`. Au lieu de cela, vous devez générer une boucle qui contient un test conditionnel, et une cible d’étiquette pour quitter la boucle.

```csharp
var nArgument = Expression.Parameter(typeof(int), "n");
var result = Expression.Variable(typeof(int), "result");

// Creating a label that represents the return value
LabelTarget label = Expression.Label(typeof(int));

var initializeResult = Expression.Assign(result, Expression.Constant(1));

// This is the inner block that performs the multiplication,
// and decrements the value of 'n'
var block = Expression.Block(
    Expression.Assign(result,
        Expression.Multiply(result, nArgument)),
    Expression.PostDecrementAssign(nArgument)
);

// Creating a method body.
BlockExpression body = Expression.Block(
    new[] { result },
    initializeResult,
    Expression.Loop(
        Expression.IfThenElse(
            Expression.GreaterThan(nArgument, Expression.Constant(1)),
            block,
            Expression.Break(label, result)
        ),
        label
    )
);
```

Le code de génération de l’arborescence d’expressions pour la fonction factorielle est un peu plus long, plus compliqué et truffé d’étiquettes, d’instructions break et d’autres éléments que nous souhaitons éviter lors de nos tâches quotidiennes de codage.

Dans cette section, j’ai également mis à jour le code de visiteur pour visiter tous les nœuds de cette arborescence d’expressions et écrire des informations sur les nœuds créés dans cet exemple. Vous pouvez [afficher ou télécharger l’exemple de code](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) à partir du dépôt GitHub dotnet/docs. Essayez par vous-même en créant et en exécutant les exemples. Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="examining-the-apis"></a>Examen des API

Les API d’arborescence d’expressions comptent parmi les plus difficiles à parcourir dans .NET Core, mais ce n’est pas grave. Leur objectif est plutôt complexe : écrire du code qui génère du code au moment de l’exécution. Elles sont nécessairement compliquées afin de fournir un équilibre entre la prise en charge de toutes les structures de contrôle disponibles en langage C# et la taille de la surface d’exposition des API (qui doit être la plus petite possible). Cet équilibre signifie que de nombreuses structures de contrôle sont représentées non pas par leurs constructions C#, mais par des constructions qui représentent la logique sous-jacente générée par le compilateur à partir de ces constructions de niveau supérieur.

Il existe aussi actuellement des expressions C# qui ne peuvent pas être créées directement à l’aide de méthodes de classe `Expression`. En général, il s’agit des opérateurs et expressions les plus récents ajoutés dans C# 5 et C# 6. (Par exemple, les expressions `async` ne peuvent pas être générées et le nouvel opérateur `?.` ne peut pas être créé directement.)

[Suivant -- Traduction d’expressions](expression-trees-translating.md)

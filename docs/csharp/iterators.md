---
title: Iterators
description: Apprenez à utiliser les itérateurs C# intégrés et à créer vos propres méthodes d’itérateur personnalisées.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 5cf36f45-f91a-4fca-a0b7-87f233e108e9
ms.openlocfilehash: efa755c2243c18fb51b653abccb2bfc702bbc055
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507375"
---
# <a name="iterators"></a>Iterators

Presque chaque programme que vous écrivez doit itérer au sein d’une collection. Vous allez écrire du code qui examine chaque élément d’une collection.

Vous allez également créer des méthodes d’itérateur qui sont des méthodes qui produisent un itérateur (qui est un objet qui traverse un conteneur, en particulier des listes) pour les éléments de cette classe. Vous pouvez les utiliser pour :

+ Effectuer une action sur chaque élément d’une collection.
+ Énumérer une collection personnalisée.
+ Étendre [LINQ](linq/index.md) ou d’autres bibliothèques.
+ Créer un pipeline de données où les données circulent efficacement via des méthodes d’itérateur.

Le langage C# fournit des fonctionnalités pour ces deux scénarios. Cet article présente une vue d’ensemble de ces fonctionnalités.

Ce didacticiel comporte plusieurs étapes. Après chaque étape, vous pourrez exécuter l’application et voir la progression. Vous pouvez également [afficher ou télécharger l’exemple complet](https://github.com/dotnet/samples/blob/master/csharp/iterators) pour cette rubrique. Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="iterating-with-foreach"></a>Itération avec foreach

L’énumération d’une collection est simple : le mot clé `foreach` énumère une collection en exécutant l’instruction incorporée une fois pour chaque élément de la collection :

```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

C’est aussi simple que cela. Pour itérer au sein du contenu d’une collection, l’instruction `foreach` suffit. L’instruction `foreach` n’est cependant pas magique. Elle s’appuie sur deux interfaces génériques définies dans la bibliothèque .NET Core afin de générer le code nécessaire pour itérer au sein d’une collection : `IEnumerable<T>` et `IEnumerator<T>`. Ce mécanisme est expliqué plus en détail ci-dessous.

Ces deux interfaces ont également des contreparties non génériques : `IEnumerable` et `IEnumerator`. Les versions [génériques](programming-guide/generics/index.md) conviennent mieux pour un code moderne.

## <a name="enumeration-sources-with-iterator-methods"></a>Sources d’énumération avec des méthodes d’itérateur

Une autre fonctionnalité intéressante du langage C# vous permet de construire des méthodes qui créent une source pour une énumération. Elles sont appelées *méthodes d’itérateur*. Une méthode d’itérateur définit comment générer les objets dans une séquence sur demande. Vous utilisez les mots clés contextuels `yield return` pour définir une méthode d’itérateur.

Vous pouvez par exemple écrire cette méthode pour produire la séquence d’entiers de 0 à 9 :

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    yield return 0;
    yield return 1;
    yield return 2;
    yield return 3;
    yield return 4;
    yield return 5;
    yield return 6;
    yield return 7;
    yield return 8;
    yield return 9;
}
```

Le code ci-dessus montre des instructions `yield return` distinctes pour mettre en évidence le fait que vous pouvez utiliser plusieurs instructions `yield return` discrètes dans une méthode d’itérateur.
Vous pouvez (et c’est souvent le cas) utiliser d’autres constructions du langage pour simplifier le code d’une méthode d’itérateur. La définition de méthode ci-dessous produit exactement la même séquence de nombres :

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;
}
```

Vous n’êtes pas obligé de choisir l’une ou l’autre. Vous pouvez avoir autant d’instructions `yield return` que nécessaire pour répondre aux besoins de votre méthode :

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;

    yield return 50;

    index = 100;
    while (index < 110)
        yield return index++;
}
```

Il s’agit de la syntaxe de base. Prenons un exemple réel où vous devez écrire une méthode d’itérateur. Imaginez que vous êtes sur un projet IoT et que les capteurs d’un appareil génèrent un flux de données très important. Pour obtenir un aperçu des données, vous pouvez écrire une méthode qui échantillonne les éléments de données à un certain intervalle. Cette petite méthode d’itérateur peut effectuer ce travail :

```csharp
public static IEnumerable<T> Sample(this IEnumerable<T> sourceSequence, int interval)
{
    int index = 0;
    foreach (T item in sourceSequence)
    {
        if (index++ % interval == 0)
            yield return item;
    }
}
```

Il existe une restriction importante sur les méthodes d’itérateur : vous ne pouvez pas avoir à la fois une instruction `return` et une instruction `yield return` dans la même méthode. Ce qui suit ne peut pas être compilé :

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;

    yield return 50;

    // generates a compile time error:
    var items = new int[] {100, 101, 102, 103, 104, 105, 106, 107, 108, 109 };
    return items;
}
```

Cette restriction n’est normalement pas un problème. Vous avez le choix entre utiliser `yield return` dans toute la méthode ou de diviser la méthode d’origine en plusieurs méthodes, certaines utilisant `return` et d’autres utilisant `yield return`.

Vous pouvez modifier légèrement la dernière méthode pour utiliser `yield return` partout :

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;

    yield return 50;

    var items = new int[] {100, 101, 102, 103, 104, 105, 106, 107, 108, 109 };
    foreach (var item in items)
        yield return item;
}
```

Parfois, la bonne réponse est de fractionner une méthode d’itérateur en deux méthodes différentes. Une qui utilise `return` et l’autre qui utilise `yield return`. Considérez une situation où vous voulez retourner une collection vide, ou bien les 5 premiers nombres impairs, en vous basant sur un argument booléen. Vous pouvez écrire ceci sous la forme de ces deux méthodes :

```csharp
public IEnumerable<int> GetSingleDigitOddNumbers(bool getCollection)
{
    if (getCollection == false)
        return new int[0];
    else
        return IteratorMethod();
}

private IEnumerable<int> IteratorMethod()
{
    int index = 0;
    while (index < 10)
    {
        if (index % 2 == 1)
            yield return index;
        index++;
    }
}
```

Examinez les méthodes ci-dessus. La première utilise l’instruction `return` standard pour retourner une collection vide ou l’itérateur créé par la deuxième méthode. La deuxième méthode utilise l’instruction `yield return` pour créer la séquence demandée.

## <a name="deeper-dive-into-foreach"></a>Aller plus loin avec `foreach`

L’instruction `foreach` se développe en un idiome standard qui utilise les interfaces `IEnumerable<T>` et `IEnumerator<T>` pour itérer à travers tous les éléments d’une collection. Elle réduit également les erreurs que font les développeurs en ne gérant pas correctement les ressources.

Le compilateur traduit la boucle `foreach` présentée dans le premier exemple en quelque chose de similaire à cette construction :

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

La construction ci-dessus représente le code généré par le compilateur C# dans la version 5 et ultérieure. Avant la version 5, la variable `item` avait une étendue différente :

```csharp
// C# versions 1 through 4:
IEnumerator<int> enumerator = collection.GetEnumerator();
int item = default(int);
while (enumerator.MoveNext())
{
    item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

Ceci a été changé, car le comportement antérieur pouvait entraîner des bogues subtils et difficiles à diagnostiquer impliquant des expressions lambda. Pour plus d’informations sur les expressions lambda, voir [Expressions lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md).

Le code exact généré par le compilateur est un peu plus compliqué et gère les cas où l’objet retourné par `GetEnumerator()` implémente l’interface `IDisposable`. L’expansion complète génère un code qui ressemble davantage à celui-ci :

```csharp
{
    var enumerator = collection.GetEnumerator();
    try
    {
        while (enumerator.MoveNext())
        {
            var item = enumerator.Current;
            Console.WriteLine(item.ToString());
        }
    } finally
    {
        // dispose of enumerator.
    }
}
```

La manière dont l’énumérateur est éliminé dépend des caractéristiques du type d’`enumerator`. En règle générale, la clause `finally` se développe en :

```csharp
finally
{
   (enumerator as IDisposable)?.Dispose();
}
```

Cependant, si le type d’`enumerator` est un type sealed et qu’il n’existe pas de conversion implicite du type d’`enumerator` en `IDisposable`, la clause `finally` se développe en un bloc vide :

```csharp
finally
{
}
```

S’il existe une conversion implicite du type d’`enumerator` en `IDisposable` et si `enumerator` est un type valeur qui n’autorise pas les valeurs Null, la clause `finally` se développe en :

```csharp
finally
{
   ((IDisposable)enumerator).Dispose();
}
```

Heureusement, vous n’avez pas besoin de mémoriser tous ces détails. L’instruction `foreach` gère toutes ces subtilités pour vous. Le compilateur génère le code correct pour toutes ces constructions.

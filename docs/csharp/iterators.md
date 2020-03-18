---
title: Iterators
description: Apprenez à utiliser les itérateurs C# intégrés et à créer vos propres méthodes d’itérateur personnalisées.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 5cf36f45-f91a-4fca-a0b7-87f233e108e9
ms.openlocfilehash: 1933ecf83e9fa234f9b88c815d8ab527997c97f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399615"
---
# <a name="iterators"></a><span data-ttu-id="e98e1-103">Iterators</span><span class="sxs-lookup"><span data-stu-id="e98e1-103">Iterators</span></span>

<span data-ttu-id="e98e1-104">Presque chaque programme que vous écrivez doit itérer au sein d’une collection.</span><span class="sxs-lookup"><span data-stu-id="e98e1-104">Almost every program you write will have some need to iterate over a collection.</span></span> <span data-ttu-id="e98e1-105">Vous allez écrire du code qui examine chaque élément d’une collection.</span><span class="sxs-lookup"><span data-stu-id="e98e1-105">You'll write code that examines every item in a collection.</span></span>

<span data-ttu-id="e98e1-106">Vous allez également créer des méthodes d’itérateur, qui sont des méthodes produisant un itérateur pour les éléments de cette classe.</span><span class="sxs-lookup"><span data-stu-id="e98e1-106">You'll also create iterator methods which are methods that produces an iterator for the elements of that class.</span></span> <span data-ttu-id="e98e1-107">Vous pouvez les utiliser pour :</span><span class="sxs-lookup"><span data-stu-id="e98e1-107">These can be used for:</span></span>

+ <span data-ttu-id="e98e1-108">Effectuer une action sur chaque élément d’une collection.</span><span class="sxs-lookup"><span data-stu-id="e98e1-108">Performing an action on each item in a collection.</span></span>
+ <span data-ttu-id="e98e1-109">Énumérer une collection personnalisée.</span><span class="sxs-lookup"><span data-stu-id="e98e1-109">Enumerating a custom collection.</span></span>
+ <span data-ttu-id="e98e1-110">Étendre [LINQ](linq/index.md) ou d’autres bibliothèques.</span><span class="sxs-lookup"><span data-stu-id="e98e1-110">Extending [LINQ](linq/index.md) or other libraries.</span></span>
+ <span data-ttu-id="e98e1-111">Créer un pipeline de données où les données circulent efficacement via des méthodes d’itérateur.</span><span class="sxs-lookup"><span data-stu-id="e98e1-111">Creating a data pipeline where data flows efficiently through iterator methods.</span></span>

<span data-ttu-id="e98e1-112">Le langage C# fournit des fonctionnalités pour ces deux scénarios.</span><span class="sxs-lookup"><span data-stu-id="e98e1-112">The C# language provides features for both these scenarios.</span></span> <span data-ttu-id="e98e1-113">Cet article présente une vue d’ensemble de ces fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="e98e1-113">This article provides an overview of those features.</span></span>

<span data-ttu-id="e98e1-114">Ce didacticiel comporte plusieurs étapes.</span><span class="sxs-lookup"><span data-stu-id="e98e1-114">This tutorial has multiple steps.</span></span> <span data-ttu-id="e98e1-115">Après chaque étape, vous pourrez exécuter l’application et voir la progression.</span><span class="sxs-lookup"><span data-stu-id="e98e1-115">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="e98e1-116">Vous pouvez également [afficher ou télécharger l’exemple complet](https://github.com/dotnet/samples/blob/master/csharp/iterators) pour cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="e98e1-116">You can also [view or download the completed sample](https://github.com/dotnet/samples/blob/master/csharp/iterators) for this topic.</span></span> <span data-ttu-id="e98e1-117">Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="e98e1-117">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="iterating-with-foreach"></a><span data-ttu-id="e98e1-118">Itération avec foreach</span><span class="sxs-lookup"><span data-stu-id="e98e1-118">Iterating with foreach</span></span>

<span data-ttu-id="e98e1-119">L’énumération d’une collection est simple : le mot clé `foreach` énumère une collection en exécutant l’instruction incorporée une fois pour chaque élément de la collection :</span><span class="sxs-lookup"><span data-stu-id="e98e1-119">Enumerating a collection is simple: The `foreach` keyword enumerates a collection, executing the embedded statement once for each element in the collection:</span></span>

```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="e98e1-120">C’est aussi simple que cela.</span><span class="sxs-lookup"><span data-stu-id="e98e1-120">That's all there is to it.</span></span> <span data-ttu-id="e98e1-121">Pour itérer au sein du contenu d’une collection, l’instruction `foreach` suffit.</span><span class="sxs-lookup"><span data-stu-id="e98e1-121">To iterate over all the contents of a collection, the `foreach` statement is all you need.</span></span> <span data-ttu-id="e98e1-122">L’instruction `foreach` n’est cependant pas magique.</span><span class="sxs-lookup"><span data-stu-id="e98e1-122">The `foreach` statement isn't magic, though.</span></span> <span data-ttu-id="e98e1-123">Elle s’appuie sur deux interfaces génériques définies dans la bibliothèque .NET Core afin de générer le code nécessaire pour itérer au sein d’une collection : `IEnumerable<T>` et `IEnumerator<T>`.</span><span class="sxs-lookup"><span data-stu-id="e98e1-123">It relies on two generic interfaces defined in the .NET core library in order to generate the code necessary to iterate a collection: `IEnumerable<T>` and `IEnumerator<T>`.</span></span> <span data-ttu-id="e98e1-124">Ce mécanisme est expliqué plus en détail ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="e98e1-124">This mechanism is explained in more detail below.</span></span>

<span data-ttu-id="e98e1-125">Ces deux interfaces ont également des contreparties non génériques : `IEnumerable` et `IEnumerator`.</span><span class="sxs-lookup"><span data-stu-id="e98e1-125">Both of these interfaces also have non-generic counterparts: `IEnumerable` and `IEnumerator`.</span></span> <span data-ttu-id="e98e1-126">Les versions [génériques](programming-guide/generics/index.md) conviennent mieux pour un code moderne.</span><span class="sxs-lookup"><span data-stu-id="e98e1-126">The [generic](programming-guide/generics/index.md) versions are preferred for modern code.</span></span>

## <a name="enumeration-sources-with-iterator-methods"></a><span data-ttu-id="e98e1-127">Sources d’énumération avec des méthodes d’itérateur</span><span class="sxs-lookup"><span data-stu-id="e98e1-127">Enumeration sources with iterator methods</span></span>

<span data-ttu-id="e98e1-128">Une autre fonctionnalité intéressante du langage C# vous permet de construire des méthodes qui créent une source pour une énumération.</span><span class="sxs-lookup"><span data-stu-id="e98e1-128">Another great feature of the C# language enables you to build methods that create a source for an enumeration.</span></span> <span data-ttu-id="e98e1-129">Elles sont appelées *méthodes d’itérateur*.</span><span class="sxs-lookup"><span data-stu-id="e98e1-129">These are referred to as *iterator methods*.</span></span> <span data-ttu-id="e98e1-130">Une méthode d’itérateur définit comment générer les objets dans une séquence sur demande.</span><span class="sxs-lookup"><span data-stu-id="e98e1-130">An iterator method defines how to generate the objects in a sequence when requested.</span></span> <span data-ttu-id="e98e1-131">Vous utilisez les mots clés contextuels `yield return` pour définir une méthode d’itérateur.</span><span class="sxs-lookup"><span data-stu-id="e98e1-131">You use the `yield return` contextual keywords to define an iterator method.</span></span>

<span data-ttu-id="e98e1-132">Vous pouvez par exemple écrire cette méthode pour produire la séquence d’entiers de 0 à 9 :</span><span class="sxs-lookup"><span data-stu-id="e98e1-132">You could write this method to produce the sequence of integers from 0 through 9:</span></span>

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

<span data-ttu-id="e98e1-133">Le code ci-dessus montre des instructions `yield return` distinctes pour mettre en évidence le fait que vous pouvez utiliser plusieurs instructions `yield return` discrètes dans une méthode d’itérateur.</span><span class="sxs-lookup"><span data-stu-id="e98e1-133">The code above shows distinct `yield return` statements to highlight the fact that you can use multiple discrete `yield return` statements in an iterator method.</span></span>
<span data-ttu-id="e98e1-134">Vous pouvez (et c’est souvent le cas) utiliser d’autres constructions du langage pour simplifier le code d’une méthode d’itérateur.</span><span class="sxs-lookup"><span data-stu-id="e98e1-134">You can (and often do) use other language constructs to simplify the code of an iterator method.</span></span> <span data-ttu-id="e98e1-135">La définition de méthode ci-dessous produit exactement la même séquence de nombres :</span><span class="sxs-lookup"><span data-stu-id="e98e1-135">The method definition below produces the exact same sequence of numbers:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;
}
```

<span data-ttu-id="e98e1-136">Vous n’êtes pas obligé de choisir l’une ou l’autre.</span><span class="sxs-lookup"><span data-stu-id="e98e1-136">You don't have to decide one or the other.</span></span> <span data-ttu-id="e98e1-137">Vous pouvez avoir autant d’instructions `yield return` que nécessaire pour répondre aux besoins de votre méthode :</span><span class="sxs-lookup"><span data-stu-id="e98e1-137">You can have as many `yield return` statements as necessary to meet the needs of your method:</span></span>

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

<span data-ttu-id="e98e1-138">Il s’agit de la syntaxe de base.</span><span class="sxs-lookup"><span data-stu-id="e98e1-138">That's the basic syntax.</span></span> <span data-ttu-id="e98e1-139">Prenons un exemple réel où vous devez écrire une méthode d’itérateur.</span><span class="sxs-lookup"><span data-stu-id="e98e1-139">Let's consider a real world example where you would write an iterator method.</span></span> <span data-ttu-id="e98e1-140">Imaginez que vous êtes sur un projet IoT et que les capteurs d’un appareil génèrent un flux de données très important.</span><span class="sxs-lookup"><span data-stu-id="e98e1-140">Imagine you're on an IoT project and the device sensors generate a very large stream of data.</span></span> <span data-ttu-id="e98e1-141">Pour obtenir un aperçu des données, vous pouvez écrire une méthode qui échantillonne les éléments de données à un certain intervalle.</span><span class="sxs-lookup"><span data-stu-id="e98e1-141">To get a feel for the data, you might write a method that samples every Nth data element.</span></span> <span data-ttu-id="e98e1-142">Cette petite méthode d’itérateur peut effectuer ce travail :</span><span class="sxs-lookup"><span data-stu-id="e98e1-142">This small iterator method does the trick:</span></span>

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

<span data-ttu-id="e98e1-143">Il existe une restriction importante sur les méthodes d’itérateur : vous ne pouvez pas avoir à la fois une instruction `return` et une instruction `yield return` dans la même méthode.</span><span class="sxs-lookup"><span data-stu-id="e98e1-143">There is one important restriction on iterator methods: you can't have both a `return` statement and a `yield return` statement in the same method.</span></span> <span data-ttu-id="e98e1-144">Ce qui suit ne peut pas être compilé :</span><span class="sxs-lookup"><span data-stu-id="e98e1-144">The following will not compile:</span></span>

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

<span data-ttu-id="e98e1-145">Cette restriction n’est normalement pas un problème.</span><span class="sxs-lookup"><span data-stu-id="e98e1-145">This restriction normally isn't a problem.</span></span> <span data-ttu-id="e98e1-146">Vous avez le choix entre utiliser `yield return` dans toute la méthode ou de diviser la méthode d’origine en plusieurs méthodes, certaines utilisant `return` et d’autres utilisant `yield return`.</span><span class="sxs-lookup"><span data-stu-id="e98e1-146">You have a choice of either using `yield return` throughout the method, or separating the original method into multiple methods, some using `return`, and some using `yield return`.</span></span>

<span data-ttu-id="e98e1-147">Vous pouvez modifier légèrement la dernière méthode pour utiliser `yield return` partout :</span><span class="sxs-lookup"><span data-stu-id="e98e1-147">You can modify the last method slightly to use `yield return` everywhere:</span></span>

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

<span data-ttu-id="e98e1-148">Parfois, la bonne réponse est de fractionner une méthode d’itérateur en deux méthodes différentes.</span><span class="sxs-lookup"><span data-stu-id="e98e1-148">Sometimes, the right answer is to split an iterator method into two different methods.</span></span> <span data-ttu-id="e98e1-149">Une qui utilise `return` et l’autre qui utilise `yield return`.</span><span class="sxs-lookup"><span data-stu-id="e98e1-149">One that uses `return`, and a second that uses `yield return`.</span></span> <span data-ttu-id="e98e1-150">Considérez une situation où vous voulez retourner une collection vide, ou bien les 5 premiers nombres impairs, en vous basant sur un argument booléen.</span><span class="sxs-lookup"><span data-stu-id="e98e1-150">Consider a situation where you might want to return an empty collection, or the first 5 odd numbers, based on a boolean argument.</span></span> <span data-ttu-id="e98e1-151">Vous pouvez écrire ceci sous la forme de ces deux méthodes :</span><span class="sxs-lookup"><span data-stu-id="e98e1-151">You could write that as these two methods:</span></span>

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

<span data-ttu-id="e98e1-152">Examinez les méthodes ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="e98e1-152">Look at the methods above.</span></span> <span data-ttu-id="e98e1-153">La première utilise l’instruction `return` standard pour retourner une collection vide ou l’itérateur créé par la deuxième méthode.</span><span class="sxs-lookup"><span data-stu-id="e98e1-153">The first uses the standard `return` statement to return either an empty collection, or the iterator created by the second method.</span></span> <span data-ttu-id="e98e1-154">La deuxième méthode utilise l’instruction `yield return` pour créer la séquence demandée.</span><span class="sxs-lookup"><span data-stu-id="e98e1-154">The second method uses the `yield return` statement to create the requested sequence.</span></span>

## <a name="deeper-dive-into-foreach"></a><span data-ttu-id="e98e1-155">Aller plus loin avec `foreach`</span><span class="sxs-lookup"><span data-stu-id="e98e1-155">Deeper Dive into `foreach`</span></span>

<span data-ttu-id="e98e1-156">L’instruction `foreach` se développe en un idiome standard qui utilise les interfaces `IEnumerable<T>` et `IEnumerator<T>` pour itérer à travers tous les éléments d’une collection.</span><span class="sxs-lookup"><span data-stu-id="e98e1-156">The `foreach` statement expands into a standard idiom that uses the `IEnumerable<T>` and `IEnumerator<T>` interfaces to iterate across all elements of a collection.</span></span> <span data-ttu-id="e98e1-157">Elle réduit également les erreurs que font les développeurs en ne gérant pas correctement les ressources.</span><span class="sxs-lookup"><span data-stu-id="e98e1-157">It also  minimizes errors developers make by not properly managing resources.</span></span>

<span data-ttu-id="e98e1-158">Le compilateur traduit la boucle `foreach` présentée dans le premier exemple en quelque chose de similaire à cette construction :</span><span class="sxs-lookup"><span data-stu-id="e98e1-158">The compiler translates the `foreach` loop shown in the first example into something similar to this construct:</span></span>

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="e98e1-159">La construction ci-dessus représente le code généré par le compilateur C# dans la version 5 et ultérieure.</span><span class="sxs-lookup"><span data-stu-id="e98e1-159">The construct above represents the code generated by the C# compiler as of version 5 and above.</span></span> <span data-ttu-id="e98e1-160">Avant la version 5, la variable `item` avait une étendue différente :</span><span class="sxs-lookup"><span data-stu-id="e98e1-160">Prior to version 5, the `item` variable had a different scope:</span></span>

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

<span data-ttu-id="e98e1-161">Ceci a été changé, car le comportement antérieur pouvait entraîner des bogues subtils et difficiles à diagnostiquer impliquant des expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="e98e1-161">This was changed because the earlier behavior could lead to subtle and hard to diagnose bugs involving lambda expressions.</span></span> <span data-ttu-id="e98e1-162">Pour plus d’informations sur les expressions lambda, voir [Expressions lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="e98e1-162">For more information about lambda expressions, see [Lambda expressions](./programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

<span data-ttu-id="e98e1-163">Le code exact généré par le compilateur est un peu plus compliqué et gère les cas où l’objet retourné par `GetEnumerator()` implémente l’interface `IDisposable`.</span><span class="sxs-lookup"><span data-stu-id="e98e1-163">The exact code generated by the compiler is somewhat more complicated, and handles situations where the object returned by `GetEnumerator()` implements the `IDisposable` interface.</span></span> <span data-ttu-id="e98e1-164">L’expansion complète génère un code qui ressemble davantage à celui-ci :</span><span class="sxs-lookup"><span data-stu-id="e98e1-164">The full expansion generates code more like this:</span></span>

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

<span data-ttu-id="e98e1-165">La manière dont l’énumérateur est éliminé dépend des caractéristiques du type d’`enumerator`.</span><span class="sxs-lookup"><span data-stu-id="e98e1-165">The manner in which the enumerator is disposed of depends on the characteristics of the type of `enumerator`.</span></span> <span data-ttu-id="e98e1-166">En règle générale, la clause `finally` se développe en :</span><span class="sxs-lookup"><span data-stu-id="e98e1-166">In the general case, the `finally` clause expands to:</span></span>

```csharp
finally
{
   (enumerator as IDisposable)?.Dispose();
}
```

<span data-ttu-id="e98e1-167">Cependant, si le type d’`enumerator` est un type sealed et qu’il n’existe pas de conversion implicite du type d’`enumerator` en `IDisposable`, la clause `finally` se développe en un bloc vide :</span><span class="sxs-lookup"><span data-stu-id="e98e1-167">However, if the type of `enumerator` is a sealed type and there is no implicit conversion from the type of `enumerator` to `IDisposable`, the `finally` clause expands to an empty block:</span></span>

```csharp
finally
{
}
```

<span data-ttu-id="e98e1-168">S’il existe une conversion implicite du type d’`enumerator` en `IDisposable` et si `enumerator` est un type valeur qui n’autorise pas les valeurs Null, la clause `finally` se développe en :</span><span class="sxs-lookup"><span data-stu-id="e98e1-168">If there is an implicit conversion from the type of `enumerator` to `IDisposable`, and `enumerator` is a non-nullable value type, the `finally` clause expands to:</span></span>

```csharp
finally
{
   ((IDisposable)enumerator).Dispose();
}
```

<span data-ttu-id="e98e1-169">Heureusement, vous n’avez pas besoin de mémoriser tous ces détails.</span><span class="sxs-lookup"><span data-stu-id="e98e1-169">Thankfully, you don't need to remember all these details.</span></span> <span data-ttu-id="e98e1-170">L’instruction `foreach` gère toutes ces subtilités pour vous.</span><span class="sxs-lookup"><span data-stu-id="e98e1-170">The `foreach` statement handles all those nuances for you.</span></span> <span data-ttu-id="e98e1-171">Le compilateur génère le code correct pour toutes ces constructions.</span><span class="sxs-lookup"><span data-stu-id="e98e1-171">The compiler will generate the correct code for any of these constructs.</span></span>

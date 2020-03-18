---
title: Comment ajouter des méthodes personnalisées pour les requêtes LINQ (C)
ms.date: 07/20/2015
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: e16175d3332b6ce36458eaa78af093e4f8772723
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141472"
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a><span data-ttu-id="67e32-102">Comment ajouter des méthodes personnalisées pour les requêtes LINQ (C)</span><span class="sxs-lookup"><span data-stu-id="67e32-102">How to add custom methods for LINQ queries (C#)</span></span>

<span data-ttu-id="67e32-103">Vous pouvez étendre l’ensemble de méthodes que vous pouvez utiliser pour les requêtes LINQ en ajoutant des méthodes d’extension à l’interface <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="67e32-103">You can extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="67e32-104">Par exemple, en plus des opérations standard d’obtention de valeur moyenne et maximale, vous pouvez créer une méthode d’agrégation personnalisée pour calculer une valeur unique à partir d’une séquence de valeurs.</span><span class="sxs-lookup"><span data-stu-id="67e32-104">For example, in addition to the standard average or maximum operations, you can create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="67e32-105">Vous pouvez également créer une méthode qui fonctionne comme un filtre personnalisé ou une transformation de données pour une séquence de valeurs, et qui retourne une nouvelle séquence.</span><span class="sxs-lookup"><span data-stu-id="67e32-105">You can also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="67e32-106"><xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A> et <xref:System.Linq.Enumerable.Reverse%2A> en sont quelques exemples.</span><span class="sxs-lookup"><span data-stu-id="67e32-106">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>

<span data-ttu-id="67e32-107">Quand vous étendez l’interface <xref:System.Collections.Generic.IEnumerable%601>, vous pouvez appliquer vos méthodes personnalisées à n’importe quelle collection énumérable.</span><span class="sxs-lookup"><span data-stu-id="67e32-107">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="67e32-108">Pour plus d’informations, consultez [Méthodes d’extension](../../classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="67e32-108">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span>

## <a name="adding-an-aggregate-method"></a><span data-ttu-id="67e32-109">Utilisation d’une méthode d’agrégation</span><span class="sxs-lookup"><span data-stu-id="67e32-109">Adding an Aggregate Method</span></span>

<span data-ttu-id="67e32-110">Une méthode d’agrégation calcule une valeur à partir d’un ensemble de valeurs.</span><span class="sxs-lookup"><span data-stu-id="67e32-110">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="67e32-111">LINQ fournit plusieurs méthodes d’agrégation, notamment <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A> et <xref:System.Linq.Enumerable.Max%2A>.</span><span class="sxs-lookup"><span data-stu-id="67e32-111">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="67e32-112">Vous pouvez créer votre propre méthode d’agrégation en ajoutant une méthode d’extension à l’interface <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="67e32-112">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="67e32-113">L’exemple de code suivant montre comment créer une méthode d’extension appelée `Median` pour calculer une valeur médiane pour une séquence de nombres de type `double`.</span><span class="sxs-lookup"><span data-stu-id="67e32-113">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>

```csharp
public static class LINQExtension
{
    public static double Median(this IEnumerable<double> source)
    {
        if (source.Count() == 0)
        {
            throw new InvalidOperationException("Cannot compute median for an empty set.");
        }

        var sortedList = from number in source
                         orderby number
                         select number;

        int itemIndex = (int)sortedList.Count() / 2;

        if (sortedList.Count() % 2 == 0)
        {
            // Even number of items.
            return (sortedList.ElementAt(itemIndex) + sortedList.ElementAt(itemIndex - 1)) / 2;
        }
        else
        {
            // Odd number of items.
            return sortedList.ElementAt(itemIndex);
        }
    }
}
```

<span data-ttu-id="67e32-114">Vous appelez cette méthode d’extension pour toute collection énumérable de la même façon que vous appelez d’autres méthodes d’agrégation depuis l’interface <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="67e32-114">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="67e32-115">L’exemple de code suivant montre comment utiliser la méthode `Median` pour un tableau de type `double`.</span><span class="sxs-lookup"><span data-stu-id="67e32-115">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>

```csharp
double[] numbers1 = { 1.9, 2, 8, 4, 5.7, 6, 7.2, 0 };

var query1 = numbers1.Median();

Console.WriteLine("double: Median = " + query1);
```

```csharp
/*
 This code produces the following output:

 Double: Median = 4.85
*/
```

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="67e32-116">Surcharge d’une méthode d’agrégation pour accepter différents types</span><span class="sxs-lookup"><span data-stu-id="67e32-116">Overloading an Aggregate Method to Accept Various Types</span></span>

<span data-ttu-id="67e32-117">Vous pouvez surcharger votre méthode d’agrégation pour qu’elle accepte des séquences de différents types.</span><span class="sxs-lookup"><span data-stu-id="67e32-117">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="67e32-118">L’approche standard consiste à créer une surcharge pour chaque type.</span><span class="sxs-lookup"><span data-stu-id="67e32-118">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="67e32-119">Une autre approche consiste à créer une surcharge qui accepte un type générique et le convertit en un autre type à l’aide d’un délégué.</span><span class="sxs-lookup"><span data-stu-id="67e32-119">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="67e32-120">Vous pouvez également combiner ces deux approches.</span><span class="sxs-lookup"><span data-stu-id="67e32-120">You can also combine both approaches.</span></span>

#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="67e32-121">Pour créer une surcharge pour chaque type</span><span class="sxs-lookup"><span data-stu-id="67e32-121">To create an overload for each type</span></span>

<span data-ttu-id="67e32-122">Vous pouvez créer une surcharge pour chacun des types que vous voulez prendre en charge.</span><span class="sxs-lookup"><span data-stu-id="67e32-122">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="67e32-123">L’exemple de code suivant montre une surcharge de la méthode `Median` pour le type `integer`.</span><span class="sxs-lookup"><span data-stu-id="67e32-123">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>

```csharp
//int overload

public static double Median(this IEnumerable<int> source)
{
    return (from num in source select (double)num).Median();
}
```

<span data-ttu-id="67e32-124">Vous pouvez maintenant appeler les surcharges `Median` pour les types `integer` et `double`, comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="67e32-124">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>

```csharp
double[] numbers1 = { 1.9, 2, 8, 4, 5.7, 6, 7.2, 0 };

var query1 = numbers1.Median();

Console.WriteLine("double: Median = " + query1);
```

```csharp
int[] numbers2 = { 1, 2, 3, 4, 5 };

var query2 = numbers2.Median();

Console.WriteLine("int: Median = " + query2);
```

```csharp
/*
 This code produces the following output:

 Double: Median = 4.85
 Integer: Median = 3
*/
```

#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="67e32-125">Pour créer une surcharge générique</span><span class="sxs-lookup"><span data-stu-id="67e32-125">To create a generic overload</span></span>

<span data-ttu-id="67e32-126">Vous pouvez également créer une surcharge qui accepte une séquence d’objets génériques.</span><span class="sxs-lookup"><span data-stu-id="67e32-126">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="67e32-127">Cette surcharge prend un délégué comme paramètre et l’utilise pour convertir une séquence d’objets de type générique en un autre type d’objets.</span><span class="sxs-lookup"><span data-stu-id="67e32-127">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>

<span data-ttu-id="67e32-128">Le code suivant montre une surcharge de la méthode `Median` qui prend le délégué <xref:System.Func%602> comme paramètre.</span><span class="sxs-lookup"><span data-stu-id="67e32-128">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="67e32-129">Ce délégué prend un objet de type générique T et retourne un objet de type `double`.</span><span class="sxs-lookup"><span data-stu-id="67e32-129">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>

```csharp
// Generic overload.

public static double Median<T>(this IEnumerable<T> numbers,
                       Func<T, double> selector)
{
    return (from num in numbers select selector(num)).Median();
}
```

<span data-ttu-id="67e32-130">Vous pouvez maintenant appeler la méthode `Median` pour une séquence d’objets de tout type.</span><span class="sxs-lookup"><span data-stu-id="67e32-130">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="67e32-131">Si le type n’a pas sa propre surcharge de méthode, vous devez passer un paramètre délégué.</span><span class="sxs-lookup"><span data-stu-id="67e32-131">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="67e32-132">En C#, vous pouvez utiliser une expression lambda à cet effet.</span><span class="sxs-lookup"><span data-stu-id="67e32-132">In C#, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="67e32-133">En outre, en Visual Basic uniquement, si vous utilisez la clause `Aggregate` ou `Group By` au lieu de l’appel de méthode, vous pouvez passer n’importe quelle valeur ou expression qui se trouve dans la portée de cette clause.</span><span class="sxs-lookup"><span data-stu-id="67e32-133">Also, in Visual Basic only, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>

<span data-ttu-id="67e32-134">L’exemple de code suivant montre comment appeler la méthode `Median` pour un tableau d’entiers et un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="67e32-134">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="67e32-135">Pour les chaînes, c’est la valeur médiane des longueurs de chaînes du tableau qui est calculée.</span><span class="sxs-lookup"><span data-stu-id="67e32-135">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="67e32-136">L’exemple montre comment passer le paramètre de délégué <xref:System.Func%602> à la méthode `Median` pour chaque cas.</span><span class="sxs-lookup"><span data-stu-id="67e32-136">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>

```csharp
int[] numbers3 = { 1, 2, 3, 4, 5 };

/*
  You can use the num=>num lambda expression as a parameter for the Median method
  so that the compiler will implicitly convert its value to double.
  If there is no implicit conversion, the compiler will display an error message.
*/

var query3 = numbers3.Median(num => num);

Console.WriteLine("int: Median = " + query3);

string[] numbers4 = { "one", "two", "three", "four", "five" };

// With the generic overload, you can also use numeric properties of objects.

var query4 = numbers4.Median(str => str.Length);

Console.WriteLine("String: Median = " + query4);

/*
 This code produces the following output:

 Integer: Median = 3
 String: Median = 4
*/
```

## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="67e32-137">Ajout d’une méthode qui retourne une collection</span><span class="sxs-lookup"><span data-stu-id="67e32-137">Adding a Method That Returns a Collection</span></span>

<span data-ttu-id="67e32-138">Vous pouvez étendre l’interface <xref:System.Collections.Generic.IEnumerable%601> avec une méthode de requête personnalisée qui retourne une séquence de valeurs.</span><span class="sxs-lookup"><span data-stu-id="67e32-138">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="67e32-139">Dans ce cas, la méthode doit retourner une collection de type <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="67e32-139">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="67e32-140">Ces méthodes peuvent être utilisées pour appliquer des filtres ou des transformations de données à une séquence de valeurs.</span><span class="sxs-lookup"><span data-stu-id="67e32-140">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>

<span data-ttu-id="67e32-141">L’exemple suivant montre comment créer une méthode d’extension nommée `AlternateElements` qui retourne un élément sur deux d’une collection, en commençant par le premier élément.</span><span class="sxs-lookup"><span data-stu-id="67e32-141">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>

```csharp
// Extension method for the IEnumerable<T> interface.
// The method returns every other element of a sequence.

public static IEnumerable<T> AlternateElements<T>(this IEnumerable<T> source)
{
    List<T> list = new List<T>();

    int i = 0;

    foreach (var element in source)
    {
        if (i % 2 == 0)
        {
            list.Add(element);
        }

        i++;
    }

    return list;
}
```

<span data-ttu-id="67e32-142">Vous pouvez appeler cette méthode d’extension pour n’importe quelle collection énumérable, de la même façon que vous appelez d’autres méthodes depuis l’interface <xref:System.Collections.Generic.IEnumerable%601>, comme le montre le code suivant :</span><span class="sxs-lookup"><span data-stu-id="67e32-142">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>

```csharp
string[] strings = { "a", "b", "c", "d", "e" };

var query = strings.AlternateElements();

foreach (var element in query)
{
    Console.WriteLine(element);
}
/*
 This code produces the following output:

 a
 c
 e
*/
```

## <a name="see-also"></a><span data-ttu-id="67e32-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67e32-143">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="67e32-144">Méthodes d’extension</span><span class="sxs-lookup"><span data-stu-id="67e32-144">Extension Methods</span></span>](../../classes-and-structs/extension-methods.md)

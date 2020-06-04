---
title: 'Procédure : ajouter des méthodes personnalisées pour les requêtes LINQ'
ms.date: 07/20/2015
ms.assetid: 099b2e2a-83cd-45c6-aa4d-01b398b5faaf
ms.openlocfilehash: 55004441d2d1d74556da6841f28d113b876d1048
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400602"
---
# <a name="how-to-add-custom-methods-for-linq-queries-visual-basic"></a><span data-ttu-id="bdd86-102">Comment : ajouter des méthodes personnalisées pour les requêtes LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bdd86-102">How to: Add Custom Methods for LINQ Queries (Visual Basic)</span></span>

<span data-ttu-id="bdd86-103">Vous pouvez étendre l’ensemble de méthodes que vous pouvez utiliser pour les requêtes LINQ en ajoutant des méthodes d’extension à l’interface <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="bdd86-103">You can extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="bdd86-104">Par exemple, en plus des opérations standard d’obtention de valeur moyenne et maximale, vous pouvez créer une méthode d’agrégation personnalisée pour calculer une valeur unique à partir d’une séquence de valeurs.</span><span class="sxs-lookup"><span data-stu-id="bdd86-104">For example, in addition to the standard average or maximum operations, you can create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="bdd86-105">Vous pouvez également créer une méthode qui fonctionne comme un filtre personnalisé ou une transformation de données pour une séquence de valeurs, et qui retourne une nouvelle séquence.</span><span class="sxs-lookup"><span data-stu-id="bdd86-105">You can also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="bdd86-106"><xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A> et <xref:System.Linq.Enumerable.Reverse%2A> en sont quelques exemples.</span><span class="sxs-lookup"><span data-stu-id="bdd86-106">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>

<span data-ttu-id="bdd86-107">Quand vous étendez l’interface <xref:System.Collections.Generic.IEnumerable%601>, vous pouvez appliquer vos méthodes personnalisées à n’importe quelle collection énumérable.</span><span class="sxs-lookup"><span data-stu-id="bdd86-107">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="bdd86-108">Pour plus d’informations, consultez [Méthodes d’extension](../../language-features/procedures/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="bdd86-108">For more information, see [Extension Methods](../../language-features/procedures/extension-methods.md).</span></span>

## <a name="adding-an-aggregate-method"></a><span data-ttu-id="bdd86-109">Utilisation d’une méthode d’agrégation</span><span class="sxs-lookup"><span data-stu-id="bdd86-109">Adding an Aggregate Method</span></span>

<span data-ttu-id="bdd86-110">Une méthode d’agrégation calcule une valeur à partir d’un ensemble de valeurs.</span><span class="sxs-lookup"><span data-stu-id="bdd86-110">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="bdd86-111">LINQ fournit plusieurs méthodes d’agrégation, notamment <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A> et <xref:System.Linq.Enumerable.Max%2A>.</span><span class="sxs-lookup"><span data-stu-id="bdd86-111">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="bdd86-112">Vous pouvez créer votre propre méthode d’agrégation en ajoutant une méthode d’extension à l’interface <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="bdd86-112">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="bdd86-113">L’exemple de code suivant montre comment créer une méthode d’extension appelée `Median` pour calculer une valeur médiane pour une séquence de nombres de type `double`.</span><span class="sxs-lookup"><span data-stu-id="bdd86-113">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>

```vb
Imports System.Runtime.CompilerServices

Module LINQExtension

    ' Extension method for the IEnumerable(of T) interface.
    ' The method accepts only values of the Double type.
    <Extension()>
    Function Median(ByVal source As IEnumerable(Of Double)) As Double
        If source.Count = 0 Then
            Throw New InvalidOperationException("Cannot compute median for an empty set.")
        End If

        Dim sortedSource = From number In source
                           Order By number

        Dim itemIndex = sortedSource.Count \ 2

        If sortedSource.Count Mod 2 = 0 Then
            ' Even number of items in list.
            Return (sortedSource(itemIndex) + sortedSource(itemIndex - 1)) / 2
        Else
            ' Odd number of items in list.
            Return sortedSource(itemIndex)
        End If
    End Function
End Module
```

<span data-ttu-id="bdd86-114">Vous appelez cette méthode d’extension pour toute collection énumérable de la même façon que vous appelez d’autres méthodes d’agrégation depuis l’interface <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="bdd86-114">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

> [!NOTE]
> <span data-ttu-id="bdd86-115">Dans Visual Basic, vous pouvez utiliser un appel de méthode ou une syntaxe de requête standard pour la `Aggregate` `Group By` clause ou.</span><span class="sxs-lookup"><span data-stu-id="bdd86-115">In Visual Basic, you can either use a method call or standard query syntax for the `Aggregate` or `Group By` clause.</span></span> <span data-ttu-id="bdd86-116">Pour plus d’informations, consultez clause [Aggregate](../../../language-reference/queries/aggregate-clause.md) et [clause Group by](../../../language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="bdd86-116">For more information, see [Aggregate Clause](../../../language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../language-reference/queries/group-by-clause.md).</span></span>

<span data-ttu-id="bdd86-117">L’exemple de code suivant montre comment utiliser la méthode `Median` pour un tableau de type `double`.</span><span class="sxs-lookup"><span data-stu-id="bdd86-117">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>

```vb
Dim numbers1() As Double = {1.9, 2, 8, 4, 5.7, 6, 7.2, 0}

Dim query1 = Aggregate num In numbers1 Into Median()

Console.WriteLine("Double: Median = " & query1)
```

```vb
' This code produces the following output:
'
' Double: Median = 4.85
```

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="bdd86-118">Surcharge d’une méthode d’agrégation pour accepter différents types</span><span class="sxs-lookup"><span data-stu-id="bdd86-118">Overloading an Aggregate Method to Accept Various Types</span></span>

<span data-ttu-id="bdd86-119">Vous pouvez surcharger votre méthode d’agrégation pour qu’elle accepte des séquences de différents types.</span><span class="sxs-lookup"><span data-stu-id="bdd86-119">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="bdd86-120">L’approche standard consiste à créer une surcharge pour chaque type.</span><span class="sxs-lookup"><span data-stu-id="bdd86-120">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="bdd86-121">Une autre approche consiste à créer une surcharge qui accepte un type générique et le convertit en un autre type à l’aide d’un délégué.</span><span class="sxs-lookup"><span data-stu-id="bdd86-121">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="bdd86-122">Vous pouvez également combiner ces deux approches.</span><span class="sxs-lookup"><span data-stu-id="bdd86-122">You can also combine both approaches.</span></span>

#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="bdd86-123">Pour créer une surcharge pour chaque type</span><span class="sxs-lookup"><span data-stu-id="bdd86-123">To create an overload for each type</span></span>

<span data-ttu-id="bdd86-124">Vous pouvez créer une surcharge pour chacun des types que vous voulez prendre en charge.</span><span class="sxs-lookup"><span data-stu-id="bdd86-124">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="bdd86-125">L’exemple de code suivant montre une surcharge de la méthode `Median` pour le type `integer`.</span><span class="sxs-lookup"><span data-stu-id="bdd86-125">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>

```vb
' Integer overload

<Extension()>
Function Median(ByVal source As IEnumerable(Of Integer)) As Double
    Return Aggregate num In source Select CDbl(num) Into med = Median()
End Function
```

<span data-ttu-id="bdd86-126">Vous pouvez maintenant appeler les surcharges `Median` pour les types `integer` et `double`, comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="bdd86-126">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>

```vb
Dim numbers1() As Double = {1.9, 2, 8, 4, 5.7, 6, 7.2, 0}

Dim query1 = Aggregate num In numbers1 Into Median()

Console.WriteLine("Double: Median = " & query1)
```

```vb
Dim numbers2() As Integer = {1, 2, 3, 4, 5}

Dim query2 = Aggregate num In numbers2 Into Median()

Console.WriteLine("Integer: Median = " & query2)
```

```vb
' This code produces the following output:
'
' Double: Median = 4.85
' Integer: Median = 3
```

#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="bdd86-127">Pour créer une surcharge générique</span><span class="sxs-lookup"><span data-stu-id="bdd86-127">To create a generic overload</span></span>

<span data-ttu-id="bdd86-128">Vous pouvez également créer une surcharge qui accepte une séquence d’objets génériques.</span><span class="sxs-lookup"><span data-stu-id="bdd86-128">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="bdd86-129">Cette surcharge prend un délégué comme paramètre et l’utilise pour convertir une séquence d’objets de type générique en un autre type d’objets.</span><span class="sxs-lookup"><span data-stu-id="bdd86-129">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>

<span data-ttu-id="bdd86-130">Le code suivant montre une surcharge de la méthode `Median` qui prend le délégué <xref:System.Func%602> comme paramètre.</span><span class="sxs-lookup"><span data-stu-id="bdd86-130">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="bdd86-131">Ce délégué prend un objet de type générique T et retourne un objet de type `double`.</span><span class="sxs-lookup"><span data-stu-id="bdd86-131">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>

```vb
' Generic overload.

<Extension()>
Function Median(Of T)(ByVal source As IEnumerable(Of T),
                      ByVal selector As Func(Of T, Double)) As Double
    Return Aggregate num In source Select selector(num) Into med = Median()
End Function
```

<span data-ttu-id="bdd86-132">Vous pouvez maintenant appeler la méthode `Median` pour une séquence d’objets de tout type.</span><span class="sxs-lookup"><span data-stu-id="bdd86-132">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="bdd86-133">Si le type n’a pas sa propre surcharge de méthode, vous devez passer un paramètre délégué.</span><span class="sxs-lookup"><span data-stu-id="bdd86-133">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="bdd86-134">Dans Visual Basic, vous pouvez utiliser une expression lambda à cet effet.</span><span class="sxs-lookup"><span data-stu-id="bdd86-134">In Visual Basic, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="bdd86-135">En outre, si vous utilisez `Aggregate` la `Group By` clause ou au lieu de l’appel de méthode, vous pouvez passer n’importe quelle valeur ou expression figurant dans la portée de cette clause.</span><span class="sxs-lookup"><span data-stu-id="bdd86-135">Also, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>

<span data-ttu-id="bdd86-136">L’exemple de code suivant montre comment appeler la méthode `Median` pour un tableau d’entiers et un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="bdd86-136">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="bdd86-137">Pour les chaînes, c’est la valeur médiane des longueurs de chaînes du tableau qui est calculée.</span><span class="sxs-lookup"><span data-stu-id="bdd86-137">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="bdd86-138">L’exemple montre comment passer le paramètre de délégué <xref:System.Func%602> à la méthode `Median` pour chaque cas.</span><span class="sxs-lookup"><span data-stu-id="bdd86-138">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>

```vb
Dim numbers3() As Integer = {1, 2, 3, 4, 5}

' You can use num as a parameter for the Median method
' so that the compiler will implicitly convert its value to double.
' If there is no implicit conversion, the compiler will
' display an error message.

Dim query3 = Aggregate num In numbers3 Into Median(num)

Console.WriteLine("Integer: Median = " & query3)

Dim numbers4() As String = {"one", "two", "three", "four", "five"}

' With the generic overload, you can also use numeric properties of objects.

Dim query4 = Aggregate str In numbers4 Into Median(str.Length)

Console.WriteLine("String: Median = " & query4)

' This code produces the following output:
'
' Integer: Median = 3
' String: Median = 4
```

## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="bdd86-139">Ajout d’une méthode qui retourne une collection</span><span class="sxs-lookup"><span data-stu-id="bdd86-139">Adding a Method That Returns a Collection</span></span>

<span data-ttu-id="bdd86-140">Vous pouvez étendre l’interface <xref:System.Collections.Generic.IEnumerable%601> avec une méthode de requête personnalisée qui retourne une séquence de valeurs.</span><span class="sxs-lookup"><span data-stu-id="bdd86-140">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="bdd86-141">Dans ce cas, la méthode doit retourner une collection de type <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="bdd86-141">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="bdd86-142">Ces méthodes peuvent être utilisées pour appliquer des filtres ou des transformations de données à une séquence de valeurs.</span><span class="sxs-lookup"><span data-stu-id="bdd86-142">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>

<span data-ttu-id="bdd86-143">L’exemple suivant montre comment créer une méthode d’extension nommée `AlternateElements` qui retourne un élément sur deux d’une collection, en commençant par le premier élément.</span><span class="sxs-lookup"><span data-stu-id="bdd86-143">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>

```vb
' Extension method for the IEnumerable(of T) interface.
' The method returns every other element of a sequence.

<Extension()>
Function AlternateElements(Of T)(
    ByVal source As IEnumerable(Of T)
    ) As IEnumerable(Of T)

    Dim list As New List(Of T)
    Dim i = 0
    For Each element In source
        If (i Mod 2 = 0) Then
            list.Add(element)
        End If
        i = i + 1
    Next
    Return list
End Function
```

<span data-ttu-id="bdd86-144">Vous pouvez appeler cette méthode d’extension pour n’importe quelle collection énumérable, de la même façon que vous appelez d’autres méthodes depuis l’interface <xref:System.Collections.Generic.IEnumerable%601>, comme le montre le code suivant :</span><span class="sxs-lookup"><span data-stu-id="bdd86-144">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>

```vb
Dim strings() As String = {"a", "b", "c", "d", "e"}

Dim query = strings.AlternateElements()

For Each element In query
    Console.WriteLine(element)
Next

' This code produces the following output:
'
' a
' c
' e
```

## <a name="see-also"></a><span data-ttu-id="bdd86-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bdd86-145">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="bdd86-146">Méthodes d’extension</span><span class="sxs-lookup"><span data-stu-id="bdd86-146">Extension Methods</span></span>](../../language-features/procedures/extension-methods.md)

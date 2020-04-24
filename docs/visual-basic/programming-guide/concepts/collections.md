---
title: Collections
ms.date: 07/20/2015
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
ms.openlocfilehash: 232b9ec7b5975092e73daf0a7384fa816f55f72f
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646344"
---
# <a name="collections-visual-basic"></a><span data-ttu-id="d107e-102">Collections (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d107e-102">Collections (Visual Basic)</span></span>

<span data-ttu-id="d107e-103">Pour de nombreuses applications, vous voulez créer et gérer des groupes d’objets connexes.</span><span class="sxs-lookup"><span data-stu-id="d107e-103">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="d107e-104">Il existe deux manières de grouper des objets : en créant des tableaux d’objets ou des collections d’objets.</span><span class="sxs-lookup"><span data-stu-id="d107e-104">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>

<span data-ttu-id="d107e-105">Les tableaux sont particulièrement utiles pour la création et l’utilisation d’un nombre fixe d’objets fortement typés.</span><span class="sxs-lookup"><span data-stu-id="d107e-105">Arrays are most useful for creating and working with a fixed number of strongly-typed objects.</span></span> <span data-ttu-id="d107e-106">Pour plus d’informations sur les tableaux, consultez [Tableaux](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="d107e-106">For information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>

<span data-ttu-id="d107e-107">Les collections offrent plus de souplesse quand il s’agit d’utiliser des groupes d’objets.</span><span class="sxs-lookup"><span data-stu-id="d107e-107">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="d107e-108">Contrairement aux tableaux, le groupe d’objets que vous utilisez peut être développé et réduit de manière dynamique selon les modifications de l’application.</span><span class="sxs-lookup"><span data-stu-id="d107e-108">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="d107e-109">Pour certaines collections, vous pouvez assigner une clé à un objet que vous placez dans la collection pour vous permettre de récupérer rapidement l’objet à l’aide de la clé.</span><span class="sxs-lookup"><span data-stu-id="d107e-109">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>

<span data-ttu-id="d107e-110">Une collection est une classe, vous devez déclarer une instance de la classe avant de pouvoir ajouter des éléments à la collection.</span><span class="sxs-lookup"><span data-stu-id="d107e-110">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>

<span data-ttu-id="d107e-111">Si votre collection contient des éléments d’un seul type de données, vous pouvez utiliser une des classes dans l’espace de noms <xref:System.Collections.Generic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d107e-111">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="d107e-112">Une collection générique applique la cohérence des types pour éviter qu’un autre type puisse y être ajouté.</span><span class="sxs-lookup"><span data-stu-id="d107e-112">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="d107e-113">Quand vous récupérez un élément d’une collection générique, il n’est pas utile de déterminer son type de données ou de le convertir.</span><span class="sxs-lookup"><span data-stu-id="d107e-113">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>

> [!NOTE]
> <span data-ttu-id="d107e-114">Pour les exemples dans ce sujet, `System.Linq` inclure [les déclarations d’importations](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pour les `System.Collections.Generic` espaces et les noms.</span><span class="sxs-lookup"><span data-stu-id="d107e-114">For the examples in this topic, include [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>

<a name="BKMK_SimpleCollection"></a>

## <a name="using-a-simple-collection"></a><span data-ttu-id="d107e-115">Utilisation d’une collection simple</span><span class="sxs-lookup"><span data-stu-id="d107e-115">Using a Simple Collection</span></span>

<span data-ttu-id="d107e-116">Les exemples de cette section utilisent la classe <xref:System.Collections.Generic.List%601> générique, qui vous permet d’utiliser une liste d’objets fortement typée.</span><span class="sxs-lookup"><span data-stu-id="d107e-116">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>

<span data-ttu-id="d107e-117">L’exemple suivant crée une liste de cordes, puis itère à travers les cordes en utilisant un [Pour chaque ... Prochaine](../../../visual-basic/language-reference/statements/for-each-next-statement.md) déclaration.</span><span class="sxs-lookup"><span data-stu-id="d107e-117">The following example creates a list of strings and then iterates through the strings by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span>

```vb
' Create a list of strings.
Dim salmons As New List(Of String)
salmons.Add("chinook")
salmons.Add("coho")
salmons.Add("pink")
salmons.Add("sockeye")

' Iterate through the list.
For Each salmon As String In salmons
    Console.Write(salmon & " ")
Next
'Output: chinook coho pink sockeye
```

<span data-ttu-id="d107e-118">Si le contenu d’une collection est connu d’avance, vous pouvez utiliser un *initialiseur de collection* pour initialiser la collection.</span><span class="sxs-lookup"><span data-stu-id="d107e-118">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="d107e-119">Pour plus d’informations, consultez [Initialiseurs de collection](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span><span class="sxs-lookup"><span data-stu-id="d107e-119">For more information, see [Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span></span>

<span data-ttu-id="d107e-120">L’exemple suivant est identique à l’exemple précédent, à la différence qu’un initialiseur de collection est utilisé pour ajouter des éléments à la collection.</span><span class="sxs-lookup"><span data-stu-id="d107e-120">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>

```vb
' Create a list of strings by using a
' collection initializer.
Dim salmons As New List(Of String) From
    {"chinook", "coho", "pink", "sockeye"}

For Each salmon As String In salmons
    Console.Write(salmon & " ")
Next
'Output: chinook coho pink sockeye
```

<span data-ttu-id="d107e-121">Vous pouvez utiliser un [For... Déclaration suivante](../../../visual-basic/language-reference/statements/for-next-statement.md) au `For Each` lieu d’une déclaration à itérer à travers une collection.</span><span class="sxs-lookup"><span data-stu-id="d107e-121">You can use a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement instead of a `For Each` statement to iterate through a collection.</span></span> <span data-ttu-id="d107e-122">Pour cela, accédez aux éléments de la collection à la position d’index.</span><span class="sxs-lookup"><span data-stu-id="d107e-122">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="d107e-123">L’index des éléments commence à 0 et se termine au nombre d’éléments moins 1.</span><span class="sxs-lookup"><span data-stu-id="d107e-123">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>

<span data-ttu-id="d107e-124">L’exemple suivant itère au sein des éléments d’une collection à l’aide de `For…Next` au lieu de `For Each`.</span><span class="sxs-lookup"><span data-stu-id="d107e-124">The following example iterates through the elements of a collection by using `For…Next` instead of `For Each`.</span></span>

```vb
Dim salmons As New List(Of String) From
    {"chinook", "coho", "pink", "sockeye"}

For index = 0 To salmons.Count - 1
    Console.Write(salmons(index) & " ")
Next
'Output: chinook coho pink sockeye
```

<span data-ttu-id="d107e-125">L’exemple suivant supprime un élément de la collection en spécifiant l’objet à supprimer.</span><span class="sxs-lookup"><span data-stu-id="d107e-125">The following example removes an element from the collection by specifying the object to remove.</span></span>

```vb
' Create a list of strings by using a
' collection initializer.
Dim salmons As New List(Of String) From
    {"chinook", "coho", "pink", "sockeye"}

' Remove an element in the list by specifying
' the object.
salmons.Remove("coho")

For Each salmon As String In salmons
    Console.Write(salmon & " ")
Next
'Output: chinook pink sockeye
```

<span data-ttu-id="d107e-126">L’exemple suivant supprime les éléments d’une liste générique.</span><span class="sxs-lookup"><span data-stu-id="d107e-126">The following example removes elements from a generic list.</span></span> <span data-ttu-id="d107e-127">Au lieu `For Each` d’une déclaration, un [Pour ... La déclaration suivante](../../../visual-basic/language-reference/statements/for-next-statement.md) selon laquelle les itérations dans l’ordre décroissant est utilisée.</span><span class="sxs-lookup"><span data-stu-id="d107e-127">Instead of a `For Each` statement, a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="d107e-128">En effet, avec la méthode <xref:System.Collections.Generic.List%601.RemoveAt%2A>, les éléments après l’élément supprimé ont une valeur d’index moins élevée.</span><span class="sxs-lookup"><span data-stu-id="d107e-128">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>

```vb
Dim numbers As New List(Of Integer) From
    {0, 1, 2, 3, 4, 5, 6, 7, 8, 9}

' Remove odd numbers.
For index As Integer = numbers.Count - 1 To 0 Step -1
    If numbers(index) Mod 2 = 1 Then
        ' Remove the element by specifying
        ' the zero-based index in the list.
        numbers.RemoveAt(index)
    End If
Next

' Iterate through the list.
' A lambda expression is placed in the ForEach method
' of the List(T) object.
numbers.ForEach(
    Sub(number) Console.Write(number & " "))
' Output: 0 2 4 6 8
```

<span data-ttu-id="d107e-129">Pour le type d’éléments de <xref:System.Collections.Generic.List%601>, vous pouvez également définir votre propre classe.</span><span class="sxs-lookup"><span data-stu-id="d107e-129">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="d107e-130">Dans l’exemple suivant, la classe `Galaxy` qui est utilisée par <xref:System.Collections.Generic.List%601> est définie dans le code.</span><span class="sxs-lookup"><span data-stu-id="d107e-130">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>

```vb
Private Sub IterateThroughList()
    Dim theGalaxies As New List(Of Galaxy) From
        {
            New Galaxy With {.Name = "Tadpole", .MegaLightYears = 400},
            New Galaxy With {.Name = "Pinwheel", .MegaLightYears = 25},
            New Galaxy With {.Name = "Milky Way", .MegaLightYears = 0},
            New Galaxy With {.Name = "Andromeda", .MegaLightYears = 3}
        }

    For Each theGalaxy In theGalaxies
        With theGalaxy
            Console.WriteLine(.Name & "  " & .MegaLightYears)
        End With
    Next

    ' Output:
    '  Tadpole  400
    '  Pinwheel  25
    '  Milky Way  0
    '  Andromeda  3
End Sub

Public Class Galaxy
    Public Property Name As String
    Public Property MegaLightYears As Integer
End Class
```

<a name="BKMK_KindsOfCollections"></a>

## <a name="kinds-of-collections"></a><span data-ttu-id="d107e-131">Types de collections</span><span class="sxs-lookup"><span data-stu-id="d107e-131">Kinds of Collections</span></span>

<span data-ttu-id="d107e-132">Plusieurs collections courantes sont fournies par le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d107e-132">Many common collections are provided by the .NET Framework.</span></span> <span data-ttu-id="d107e-133">Chaque type de collection est conçu dans un but spécifique.</span><span class="sxs-lookup"><span data-stu-id="d107e-133">Each type of collection is designed for a specific purpose.</span></span>

<span data-ttu-id="d107e-134">Certaines des classes de collection courantes sont décrites dans cette section :</span><span class="sxs-lookup"><span data-stu-id="d107e-134">Some of the common collection classes are described in this section:</span></span>

- <span data-ttu-id="d107e-135">Classes <xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="d107e-135"><xref:System.Collections.Generic> classes</span></span>

- <span data-ttu-id="d107e-136">Classes <xref:System.Collections.Concurrent></span><span class="sxs-lookup"><span data-stu-id="d107e-136"><xref:System.Collections.Concurrent> classes</span></span>

- <span data-ttu-id="d107e-137">Classes <xref:System.Collections></span><span class="sxs-lookup"><span data-stu-id="d107e-137"><xref:System.Collections> classes</span></span>

- <span data-ttu-id="d107e-138">Classe `Collection` Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d107e-138">Visual Basic `Collection` class</span></span>

<a name="BKMK_Generic"></a>

### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="d107e-139">Classes System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="d107e-139">System.Collections.Generic Classes</span></span>

<span data-ttu-id="d107e-140">Vous pouvez créer une collection générique en utilisant l’une des classes dans l’espace de noms <xref:System.Collections.Generic>.</span><span class="sxs-lookup"><span data-stu-id="d107e-140">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="d107e-141">Une collection générique est utile quand chaque élément de la collection a le même type de données.</span><span class="sxs-lookup"><span data-stu-id="d107e-141">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="d107e-142">Une collection générique applique un typage fort en autorisant uniquement l’ajout des types de données souhaités.</span><span class="sxs-lookup"><span data-stu-id="d107e-142">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>

<span data-ttu-id="d107e-143">Le tableau suivant liste quelques classes de l’espace de noms <xref:System.Collections.Generic?displayProperty=nameWithType> fréquemment utilisées :</span><span class="sxs-lookup"><span data-stu-id="d107e-143">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="d107e-144">Classe</span><span class="sxs-lookup"><span data-stu-id="d107e-144">Class</span></span>|<span data-ttu-id="d107e-145">Description</span><span class="sxs-lookup"><span data-stu-id="d107e-145">Description</span></span>|
|---|---|
|<xref:System.Collections.Generic.Dictionary%602>|<span data-ttu-id="d107e-146">Représente une collection de paires clé/valeur organisées en fonction de la clé.</span><span class="sxs-lookup"><span data-stu-id="d107e-146">Represents a collection of key/value pairs that are organized based on the key.</span></span>|
|<xref:System.Collections.Generic.List%601>|<span data-ttu-id="d107e-147">Représente une liste d’objets accessibles par index.</span><span class="sxs-lookup"><span data-stu-id="d107e-147">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="d107e-148">Fournit des méthodes de recherche, de tri et de modification de listes.</span><span class="sxs-lookup"><span data-stu-id="d107e-148">Provides methods to search, sort, and modify lists.</span></span>|
|<xref:System.Collections.Generic.Queue%601>|<span data-ttu-id="d107e-149">Représente une collection d’objets premier entré, premier sorti (FIFO).</span><span class="sxs-lookup"><span data-stu-id="d107e-149">Represents a first in, first out (FIFO) collection of objects.</span></span>|
|<xref:System.Collections.Generic.SortedList%602>|<span data-ttu-id="d107e-150">Représente une collection de paires clé/valeur triées par clé en fonction de l'implémentation <xref:System.Collections.Generic.IComparer%601> associée.</span><span class="sxs-lookup"><span data-stu-id="d107e-150">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|
|<xref:System.Collections.Generic.Stack%601>|<span data-ttu-id="d107e-151">Représente une collection d’objets dernier entré, premier sorti (LIFO).</span><span class="sxs-lookup"><span data-stu-id="d107e-151">Represents a last in, first out (LIFO) collection of objects.</span></span>|

<span data-ttu-id="d107e-152">Pour plus d’informations, consultez [Types de collections couramment utilisés](../../../standard/collections/commonly-used-collection-types.md), [Sélection d’une classe de collection](../../../standard/collections/selecting-a-collection-class.md) et <xref:System.Collections.Generic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d107e-152">For additional information, see [Commonly Used Collection Types](../../../standard/collections/commonly-used-collection-types.md), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic?displayProperty=nameWithType>.</span></span>

<a name="BKMK_Concurrent"></a>

### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="d107e-153">Classes System.Collections.Concurrent</span><span class="sxs-lookup"><span data-stu-id="d107e-153">System.Collections.Concurrent Classes</span></span>

<span data-ttu-id="d107e-154">Dans .NET Framework 4 ou ultérieur, les collections de l’espace de noms <xref:System.Collections.Concurrent> fournissent des opérations thread-safe efficaces pour accéder aux éléments de collection à partir de plusieurs threads.</span><span class="sxs-lookup"><span data-stu-id="d107e-154">In the .NET Framework 4 or newer, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>

<span data-ttu-id="d107e-155">Les classes de l’espace de noms <xref:System.Collections.Concurrent> doivent être utilisées à la place des types correspondants dans les espaces de noms <xref:System.Collections.Generic?displayProperty=nameWithType> et <xref:System.Collections?displayProperty=nameWithType> chaque fois que plusieurs threads accèdent simultanément à la collection.</span><span class="sxs-lookup"><span data-stu-id="d107e-155">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=nameWithType> and <xref:System.Collections?displayProperty=nameWithType> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="d107e-156">Pour plus d’informations, consultez [Collections thread-safe](../../../standard/collections/thread-safe/index.md) et <xref:System.Collections.Concurrent>.</span><span class="sxs-lookup"><span data-stu-id="d107e-156">For more information, see [Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.</span></span>

<span data-ttu-id="d107e-157">Certaines classes incluses dans l’espace de noms <xref:System.Collections.Concurrent> sont <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601> et <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span><span class="sxs-lookup"><span data-stu-id="d107e-157">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>

<a name="BKMK_Collections"></a>

### <a name="systemcollections-classes"></a><span data-ttu-id="d107e-158">Classes System.Collections</span><span class="sxs-lookup"><span data-stu-id="d107e-158">System.Collections Classes</span></span>

<span data-ttu-id="d107e-159">Les classes de l’espace de noms <xref:System.Collections?displayProperty=nameWithType> ne stockent pas les éléments comme des objets spécifiquement typés, mais comme des objets de type `Object`.</span><span class="sxs-lookup"><span data-stu-id="d107e-159">The classes in the <xref:System.Collections?displayProperty=nameWithType> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>

<span data-ttu-id="d107e-160">Si possible, vous devez utiliser les collections génériques dans l’espace de noms <xref:System.Collections.Generic?displayProperty=nameWithType> ou <xref:System.Collections.Concurrent> à la place des types hérités de l’espace de noms `System.Collections`.</span><span class="sxs-lookup"><span data-stu-id="d107e-160">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>

<span data-ttu-id="d107e-161">Le tableau suivant répertorie certaines des classes fréquemment utilisées de l’espace de noms `System.Collections` :</span><span class="sxs-lookup"><span data-stu-id="d107e-161">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>

|<span data-ttu-id="d107e-162">Classe</span><span class="sxs-lookup"><span data-stu-id="d107e-162">Class</span></span>|<span data-ttu-id="d107e-163">Description</span><span class="sxs-lookup"><span data-stu-id="d107e-163">Description</span></span>|
|---|---|
|<xref:System.Collections.ArrayList>|<span data-ttu-id="d107e-164">Représente un tableau d’objets dont la taille est augmentée de manière dynamique selon les besoins.</span><span class="sxs-lookup"><span data-stu-id="d107e-164">Represents an array of objects whose size is dynamically increased as required.</span></span>|
|<xref:System.Collections.Hashtable>|<span data-ttu-id="d107e-165">Représente une collection de paires clé/valeur qui sont organisées en fonction du code de hachage de la clé.</span><span class="sxs-lookup"><span data-stu-id="d107e-165">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|
|<xref:System.Collections.Queue>|<span data-ttu-id="d107e-166">Représente une collection d’objets premier entré, premier sorti (FIFO).</span><span class="sxs-lookup"><span data-stu-id="d107e-166">Represents a first in, first out (FIFO) collection of objects.</span></span>|
|<xref:System.Collections.Stack>|<span data-ttu-id="d107e-167">Représente une collection d’objets dernier entré, premier sorti (LIFO).</span><span class="sxs-lookup"><span data-stu-id="d107e-167">Represents a last in, first out (LIFO) collection of objects.</span></span>|

<span data-ttu-id="d107e-168">L’espace de noms <xref:System.Collections.Specialized> fournit des classes de collection spécialisées et fortement typées, telles que les collections à chaîne unique et les dictionnaires de liste liée et hybrides.</span><span class="sxs-lookup"><span data-stu-id="d107e-168">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>

<a name="BKMK_VisualBasic"></a>

### <a name="visual-basic-collection-class"></a><span data-ttu-id="d107e-169">Classe de la collection Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d107e-169">Visual Basic Collection Class</span></span>

<span data-ttu-id="d107e-170">Vous pouvez utiliser la classe Visual Basic <xref:Microsoft.VisualBasic.Collection> pour accéder à une collection d’éléments à l’aide d’un index numérique ou d’une clé `String`.</span><span class="sxs-lookup"><span data-stu-id="d107e-170">You can use the Visual Basic <xref:Microsoft.VisualBasic.Collection> class to access a collection item by using either a numeric index or a `String` key.</span></span> <span data-ttu-id="d107e-171">Vous pouvez ajouter des éléments à un objet de collection en spécifiant ou non une clé.</span><span class="sxs-lookup"><span data-stu-id="d107e-171">You can add items to a collection object either with or without specifying a key.</span></span> <span data-ttu-id="d107e-172">Si vous ajoutez un élément sans clé, vous devez utiliser son index numérique pour y accéder.</span><span class="sxs-lookup"><span data-stu-id="d107e-172">If you add an item without a key, you must use its numeric index to access it.</span></span>

<span data-ttu-id="d107e-173">La classe Visual Basic `Collection` stocke tous ses éléments sous le type `Object`, de sorte que vous pouvez ajouter un élément de n’importe quel type de données.</span><span class="sxs-lookup"><span data-stu-id="d107e-173">The Visual Basic `Collection` class stores all its elements as type `Object`, so you can add an item of any data type.</span></span> <span data-ttu-id="d107e-174">Il n’existe aucun dispositif de protection contre l’ajout de types de données inappropriés.</span><span class="sxs-lookup"><span data-stu-id="d107e-174">There is no safeguard against inappropriate data types being added.</span></span>

<span data-ttu-id="d107e-175">Quand vous utilisez la classe Visual Basic `Collection`, le premier élément d’une collection a un index égal à 1.</span><span class="sxs-lookup"><span data-stu-id="d107e-175">When you use the Visual Basic `Collection` class, the first item in a collection has an index of 1.</span></span> <span data-ttu-id="d107e-176">Ce n’est pas le cas pour les classes de collection .NET Framework, pour lesquelles l’index de départ est 0.</span><span class="sxs-lookup"><span data-stu-id="d107e-176">This differs from the .NET Framework collection classes, for which the starting index is 0.</span></span>

<span data-ttu-id="d107e-177">Si possible, vous devez utiliser les collections génériques dans l’espace de noms <xref:System.Collections.Generic?displayProperty=nameWithType> ou <xref:System.Collections.Concurrent> à la place de la classe Visual Basic `Collection`.</span><span class="sxs-lookup"><span data-stu-id="d107e-177">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the Visual Basic `Collection` class.</span></span>

<span data-ttu-id="d107e-178">Pour plus d’informations, consultez <xref:Microsoft.VisualBasic.Collection>.</span><span class="sxs-lookup"><span data-stu-id="d107e-178">For more information, see <xref:Microsoft.VisualBasic.Collection>.</span></span>

<a name="BKMK_KeyValuePairs"></a>

## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="d107e-179">Implémentation d’une collection de paires clé/valeur</span><span class="sxs-lookup"><span data-stu-id="d107e-179">Implementing a Collection of Key/Value Pairs</span></span>

<span data-ttu-id="d107e-180">La collection générique <xref:System.Collections.Generic.Dictionary%602> vous permet d’accéder aux éléments d’une collection à l’aide de la clé de chaque élément.</span><span class="sxs-lookup"><span data-stu-id="d107e-180">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="d107e-181">Chaque ajout au dictionnaire se compose d’une valeur et de sa clé associée.</span><span class="sxs-lookup"><span data-stu-id="d107e-181">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="d107e-182">La récupération d’une valeur à l’aide de sa clé est très rapide, car la classe `Dictionary` est implémentée en tant que table de hachage.</span><span class="sxs-lookup"><span data-stu-id="d107e-182">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>

<span data-ttu-id="d107e-183">L’exemple suivant crée une collection `Dictionary` et itère au sein du dictionnaire à l’aide d’une instruction `For Each`.</span><span class="sxs-lookup"><span data-stu-id="d107e-183">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `For Each` statement.</span></span>

```vb
Private Sub IterateThroughDictionary()
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()

    For Each kvp As KeyValuePair(Of String, Element) In elements
        Dim theElement As Element = kvp.Value

        Console.WriteLine("key: " & kvp.Key)
        With theElement
            Console.WriteLine("values: " & .Symbol & " " &
                .Name & " " & .AtomicNumber)
        End With
    Next
End Sub

Private Function BuildDictionary() As Dictionary(Of String, Element)
    Dim elements As New Dictionary(Of String, Element)

    AddToDictionary(elements, "K", "Potassium", 19)
    AddToDictionary(elements, "Ca", "Calcium", 20)
    AddToDictionary(elements, "Sc", "Scandium", 21)
    AddToDictionary(elements, "Ti", "Titanium", 22)

    Return elements
End Function

Private Sub AddToDictionary(ByVal elements As Dictionary(Of String, Element),
ByVal symbol As String, ByVal name As String, ByVal atomicNumber As Integer)
    Dim theElement As New Element

    theElement.Symbol = symbol
    theElement.Name = name
    theElement.AtomicNumber = atomicNumber

    elements.Add(Key:=theElement.Symbol, value:=theElement)
End Sub

Public Class Element
    Public Property Symbol As String
    Public Property Name As String
    Public Property AtomicNumber As Integer
End Class
```

<span data-ttu-id="d107e-184">Au lieu d’utiliser un initialiseur de collection pour générer la collection `Dictionary`, vous pouvez remplacer les méthodes `BuildDictionary` et `AddToDictionary` par la méthode suivante.</span><span class="sxs-lookup"><span data-stu-id="d107e-184">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>

```vb
Private Function BuildDictionary2() As Dictionary(Of String, Element)
    Return New Dictionary(Of String, Element) From
        {
            {"K", New Element With
                {.Symbol = "K", .Name = "Potassium", .AtomicNumber = 19}},
            {"Ca", New Element With
                {.Symbol = "Ca", .Name = "Calcium", .AtomicNumber = 20}},
            {"Sc", New Element With
                {.Symbol = "Sc", .Name = "Scandium", .AtomicNumber = 21}},
            {"Ti", New Element With
                {.Symbol = "Ti", .Name = "Titanium", .AtomicNumber = 22}}
        }
End Function
```

<span data-ttu-id="d107e-185">L’exemple suivant utilise la méthode <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> et la propriété <xref:System.Collections.Generic.Dictionary%602.Item%2A> de `Dictionary` pour rechercher rapidement un élément par clé.</span><span class="sxs-lookup"><span data-stu-id="d107e-185">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="d107e-186">La `Item` propriété vous permet d’accéder à un élément de la `elements` collection en utilisant le `elements(symbol)` code dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d107e-186">The `Item` property enables you to access an item in the `elements` collection by using the `elements(symbol)` code in Visual Basic.</span></span>

```vb
Private Sub FindInDictionary(ByVal symbol As String)
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()

    If elements.ContainsKey(symbol) = False Then
        Console.WriteLine(symbol & " not found")
    Else
        Dim theElement = elements(symbol)
        Console.WriteLine("found: " & theElement.Name)
    End If
End Sub
```

<span data-ttu-id="d107e-187">L’exemple suivant utilise à la place la méthode <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> pour rechercher rapidement un élément par clé.</span><span class="sxs-lookup"><span data-stu-id="d107e-187">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>

```vb
Private Sub FindInDictionary2(ByVal symbol As String)
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()

    Dim theElement As Element = Nothing
    If elements.TryGetValue(symbol, theElement) = False Then
        Console.WriteLine(symbol & " not found")
    Else
        Console.WriteLine("found: " & theElement.Name)
    End If
End Sub
```

<a name="BKMK_LINQ"></a>

## <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="d107e-188">Utilisation de LINQ pour accéder à une collection</span><span class="sxs-lookup"><span data-stu-id="d107e-188">Using LINQ to Access a Collection</span></span>

<span data-ttu-id="d107e-189">LINQ (Language-Integrated Query) peut être utilisé pour accéder aux collections.</span><span class="sxs-lookup"><span data-stu-id="d107e-189">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="d107e-190">Les requêtes LINQ fournissent des fonctionnalités de filtrage, de classement et de regroupement.</span><span class="sxs-lookup"><span data-stu-id="d107e-190">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="d107e-191">Pour plus d’informations, voir [Getting Started avec LINQ dans Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="d107e-191">For more information, see [Getting Started with LINQ in Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>

<span data-ttu-id="d107e-192">L’exemple suivant exécute une requête LINQ sur un `List` générique.</span><span class="sxs-lookup"><span data-stu-id="d107e-192">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="d107e-193">La requête LINQ retourne une autre collection qui contient les résultats.</span><span class="sxs-lookup"><span data-stu-id="d107e-193">The LINQ query returns a different collection that contains the results.</span></span>

```vb
Private Sub ShowLINQ()
    Dim elements As List(Of Element) = BuildList()

    ' LINQ Query.
    Dim subset = From theElement In elements
                  Where theElement.AtomicNumber < 22
                  Order By theElement.Name

    For Each theElement In subset
        Console.WriteLine(theElement.Name & " " & theElement.AtomicNumber)
    Next

    ' Output:
    '  Calcium 20
    '  Potassium 19
    '  Scandium 21
End Sub

Private Function BuildList() As List(Of Element)
    Return New List(Of Element) From
        {
            {New Element With
                {.Symbol = "K", .Name = "Potassium", .AtomicNumber = 19}},
            {New Element With
                {.Symbol = "Ca", .Name = "Calcium", .AtomicNumber = 20}},
            {New Element With
                {.Symbol = "Sc", .Name = "Scandium", .AtomicNumber = 21}},
            {New Element With
                {.Symbol = "Ti", .Name = "Titanium", .AtomicNumber = 22}}
        }
End Function

Public Class Element
    Public Property Symbol As String
    Public Property Name As String
    Public Property AtomicNumber As Integer
End Class
```

<a name="BKMK_Sorting"></a>

## <a name="sorting-a-collection"></a><span data-ttu-id="d107e-194">Tri d’une collection</span><span class="sxs-lookup"><span data-stu-id="d107e-194">Sorting a Collection</span></span>

<span data-ttu-id="d107e-195">L’exemple suivant illustre une procédure de tri d’une collection.</span><span class="sxs-lookup"><span data-stu-id="d107e-195">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="d107e-196">L’exemple trie les instances de la classe `Car` stockées dans un <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="d107e-196">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="d107e-197">La classe `Car` implémente l’interface <xref:System.IComparable%601>, ce qui implique l’implémentation de la méthode <xref:System.IComparable%601.CompareTo%2A>.</span><span class="sxs-lookup"><span data-stu-id="d107e-197">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>

<span data-ttu-id="d107e-198">Chaque appel à la méthode <xref:System.IComparable%601.CompareTo%2A> effectue une comparaison unique qui est utilisée pour le tri.</span><span class="sxs-lookup"><span data-stu-id="d107e-198">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="d107e-199">Le code écrit par l’utilisateur dans la méthode `CompareTo` retourne une valeur pour chaque comparaison de l’objet actuel avec un autre objet.</span><span class="sxs-lookup"><span data-stu-id="d107e-199">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="d107e-200">La valeur retournée est inférieure à zéro si l’objet actuel est inférieur à l’autre objet, supérieure à zéro l’objet actuel est supérieur à l’autre et égale à zéro s’ils sont égaux.</span><span class="sxs-lookup"><span data-stu-id="d107e-200">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="d107e-201">Cela vous permet de définir dans le code les critères définissant « supérieur à », « inférieur à » et « égal à ».</span><span class="sxs-lookup"><span data-stu-id="d107e-201">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>

<span data-ttu-id="d107e-202">Dans la méthode `ListCars`, l’instruction `cars.Sort()` trie la liste.</span><span class="sxs-lookup"><span data-stu-id="d107e-202">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="d107e-203">Cet appel à la méthode <xref:System.Collections.Generic.List%601.Sort%2A> de <xref:System.Collections.Generic.List%601> entraîne l’appel automatique de la méthode `CompareTo` pour les objets `Car` dans `List`.</span><span class="sxs-lookup"><span data-stu-id="d107e-203">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>

```vb
Public Sub ListCars()

    ' Create some new cars.
    Dim cars As New List(Of Car) From
    {
        New Car With {.Name = "car1", .Color = "blue", .Speed = 20},
        New Car With {.Name = "car2", .Color = "red", .Speed = 50},
        New Car With {.Name = "car3", .Color = "green", .Speed = 10},
        New Car With {.Name = "car4", .Color = "blue", .Speed = 50},
        New Car With {.Name = "car5", .Color = "blue", .Speed = 30},
        New Car With {.Name = "car6", .Color = "red", .Speed = 60},
        New Car With {.Name = "car7", .Color = "green", .Speed = 50}
    }

    ' Sort the cars by color alphabetically, and then by speed
    ' in descending order.
    cars.Sort()

    ' View all of the cars.
    For Each thisCar As Car In cars
        Console.Write(thisCar.Color.PadRight(5) & " ")
        Console.Write(thisCar.Speed.ToString & " ")
        Console.Write(thisCar.Name)
        Console.WriteLine()
    Next

    ' Output:
    '  blue  50 car4
    '  blue  30 car5
    '  blue  20 car1
    '  green 50 car7
    '  green 10 car3
    '  red   60 car6
    '  red   50 car2
End Sub

Public Class Car
    Implements IComparable(Of Car)

    Public Property Name As String
    Public Property Speed As Integer
    Public Property Color As String

    Public Function CompareTo(ByVal other As Car) As Integer _
        Implements System.IComparable(Of Car).CompareTo
        ' A call to this method makes a single comparison that is
        ' used for sorting.

        ' Determine the relative order of the objects being compared.
        ' Sort by color alphabetically, and then by speed in
        ' descending order.

        ' Compare the colors.
        Dim compare As Integer
        compare = String.Compare(Me.Color, other.Color, True)

        ' If the colors are the same, compare the speeds.
        If compare = 0 Then
            compare = Me.Speed.CompareTo(other.Speed)

            ' Use descending order for speed.
            compare = -compare
        End If

        Return compare
    End Function
End Class
```

<a name="BKMK_CustomCollection"></a>

## <a name="defining-a-custom-collection"></a><span data-ttu-id="d107e-204">Définition d’une collection personnalisée</span><span class="sxs-lookup"><span data-stu-id="d107e-204">Defining a Custom Collection</span></span>

<span data-ttu-id="d107e-205">Vous pouvez définir une collection en implémentant l’interface <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="d107e-205">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="d107e-206">Pour plus d’informations, voir [Énumérer une collection](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hwyysy67(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d107e-206">For additional information, see [Enumerating a Collection](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hwyysy67(v=vs.100)).</span></span>

<span data-ttu-id="d107e-207">Même si vous pouvez définir une collection personnalisée, il est généralement préférable d’utiliser les collections comprises dans le .NET Framework, lesquelles sont décrites dans [Types de collections](#kinds-of-collections), plus haut dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="d107e-207">Although you can define a custom collection, it is usually better to instead use the collections that are included in the .NET Framework, which are described in [Kinds of Collections](#kinds-of-collections) earlier in this topic.</span></span>

<span data-ttu-id="d107e-208">L’exemple suivant définit une classe de collection personnalisée nommée `AllColors`.</span><span class="sxs-lookup"><span data-stu-id="d107e-208">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="d107e-209">Cette classe implémente l’interface <xref:System.Collections.IEnumerable>, ce qui implique l’implémentation de la méthode <xref:System.Collections.IEnumerable.GetEnumerator%2A>.</span><span class="sxs-lookup"><span data-stu-id="d107e-209">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>

<span data-ttu-id="d107e-210">La méthode `GetEnumerator` retourne une instance de la classe `ColorEnumerator`.</span><span class="sxs-lookup"><span data-stu-id="d107e-210">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="d107e-211">`ColorEnumerator` implémente l’interface <xref:System.Collections.IEnumerator>, ce qui implique l’implémentation de la propriété <xref:System.Collections.IEnumerator.Current%2A>, la méthode <xref:System.Collections.IEnumerator.MoveNext%2A> et la méthode <xref:System.Collections.IEnumerator.Reset%2A>.</span><span class="sxs-lookup"><span data-stu-id="d107e-211">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>

```vb
Public Sub ListColors()
    Dim colors As New AllColors()

    For Each theColor As Color In colors
        Console.Write(theColor.Name & " ")
    Next
    Console.WriteLine()
    ' Output: red blue green
End Sub

' Collection class.
Public Class AllColors
    Implements System.Collections.IEnumerable

    Private _colors() As Color =
    {
        New Color With {.Name = "red"},
        New Color With {.Name = "blue"},
        New Color With {.Name = "green"}
    }

    Public Function GetEnumerator() As System.Collections.IEnumerator _
        Implements System.Collections.IEnumerable.GetEnumerator

        Return New ColorEnumerator(_colors)

        ' Instead of creating a custom enumerator, you could
        ' use the GetEnumerator of the array.
        'Return _colors.GetEnumerator
    End Function

    ' Custom enumerator.
    Private Class ColorEnumerator
        Implements System.Collections.IEnumerator

        Private _colors() As Color
        Private _position As Integer = -1

        Public Sub New(ByVal colors() As Color)
            _colors = colors
        End Sub

        Public ReadOnly Property Current() As Object _
            Implements System.Collections.IEnumerator.Current
            Get
                Return _colors(_position)
            End Get
        End Property

        Public Function MoveNext() As Boolean _
            Implements System.Collections.IEnumerator.MoveNext
            _position += 1
            Return (_position < _colors.Length)
        End Function

        Public Sub Reset() Implements System.Collections.IEnumerator.Reset
            _position = -1
        End Sub
    End Class
End Class

' Element class.
Public Class Color
    Public Property Name As String
End Class
```

<a name="BKMK_Iterators"></a>

## <a name="iterators"></a><span data-ttu-id="d107e-212">Iterators</span><span class="sxs-lookup"><span data-stu-id="d107e-212">Iterators</span></span>

<span data-ttu-id="d107e-213">Un *itérateur* est utilisé pour exécuter une itération personnalisée sur une collection.</span><span class="sxs-lookup"><span data-stu-id="d107e-213">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="d107e-214">Un itérateur peut être une méthode ou un accesseur `get`.</span><span class="sxs-lookup"><span data-stu-id="d107e-214">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="d107e-215">Un itérateur utilise une déclaration [de rendement](../../../visual-basic/language-reference/statements/yield-statement.md) pour renvoyer chaque élément de la collection un à la fois.</span><span class="sxs-lookup"><span data-stu-id="d107e-215">An iterator uses a [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element of the collection one at a time.</span></span>

<span data-ttu-id="d107e-216">Vous appelez un itérateur en utilisant un [Pour chaque... Prochaine](../../../visual-basic/language-reference/statements/for-each-next-statement.md) déclaration.</span><span class="sxs-lookup"><span data-stu-id="d107e-216">You call an iterator by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span> <span data-ttu-id="d107e-217">Chaque itération de la boucle `For Each` appelle l’itérateur.</span><span class="sxs-lookup"><span data-stu-id="d107e-217">Each iteration of the `For Each` loop calls the iterator.</span></span> <span data-ttu-id="d107e-218">Quand une instruction `Yield` est atteinte dans l’itérateur, une expression est retournée et la localisation actuelle dans le code est retenue.</span><span class="sxs-lookup"><span data-stu-id="d107e-218">When a `Yield` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="d107e-219">L’exécution est redémarrée à partir de cet emplacement la prochaine fois que l’itérateur est appelé.</span><span class="sxs-lookup"><span data-stu-id="d107e-219">Execution is restarted from that location the next time that the iterator is called.</span></span>

<span data-ttu-id="d107e-220">Pour plus d’informations, voir [Iterators (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="d107e-220">For more information, see [Iterators (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).</span></span>

<span data-ttu-id="d107e-221">L'exemple suivant utilise une méthode Iterator.</span><span class="sxs-lookup"><span data-stu-id="d107e-221">The following example uses an iterator method.</span></span> <span data-ttu-id="d107e-222">La méthode itérateur `Yield` a une déclaration qui est à l’intérieur [d’un For ... Prochaine](../../../visual-basic/language-reference/statements/for-next-statement.md) boucle.</span><span class="sxs-lookup"><span data-stu-id="d107e-222">The iterator method has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="d107e-223">Dans la méthode `ListEvenNumbers`, chaque itération du corps de l’instruction `For Each` crée un appel à la méthode Iterator, qui continue sur l’instruction `Yield` suivante.</span><span class="sxs-lookup"><span data-stu-id="d107e-223">In the `ListEvenNumbers` method, each iteration of the `For Each` statement body creates a call to the iterator method, which proceeds to the next `Yield` statement.</span></span>

```vb
Public Sub ListEvenNumbers()
    For Each number As Integer In EvenSequence(5, 18)
        Console.Write(number & " ")
    Next
    Console.WriteLine()
    ' Output: 6 8 10 12 14 16 18
End Sub

Private Iterator Function EvenSequence(
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _
As IEnumerable(Of Integer)

' Yield even numbers in the range.
    For number = firstNumber To lastNumber
        If number Mod 2 = 0 Then
            Yield number
        End If
    Next
End Function
```

## <a name="see-also"></a><span data-ttu-id="d107e-224">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d107e-224">See also</span></span>

- [<span data-ttu-id="d107e-225">Initialisateurs de collection</span><span class="sxs-lookup"><span data-stu-id="d107e-225">Collection Initializers</span></span>](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [<span data-ttu-id="d107e-226">Concepts de programmation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d107e-226">Programming Concepts (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="d107e-227">Option Strict (instruction)</span><span class="sxs-lookup"><span data-stu-id="d107e-227">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="d107e-228">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d107e-228">LINQ to Objects (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="d107e-229">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="d107e-229">Parallel LINQ (PLINQ)</span></span>](../../../standard/parallel-programming/introduction-to-plinq.md)
- [<span data-ttu-id="d107e-230">Collections et structures de données</span><span class="sxs-lookup"><span data-stu-id="d107e-230">Collections and Data Structures</span></span>](../../../standard/collections/index.md)
- [<span data-ttu-id="d107e-231">Sélection d’une classe de collection</span><span class="sxs-lookup"><span data-stu-id="d107e-231">Selecting a Collection Class</span></span>](../../../standard/collections/selecting-a-collection-class.md)
- [<span data-ttu-id="d107e-232">Comparaisons et tris au sein des collections</span><span class="sxs-lookup"><span data-stu-id="d107e-232">Comparisons and Sorts Within Collections</span></span>](../../../standard/collections/comparisons-and-sorts-within-collections.md)
- [<span data-ttu-id="d107e-233">Quand utiliser les collections génériques</span><span class="sxs-lookup"><span data-stu-id="d107e-233">When to Use Generic Collections</span></span>](../../../standard/collections/when-to-use-generic-collections.md)

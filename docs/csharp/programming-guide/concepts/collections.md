---
title: Collections (C#)
ms.date: 07/20/2015
ms.assetid: 317d7dc3-8587-4873-8b3e-556f86497939
ms.openlocfilehash: ecab30d50be58f810246e58e637b331d492e4a47
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241394"
---
# <a name="collections-c"></a><span data-ttu-id="0ecba-102">Collections (C#)</span><span class="sxs-lookup"><span data-stu-id="0ecba-102">Collections (C#)</span></span>

<span data-ttu-id="0ecba-103">Pour de nombreuses applications, vous voulez créer et gérer des groupes d’objets connexes.</span><span class="sxs-lookup"><span data-stu-id="0ecba-103">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="0ecba-104">Il existe deux manières de grouper des objets : en créant des tableaux d’objets ou des collections d’objets.</span><span class="sxs-lookup"><span data-stu-id="0ecba-104">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>

<span data-ttu-id="0ecba-105">Les tableaux s’avèrent particulièrement utiles pour créer et utiliser un nombre fixe d’objets fortement typés.</span><span class="sxs-lookup"><span data-stu-id="0ecba-105">Arrays are most useful for creating and working with a fixed number of strongly typed objects.</span></span> <span data-ttu-id="0ecba-106">Pour plus d’informations sur les tableaux, consultez [Tableaux](../arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="0ecba-106">For information about arrays, see [Arrays](../arrays/index.md).</span></span>

<span data-ttu-id="0ecba-107">Les collections offrent plus de souplesse quand il s’agit d’utiliser des groupes d’objets.</span><span class="sxs-lookup"><span data-stu-id="0ecba-107">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="0ecba-108">Contrairement aux tableaux, le groupe d’objets que vous utilisez peut être développé et réduit de manière dynamique selon les modifications de l’application.</span><span class="sxs-lookup"><span data-stu-id="0ecba-108">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="0ecba-109">Pour certaines collections, vous pouvez assigner une clé à un objet que vous placez dans la collection pour vous permettre de récupérer rapidement l’objet à l’aide de la clé.</span><span class="sxs-lookup"><span data-stu-id="0ecba-109">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>

<span data-ttu-id="0ecba-110">Une collection est une classe, vous devez déclarer une instance de la classe avant de pouvoir ajouter des éléments à la collection.</span><span class="sxs-lookup"><span data-stu-id="0ecba-110">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>

<span data-ttu-id="0ecba-111">Si votre collection contient des éléments d’un seul type de données, vous pouvez utiliser une des classes dans l’espace de noms <xref:System.Collections.Generic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0ecba-111">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="0ecba-112">Une collection générique applique la cohérence des types pour éviter qu’un autre type puisse y être ajouté.</span><span class="sxs-lookup"><span data-stu-id="0ecba-112">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="0ecba-113">Quand vous récupérez un élément d’une collection générique, il n’est pas utile de déterminer son type de données ou de le convertir.</span><span class="sxs-lookup"><span data-stu-id="0ecba-113">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>

> [!NOTE]
> <span data-ttu-id="0ecba-114">Pour les exemples de cette rubrique, ajoutez des instructions [using](../../language-reference/keywords/using-directive.md) pour les espaces de noms `System.Collections.Generic` et `System.Linq`.</span><span class="sxs-lookup"><span data-stu-id="0ecba-114">For the examples in this topic, include [using](../../language-reference/keywords/using-directive.md) directives for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>

 <span data-ttu-id="0ecba-115">**Dans cette rubrique**</span><span class="sxs-lookup"><span data-stu-id="0ecba-115">**In this topic**</span></span>

- [<span data-ttu-id="0ecba-116">Utilisation d’une collection simple</span><span class="sxs-lookup"><span data-stu-id="0ecba-116">Using a Simple Collection</span></span>](#BKMK_SimpleCollection)

- [<span data-ttu-id="0ecba-117">Types de collections</span><span class="sxs-lookup"><span data-stu-id="0ecba-117">Kinds of Collections</span></span>](#BKMK_KindsOfCollections)

  - [<span data-ttu-id="0ecba-118">Classes System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="0ecba-118">System.Collections.Generic Classes</span></span>](#BKMK_Generic)

  - [<span data-ttu-id="0ecba-119">Classes System.Collections.Concurrent</span><span class="sxs-lookup"><span data-stu-id="0ecba-119">System.Collections.Concurrent Classes</span></span>](#BKMK_Concurrent)

  - [<span data-ttu-id="0ecba-120">Classes System.Collections</span><span class="sxs-lookup"><span data-stu-id="0ecba-120">System.Collections Classes</span></span>](#BKMK_Collections)

- [<span data-ttu-id="0ecba-121">Implémentation d’une collection de paires clé-valeur</span><span class="sxs-lookup"><span data-stu-id="0ecba-121">Implementing a Collection of Key/Value Pairs</span></span>](#BKMK_KeyValuePairs)

- [<span data-ttu-id="0ecba-122">Utilisation de LINQ pour accéder à une collection</span><span class="sxs-lookup"><span data-stu-id="0ecba-122">Using LINQ to Access a Collection</span></span>](#BKMK_LINQ)

- [<span data-ttu-id="0ecba-123">Tri d’une collection</span><span class="sxs-lookup"><span data-stu-id="0ecba-123">Sorting a Collection</span></span>](#BKMK_Sorting)

- [<span data-ttu-id="0ecba-124">Définition d’une collection personnalisée</span><span class="sxs-lookup"><span data-stu-id="0ecba-124">Defining a Custom Collection</span></span>](#BKMK_CustomCollection)

- [<span data-ttu-id="0ecba-125">Iterators</span><span class="sxs-lookup"><span data-stu-id="0ecba-125">Iterators</span></span>](#BKMK_Iterators)

<a name="BKMK_SimpleCollection"></a>

## <a name="using-a-simple-collection"></a><span data-ttu-id="0ecba-126">Utilisation d’une collection simple</span><span class="sxs-lookup"><span data-stu-id="0ecba-126">Using a Simple Collection</span></span>

<span data-ttu-id="0ecba-127">Les exemples de cette section utilisent la classe <xref:System.Collections.Generic.List%601> générique, qui vous permet d’utiliser une liste d’objets fortement typée.</span><span class="sxs-lookup"><span data-stu-id="0ecba-127">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>

<span data-ttu-id="0ecba-128">L’exemple suivant crée une liste de chaînes, puis itère au sein des chaînes à l’aide d’une instruction [foreach](../../language-reference/keywords/foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="0ecba-128">The following example creates a list of strings and then iterates through the strings by using a [foreach](../../language-reference/keywords/foreach-in.md) statement.</span></span>

```csharp
// Create a list of strings.
var salmons = new List<string>();
salmons.Add("chinook");
salmons.Add("coho");
salmons.Add("pink");
salmons.Add("sockeye");

// Iterate through the list.
foreach (var salmon in salmons)
{
    Console.Write(salmon + " ");
}
// Output: chinook coho pink sockeye
```

<span data-ttu-id="0ecba-129">Si le contenu d’une collection est connu d’avance, vous pouvez utiliser un *initialiseur de collection* pour initialiser la collection.</span><span class="sxs-lookup"><span data-stu-id="0ecba-129">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="0ecba-130">Pour plus d’informations, consultez la page [Initialiseurs d’objets et de collections](../classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="0ecba-130">For more information, see [Object and Collection Initializers](../classes-and-structs/object-and-collection-initializers.md).</span></span>

<span data-ttu-id="0ecba-131">L’exemple suivant est identique à l’exemple précédent, à la différence qu’un initialiseur de collection est utilisé pour ajouter des éléments à la collection.</span><span class="sxs-lookup"><span data-stu-id="0ecba-131">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>

```csharp
// Create a list of strings by using a
// collection initializer.
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };

// Iterate through the list.
foreach (var salmon in salmons)
{
    Console.Write(salmon + " ");
}
// Output: chinook coho pink sockeye
```

<span data-ttu-id="0ecba-132">Vous pouvez utiliser une instruction [for](../../language-reference/keywords/for.md) au lieu d’une instruction `foreach` pour itérer au sein d’une collection.</span><span class="sxs-lookup"><span data-stu-id="0ecba-132">You can use a [for](../../language-reference/keywords/for.md) statement instead of a `foreach` statement to iterate through a collection.</span></span> <span data-ttu-id="0ecba-133">Pour cela, accédez aux éléments de la collection à la position d’index.</span><span class="sxs-lookup"><span data-stu-id="0ecba-133">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="0ecba-134">L’index des éléments commence à 0 et se termine au nombre d’éléments moins 1.</span><span class="sxs-lookup"><span data-stu-id="0ecba-134">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>

<span data-ttu-id="0ecba-135">L’exemple suivant itère au sein des éléments d’une collection à l’aide de `for` au lieu de `foreach`.</span><span class="sxs-lookup"><span data-stu-id="0ecba-135">The following example iterates through the elements of a collection by using `for` instead of `foreach`.</span></span>

```csharp
// Create a list of strings by using a
// collection initializer.
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };

for (var index = 0; index < salmons.Count; index++)
{
    Console.Write(salmons[index] + " ");
}
// Output: chinook coho pink sockeye
```

<span data-ttu-id="0ecba-136">L’exemple suivant supprime un élément de la collection en spécifiant l’objet à supprimer.</span><span class="sxs-lookup"><span data-stu-id="0ecba-136">The following example removes an element from the collection by specifying the object to remove.</span></span>

```csharp
// Create a list of strings by using a
// collection initializer.
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };

// Remove an element from the list by specifying
// the object.
salmons.Remove("coho");

// Iterate through the list.
foreach (var salmon in salmons)
{
    Console.Write(salmon + " ");
}
// Output: chinook pink sockeye
```

<span data-ttu-id="0ecba-137">L’exemple suivant supprime les éléments d’une liste générique.</span><span class="sxs-lookup"><span data-stu-id="0ecba-137">The following example removes elements from a generic list.</span></span> <span data-ttu-id="0ecba-138">À la place d’une instruction `foreach`, une instruction [for](../../language-reference/keywords/for.md), qui itère dans l’ordre décroissant, est utilisée.</span><span class="sxs-lookup"><span data-stu-id="0ecba-138">Instead of a `foreach` statement, a [for](../../language-reference/keywords/for.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="0ecba-139">En effet, avec la méthode <xref:System.Collections.Generic.List%601.RemoveAt%2A>, les éléments après l’élément supprimé ont une valeur d’index moins élevée.</span><span class="sxs-lookup"><span data-stu-id="0ecba-139">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>

```csharp
var numbers = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };

// Remove odd numbers.
for (var index = numbers.Count - 1; index >= 0; index--)
{
    if (numbers[index] % 2 == 1)
    {
        // Remove the element by specifying
        // the zero-based index in the list.
        numbers.RemoveAt(index);
    }
}

// Iterate through the list.
// A lambda expression is placed in the ForEach method
// of the List(T) object.
numbers.ForEach(
    number => Console.Write(number + " "));
// Output: 0 2 4 6 8
```

<span data-ttu-id="0ecba-140">Pour le type d’éléments de <xref:System.Collections.Generic.List%601>, vous pouvez également définir votre propre classe.</span><span class="sxs-lookup"><span data-stu-id="0ecba-140">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="0ecba-141">Dans l’exemple suivant, la classe `Galaxy` qui est utilisée par <xref:System.Collections.Generic.List%601> est définie dans le code.</span><span class="sxs-lookup"><span data-stu-id="0ecba-141">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>

```csharp
private static void IterateThroughList()
{
    var theGalaxies = new List<Galaxy>
        {
            new Galaxy() { Name="Tadpole", MegaLightYears=400},
            new Galaxy() { Name="Pinwheel", MegaLightYears=25},
            new Galaxy() { Name="Milky Way", MegaLightYears=0},
            new Galaxy() { Name="Andromeda", MegaLightYears=3}
        };

    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears);
    }

    // Output:
    //  Tadpole  400
    //  Pinwheel  25
    //  Milky Way  0
    //  Andromeda  3
}

public class Galaxy
{
    public string Name { get; set; }
    public int MegaLightYears { get; set; }
}
```

<a name="BKMK_KindsOfCollections"></a>

## <a name="kinds-of-collections"></a><span data-ttu-id="0ecba-142">Types de collections</span><span class="sxs-lookup"><span data-stu-id="0ecba-142">Kinds of Collections</span></span>

<span data-ttu-id="0ecba-143">De nombreuses collections courantes sont fournies par .NET.</span><span class="sxs-lookup"><span data-stu-id="0ecba-143">Many common collections are provided by .NET.</span></span> <span data-ttu-id="0ecba-144">Chaque type de collection est conçu dans un but spécifique.</span><span class="sxs-lookup"><span data-stu-id="0ecba-144">Each type of collection is designed for a specific purpose.</span></span>

<span data-ttu-id="0ecba-145">Certaines des classes de collection courantes sont décrites dans cette section :</span><span class="sxs-lookup"><span data-stu-id="0ecba-145">Some of the common collection classes are described in this section:</span></span>

- <span data-ttu-id="0ecba-146">Classes <xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="0ecba-146"><xref:System.Collections.Generic> classes</span></span>

- <span data-ttu-id="0ecba-147">Classes <xref:System.Collections.Concurrent></span><span class="sxs-lookup"><span data-stu-id="0ecba-147"><xref:System.Collections.Concurrent> classes</span></span>

- <span data-ttu-id="0ecba-148">Classes <xref:System.Collections></span><span class="sxs-lookup"><span data-stu-id="0ecba-148"><xref:System.Collections> classes</span></span>

<a name="BKMK_Generic"></a>

### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="0ecba-149">Classes System.Collections.Generic</span><span class="sxs-lookup"><span data-stu-id="0ecba-149">System.Collections.Generic Classes</span></span>

<span data-ttu-id="0ecba-150">Vous pouvez créer une collection générique en utilisant l’une des classes dans l’espace de noms <xref:System.Collections.Generic>.</span><span class="sxs-lookup"><span data-stu-id="0ecba-150">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="0ecba-151">Une collection générique est utile quand chaque élément de la collection a le même type de données.</span><span class="sxs-lookup"><span data-stu-id="0ecba-151">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="0ecba-152">Une collection générique applique un typage fort en autorisant uniquement l’ajout des types de données souhaités.</span><span class="sxs-lookup"><span data-stu-id="0ecba-152">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>

<span data-ttu-id="0ecba-153">Le tableau suivant liste quelques classes de l’espace de noms <xref:System.Collections.Generic?displayProperty=nameWithType> fréquemment utilisées :</span><span class="sxs-lookup"><span data-stu-id="0ecba-153">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="0ecba-154">Classe</span><span class="sxs-lookup"><span data-stu-id="0ecba-154">Class</span></span>|<span data-ttu-id="0ecba-155">Description</span><span class="sxs-lookup"><span data-stu-id="0ecba-155">Description</span></span>|
|---|---|
|<xref:System.Collections.Generic.Dictionary%602>|<span data-ttu-id="0ecba-156">Représente une collection de paires clé/valeur organisées en fonction de la clé.</span><span class="sxs-lookup"><span data-stu-id="0ecba-156">Represents a collection of key/value pairs that are organized based on the key.</span></span>|
|<xref:System.Collections.Generic.List%601>|<span data-ttu-id="0ecba-157">Représente une liste d’objets accessibles par index.</span><span class="sxs-lookup"><span data-stu-id="0ecba-157">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="0ecba-158">Fournit des méthodes de recherche, de tri et de modification de listes.</span><span class="sxs-lookup"><span data-stu-id="0ecba-158">Provides methods to search, sort, and modify lists.</span></span>|
|<xref:System.Collections.Generic.Queue%601>|<span data-ttu-id="0ecba-159">Représente une collection d’objets premier entré, premier sorti (FIFO).</span><span class="sxs-lookup"><span data-stu-id="0ecba-159">Represents a first in, first out (FIFO) collection of objects.</span></span>|
|<xref:System.Collections.Generic.SortedList%602>|<span data-ttu-id="0ecba-160">Représente une collection de paires clé/valeur triées par clé en fonction de l'implémentation <xref:System.Collections.Generic.IComparer%601> associée.</span><span class="sxs-lookup"><span data-stu-id="0ecba-160">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|
|<xref:System.Collections.Generic.Stack%601>|<span data-ttu-id="0ecba-161">Représente une collection d’objets dernier entré, premier sorti (LIFO).</span><span class="sxs-lookup"><span data-stu-id="0ecba-161">Represents a last in, first out (LIFO) collection of objects.</span></span>|

<span data-ttu-id="0ecba-162">Pour plus d’informations, consultez [Types de collections couramment utilisés](../../../standard/collections/commonly-used-collection-types.md), [Sélection d’une classe de collection](../../../standard/collections/selecting-a-collection-class.md) et <xref:System.Collections.Generic>.</span><span class="sxs-lookup"><span data-stu-id="0ecba-162">For additional information, see [Commonly Used Collection Types](../../../standard/collections/commonly-used-collection-types.md), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic>.</span></span>

<a name="BKMK_Concurrent"></a>

### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="0ecba-163">Classes System.Collections.Concurrent</span><span class="sxs-lookup"><span data-stu-id="0ecba-163">System.Collections.Concurrent Classes</span></span>

<span data-ttu-id="0ecba-164">Dans .NET Framework 4 et versions ultérieures, les collections de l' <xref:System.Collections.Concurrent> espace de noms fournissent des opérations thread-safe efficaces pour accéder aux éléments de collection à partir de plusieurs threads.</span><span class="sxs-lookup"><span data-stu-id="0ecba-164">In .NET Framework 4 and later versions, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>

<span data-ttu-id="0ecba-165">Les classes de l’espace de noms <xref:System.Collections.Concurrent> doivent être utilisées à la place des types correspondants dans les espaces de noms <xref:System.Collections.Generic?displayProperty=nameWithType> et <xref:System.Collections?displayProperty=nameWithType> chaque fois que plusieurs threads accèdent simultanément à la collection.</span><span class="sxs-lookup"><span data-stu-id="0ecba-165">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=nameWithType> and <xref:System.Collections?displayProperty=nameWithType> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="0ecba-166">Pour plus d’informations, consultez [Collections thread-safe](../../../standard/collections/thread-safe/index.md) et <xref:System.Collections.Concurrent>.</span><span class="sxs-lookup"><span data-stu-id="0ecba-166">For more information, see [Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.</span></span>

<span data-ttu-id="0ecba-167">Certaines classes incluses dans l’espace de noms <xref:System.Collections.Concurrent> sont <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601> et <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span><span class="sxs-lookup"><span data-stu-id="0ecba-167">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>

<a name="BKMK_Collections"></a>

### <a name="systemcollections-classes"></a><span data-ttu-id="0ecba-168">Classes System.Collections</span><span class="sxs-lookup"><span data-stu-id="0ecba-168">System.Collections Classes</span></span>

<span data-ttu-id="0ecba-169">Les classes de l’espace de noms <xref:System.Collections?displayProperty=nameWithType> ne stockent pas les éléments comme des objets spécifiquement typés, mais comme des objets de type `Object`.</span><span class="sxs-lookup"><span data-stu-id="0ecba-169">The classes in the <xref:System.Collections?displayProperty=nameWithType> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>

<span data-ttu-id="0ecba-170">Si possible, vous devez utiliser les collections génériques dans l’espace de noms <xref:System.Collections.Generic?displayProperty=nameWithType> ou <xref:System.Collections.Concurrent> à la place des types hérités de l’espace de noms `System.Collections`.</span><span class="sxs-lookup"><span data-stu-id="0ecba-170">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>

<span data-ttu-id="0ecba-171">Le tableau suivant répertorie certaines des classes fréquemment utilisées de l’espace de noms `System.Collections` :</span><span class="sxs-lookup"><span data-stu-id="0ecba-171">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>

|<span data-ttu-id="0ecba-172">Classe</span><span class="sxs-lookup"><span data-stu-id="0ecba-172">Class</span></span>|<span data-ttu-id="0ecba-173">Description</span><span class="sxs-lookup"><span data-stu-id="0ecba-173">Description</span></span>|
|---|---|
|<xref:System.Collections.ArrayList>|<span data-ttu-id="0ecba-174">Représente un tableau d’objets dont la taille est augmentée de manière dynamique selon les besoins.</span><span class="sxs-lookup"><span data-stu-id="0ecba-174">Represents an array of objects whose size is dynamically increased as required.</span></span>|
|<xref:System.Collections.Hashtable>|<span data-ttu-id="0ecba-175">Représente une collection de paires clé/valeur qui sont organisées en fonction du code de hachage de la clé.</span><span class="sxs-lookup"><span data-stu-id="0ecba-175">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|
|<xref:System.Collections.Queue>|<span data-ttu-id="0ecba-176">Représente une collection d’objets premier entré, premier sorti (FIFO).</span><span class="sxs-lookup"><span data-stu-id="0ecba-176">Represents a first in, first out (FIFO) collection of objects.</span></span>|
|<xref:System.Collections.Stack>|<span data-ttu-id="0ecba-177">Représente une collection d’objets dernier entré, premier sorti (LIFO).</span><span class="sxs-lookup"><span data-stu-id="0ecba-177">Represents a last in, first out (LIFO) collection of objects.</span></span>|

<span data-ttu-id="0ecba-178">L’espace de noms <xref:System.Collections.Specialized> fournit des classes de collection spécialisées et fortement typées, telles que les collections à chaîne unique et les dictionnaires de liste liée et hybrides.</span><span class="sxs-lookup"><span data-stu-id="0ecba-178">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>

<a name="BKMK_KeyValuePairs"></a>

## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="0ecba-179">Implémentation d’une collection de paires clé/valeur</span><span class="sxs-lookup"><span data-stu-id="0ecba-179">Implementing a Collection of Key/Value Pairs</span></span>

<span data-ttu-id="0ecba-180">La collection générique <xref:System.Collections.Generic.Dictionary%602> vous permet d’accéder aux éléments d’une collection à l’aide de la clé de chaque élément.</span><span class="sxs-lookup"><span data-stu-id="0ecba-180">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="0ecba-181">Chaque ajout au dictionnaire se compose d’une valeur et de sa clé associée.</span><span class="sxs-lookup"><span data-stu-id="0ecba-181">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="0ecba-182">La récupération d’une valeur à l’aide de sa clé est très rapide, car la classe `Dictionary` est implémentée en tant que table de hachage.</span><span class="sxs-lookup"><span data-stu-id="0ecba-182">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>

<span data-ttu-id="0ecba-183">L’exemple suivant crée une collection `Dictionary` et itère au sein du dictionnaire à l’aide d’une instruction `foreach`.</span><span class="sxs-lookup"><span data-stu-id="0ecba-183">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `foreach` statement.</span></span>

```csharp
private static void IterateThruDictionary()
{
    Dictionary<string, Element> elements = BuildDictionary();

    foreach (KeyValuePair<string, Element> kvp in elements)
    {
        Element theElement = kvp.Value;

        Console.WriteLine("key: " + kvp.Key);
        Console.WriteLine("values: " + theElement.Symbol + " " +
            theElement.Name + " " + theElement.AtomicNumber);
    }
}

private static Dictionary<string, Element> BuildDictionary()
{
    var elements = new Dictionary<string, Element>();

    AddToDictionary(elements, "K", "Potassium", 19);
    AddToDictionary(elements, "Ca", "Calcium", 20);
    AddToDictionary(elements, "Sc", "Scandium", 21);
    AddToDictionary(elements, "Ti", "Titanium", 22);

    return elements;
}

private static void AddToDictionary(Dictionary<string, Element> elements,
    string symbol, string name, int atomicNumber)
{
    Element theElement = new Element();

    theElement.Symbol = symbol;
    theElement.Name = name;
    theElement.AtomicNumber = atomicNumber;

    elements.Add(key: theElement.Symbol, value: theElement);
}

public class Element
{
    public string Symbol { get; set; }
    public string Name { get; set; }
    public int AtomicNumber { get; set; }
}
```

<span data-ttu-id="0ecba-184">Au lieu d’utiliser un initialiseur de collection pour générer la collection `Dictionary`, vous pouvez remplacer les méthodes `BuildDictionary` et `AddToDictionary` par la méthode suivante.</span><span class="sxs-lookup"><span data-stu-id="0ecba-184">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>

```csharp
private static Dictionary<string, Element> BuildDictionary2()
{
    return new Dictionary<string, Element>
    {
        {"K",
            new Element() { Symbol="K", Name="Potassium", AtomicNumber=19}},
        {"Ca",
            new Element() { Symbol="Ca", Name="Calcium", AtomicNumber=20}},
        {"Sc",
            new Element() { Symbol="Sc", Name="Scandium", AtomicNumber=21}},
        {"Ti",
            new Element() { Symbol="Ti", Name="Titanium", AtomicNumber=22}}
    };
}
```

<span data-ttu-id="0ecba-185">L’exemple suivant utilise la méthode <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> et la propriété <xref:System.Collections.Generic.Dictionary%602.Item%2A> de `Dictionary` pour rechercher rapidement un élément par clé.</span><span class="sxs-lookup"><span data-stu-id="0ecba-185">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="0ecba-186">En C#, la propriété `Item` vous permet d’accéder à un élément de la collection `elements` à l’aide d’`elements[symbol]`.</span><span class="sxs-lookup"><span data-stu-id="0ecba-186">The `Item` property enables you to access an item in the `elements` collection by using the `elements[symbol]` in C#.</span></span>

```csharp
private static void FindInDictionary(string symbol)
{
    Dictionary<string, Element> elements = BuildDictionary();

    if (elements.ContainsKey(symbol) == false)
    {
        Console.WriteLine(symbol + " not found");
    }
    else
    {
        Element theElement = elements[symbol];
        Console.WriteLine("found: " + theElement.Name);
    }
}
```

<span data-ttu-id="0ecba-187">L’exemple suivant utilise à la place la méthode <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> pour rechercher rapidement un élément par clé.</span><span class="sxs-lookup"><span data-stu-id="0ecba-187">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>

```csharp
private static void FindInDictionary2(string symbol)
{
    Dictionary<string, Element> elements = BuildDictionary();

    Element theElement = null;
    if (elements.TryGetValue(symbol, out theElement) == false)
        Console.WriteLine(symbol + " not found");
    else
        Console.WriteLine("found: " + theElement.Name);
}
```

<a name="BKMK_LINQ"></a>

## <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="0ecba-188">Utilisation de LINQ pour accéder à une collection</span><span class="sxs-lookup"><span data-stu-id="0ecba-188">Using LINQ to Access a Collection</span></span>

<span data-ttu-id="0ecba-189">LINQ (Language-Integrated Query) peut être utilisé pour accéder aux collections.</span><span class="sxs-lookup"><span data-stu-id="0ecba-189">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="0ecba-190">Les requêtes LINQ fournissent des fonctionnalités de filtrage, de classement et de regroupement.</span><span class="sxs-lookup"><span data-stu-id="0ecba-190">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="0ecba-191">Pour plus d’informations, consultez [prise en main avec LINQ en C#](linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="0ecba-191">For more information, see [Getting Started with LINQ in C#](linq/index.md).</span></span>

<span data-ttu-id="0ecba-192">L’exemple suivant exécute une requête LINQ sur un `List` générique.</span><span class="sxs-lookup"><span data-stu-id="0ecba-192">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="0ecba-193">La requête LINQ retourne une autre collection qui contient les résultats.</span><span class="sxs-lookup"><span data-stu-id="0ecba-193">The LINQ query returns a different collection that contains the results.</span></span>

```csharp
private static void ShowLINQ()
{
    List<Element> elements = BuildList();

    // LINQ Query.
    var subset = from theElement in elements
                 where theElement.AtomicNumber < 22
                 orderby theElement.Name
                 select theElement;

    foreach (Element theElement in subset)
    {
        Console.WriteLine(theElement.Name + " " + theElement.AtomicNumber);
    }

    // Output:
    //  Calcium 20
    //  Potassium 19
    //  Scandium 21
}

private static List<Element> BuildList()
{
    return new List<Element>
    {
        { new Element() { Symbol="K", Name="Potassium", AtomicNumber=19}},
        { new Element() { Symbol="Ca", Name="Calcium", AtomicNumber=20}},
        { new Element() { Symbol="Sc", Name="Scandium", AtomicNumber=21}},
        { new Element() { Symbol="Ti", Name="Titanium", AtomicNumber=22}}
    };
}

public class Element
{
    public string Symbol { get; set; }
    public string Name { get; set; }
    public int AtomicNumber { get; set; }
}
```

<a name="BKMK_Sorting"></a>

## <a name="sorting-a-collection"></a><span data-ttu-id="0ecba-194">Tri d’une collection</span><span class="sxs-lookup"><span data-stu-id="0ecba-194">Sorting a Collection</span></span>

<span data-ttu-id="0ecba-195">L’exemple suivant illustre une procédure de tri d’une collection.</span><span class="sxs-lookup"><span data-stu-id="0ecba-195">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="0ecba-196">L’exemple trie les instances de la classe `Car` stockées dans un <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="0ecba-196">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="0ecba-197">La classe `Car` implémente l’interface <xref:System.IComparable%601>, ce qui implique l’implémentation de la méthode <xref:System.IComparable%601.CompareTo%2A>.</span><span class="sxs-lookup"><span data-stu-id="0ecba-197">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>

<span data-ttu-id="0ecba-198">Chaque appel à la méthode <xref:System.IComparable%601.CompareTo%2A> effectue une comparaison unique qui est utilisée pour le tri.</span><span class="sxs-lookup"><span data-stu-id="0ecba-198">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="0ecba-199">Le code écrit par l’utilisateur dans la méthode `CompareTo` retourne une valeur pour chaque comparaison de l’objet actuel avec un autre objet.</span><span class="sxs-lookup"><span data-stu-id="0ecba-199">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="0ecba-200">La valeur retournée est inférieure à zéro si l’objet actuel est inférieur à l’autre objet, supérieure à zéro l’objet actuel est supérieur à l’autre et égale à zéro s’ils sont égaux.</span><span class="sxs-lookup"><span data-stu-id="0ecba-200">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="0ecba-201">Cela vous permet de définir dans le code les critères définissant « supérieur à », « inférieur à » et « égal à ».</span><span class="sxs-lookup"><span data-stu-id="0ecba-201">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>

<span data-ttu-id="0ecba-202">Dans la méthode `ListCars`, l’instruction `cars.Sort()` trie la liste.</span><span class="sxs-lookup"><span data-stu-id="0ecba-202">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="0ecba-203">Cet appel à la méthode <xref:System.Collections.Generic.List%601.Sort%2A> de <xref:System.Collections.Generic.List%601> entraîne l’appel automatique de la méthode `CompareTo` pour les objets `Car` dans `List`.</span><span class="sxs-lookup"><span data-stu-id="0ecba-203">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>

```csharp
private static void ListCars()
{
    var cars = new List<Car>
    {
        { new Car() { Name = "car1", Color = "blue", Speed = 20}},
        { new Car() { Name = "car2", Color = "red", Speed = 50}},
        { new Car() { Name = "car3", Color = "green", Speed = 10}},
        { new Car() { Name = "car4", Color = "blue", Speed = 50}},
        { new Car() { Name = "car5", Color = "blue", Speed = 30}},
        { new Car() { Name = "car6", Color = "red", Speed = 60}},
        { new Car() { Name = "car7", Color = "green", Speed = 50}}
    };

    // Sort the cars by color alphabetically, and then by speed
    // in descending order.
    cars.Sort();

    // View all of the cars.
    foreach (Car thisCar in cars)
    {
        Console.Write(thisCar.Color.PadRight(5) + " ");
        Console.Write(thisCar.Speed.ToString() + " ");
        Console.Write(thisCar.Name);
        Console.WriteLine();
    }

    // Output:
    //  blue  50 car4
    //  blue  30 car5
    //  blue  20 car1
    //  green 50 car7
    //  green 10 car3
    //  red   60 car6
    //  red   50 car2
}

public class Car : IComparable<Car>
{
    public string Name { get; set; }
    public int Speed { get; set; }
    public string Color { get; set; }

    public int CompareTo(Car other)
    {
        // A call to this method makes a single comparison that is
        // used for sorting.

        // Determine the relative order of the objects being compared.
        // Sort by color alphabetically, and then by speed in
        // descending order.

        // Compare the colors.
        int compare;
        compare = String.Compare(this.Color, other.Color, true);

        // If the colors are the same, compare the speeds.
        if (compare == 0)
        {
            compare = this.Speed.CompareTo(other.Speed);

            // Use descending order for speed.
            compare = -compare;
        }

        return compare;
    }
}
```

<a name="BKMK_CustomCollection"></a>

## <a name="defining-a-custom-collection"></a><span data-ttu-id="0ecba-204">Définition d’une collection personnalisée</span><span class="sxs-lookup"><span data-stu-id="0ecba-204">Defining a Custom Collection</span></span>

<span data-ttu-id="0ecba-205">Vous pouvez définir une collection en implémentant l’interface <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="0ecba-205">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span>

<span data-ttu-id="0ecba-206">Bien que vous puissiez définir une collection personnalisée, il est généralement préférable d’utiliser les collections incluses dans .NET, qui sont décrites dans [genres de collections](#BKMK_KindsOfCollections) , plus haut dans cet article.</span><span class="sxs-lookup"><span data-stu-id="0ecba-206">Although you can define a custom collection, it is usually better to instead use the collections that are included in .NET, which are described in [Kinds of Collections](#BKMK_KindsOfCollections) earlier in this article.</span></span>

<span data-ttu-id="0ecba-207">L’exemple suivant définit une classe de collection personnalisée nommée `AllColors`.</span><span class="sxs-lookup"><span data-stu-id="0ecba-207">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="0ecba-208">Cette classe implémente l’interface <xref:System.Collections.IEnumerable>, ce qui implique l’implémentation de la méthode <xref:System.Collections.IEnumerable.GetEnumerator%2A>.</span><span class="sxs-lookup"><span data-stu-id="0ecba-208">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>

<span data-ttu-id="0ecba-209">La méthode `GetEnumerator` retourne une instance de la classe `ColorEnumerator`.</span><span class="sxs-lookup"><span data-stu-id="0ecba-209">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="0ecba-210">`ColorEnumerator` implémente l’interface <xref:System.Collections.IEnumerator>, ce qui implique l’implémentation de la propriété <xref:System.Collections.IEnumerator.Current%2A>, la méthode <xref:System.Collections.IEnumerator.MoveNext%2A> et la méthode <xref:System.Collections.IEnumerator.Reset%2A>.</span><span class="sxs-lookup"><span data-stu-id="0ecba-210">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>

```csharp
private static void ListColors()
{
    var colors = new AllColors();

    foreach (Color theColor in colors)
    {
        Console.Write(theColor.Name + " ");
    }
    Console.WriteLine();
    // Output: red blue green
}

// Collection class.
public class AllColors : System.Collections.IEnumerable
{
    Color[] _colors =
    {
        new Color() { Name = "red" },
        new Color() { Name = "blue" },
        new Color() { Name = "green" }
    };

    public System.Collections.IEnumerator GetEnumerator()
    {
        return new ColorEnumerator(_colors);

        // Instead of creating a custom enumerator, you could
        // use the GetEnumerator of the array.
        //return _colors.GetEnumerator();
    }

    // Custom enumerator.
    private class ColorEnumerator : System.Collections.IEnumerator
    {
        private Color[] _colors;
        private int _position = -1;

        public ColorEnumerator(Color[] colors)
        {
            _colors = colors;
        }

        object System.Collections.IEnumerator.Current
        {
            get
            {
                return _colors[_position];
            }
        }

        bool System.Collections.IEnumerator.MoveNext()
        {
            _position++;
            return (_position < _colors.Length);
        }

        void System.Collections.IEnumerator.Reset()
        {
            _position = -1;
        }
    }
}

// Element class.
public class Color
{
    public string Name { get; set; }
}
```

<a name="BKMK_Iterators"></a>

## <a name="iterators"></a><span data-ttu-id="0ecba-211">Iterators</span><span class="sxs-lookup"><span data-stu-id="0ecba-211">Iterators</span></span>

<span data-ttu-id="0ecba-212">Un *itérateur* est utilisé pour exécuter une itération personnalisée sur une collection.</span><span class="sxs-lookup"><span data-stu-id="0ecba-212">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="0ecba-213">Un itérateur peut être une méthode ou un accesseur `get`.</span><span class="sxs-lookup"><span data-stu-id="0ecba-213">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="0ecba-214">Un itérateur utilise une instruction [yield return](../../language-reference/keywords/yield.md) pour retourner chaque élément de la collection un par un.</span><span class="sxs-lookup"><span data-stu-id="0ecba-214">An iterator uses a [yield return](../../language-reference/keywords/yield.md) statement to return each element of the collection one at a time.</span></span>

<span data-ttu-id="0ecba-215">Vous appelez un itérateur en utilisant une instruction [foreach](../../language-reference/keywords/foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="0ecba-215">You call an iterator by using a [foreach](../../language-reference/keywords/foreach-in.md) statement.</span></span> <span data-ttu-id="0ecba-216">Chaque itération de la boucle `foreach` appelle l’itérateur.</span><span class="sxs-lookup"><span data-stu-id="0ecba-216">Each iteration of the `foreach` loop calls the iterator.</span></span> <span data-ttu-id="0ecba-217">Quand une instruction `yield return` est atteinte dans l’itérateur, une expression est retournée et la localisation actuelle dans le code est retenue.</span><span class="sxs-lookup"><span data-stu-id="0ecba-217">When a `yield return` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="0ecba-218">L’exécution est redémarrée à partir de cet emplacement la prochaine fois que l’itérateur est appelé.</span><span class="sxs-lookup"><span data-stu-id="0ecba-218">Execution is restarted from that location the next time that the iterator is called.</span></span>

<span data-ttu-id="0ecba-219">Pour plus d’informations, consultez [Itérateurs (C#)](./iterators.md).</span><span class="sxs-lookup"><span data-stu-id="0ecba-219">For more information, see [Iterators (C#)](./iterators.md).</span></span>

<span data-ttu-id="0ecba-220">L'exemple suivant utilise une méthode Iterator.</span><span class="sxs-lookup"><span data-stu-id="0ecba-220">The following example uses an iterator method.</span></span> <span data-ttu-id="0ecba-221">La méthode Iterator a une instruction `yield return` qui se trouve à l’intérieur d’une boucle [for](../../language-reference/keywords/for.md).</span><span class="sxs-lookup"><span data-stu-id="0ecba-221">The iterator method has a `yield return` statement that is inside a [for](../../language-reference/keywords/for.md) loop.</span></span> <span data-ttu-id="0ecba-222">Dans la méthode `ListEvenNumbers`, chaque itération du corps de l’instruction `foreach` crée un appel à la méthode Iterator, qui continue sur l’instruction `yield return` suivante.</span><span class="sxs-lookup"><span data-stu-id="0ecba-222">In the `ListEvenNumbers` method, each iteration of the `foreach` statement body creates a call to the iterator method, which proceeds to the next `yield return` statement.</span></span>

```csharp
private static void ListEvenNumbers()
{
    foreach (int number in EvenSequence(5, 18))
    {
        Console.Write(number.ToString() + " ");
    }
    Console.WriteLine();
    // Output: 6 8 10 12 14 16 18
}

private static IEnumerable<int> EvenSequence(
    int firstNumber, int lastNumber)
{
    // Yield even numbers in the range.
    for (var number = firstNumber; number <= lastNumber; number++)
    {
        if (number % 2 == 0)
        {
            yield return number;
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="0ecba-223">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ecba-223">See also</span></span>

- [<span data-ttu-id="0ecba-224">Initialiseurs d’objets et de collections</span><span class="sxs-lookup"><span data-stu-id="0ecba-224">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)
- [<span data-ttu-id="0ecba-225">Concepts de programmation (C#)</span><span class="sxs-lookup"><span data-stu-id="0ecba-225">Programming Concepts (C#)</span></span>](./index.md)
- [<span data-ttu-id="0ecba-226">Option Strict Statement</span><span class="sxs-lookup"><span data-stu-id="0ecba-226">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="0ecba-227">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="0ecba-227">LINQ to Objects (C#)</span></span>](./linq/linq-to-objects.md)
- [<span data-ttu-id="0ecba-228">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="0ecba-228">Parallel LINQ (PLINQ)</span></span>](../../../standard/parallel-programming/introduction-to-plinq.md)
- [<span data-ttu-id="0ecba-229">Collections et structures de données</span><span class="sxs-lookup"><span data-stu-id="0ecba-229">Collections and Data Structures</span></span>](../../../standard/collections/index.md)
- [<span data-ttu-id="0ecba-230">Sélection d’une classe de collection</span><span class="sxs-lookup"><span data-stu-id="0ecba-230">Selecting a Collection Class</span></span>](../../../standard/collections/selecting-a-collection-class.md)
- [<span data-ttu-id="0ecba-231">Comparaisons et tris dans les collections</span><span class="sxs-lookup"><span data-stu-id="0ecba-231">Comparisons and Sorts Within Collections</span></span>](../../../standard/collections/comparisons-and-sorts-within-collections.md)
- [<span data-ttu-id="0ecba-232">Quand utiliser des collections génériques</span><span class="sxs-lookup"><span data-stu-id="0ecba-232">When to Use Generic Collections</span></span>](../../../standard/collections/when-to-use-generic-collections.md)

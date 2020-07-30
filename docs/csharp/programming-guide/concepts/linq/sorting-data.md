---
title: Tri des données (C#)
description: En savoir plus sur les opérations de tri et les méthodes d’opérateur de requête standard qui effectuent des opérations de tri dans LINQ en C#.
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 5feeb0e2229fc370fdcb9608817f41832bffd7cc
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302332"
---
# <a name="sorting-data-c"></a><span data-ttu-id="c4919-103">Tri des données (C#)</span><span class="sxs-lookup"><span data-stu-id="c4919-103">Sorting Data (C#)</span></span>
<span data-ttu-id="c4919-104">Une opération de tri ordonne les éléments d’une séquence en fonction d’un ou de plusieurs attributs.</span><span class="sxs-lookup"><span data-stu-id="c4919-104">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="c4919-105">Le premier critère de tri effectue un tri principal sur les éléments.</span><span class="sxs-lookup"><span data-stu-id="c4919-105">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="c4919-106">En spécifiant un deuxième critère de tri, vous pouvez trier les éléments dans chaque groupe de tri principal.</span><span class="sxs-lookup"><span data-stu-id="c4919-106">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="c4919-107">L’illustration suivante montre les résultats d’une opération de tri par ordre alphabétique sur une séquence de caractères :</span><span class="sxs-lookup"><span data-stu-id="c4919-107">The following illustration shows the results of an alphabetical sort operation on a sequence of characters:</span></span>
  
 ![Graphique montrant une opération de tri par ordre alphabétique.](./media/sorting-data/alphabetical-sort-operation.png)  
  
 <span data-ttu-id="c4919-109">Les méthodes d’opérateurs de requête standard qui trient les données sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="c4919-109">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c4919-110">Méthodes</span><span class="sxs-lookup"><span data-stu-id="c4919-110">Methods</span></span>  
  
|<span data-ttu-id="c4919-111">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="c4919-111">Method Name</span></span>|<span data-ttu-id="c4919-112">Description</span><span class="sxs-lookup"><span data-stu-id="c4919-112">Description</span></span>|<span data-ttu-id="c4919-113">Syntaxe d'expression de requête C#</span><span class="sxs-lookup"><span data-stu-id="c4919-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="c4919-114">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="c4919-114">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="c4919-115">OrderBy</span><span class="sxs-lookup"><span data-stu-id="c4919-115">OrderBy</span></span>|<span data-ttu-id="c4919-116">Trie les valeurs dans l’ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="c4919-116">Sorts values in ascending order.</span></span>|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c4919-117">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="c4919-117">OrderByDescending</span></span>|<span data-ttu-id="c4919-118">Trie les valeurs dans l’ordre décroissant.</span><span class="sxs-lookup"><span data-stu-id="c4919-118">Sorts values in descending order.</span></span>|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c4919-119">ThenBy</span><span class="sxs-lookup"><span data-stu-id="c4919-119">ThenBy</span></span>|<span data-ttu-id="c4919-120">Effectue un tri secondaire dans l’ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="c4919-120">Performs a secondary sort in ascending order.</span></span>|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c4919-121">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="c4919-121">ThenByDescending</span></span>|<span data-ttu-id="c4919-122">Effectue un tri secondaire dans l’ordre décroissant.</span><span class="sxs-lookup"><span data-stu-id="c4919-122">Performs a secondary sort in descending order.</span></span>|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c4919-123">Inverser</span><span class="sxs-lookup"><span data-stu-id="c4919-123">Reverse</span></span>|<span data-ttu-id="c4919-124">Inverse l’ordre des éléments dans une collection.</span><span class="sxs-lookup"><span data-stu-id="c4919-124">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="c4919-125">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="c4919-125">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="c4919-126">Exemples de syntaxe d'expression de requête</span><span class="sxs-lookup"><span data-stu-id="c4919-126">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="c4919-127">Exemples de tri principal</span><span class="sxs-lookup"><span data-stu-id="c4919-127">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="c4919-128">Tri principal croissant</span><span class="sxs-lookup"><span data-stu-id="c4919-128">Primary Ascending Sort</span></span>  
 <span data-ttu-id="c4919-129">L’exemple suivant montre comment utiliser la clause `orderby` dans une requête LINQ pour trier les chaînes dans un tableau par longueur de chaîne, dans l’ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="c4919-129">The following example demonstrates how to use the `orderby` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
    quick  
    brown  
    jumps  
*/  
```  
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="c4919-130">Tri principal décroissant</span><span class="sxs-lookup"><span data-stu-id="c4919-130">Primary Descending Sort</span></span>  
 <span data-ttu-id="c4919-131">L’exemple suivant montre comment utiliser la clause `orderby descending` dans une requête LINQ pour trier les chaînes selon leur première lettre, dans l’ordre décroissant.</span><span class="sxs-lookup"><span data-stu-id="c4919-131">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Substring(0, 1) descending  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    quick  
    jumps  
    fox  
    brown  
*/  
```  
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="c4919-132">Exemples de tri secondaire</span><span class="sxs-lookup"><span data-stu-id="c4919-132">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="c4919-133">Tri secondaire croissant</span><span class="sxs-lookup"><span data-stu-id="c4919-133">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="c4919-134">L’exemple suivant montre comment utiliser la clause `orderby` dans une requête LINQ pour effectuer un tri principal et un tri secondaire des chaînes dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="c4919-134">The following example demonstrates how to use the `orderby` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="c4919-135">Les chaînes sont triées en premier lieu selon leur longueur, puis secondairement en fonction de la première lettre de la chaîne, chaque fois dans l’ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="c4919-135">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length, word.Substring(0, 1)  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    fox  
    the  
    brown  
    jumps  
    quick  
*/  
```  
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="c4919-136">Tri secondaire décroissant</span><span class="sxs-lookup"><span data-stu-id="c4919-136">Secondary Descending Sort</span></span>  
 <span data-ttu-id="c4919-137">L’exemple suivant montre comment utiliser la clause `orderby descending` dans une requête LINQ pour effectuer un tri principal dans l’ordre croissant et un tri secondaire dans l’ordre décroissant.</span><span class="sxs-lookup"><span data-stu-id="c4919-137">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="c4919-138">Les chaînes sont triées en premier lieu selon leur longueur, puis secondairement en fonction de la première lettre de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="c4919-138">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length, word.Substring(0, 1) descending  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
    quick  
    jumps  
    brown  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="c4919-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4919-139">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="c4919-140">Vue d’ensemble des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="c4919-140">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="c4919-141">orderby, clause</span><span class="sxs-lookup"><span data-stu-id="c4919-141">orderby clause</span></span>](../../../language-reference/keywords/orderby-clause.md)
- [<span data-ttu-id="c4919-142">Classer les résultats d’une clause join</span><span class="sxs-lookup"><span data-stu-id="c4919-142">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="c4919-143">Guide pratique pour trier ou filtrer des données texte par mot ou par champ (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="c4919-143">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

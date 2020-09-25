---
title: Tri des données (C#)
description: En savoir plus sur les opérations de tri et les méthodes d’opérateur de requête standard qui effectuent des opérations de tri dans LINQ en C#.
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 0665e5dec95fd2929d24d82568de66597df1c0bd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195504"
---
# <a name="sorting-data-c"></a><span data-ttu-id="0f0ae-103">Tri des données (C#)</span><span class="sxs-lookup"><span data-stu-id="0f0ae-103">Sorting Data (C#)</span></span>

<span data-ttu-id="0f0ae-104">Une opération de tri ordonne les éléments d’une séquence en fonction d’un ou de plusieurs attributs.</span><span class="sxs-lookup"><span data-stu-id="0f0ae-104">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="0f0ae-105">Le premier critère de tri effectue un tri principal sur les éléments.</span><span class="sxs-lookup"><span data-stu-id="0f0ae-105">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="0f0ae-106">En spécifiant un deuxième critère de tri, vous pouvez trier les éléments dans chaque groupe de tri principal.</span><span class="sxs-lookup"><span data-stu-id="0f0ae-106">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="0f0ae-107">L’illustration suivante montre les résultats d’une opération de tri par ordre alphabétique sur une séquence de caractères :</span><span class="sxs-lookup"><span data-stu-id="0f0ae-107">The following illustration shows the results of an alphabetical sort operation on a sequence of characters:</span></span>
  
 ![Graphique montrant une opération de tri par ordre alphabétique.](./media/sorting-data/alphabetical-sort-operation.png)  
  
 <span data-ttu-id="0f0ae-109">Les méthodes d’opérateurs de requête standard qui trient les données sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="0f0ae-109">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0f0ae-110">Méthodes</span><span class="sxs-lookup"><span data-stu-id="0f0ae-110">Methods</span></span>  
  
|<span data-ttu-id="0f0ae-111">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="0f0ae-111">Method Name</span></span>|<span data-ttu-id="0f0ae-112">Description</span><span class="sxs-lookup"><span data-stu-id="0f0ae-112">Description</span></span>|<span data-ttu-id="0f0ae-113">Syntaxe d'expression de requête C#</span><span class="sxs-lookup"><span data-stu-id="0f0ae-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="0f0ae-114">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="0f0ae-114">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="0f0ae-115">OrderBy</span><span class="sxs-lookup"><span data-stu-id="0f0ae-115">OrderBy</span></span>|<span data-ttu-id="0f0ae-116">Trie les valeurs dans l’ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="0f0ae-116">Sorts values in ascending order.</span></span>|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="0f0ae-117">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="0f0ae-117">OrderByDescending</span></span>|<span data-ttu-id="0f0ae-118">Trie les valeurs dans l’ordre décroissant.</span><span class="sxs-lookup"><span data-stu-id="0f0ae-118">Sorts values in descending order.</span></span>|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="0f0ae-119">ThenBy</span><span class="sxs-lookup"><span data-stu-id="0f0ae-119">ThenBy</span></span>|<span data-ttu-id="0f0ae-120">Effectue un tri secondaire dans l’ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="0f0ae-120">Performs a secondary sort in ascending order.</span></span>|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="0f0ae-121">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="0f0ae-121">ThenByDescending</span></span>|<span data-ttu-id="0f0ae-122">Effectue un tri secondaire dans l’ordre décroissant.</span><span class="sxs-lookup"><span data-stu-id="0f0ae-122">Performs a secondary sort in descending order.</span></span>|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="0f0ae-123">Inverser</span><span class="sxs-lookup"><span data-stu-id="0f0ae-123">Reverse</span></span>|<span data-ttu-id="0f0ae-124">Inverse l’ordre des éléments dans une collection.</span><span class="sxs-lookup"><span data-stu-id="0f0ae-124">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="0f0ae-125">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="0f0ae-125">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="0f0ae-126">Exemples de syntaxe d'expression de requête</span><span class="sxs-lookup"><span data-stu-id="0f0ae-126">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="0f0ae-127">Exemples de tri principal</span><span class="sxs-lookup"><span data-stu-id="0f0ae-127">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="0f0ae-128">Tri principal croissant</span><span class="sxs-lookup"><span data-stu-id="0f0ae-128">Primary Ascending Sort</span></span>  

 <span data-ttu-id="0f0ae-129">L’exemple suivant montre comment utiliser la clause `orderby` dans une requête LINQ pour trier les chaînes dans un tableau par longueur de chaîne, dans l’ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="0f0ae-129">The following example demonstrates how to use the `orderby` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
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
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="0f0ae-130">Tri principal décroissant</span><span class="sxs-lookup"><span data-stu-id="0f0ae-130">Primary Descending Sort</span></span>  

 <span data-ttu-id="0f0ae-131">L’exemple suivant montre comment utiliser la clause `orderby descending` dans une requête LINQ pour trier les chaînes selon leur première lettre, dans l’ordre décroissant.</span><span class="sxs-lookup"><span data-stu-id="0f0ae-131">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
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
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="0f0ae-132">Exemples de tri secondaire</span><span class="sxs-lookup"><span data-stu-id="0f0ae-132">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="0f0ae-133">Tri secondaire croissant</span><span class="sxs-lookup"><span data-stu-id="0f0ae-133">Secondary Ascending Sort</span></span>  

 <span data-ttu-id="0f0ae-134">L’exemple suivant montre comment utiliser la clause `orderby` dans une requête LINQ pour effectuer un tri principal et un tri secondaire des chaînes dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="0f0ae-134">The following example demonstrates how to use the `orderby` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="0f0ae-135">Les chaînes sont triées en premier lieu selon leur longueur, puis secondairement en fonction de la première lettre de la chaîne, chaque fois dans l’ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="0f0ae-135">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
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
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="0f0ae-136">Tri secondaire décroissant</span><span class="sxs-lookup"><span data-stu-id="0f0ae-136">Secondary Descending Sort</span></span>  

 <span data-ttu-id="0f0ae-137">L’exemple suivant montre comment utiliser la clause `orderby descending` dans une requête LINQ pour effectuer un tri principal dans l’ordre croissant et un tri secondaire dans l’ordre décroissant.</span><span class="sxs-lookup"><span data-stu-id="0f0ae-137">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="0f0ae-138">Les chaînes sont triées en premier lieu selon leur longueur, puis secondairement en fonction de la première lettre de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="0f0ae-138">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0f0ae-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f0ae-139">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="0f0ae-140">Présentation des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="0f0ae-140">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="0f0ae-141">orderby, clause</span><span class="sxs-lookup"><span data-stu-id="0f0ae-141">orderby clause</span></span>](../../../language-reference/keywords/orderby-clause.md)
- [<span data-ttu-id="0f0ae-142">Classer les résultats d’une clause join</span><span class="sxs-lookup"><span data-stu-id="0f0ae-142">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="0f0ae-143">Guide pratique pour trier ou filtrer des données texte par mot ou par champ (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="0f0ae-143">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

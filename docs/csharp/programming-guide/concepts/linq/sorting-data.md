---
title: Tri des données (C#)
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 8db5ab2ead0e59b8d41d83704ff237d4493155c3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346457"
---
# <a name="sorting-data-c"></a><span data-ttu-id="74365-102">Tri des données (C#)</span><span class="sxs-lookup"><span data-stu-id="74365-102">Sorting Data (C#)</span></span>
<span data-ttu-id="74365-103">Une opération de tri ordonne les éléments d’une séquence en fonction d’un ou de plusieurs attributs.</span><span class="sxs-lookup"><span data-stu-id="74365-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="74365-104">Le premier critère de tri effectue un tri principal sur les éléments.</span><span class="sxs-lookup"><span data-stu-id="74365-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="74365-105">En spécifiant un deuxième critère de tri, vous pouvez trier les éléments dans chaque groupe de tri principal.</span><span class="sxs-lookup"><span data-stu-id="74365-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="74365-106">L’illustration suivante montre les résultats d’une opération de tri par ordre alphabétique sur une séquence de caractères :</span><span class="sxs-lookup"><span data-stu-id="74365-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters:</span></span> 
  
 ![Graphique montrant une opération de tri par ordre alphabétique.](./media/sorting-data/alphabetical-sort-operation.png)  
  
 <span data-ttu-id="74365-108">Les méthodes d’opérateurs de requête standard qui trient les données sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="74365-108">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="74365-109">Méthodes</span><span class="sxs-lookup"><span data-stu-id="74365-109">Methods</span></span>  
  
|<span data-ttu-id="74365-110">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="74365-110">Method Name</span></span>|<span data-ttu-id="74365-111">Description</span><span class="sxs-lookup"><span data-stu-id="74365-111">Description</span></span>|<span data-ttu-id="74365-112">Syntaxe d'expression de requête C#</span><span class="sxs-lookup"><span data-stu-id="74365-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="74365-113">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="74365-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="74365-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="74365-114">OrderBy</span></span>|<span data-ttu-id="74365-115">Trie les valeurs dans l’ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="74365-115">Sorts values in ascending order.</span></span>|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="74365-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="74365-116">OrderByDescending</span></span>|<span data-ttu-id="74365-117">Trie les valeurs dans l’ordre décroissant.</span><span class="sxs-lookup"><span data-stu-id="74365-117">Sorts values in descending order.</span></span>|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="74365-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="74365-118">ThenBy</span></span>|<span data-ttu-id="74365-119">Effectue un tri secondaire dans l’ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="74365-119">Performs a secondary sort in ascending order.</span></span>|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="74365-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="74365-120">ThenByDescending</span></span>|<span data-ttu-id="74365-121">Effectue un tri secondaire dans l’ordre décroissant.</span><span class="sxs-lookup"><span data-stu-id="74365-121">Performs a secondary sort in descending order.</span></span>|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="74365-122">Reverse</span><span class="sxs-lookup"><span data-stu-id="74365-122">Reverse</span></span>|<span data-ttu-id="74365-123">Inverse l’ordre des éléments dans une collection.</span><span class="sxs-lookup"><span data-stu-id="74365-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="74365-124">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="74365-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="74365-125">Exemples de syntaxe d'expression de requête</span><span class="sxs-lookup"><span data-stu-id="74365-125">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="74365-126">Exemples de tri principal</span><span class="sxs-lookup"><span data-stu-id="74365-126">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="74365-127">Tri principal croissant</span><span class="sxs-lookup"><span data-stu-id="74365-127">Primary Ascending Sort</span></span>  
 <span data-ttu-id="74365-128">L’exemple suivant montre comment utiliser la clause `orderby` dans une requête LINQ pour trier les chaînes dans un tableau par longueur de chaîne, dans l’ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="74365-128">The following example demonstrates how to use the `orderby` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
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
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="74365-129">Tri principal décroissant</span><span class="sxs-lookup"><span data-stu-id="74365-129">Primary Descending Sort</span></span>  
 <span data-ttu-id="74365-130">L’exemple suivant montre comment utiliser la clause `orderby descending` dans une requête LINQ pour trier les chaînes selon leur première lettre, dans l’ordre décroissant.</span><span class="sxs-lookup"><span data-stu-id="74365-130">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
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
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="74365-131">Exemples de tri secondaire</span><span class="sxs-lookup"><span data-stu-id="74365-131">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="74365-132">Tri secondaire croissant</span><span class="sxs-lookup"><span data-stu-id="74365-132">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="74365-133">L’exemple suivant montre comment utiliser la clause `orderby` dans une requête LINQ pour effectuer un tri principal et un tri secondaire des chaînes dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="74365-133">The following example demonstrates how to use the `orderby` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="74365-134">Les chaînes sont triées en premier lieu selon leur longueur, puis secondairement en fonction de la première lettre de la chaîne, chaque fois dans l’ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="74365-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
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
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="74365-135">Tri secondaire décroissant</span><span class="sxs-lookup"><span data-stu-id="74365-135">Secondary Descending Sort</span></span>  
 <span data-ttu-id="74365-136">L’exemple suivant montre comment utiliser la clause `orderby descending` dans une requête LINQ pour effectuer un tri principal dans l’ordre croissant et un tri secondaire dans l’ordre décroissant.</span><span class="sxs-lookup"><span data-stu-id="74365-136">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="74365-137">Les chaînes sont triées en premier lieu selon leur longueur, puis secondairement en fonction de la première lettre de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="74365-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="74365-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74365-138">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="74365-139">Vue d’ensemble des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="74365-139">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="74365-140">orderby, clause</span><span class="sxs-lookup"><span data-stu-id="74365-140">orderby clause</span></span>](../../../language-reference/keywords/orderby-clause.md)
- [<span data-ttu-id="74365-141">Classer les résultats d’une clause Join</span><span class="sxs-lookup"><span data-stu-id="74365-141">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="74365-142">Guide pratique pour trier ou filtrer des données texte par mot ou par champ (LINQC#) ()</span><span class="sxs-lookup"><span data-stu-id="74365-142">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

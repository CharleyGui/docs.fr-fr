---
title: Regroupement des données (C#)
ms.date: 07/20/2015
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
ms.openlocfilehash: e7f10b121a7a1c599d88731a806fe784eb1a7e66
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423415"
---
# <a name="grouping-data-c"></a><span data-ttu-id="04153-102">Regroupement des données (C#)</span><span class="sxs-lookup"><span data-stu-id="04153-102">Grouping Data (C#)</span></span>
<span data-ttu-id="04153-103">Le regroupement consiste à placer des données dans des groupes afin que les éléments de chaque groupe partagent un attribut commun.</span><span class="sxs-lookup"><span data-stu-id="04153-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="04153-104">L’illustration suivante montre les résultats du regroupement d’une séquence de caractères.</span><span class="sxs-lookup"><span data-stu-id="04153-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="04153-105">La clé de chaque groupe est le caractère.</span><span class="sxs-lookup"><span data-stu-id="04153-105">The key for each group is the character.</span></span>  
  
 ![Diagramme illustrant une opération de regroupement LINQ.](./media/grouping-data/linq-group-operation.png)  
  
 <span data-ttu-id="04153-107">Les méthodes d’opérateurs de requête standard qui regroupent les éléments de données sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="04153-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="04153-108">Méthodes</span><span class="sxs-lookup"><span data-stu-id="04153-108">Methods</span></span>  
  
|<span data-ttu-id="04153-109">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="04153-109">Method Name</span></span>|<span data-ttu-id="04153-110">Description</span><span class="sxs-lookup"><span data-stu-id="04153-110">Description</span></span>|<span data-ttu-id="04153-111">Syntaxe d'expression de requête C#</span><span class="sxs-lookup"><span data-stu-id="04153-111">C# Query Expression Syntax</span></span>|<span data-ttu-id="04153-112">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="04153-112">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="04153-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="04153-113">GroupBy</span></span>|<span data-ttu-id="04153-114">Regroupe les éléments qui partagent un attribut commun.</span><span class="sxs-lookup"><span data-stu-id="04153-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="04153-115">Chaque groupe est représenté par un objet <xref:System.Linq.IGrouping%602>.</span><span class="sxs-lookup"><span data-stu-id="04153-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`group … by`<br /><br /> <span data-ttu-id="04153-116">ou</span><span class="sxs-lookup"><span data-stu-id="04153-116">-or-</span></span><br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="04153-117">ToLookup</span><span class="sxs-lookup"><span data-stu-id="04153-117">ToLookup</span></span>|<span data-ttu-id="04153-118">Insère des éléments dans un <xref:System.Linq.Lookup%602> (un dictionnaire de type un-à-plusieurs) basé sur une fonction de sélecteur de clés.</span><span class="sxs-lookup"><span data-stu-id="04153-118">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="04153-119">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="04153-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="04153-120">Exemple de syntaxe d’expression de requête</span><span class="sxs-lookup"><span data-stu-id="04153-120">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="04153-121">L’exemple de code suivant utilise la clause `group by` pour regrouper des entiers dans une liste selon qu’ils sont pairs ou impairs.</span><span class="sxs-lookup"><span data-stu-id="04153-121">The following code example uses the `group by` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
```csharp  
List<int> numbers = new List<int>() { 35, 44, 200, 84, 3987, 4, 199, 329, 446, 208 };  
  
IEnumerable<IGrouping<int, int>> query = from number in numbers  
                                         group number by number % 2;  
  
foreach (var group in query)  
{  
    Console.WriteLine(group.Key == 0 ? "\nEven numbers:" : "\nOdd numbers:");  
    foreach (int i in group)  
        Console.WriteLine(i);  
}  
  
/* This code produces the following output:  
  
    Odd numbers:  
    35  
    3987  
    199  
    329  
  
    Even numbers:  
    44  
    200  
    84  
    4  
    446  
    208  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="04153-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04153-122">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="04153-123">Vue d’ensemble des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="04153-123">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="04153-124">group, clause</span><span class="sxs-lookup"><span data-stu-id="04153-124">group clause</span></span>](../../../language-reference/keywords/group-clause.md)
- [<span data-ttu-id="04153-125">Comment : créer un groupe imbriqué</span><span class="sxs-lookup"><span data-stu-id="04153-125">How to: Create a Nested Group</span></span>](../../../linq/create-a-nested-group.md)
- [<span data-ttu-id="04153-126">Guide pratique pour regrouper des fichiers par extension (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="04153-126">How to: Group Files by Extension (LINQ) (C#)</span></span>](./how-to-group-files-by-extension-linq.md)
- [<span data-ttu-id="04153-127">Comment : regrouper les résultats d’une requête</span><span class="sxs-lookup"><span data-stu-id="04153-127">How to: Group Query Results</span></span>](../../../linq/group-query-results.md)
- [<span data-ttu-id="04153-128">Guide pratique pour effectuer une sous-requête sur une opération de regroupement</span><span class="sxs-lookup"><span data-stu-id="04153-128">How to: Perform a Subquery on a Grouping Operation</span></span>](../../../linq/perform-a-subquery-on-a-grouping-operation.md)
- [<span data-ttu-id="04153-129">Guide pratique pour fractionner un fichier en plusieurs fichiers à l’aide de groupes (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="04153-129">How to: Split a File Into Many Files by Using Groups (LINQ) (C#)</span></span>](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)

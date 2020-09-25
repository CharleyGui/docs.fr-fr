---
title: Filtrage des données (C#)
description: Le filtrage, également appelé « sélection », limite les résultats en fonction d’une condition. En savoir plus sur les méthodes d’opérateur de requête standard dans LINQ en C# qui effectuent le filtrage.
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: 51bf9f930ba67ba07c7c0f357910d5e36014138d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186040"
---
# <a name="filtering-data-c"></a><span data-ttu-id="34b89-104">Filtrage des données (C#)</span><span class="sxs-lookup"><span data-stu-id="34b89-104">Filtering Data (C#)</span></span>

<span data-ttu-id="34b89-105">Le filtrage fait référence à l’opération de restriction du jeu de résultats pour que celui-ci contienne uniquement les éléments qui répondent à une condition spécifiée.</span><span class="sxs-lookup"><span data-stu-id="34b89-105">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="34b89-106">Cette opération est également appelée « sélection ».</span><span class="sxs-lookup"><span data-stu-id="34b89-106">It is also known as selection.</span></span>  
  
 <span data-ttu-id="34b89-107">L’illustration suivante montre les résultats du filtrage d’une séquence de caractères.</span><span class="sxs-lookup"><span data-stu-id="34b89-107">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="34b89-108">Le prédicat de l’opération de filtrage spécifie que le caractère doit être « A ».</span><span class="sxs-lookup"><span data-stu-id="34b89-108">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 ![Diagramme illustrant une opération de filtrage LINQ](./media/filtering-data/linq-filter-operation.png)  
  
 <span data-ttu-id="34b89-110">Les méthodes d’opérateurs de requête standard qui effectuent des opérations de sélection sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="34b89-110">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="34b89-111">Méthodes</span><span class="sxs-lookup"><span data-stu-id="34b89-111">Methods</span></span>  
  
|<span data-ttu-id="34b89-112">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="34b89-112">Method Name</span></span>|<span data-ttu-id="34b89-113">Description</span><span class="sxs-lookup"><span data-stu-id="34b89-113">Description</span></span>|<span data-ttu-id="34b89-114">Syntaxe d'expression de requête C#</span><span class="sxs-lookup"><span data-stu-id="34b89-114">C# Query Expression Syntax</span></span>|<span data-ttu-id="34b89-115">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="34b89-115">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="34b89-116">OfType</span><span class="sxs-lookup"><span data-stu-id="34b89-116">OfType</span></span>|<span data-ttu-id="34b89-117">Sélectionne des valeurs, en fonction de leur capacité à être castées en un type spécifié.</span><span class="sxs-lookup"><span data-stu-id="34b89-117">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="34b89-118">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="34b89-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="34b89-119">Where</span><span class="sxs-lookup"><span data-stu-id="34b89-119">Where</span></span>|<span data-ttu-id="34b89-120">Sélectionne les valeurs qui sont basées sur une fonction de prédicat.</span><span class="sxs-lookup"><span data-stu-id="34b89-120">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="34b89-121">Exemple de syntaxe d’expression de requête</span><span class="sxs-lookup"><span data-stu-id="34b89-121">Query Expression Syntax Example</span></span>  

 <span data-ttu-id="34b89-122">L’exemple suivant utilise la clause `where` pour filtrer les chaînes d’un tableau qui ont une longueur spécifique.</span><span class="sxs-lookup"><span data-stu-id="34b89-122">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            where word.Length == 3  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="34b89-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34b89-123">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="34b89-124">Présentation des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="34b89-124">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="34b89-125">clause WHERE</span><span class="sxs-lookup"><span data-stu-id="34b89-125">where clause</span></span>](../../../language-reference/keywords/where-clause.md)
- [<span data-ttu-id="34b89-126">Spécifier dynamiquement des filtres de prédicat au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="34b89-126">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="34b89-127">Comment interroger les métadonnées d’un assembly avec la réflexion (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="34b89-127">How to query an assembly's metadata with Reflection (LINQ) (C#)</span></span>](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="34b89-128">Comment rechercher des fichiers avec un attribut ou un nom spécifié (C#)</span><span class="sxs-lookup"><span data-stu-id="34b89-128">How to query for files with a specified attribute or name (C#)</span></span>](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="34b89-129">Guide pratique pour trier ou filtrer des données texte par mot ou par champ (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="34b89-129">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

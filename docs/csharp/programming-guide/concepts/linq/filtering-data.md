---
title: Filtrage des données (C#)
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: 74399244990f8ff2deaa1d10576ea94a57c16bee
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346992"
---
# <a name="filtering-data-c"></a><span data-ttu-id="445c5-102">Filtrage des données (C#)</span><span class="sxs-lookup"><span data-stu-id="445c5-102">Filtering Data (C#)</span></span>
<span data-ttu-id="445c5-103">Le filtrage fait référence à l’opération de restriction du jeu de résultats pour que celui-ci contienne uniquement les éléments qui répondent à une condition spécifiée.</span><span class="sxs-lookup"><span data-stu-id="445c5-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="445c5-104">Cette opération est également appelée « sélection ».</span><span class="sxs-lookup"><span data-stu-id="445c5-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="445c5-105">L’illustration suivante montre les résultats du filtrage d’une séquence de caractères.</span><span class="sxs-lookup"><span data-stu-id="445c5-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="445c5-106">Le prédicat de l’opération de filtrage spécifie que le caractère doit être « A ».</span><span class="sxs-lookup"><span data-stu-id="445c5-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 ![Diagramme illustrant une opération de filtrage LINQ](./media/filtering-data/linq-filter-operation.png)  
  
 <span data-ttu-id="445c5-108">Les méthodes d’opérateurs de requête standard qui effectuent des opérations de sélection sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="445c5-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="445c5-109">Méthodes</span><span class="sxs-lookup"><span data-stu-id="445c5-109">Methods</span></span>  
  
|<span data-ttu-id="445c5-110">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="445c5-110">Method Name</span></span>|<span data-ttu-id="445c5-111">Description</span><span class="sxs-lookup"><span data-stu-id="445c5-111">Description</span></span>|<span data-ttu-id="445c5-112">Syntaxe d'expression de requête C#</span><span class="sxs-lookup"><span data-stu-id="445c5-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="445c5-113">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="445c5-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="445c5-114">OfType</span><span class="sxs-lookup"><span data-stu-id="445c5-114">OfType</span></span>|<span data-ttu-id="445c5-115">Sélectionne des valeurs, en fonction de leur capacité à être castées en un type spécifié.</span><span class="sxs-lookup"><span data-stu-id="445c5-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="445c5-116">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="445c5-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="445c5-117">Où</span><span class="sxs-lookup"><span data-stu-id="445c5-117">Where</span></span>|<span data-ttu-id="445c5-118">Sélectionne les valeurs qui sont basées sur une fonction de prédicat.</span><span class="sxs-lookup"><span data-stu-id="445c5-118">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="445c5-119">Exemple de syntaxe d’expression de requête</span><span class="sxs-lookup"><span data-stu-id="445c5-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="445c5-120">L’exemple suivant utilise la clause `where` pour filtrer les chaînes d’un tableau qui ont une longueur spécifique.</span><span class="sxs-lookup"><span data-stu-id="445c5-120">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="445c5-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="445c5-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="445c5-122">Vue d’ensemble des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="445c5-122">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="445c5-123">where, clause</span><span class="sxs-lookup"><span data-stu-id="445c5-123">where clause</span></span>](../../../language-reference/keywords/where-clause.md)
- [<span data-ttu-id="445c5-124">Spécifier dynamiquement des filtres de prédicat au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="445c5-124">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="445c5-125">Comment interroger les métadonnées d’un assembly avec la réflexionC#(LINQ) ()</span><span class="sxs-lookup"><span data-stu-id="445c5-125">How to query an assembly's metadata with Reflection (LINQ) (C#)</span></span>](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="445c5-126">Comment interroger des fichiers ayant un attribut ou un nom spécifiéC#()</span><span class="sxs-lookup"><span data-stu-id="445c5-126">How to query for files with a specified attribute or name (C#)</span></span>](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="445c5-127">Guide pratique pour trier ou filtrer des données texte par mot ou par champ (LINQC#) ()</span><span class="sxs-lookup"><span data-stu-id="445c5-127">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

---
title: Filtrage des données (C#)
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: 74399244990f8ff2deaa1d10576ea94a57c16bee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75346992"
---
# <a name="filtering-data-c"></a><span data-ttu-id="fe5ef-102">Filtrage des données (C#)</span><span class="sxs-lookup"><span data-stu-id="fe5ef-102">Filtering Data (C#)</span></span>
<span data-ttu-id="fe5ef-103">Le filtrage fait référence à l’opération de restriction du jeu de résultats pour que celui-ci contienne uniquement les éléments qui répondent à une condition spécifiée.</span><span class="sxs-lookup"><span data-stu-id="fe5ef-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="fe5ef-104">Cette opération est également appelée « sélection ».</span><span class="sxs-lookup"><span data-stu-id="fe5ef-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="fe5ef-105">L’illustration suivante montre les résultats du filtrage d’une séquence de caractères.</span><span class="sxs-lookup"><span data-stu-id="fe5ef-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="fe5ef-106">Le prédicat de l’opération de filtrage spécifie que le caractère doit être « A ».</span><span class="sxs-lookup"><span data-stu-id="fe5ef-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 ![Diagramme illustrant une opération de filtrage LINQ](./media/filtering-data/linq-filter-operation.png)  
  
 <span data-ttu-id="fe5ef-108">Les méthodes d’opérateurs de requête standard qui effectuent des opérations de sélection sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="fe5ef-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fe5ef-109">Méthodes</span><span class="sxs-lookup"><span data-stu-id="fe5ef-109">Methods</span></span>  
  
|<span data-ttu-id="fe5ef-110">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="fe5ef-110">Method Name</span></span>|<span data-ttu-id="fe5ef-111">Description</span><span class="sxs-lookup"><span data-stu-id="fe5ef-111">Description</span></span>|<span data-ttu-id="fe5ef-112">Syntaxe d'expression de requête C#</span><span class="sxs-lookup"><span data-stu-id="fe5ef-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="fe5ef-113">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="fe5ef-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="fe5ef-114">OfType</span><span class="sxs-lookup"><span data-stu-id="fe5ef-114">OfType</span></span>|<span data-ttu-id="fe5ef-115">Sélectionne des valeurs, en fonction de leur capacité à être castées en un type spécifié.</span><span class="sxs-lookup"><span data-stu-id="fe5ef-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="fe5ef-116">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="fe5ef-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fe5ef-117">Where</span><span class="sxs-lookup"><span data-stu-id="fe5ef-117">Where</span></span>|<span data-ttu-id="fe5ef-118">Sélectionne les valeurs qui sont basées sur une fonction de prédicat.</span><span class="sxs-lookup"><span data-stu-id="fe5ef-118">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="fe5ef-119">Exemple de syntaxe d’expression de requête</span><span class="sxs-lookup"><span data-stu-id="fe5ef-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="fe5ef-120">L’exemple suivant utilise la clause `where` pour filtrer les chaînes d’un tableau qui ont une longueur spécifique.</span><span class="sxs-lookup"><span data-stu-id="fe5ef-120">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fe5ef-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe5ef-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="fe5ef-122">Vue d’ensemble des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="fe5ef-122">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="fe5ef-123">où la clause</span><span class="sxs-lookup"><span data-stu-id="fe5ef-123">where clause</span></span>](../../../language-reference/keywords/where-clause.md)
- [<span data-ttu-id="fe5ef-124">Spécifier dynamiquement les filtres de prédication au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="fe5ef-124">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="fe5ef-125">Comment interroger les métadonnées d’une assemblée avec Réflexion (LINQ) (C)</span><span class="sxs-lookup"><span data-stu-id="fe5ef-125">How to query an assembly's metadata with Reflection (LINQ) (C#)</span></span>](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="fe5ef-126">Comment interroger les fichiers avec un attribut ou un nom spécifié (C)</span><span class="sxs-lookup"><span data-stu-id="fe5ef-126">How to query for files with a specified attribute or name (C#)</span></span>](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="fe5ef-127">Comment trier ou filtrer les données de texte par n’importe quel mot ou champ (LINQ) (C)</span><span class="sxs-lookup"><span data-stu-id="fe5ef-127">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

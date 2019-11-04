---
title: Opérations de quantificateur (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 5899af79799d5b8404e60027d7ba1b005c4b1b79
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423365"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="d36f4-102">Opérations de quantificateur (C#)</span><span class="sxs-lookup"><span data-stu-id="d36f4-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="d36f4-103">Les opérations de quantificateur retournent une valeur <xref:System.Boolean> qui indique si certains ou tous les éléments d’une séquence remplissent une condition.</span><span class="sxs-lookup"><span data-stu-id="d36f4-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="d36f4-104">L’illustration suivante représente deux opérations de quantificateur différentes sur deux séquences sources différentes.</span><span class="sxs-lookup"><span data-stu-id="d36f4-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="d36f4-105">La première opération demande si un ou plusieurs des éléments sont le caractère 'A' et le résultat est `true`.</span><span class="sxs-lookup"><span data-stu-id="d36f4-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="d36f4-106">La deuxième opération demande si tous les éléments sont le caractère 'A' et le résultat est `true`.</span><span class="sxs-lookup"><span data-stu-id="d36f4-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![Opérations de quantificateur LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="d36f4-108">Les méthodes d’opérateur de requête standard qui effectuent des opérations de quantificateur sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="d36f4-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d36f4-109">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d36f4-109">Methods</span></span>  
  
|<span data-ttu-id="d36f4-110">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="d36f4-110">Method Name</span></span>|<span data-ttu-id="d36f4-111">Description</span><span class="sxs-lookup"><span data-stu-id="d36f4-111">Description</span></span>|<span data-ttu-id="d36f4-112">Syntaxe d'expression de requête C#</span><span class="sxs-lookup"><span data-stu-id="d36f4-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="d36f4-113">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="d36f4-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="d36f4-114">Tout</span><span class="sxs-lookup"><span data-stu-id="d36f4-114">All</span></span>|<span data-ttu-id="d36f4-115">Détermine si tous les éléments d’une séquence remplissent une condition.</span><span class="sxs-lookup"><span data-stu-id="d36f4-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="d36f4-116">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="d36f4-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d36f4-117">Any</span><span class="sxs-lookup"><span data-stu-id="d36f4-117">Any</span></span>|<span data-ttu-id="d36f4-118">Détermine si certains éléments d’une séquence remplissent une condition.</span><span class="sxs-lookup"><span data-stu-id="d36f4-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="d36f4-119">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="d36f4-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d36f4-120">Contient</span><span class="sxs-lookup"><span data-stu-id="d36f4-120">Contains</span></span>|<span data-ttu-id="d36f4-121">Détermine si une séquence contient un élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="d36f4-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="d36f4-122">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="d36f4-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="d36f4-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d36f4-123">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="d36f4-124">Vue d’ensemble des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="d36f4-124">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="d36f4-125">Guide pratique pour spécifier dynamiquement des filtres de prédicat au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="d36f4-125">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="d36f4-126">Guide pratique pour rechercher des phrases qui contiennent un groupe de mots spécifié (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d36f4-126">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

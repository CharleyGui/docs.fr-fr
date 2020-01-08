---
title: Opérations de quantificateur (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 5c931e0971a2ae7970415905be8772a64a82ee39
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635481"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="c7253-102">Opérations de quantificateur (C#)</span><span class="sxs-lookup"><span data-stu-id="c7253-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="c7253-103">Les opérations de quantificateur retournent une valeur <xref:System.Boolean> qui indique si certains ou tous les éléments d’une séquence remplissent une condition.</span><span class="sxs-lookup"><span data-stu-id="c7253-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="c7253-104">L’illustration suivante représente deux opérations de quantificateur différentes sur deux séquences sources différentes.</span><span class="sxs-lookup"><span data-stu-id="c7253-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="c7253-105">La première opération demande si un ou plusieurs des éléments sont le caractère 'A' et le résultat est `true`.</span><span class="sxs-lookup"><span data-stu-id="c7253-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="c7253-106">La deuxième opération demande si tous les éléments sont le caractère 'A' et le résultat est `true`.</span><span class="sxs-lookup"><span data-stu-id="c7253-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![Opérations de quantificateur LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="c7253-108">Les méthodes d’opérateur de requête standard qui effectuent des opérations de quantificateur sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="c7253-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c7253-109">Méthodes</span><span class="sxs-lookup"><span data-stu-id="c7253-109">Methods</span></span>  
  
|<span data-ttu-id="c7253-110">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="c7253-110">Method Name</span></span>|<span data-ttu-id="c7253-111">Description</span><span class="sxs-lookup"><span data-stu-id="c7253-111">Description</span></span>|<span data-ttu-id="c7253-112">Syntaxe d'expression de requête C#</span><span class="sxs-lookup"><span data-stu-id="c7253-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="c7253-113">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="c7253-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="c7253-114">Toutes les</span><span class="sxs-lookup"><span data-stu-id="c7253-114">All</span></span>|<span data-ttu-id="c7253-115">Détermine si tous les éléments d’une séquence remplissent une condition.</span><span class="sxs-lookup"><span data-stu-id="c7253-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="c7253-116">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="c7253-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c7253-117">Tous</span><span class="sxs-lookup"><span data-stu-id="c7253-117">Any</span></span>|<span data-ttu-id="c7253-118">Détermine si certains éléments d’une séquence remplissent une condition.</span><span class="sxs-lookup"><span data-stu-id="c7253-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="c7253-119">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="c7253-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c7253-120">Contient</span><span class="sxs-lookup"><span data-stu-id="c7253-120">Contains</span></span>|<span data-ttu-id="c7253-121">Détermine si une séquence contient un élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="c7253-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="c7253-122">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="c7253-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="c7253-123">Exemples de syntaxe d'expression de requête</span><span class="sxs-lookup"><span data-stu-id="c7253-123">Query Expression Syntax Examples</span></span>  
  
### <a name="all"></a><span data-ttu-id="c7253-124">Toutes les</span><span class="sxs-lookup"><span data-stu-id="c7253-124">All</span></span>  
<span data-ttu-id="c7253-125">L’exemple suivant utilise la `All` pour vérifier que toutes les chaînes ont une longueur spécifique.</span><span class="sxs-lookup"><span data-stu-id="c7253-125">The following example uses the `All` to check that all strings are of a specific length.</span></span>
  
[!code-csharp[All](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#All)]  
  
### <a name="any"></a><span data-ttu-id="c7253-126">Tous</span><span class="sxs-lookup"><span data-stu-id="c7253-126">Any</span></span>  
<span data-ttu-id="c7253-127">L’exemple suivant utilise la `Any` pour vérifier que toutes les chaînes commencent par « o ».</span><span class="sxs-lookup"><span data-stu-id="c7253-127">The following example uses the `Any` to check that any strings are start with 'o'.</span></span>  
  
[!code-csharp[Any](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Any)]  
  
### <a name="contains"></a><span data-ttu-id="c7253-128">Contient</span><span class="sxs-lookup"><span data-stu-id="c7253-128">Contains</span></span>  
<span data-ttu-id="c7253-129">L’exemple suivant utilise la `Contains` pour vérifier qu’un tableau a un élément spécifique.</span><span class="sxs-lookup"><span data-stu-id="c7253-129">The following example uses the `Contains` to check an array have a specific element.</span></span>  
  
[!code-csharp[Contains](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Contains)]  
  
## <a name="see-also"></a><span data-ttu-id="c7253-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7253-130">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="c7253-131">Vue d’ensemble des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="c7253-131">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="c7253-132">Spécifier dynamiquement des filtres de prédicat au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="c7253-132">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="c7253-133">Comment rechercher des phrases qui contiennent un ensemble de mots spécifié (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="c7253-133">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

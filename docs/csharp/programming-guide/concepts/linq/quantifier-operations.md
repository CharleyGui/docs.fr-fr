---
title: Opérations de quantificateur (C#)
description: En savoir plus sur les opérations de quantificateur. Ces opérations retournent une valeur booléenne indiquant si certains ou tous les éléments d’une séquence satisfont à une condition.
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: ce06f887d3ad7b10cbdedf9e33072df2c0819ef1
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299147"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="14cb3-104">Opérations de quantificateur (C#)</span><span class="sxs-lookup"><span data-stu-id="14cb3-104">Quantifier Operations (C#)</span></span>
<span data-ttu-id="14cb3-105">Les opérations de quantificateur retournent une valeur <xref:System.Boolean> qui indique si certains ou tous les éléments d’une séquence remplissent une condition.</span><span class="sxs-lookup"><span data-stu-id="14cb3-105">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="14cb3-106">L’illustration suivante représente deux opérations de quantificateur différentes sur deux séquences sources différentes.</span><span class="sxs-lookup"><span data-stu-id="14cb3-106">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="14cb3-107">La première opération demande si un ou plusieurs des éléments sont le caractère 'A' et le résultat est `true`.</span><span class="sxs-lookup"><span data-stu-id="14cb3-107">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="14cb3-108">La deuxième opération demande si tous les éléments sont le caractère 'A' et le résultat est `true`.</span><span class="sxs-lookup"><span data-stu-id="14cb3-108">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![Opérations de quantificateur LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="14cb3-110">Les méthodes d’opérateur de requête standard qui effectuent des opérations de quantificateur sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="14cb3-110">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="14cb3-111">Méthodes</span><span class="sxs-lookup"><span data-stu-id="14cb3-111">Methods</span></span>  
  
|<span data-ttu-id="14cb3-112">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="14cb3-112">Method Name</span></span>|<span data-ttu-id="14cb3-113">Description</span><span class="sxs-lookup"><span data-stu-id="14cb3-113">Description</span></span>|<span data-ttu-id="14cb3-114">Syntaxe d'expression de requête C#</span><span class="sxs-lookup"><span data-stu-id="14cb3-114">C# Query Expression Syntax</span></span>|<span data-ttu-id="14cb3-115">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="14cb3-115">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="14cb3-116">Tous</span><span class="sxs-lookup"><span data-stu-id="14cb3-116">All</span></span>|<span data-ttu-id="14cb3-117">Détermine si tous les éléments d’une séquence remplissent une condition.</span><span class="sxs-lookup"><span data-stu-id="14cb3-117">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="14cb3-118">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="14cb3-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="14cb3-119">Quelconque</span><span class="sxs-lookup"><span data-stu-id="14cb3-119">Any</span></span>|<span data-ttu-id="14cb3-120">Détermine si certains éléments d’une séquence remplissent une condition.</span><span class="sxs-lookup"><span data-stu-id="14cb3-120">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="14cb3-121">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="14cb3-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="14cb3-122">Contient</span><span class="sxs-lookup"><span data-stu-id="14cb3-122">Contains</span></span>|<span data-ttu-id="14cb3-123">Détermine si une séquence contient un élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="14cb3-123">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="14cb3-124">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="14cb3-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="14cb3-125">Exemples de syntaxe d'expression de requête</span><span class="sxs-lookup"><span data-stu-id="14cb3-125">Query Expression Syntax Examples</span></span>  
  
### <a name="all"></a><span data-ttu-id="14cb3-126">Tous</span><span class="sxs-lookup"><span data-stu-id="14cb3-126">All</span></span>  
<span data-ttu-id="14cb3-127">L’exemple suivant utilise `All` pour vérifier que toutes les chaînes ont une longueur spécifique.</span><span class="sxs-lookup"><span data-stu-id="14cb3-127">The following example uses the `All` to check that all strings are of a specific length.</span></span>
  
[!code-csharp[All](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#All)]  
  
### <a name="any"></a><span data-ttu-id="14cb3-128">Quelconque</span><span class="sxs-lookup"><span data-stu-id="14cb3-128">Any</span></span>  
<span data-ttu-id="14cb3-129">L’exemple suivant utilise `Any` pour vérifier que toutes les chaînes commencent par « o ».</span><span class="sxs-lookup"><span data-stu-id="14cb3-129">The following example uses the `Any` to check that any strings are start with 'o'.</span></span>  
  
[!code-csharp[Any](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Any)]  
  
### <a name="contains"></a><span data-ttu-id="14cb3-130">Contient</span><span class="sxs-lookup"><span data-stu-id="14cb3-130">Contains</span></span>  
<span data-ttu-id="14cb3-131">L’exemple suivant utilise `Contains` pour vérifier qu’un tableau a un élément spécifique.</span><span class="sxs-lookup"><span data-stu-id="14cb3-131">The following example uses the `Contains` to check an array have a specific element.</span></span>  
  
[!code-csharp[Contains](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Contains)]  
  
## <a name="see-also"></a><span data-ttu-id="14cb3-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14cb3-132">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="14cb3-133">Vue d’ensemble des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="14cb3-133">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="14cb3-134">Spécifier dynamiquement des filtres de prédicat au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="14cb3-134">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="14cb3-135">Comment interroger des phrases qui contiennent un ensemble de mots spécifié (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="14cb3-135">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

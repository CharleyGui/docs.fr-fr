---
title: Opérations de quantificateur
ms.date: 07/20/2015
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
ms.openlocfilehash: 0c1c69cb36ac16126454dc0c24cd84fc85b0b218
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075302"
---
# <a name="quantifier-operations-visual-basic"></a><span data-ttu-id="861f2-102">Opérations de quantificateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="861f2-102">Quantifier Operations (Visual Basic)</span></span>

<span data-ttu-id="861f2-103">Les opérations de quantificateur retournent une valeur <xref:System.Boolean> qui indique si certains ou tous les éléments d’une séquence remplissent une condition.</span><span class="sxs-lookup"><span data-stu-id="861f2-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="861f2-104">L’illustration suivante représente deux opérations de quantificateur différentes sur deux séquences sources différentes.</span><span class="sxs-lookup"><span data-stu-id="861f2-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="861f2-105">La première opération demande si un ou plusieurs des éléments sont le caractère 'A' et le résultat est `true`.</span><span class="sxs-lookup"><span data-stu-id="861f2-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="861f2-106">La deuxième opération demande si tous les éléments sont le caractère 'A' et le résultat est `true`.</span><span class="sxs-lookup"><span data-stu-id="861f2-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![Opérations de quantificateur LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="861f2-108">Les méthodes d’opérateur de requête standard qui effectuent des opérations de quantificateur sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="861f2-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="861f2-109">Méthodes</span><span class="sxs-lookup"><span data-stu-id="861f2-109">Methods</span></span>  
  
|<span data-ttu-id="861f2-110">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="861f2-110">Method Name</span></span>|<span data-ttu-id="861f2-111">Description</span><span class="sxs-lookup"><span data-stu-id="861f2-111">Description</span></span>|<span data-ttu-id="861f2-112">Syntaxe des expressions de requête Visual Basic</span><span class="sxs-lookup"><span data-stu-id="861f2-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="861f2-113">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="861f2-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="861f2-114">Tous</span><span class="sxs-lookup"><span data-stu-id="861f2-114">All</span></span>|<span data-ttu-id="861f2-115">Détermine si tous les éléments d’une séquence remplissent une condition.</span><span class="sxs-lookup"><span data-stu-id="861f2-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="861f2-116">Quelconque</span><span class="sxs-lookup"><span data-stu-id="861f2-116">Any</span></span>|<span data-ttu-id="861f2-117">Détermine si certains éléments d’une séquence remplissent une condition.</span><span class="sxs-lookup"><span data-stu-id="861f2-117">Determines whether any elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="861f2-118">Contient</span><span class="sxs-lookup"><span data-stu-id="861f2-118">Contains</span></span>|<span data-ttu-id="861f2-119">Détermine si une séquence contient un élément spécifié.</span><span class="sxs-lookup"><span data-stu-id="861f2-119">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="861f2-120">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="861f2-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="861f2-121">Exemples de syntaxe d'expression de requête</span><span class="sxs-lookup"><span data-stu-id="861f2-121">Query Expression Syntax Examples</span></span>  

 <span data-ttu-id="861f2-122">Ces exemples utilisent la `Aggregate` clause dans Visual Basic dans le cadre de la condition de filtrage dans une requête LINQ.</span><span class="sxs-lookup"><span data-stu-id="861f2-122">These examples use the `Aggregate` clause in Visual Basic as part of the filtering condition in a LINQ query.</span></span>  
  
 <span data-ttu-id="861f2-123">L’exemple suivant utilise la `Aggregate` clause et la <xref:System.Linq.Enumerable.All%2A> méthode d’extension pour retourner à partir d’une collection les personnes dont les animaux sont tous antérieurs à un âge spécifié.</span><span class="sxs-lookup"><span data-stu-id="861f2-123">The following example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.All%2A> extension method to return from a collection those people whose pets are all older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#1)]  
  
 <span data-ttu-id="861f2-124">L’exemple suivant utilise la `Aggregate` clause et la <xref:System.Linq.Enumerable.Any%2A> méthode d’extension pour retourner à partir d’une collection les personnes qui ont au moins un animal familier antérieur à un âge spécifié.</span><span class="sxs-lookup"><span data-stu-id="861f2-124">The next example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.Any%2A> extension method to return from a collection those people who have at least one pet that is older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="861f2-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="861f2-125">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="861f2-126">Vue d’ensemble des opérateurs de requête standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="861f2-126">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="861f2-127">Aggregate Clause</span><span class="sxs-lookup"><span data-stu-id="861f2-127">Aggregate Clause</span></span>](../../../language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="861f2-128">Comment : rechercher des phrases qui contiennent un groupe de mots spécifié (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="861f2-128">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

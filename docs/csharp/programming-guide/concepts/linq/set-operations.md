---
title: Opérations ensemblistes (C#)
description: En savoir plus sur les opérations de définition et les méthodes d’opérateur de requête standard qui effectuent des opérations de définition dans LINQ en C#.
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: ab2608b267113ad5d47a33e64cd9a5e21496f668
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302371"
---
# <a name="set-operations-c"></a><span data-ttu-id="4f981-103">Opérations ensemblistes (C#)</span><span class="sxs-lookup"><span data-stu-id="4f981-103">Set Operations (C#)</span></span>
<span data-ttu-id="4f981-104">Les opérations ensemblistes dans LINQ font référence à des opérations de requête qui génèrent un jeu de résultats basé sur la présence ou l’absence d’éléments équivalents dans la même collection (ou le même ensemble) ou dans une collection distincte (ou un ensemble distinct).</span><span class="sxs-lookup"><span data-stu-id="4f981-104">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="4f981-105">Les méthodes d’opérateur de requête standard qui effectuent des opérations ensemblistes sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="4f981-105">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4f981-106">Méthodes</span><span class="sxs-lookup"><span data-stu-id="4f981-106">Methods</span></span>  
  
|<span data-ttu-id="4f981-107">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="4f981-107">Method Name</span></span>|<span data-ttu-id="4f981-108">Description</span><span class="sxs-lookup"><span data-stu-id="4f981-108">Description</span></span>|<span data-ttu-id="4f981-109">Syntaxe d'expression de requête C#</span><span class="sxs-lookup"><span data-stu-id="4f981-109">C# Query Expression Syntax</span></span>|<span data-ttu-id="4f981-110">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="4f981-110">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="4f981-111">Distinct</span><span class="sxs-lookup"><span data-stu-id="4f981-111">Distinct</span></span>|<span data-ttu-id="4f981-112">Supprime les valeurs en double d’une collection.</span><span class="sxs-lookup"><span data-stu-id="4f981-112">Removes duplicate values from a collection.</span></span>|<span data-ttu-id="4f981-113">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="4f981-113">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="4f981-114">Except</span><span class="sxs-lookup"><span data-stu-id="4f981-114">Except</span></span>|<span data-ttu-id="4f981-115">Retourne la différence ensembliste, à savoir les éléments d’une collection qui n’apparaissent pas dans une seconde collection.</span><span class="sxs-lookup"><span data-stu-id="4f981-115">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="4f981-116">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="4f981-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="4f981-117">Intersect</span><span class="sxs-lookup"><span data-stu-id="4f981-117">Intersect</span></span>|<span data-ttu-id="4f981-118">Retourne l’intersection ensembliste, à savoir les éléments qui apparaissent dans chacune des deux collections.</span><span class="sxs-lookup"><span data-stu-id="4f981-118">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="4f981-119">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="4f981-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="4f981-120">Union</span><span class="sxs-lookup"><span data-stu-id="4f981-120">Union</span></span>|<span data-ttu-id="4f981-121">Retourne l’union ensembliste, à savoir les éléments uniques qui apparaissent dans l’une ou l’autre des deux collections.</span><span class="sxs-lookup"><span data-stu-id="4f981-121">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="4f981-122">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="4f981-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="4f981-123">Comparaison d’opérations ensemblistes</span><span class="sxs-lookup"><span data-stu-id="4f981-123">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="4f981-124">Distinct</span><span class="sxs-lookup"><span data-stu-id="4f981-124">Distinct</span></span>  
 <span data-ttu-id="4f981-125">L’exemple suivant illustre le comportement de la <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> méthode sur une séquence de caractères.</span><span class="sxs-lookup"><span data-stu-id="4f981-125">The following example depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="4f981-126">La séquence retournée contient les éléments uniques de la séquence d’entrée.</span><span class="sxs-lookup"><span data-stu-id="4f981-126">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 ![Graphique illustrant le comportement de Distinct&#40;&#41;.](./media/set-operations/distinct-method-behavior.png)  

 [!code-csharp-interactive[Distinct](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#1)]
  
### <a name="except"></a><span data-ttu-id="4f981-128">Except</span><span class="sxs-lookup"><span data-stu-id="4f981-128">Except</span></span>  
 <span data-ttu-id="4f981-129">L’exemple suivant illustre le comportement de <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="4f981-129">The following example depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4f981-130">La séquence retournée contient uniquement les éléments de la première séquence d’entrée qui ne figurent pas dans la seconde séquence d’entrée.</span><span class="sxs-lookup"><span data-stu-id="4f981-130">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="4f981-131">![Graphique présentant l’action de, à l’exception de&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Montre le comportement de except.")</span><span class="sxs-lookup"><span data-stu-id="4f981-131">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>  
  
[!code-csharp-interactive[Except](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#2)]

### <a name="intersect"></a><span data-ttu-id="4f981-132">Intersect</span><span class="sxs-lookup"><span data-stu-id="4f981-132">Intersect</span></span>  
 <span data-ttu-id="4f981-133">L’exemple suivant illustre le comportement de <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="4f981-133">The following example depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4f981-134">La séquence retournée contient les éléments qui sont communs aux deux séquences d’entrée.</span><span class="sxs-lookup"><span data-stu-id="4f981-134">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 ![Graphique illustrant l’intersection de deux séquences.](./media/set-operations/intersection-two-sequences.png)  

[!code-csharp-interactive[Intersect](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#3)]

### <a name="union"></a><span data-ttu-id="4f981-136">Union</span><span class="sxs-lookup"><span data-stu-id="4f981-136">Union</span></span>  
 <span data-ttu-id="4f981-137">L’exemple suivant illustre une opération d’Union sur deux séquences de caractères.</span><span class="sxs-lookup"><span data-stu-id="4f981-137">The following example depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="4f981-138">La séquence retournée contient les éléments uniques des deux séquences d’entrée.</span><span class="sxs-lookup"><span data-stu-id="4f981-138">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 ![Graphique illustrant l’union de deux séquences.](./media/set-operations/union-operation-two-sequences.png)  

[!code-csharp-interactive[Union](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#4)]

## <a name="see-also"></a><span data-ttu-id="4f981-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f981-140">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="4f981-141">Vue d’ensemble des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="4f981-141">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="4f981-142">Comment combiner et comparer des collections de chaînes (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="4f981-142">How to combine and compare string collections (LINQ) (C#)</span></span>](./how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="4f981-143">Guide pratique pour rechercher la différence définie entre deux listes (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="4f981-143">How to find the set difference between two lists (LINQ) (C#)</span></span>](./how-to-find-the-set-difference-between-two-lists-linq.md)

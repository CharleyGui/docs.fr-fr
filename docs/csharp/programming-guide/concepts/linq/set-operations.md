---
title: Opérations ensemblistes (C#)
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: 170316b36705eaed51a9a17f8f79333a29e8c315
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346511"
---
# <a name="set-operations-c"></a><span data-ttu-id="5679f-102">Opérations ensemblistes (C#)</span><span class="sxs-lookup"><span data-stu-id="5679f-102">Set Operations (C#)</span></span>
<span data-ttu-id="5679f-103">Les opérations ensemblistes dans LINQ font référence à des opérations de requête qui génèrent un jeu de résultats basé sur la présence ou l’absence d’éléments équivalents dans la même collection (ou le même ensemble) ou dans une collection distincte (ou un ensemble distinct).</span><span class="sxs-lookup"><span data-stu-id="5679f-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="5679f-104">Les méthodes d’opérateur de requête standard qui effectuent des opérations ensemblistes sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="5679f-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5679f-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="5679f-105">Methods</span></span>  
  
|<span data-ttu-id="5679f-106">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="5679f-106">Method Name</span></span>|<span data-ttu-id="5679f-107">Description</span><span class="sxs-lookup"><span data-stu-id="5679f-107">Description</span></span>|<span data-ttu-id="5679f-108">Syntaxe d'expression de requête C#</span><span class="sxs-lookup"><span data-stu-id="5679f-108">C# Query Expression Syntax</span></span>|<span data-ttu-id="5679f-109">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="5679f-109">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="5679f-110">distinct</span><span class="sxs-lookup"><span data-stu-id="5679f-110">Distinct</span></span>|<span data-ttu-id="5679f-111">Supprime les valeurs en double d’une collection.</span><span class="sxs-lookup"><span data-stu-id="5679f-111">Removes duplicate values from a collection.</span></span>|<span data-ttu-id="5679f-112">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="5679f-112">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="5679f-113">À l'exception</span><span class="sxs-lookup"><span data-stu-id="5679f-113">Except</span></span>|<span data-ttu-id="5679f-114">Retourne la différence ensembliste, à savoir les éléments d’une collection qui n’apparaissent pas dans une seconde collection.</span><span class="sxs-lookup"><span data-stu-id="5679f-114">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="5679f-115">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="5679f-115">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="5679f-116">Définir une intersection</span><span class="sxs-lookup"><span data-stu-id="5679f-116">Intersect</span></span>|<span data-ttu-id="5679f-117">Retourne l’intersection ensembliste, à savoir les éléments qui apparaissent dans chacune des deux collections.</span><span class="sxs-lookup"><span data-stu-id="5679f-117">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="5679f-118">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="5679f-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="5679f-119">Union</span><span class="sxs-lookup"><span data-stu-id="5679f-119">Union</span></span>|<span data-ttu-id="5679f-120">Retourne l’union ensembliste, à savoir les éléments uniques qui apparaissent dans l’une ou l’autre des deux collections.</span><span class="sxs-lookup"><span data-stu-id="5679f-120">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="5679f-121">Non applicable.</span><span class="sxs-lookup"><span data-stu-id="5679f-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="5679f-122">Comparaison d’opérations ensemblistes</span><span class="sxs-lookup"><span data-stu-id="5679f-122">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="5679f-123">distinct</span><span class="sxs-lookup"><span data-stu-id="5679f-123">Distinct</span></span>  
 <span data-ttu-id="5679f-124">L’exemple suivant illustre le comportement de la méthode <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> sur une séquence de caractères.</span><span class="sxs-lookup"><span data-stu-id="5679f-124">The following example depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="5679f-125">La séquence retournée contient les éléments uniques de la séquence d’entrée.</span><span class="sxs-lookup"><span data-stu-id="5679f-125">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 ![Graphique illustrant le comportement de Distinct&#40;&#41;.](./media/set-operations/distinct-method-behavior.png)  
 
 [!code-csharp-interactive[Distinct](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#1)]
  
### <a name="except"></a><span data-ttu-id="5679f-127">À l'exception</span><span class="sxs-lookup"><span data-stu-id="5679f-127">Except</span></span>  
 <span data-ttu-id="5679f-128">L’exemple suivant illustre le comportement de <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5679f-128">The following example depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5679f-129">La séquence retournée contient uniquement les éléments de la première séquence d’entrée qui ne figurent pas dans la seconde séquence d’entrée.</span><span class="sxs-lookup"><span data-stu-id="5679f-129">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="5679f-130">![Graphique présentant l’action de Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Montre le comportement de except.")</span><span class="sxs-lookup"><span data-stu-id="5679f-130">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>  
  
[!code-csharp-interactive[Except](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#2)]

### <a name="intersect"></a><span data-ttu-id="5679f-131">Définir une intersection</span><span class="sxs-lookup"><span data-stu-id="5679f-131">Intersect</span></span>  
 <span data-ttu-id="5679f-132">L’exemple suivant illustre le comportement de <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5679f-132">The following example depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5679f-133">La séquence retournée contient les éléments qui sont communs aux deux séquences d’entrée.</span><span class="sxs-lookup"><span data-stu-id="5679f-133">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 ![Graphique illustrant l’intersection de deux séquences.](./media/set-operations/intersection-two-sequences.png)  
 
[!code-csharp-interactive[Intersect](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#3)]

### <a name="union"></a><span data-ttu-id="5679f-135">Union</span><span class="sxs-lookup"><span data-stu-id="5679f-135">Union</span></span>  
 <span data-ttu-id="5679f-136">L’exemple suivant illustre une opération d’Union sur deux séquences de caractères.</span><span class="sxs-lookup"><span data-stu-id="5679f-136">The following example depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="5679f-137">La séquence retournée contient les éléments uniques des deux séquences d’entrée.</span><span class="sxs-lookup"><span data-stu-id="5679f-137">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 ![Graphique illustrant l’union de deux séquences.](./media/set-operations/union-operation-two-sequences.png)  

[!code-csharp-interactive[Union](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#4)]
 
## <a name="see-also"></a><span data-ttu-id="5679f-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5679f-139">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="5679f-140">Vue d’ensemble des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="5679f-140">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="5679f-141">Comment combiner et comparer des collections de chaînes (LINQ)C#()</span><span class="sxs-lookup"><span data-stu-id="5679f-141">How to combine and compare string collections (LINQ) (C#)</span></span>](./how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="5679f-142">Comment rechercher la différence définie entre deux listes (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="5679f-142">How to find the set difference between two lists (LINQ) (C#)</span></span>](./how-to-find-the-set-difference-between-two-lists-linq.md)

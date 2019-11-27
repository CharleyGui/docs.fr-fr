---
title: Partitionnement des données
ms.date: 07/20/2015
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
ms.openlocfilehash: 2ab4e27ef6d825b9100fc3c15b7a9554ae49e516
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353153"
---
# <a name="partitioning-data-visual-basic"></a><span data-ttu-id="3669f-102">Partitionnement des données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3669f-102">Partitioning Data (Visual Basic)</span></span>
<span data-ttu-id="3669f-103">Le partitionnement dans LINQ désigne l’opération consistant à diviser une séquence d’entrée en deux sections, sans réorganiser les éléments, puis à retourner l’une des sections.</span><span class="sxs-lookup"><span data-stu-id="3669f-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="3669f-104">L’illustration suivante montre les résultats de trois opérations de partitionnement différentes sur une séquence de caractères.</span><span class="sxs-lookup"><span data-stu-id="3669f-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="3669f-105">La première opération retourne les trois premiers éléments de la séquence.</span><span class="sxs-lookup"><span data-stu-id="3669f-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="3669f-106">La deuxième opération ignore les trois premiers éléments et retourne les éléments restants.</span><span class="sxs-lookup"><span data-stu-id="3669f-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="3669f-107">La troisième opération ignore les deux premiers éléments de la séquence et retourne les trois éléments suivants.</span><span class="sxs-lookup"><span data-stu-id="3669f-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![Illustration des trois opérations de partitionnement LINQ.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="3669f-109">Les méthodes d’opérateurs de requête standard qui partitionnent des séquences sont répertoriées dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="3669f-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="3669f-110">Opérateurs</span><span class="sxs-lookup"><span data-stu-id="3669f-110">Operators</span></span>  
  
|<span data-ttu-id="3669f-111">Nom d'opérateur</span><span class="sxs-lookup"><span data-stu-id="3669f-111">Operator Name</span></span>|<span data-ttu-id="3669f-112">Description</span><span class="sxs-lookup"><span data-stu-id="3669f-112">Description</span></span>|<span data-ttu-id="3669f-113">Syntaxe des expressions de requête Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3669f-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="3669f-114">Informations supplémentaires</span><span class="sxs-lookup"><span data-stu-id="3669f-114">More Information</span></span>|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="3669f-115">Skip</span><span class="sxs-lookup"><span data-stu-id="3669f-115">Skip</span></span>|<span data-ttu-id="3669f-116">Ignore les éléments jusqu’à une position spécifiée dans une séquence.</span><span class="sxs-lookup"><span data-stu-id="3669f-116">Skips elements up to a specified position in a sequence.</span></span>|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3669f-117">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="3669f-117">SkipWhile</span></span>|<span data-ttu-id="3669f-118">Ignore les éléments basés sur une fonction de prédicat jusqu’à un élément qui ne remplit pas la condition.</span><span class="sxs-lookup"><span data-stu-id="3669f-118">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3669f-119">Take</span><span class="sxs-lookup"><span data-stu-id="3669f-119">Take</span></span>|<span data-ttu-id="3669f-120">Prend les éléments jusqu’à une position spécifiée dans une séquence.</span><span class="sxs-lookup"><span data-stu-id="3669f-120">Takes elements up to a specified position in a sequence.</span></span>|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3669f-121">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="3669f-121">TakeWhile</span></span>|<span data-ttu-id="3669f-122">Prend les éléments basés sur une fonction de prédicat jusqu’à un élément qui ne remplit pas la condition.</span><span class="sxs-lookup"><span data-stu-id="3669f-122">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="3669f-123">Exemples de syntaxe d'expression de requête</span><span class="sxs-lookup"><span data-stu-id="3669f-123">Query Expression Syntax Examples</span></span>  
  
### <a name="skip"></a><span data-ttu-id="3669f-124">Skip</span><span class="sxs-lookup"><span data-stu-id="3669f-124">Skip</span></span>  
 <span data-ttu-id="3669f-125">L’exemple de code suivant utilise la clause `Skip` dans Visual Basic pour ignorer les quatre premières chaînes d’un tableau de chaînes avant de retourner les chaînes restantes dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="3669f-125">The following code example uses the `Skip` clause in Visual Basic to skip over the first four strings in an array of strings before returning the remaining strings in the array.</span></span>  
  
 [!code-vb[CsLINQPartitioning#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#1)]  
  
### <a name="skipwhile"></a><span data-ttu-id="3669f-126">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="3669f-126">SkipWhile</span></span>  
 <span data-ttu-id="3669f-127">L’exemple de code suivant utilise la clause `Skip While` dans Visual Basic pour ignorer les chaînes dans un tableau, tandis que la première lettre de la chaîne est « a ».</span><span class="sxs-lookup"><span data-stu-id="3669f-127">The following code example uses the `Skip While` clause in Visual Basic to skip over the strings in an array while the first letter of the string is "a".</span></span> <span data-ttu-id="3669f-128">Les chaînes restantes dans le tableau sont retournées.</span><span class="sxs-lookup"><span data-stu-id="3669f-128">The remaining strings in the array are returned.</span></span>  
  
 [!code-vb[CsLINQPartitioning#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#2)]  
  
### <a name="take"></a><span data-ttu-id="3669f-129">Take</span><span class="sxs-lookup"><span data-stu-id="3669f-129">Take</span></span>  
 <span data-ttu-id="3669f-130">L’exemple de code suivant utilise la clause `Take` dans Visual Basic pour retourner les deux premières chaînes d’un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="3669f-130">The following code example uses the `Take` clause in Visual Basic to return the first two strings in an array of strings.</span></span>  
  
 [!code-vb[CsLINQPartitioning#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#3)]  
  
### <a name="takewhile"></a><span data-ttu-id="3669f-131">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="3669f-131">TakeWhile</span></span>  
 <span data-ttu-id="3669f-132">L’exemple de code suivant utilise la clause `Take While` dans Visual Basic pour retourner des chaînes à partir d’un tableau, tandis que la longueur de la chaîne est inférieure ou égale à cinq.</span><span class="sxs-lookup"><span data-stu-id="3669f-132">The following code example uses the `Take While` clause in Visual Basic to return strings from an array while the length of the string is five or less.</span></span>  
  
 [!code-vb[CsLINQPartitioning#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="3669f-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3669f-133">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="3669f-134">Vue d’ensemble des opérateurs de requête standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3669f-134">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="3669f-135">Skip (clause)</span><span class="sxs-lookup"><span data-stu-id="3669f-135">Skip Clause</span></span>](../../../../visual-basic/language-reference/queries/skip-clause.md)
- [<span data-ttu-id="3669f-136">Skip While (clause)</span><span class="sxs-lookup"><span data-stu-id="3669f-136">Skip While Clause</span></span>](../../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="3669f-137">Take (clause)</span><span class="sxs-lookup"><span data-stu-id="3669f-137">Take Clause</span></span>](../../../../visual-basic/language-reference/queries/take-clause.md)
- [<span data-ttu-id="3669f-138">Take While (clause)</span><span class="sxs-lookup"><span data-stu-id="3669f-138">Take While Clause</span></span>](../../../../visual-basic/language-reference/queries/take-while-clause.md)

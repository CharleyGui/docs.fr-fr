---
title: Requêtes d'agrégation
ms.date: 03/30/2017
ms.assetid: 13ec5580-05ce-4a1f-9d3d-8660be7891a2
ms.openlocfilehash: 2085808d631d1d9f97573c557e9e66e07113df52
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554219"
---
# <a name="aggregate-queries"></a><span data-ttu-id="627cb-102">Requêtes d'agrégation</span><span class="sxs-lookup"><span data-stu-id="627cb-102">Aggregate Queries</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="627cb-103">prend en charge les opérateurs d'agrégation `Average`, `Count`, `Max`, `Min` et `Sum`.</span><span class="sxs-lookup"><span data-stu-id="627cb-103">supports the `Average`, `Count`, `Max`, `Min`, and `Sum` aggregate operators.</span></span> <span data-ttu-id="627cb-104">Notez les caractéristiques suivantes des opérateurs d'agrégation dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="627cb-104">Note the following characteristics of aggregate operators in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
- <span data-ttu-id="627cb-105">Les requêtes d'agrégation sont exécutées immédiatement.</span><span class="sxs-lookup"><span data-stu-id="627cb-105">Aggregate queries are executed immediately.</span></span>  
  
     <span data-ttu-id="627cb-106">Pour plus d’informations, consultez [Introduction aux requêtes LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="627cb-106">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
- <span data-ttu-id="627cb-107">Les requêtes d’agrégation retournent généralement un nombre au lieu d’une collection.</span><span class="sxs-lookup"><span data-stu-id="627cb-107">Aggregate queries typically return a number instead of a collection.</span></span>  
  
     <span data-ttu-id="627cb-108">Pour plus d’informations, consultez [opérations d’agrégation](/previous-versions/visualstudio/visual-studio-2013/bb546138(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="627cb-108">For more information, see [Aggregation Operations](/previous-versions/visualstudio/visual-studio-2013/bb546138(v=vs.120)).</span></span>  
  
- <span data-ttu-id="627cb-109">Vous ne pouvez pas appeler d'agrégats à l'aide de types anonymes.</span><span class="sxs-lookup"><span data-stu-id="627cb-109">You cannot call aggregates against anonymous types.</span></span>  
  
 <span data-ttu-id="627cb-110">Les exemples des rubriques suivantes dérivent de l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="627cb-110">The examples in the following topics derive from the Northwind sample database.</span></span> <span data-ttu-id="627cb-111">Pour plus d’informations, consultez [téléchargement d’exemples de bases de données](downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="627cb-111">For more information, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="627cb-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="627cb-112">In This Section</span></span>  
 [<span data-ttu-id="627cb-113">Retourner la valeur moyenne d'une séquence numérique</span><span class="sxs-lookup"><span data-stu-id="627cb-113">Return the Average Value From a Numeric Sequence</span></span>](return-the-average-value-from-a-numeric-sequence.md)  
 <span data-ttu-id="627cb-114">Montre comment utiliser l'opérateur <xref:System.Linq.Enumerable.Average%2A>.</span><span class="sxs-lookup"><span data-stu-id="627cb-114">Demonstrates how to use the <xref:System.Linq.Enumerable.Average%2A> operator.</span></span>  
  
 [<span data-ttu-id="627cb-115">Dénombrer les éléments d'une séquence</span><span class="sxs-lookup"><span data-stu-id="627cb-115">Count the Number of Elements in a Sequence</span></span>](count-the-number-of-elements-in-a-sequence.md)  
 <span data-ttu-id="627cb-116">Montre comment utiliser l'opérateur <xref:System.Linq.Enumerable.Count%2A>.</span><span class="sxs-lookup"><span data-stu-id="627cb-116">Demonstrates how to use the <xref:System.Linq.Enumerable.Count%2A> operator.</span></span>  
  
 [<span data-ttu-id="627cb-117">Comment : rechercher la valeur maximale dans une séquence numérique</span><span class="sxs-lookup"><span data-stu-id="627cb-117">Find the Maximum Value in a Numeric Sequence</span></span>](find-the-maximum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="627cb-118">Montre comment utiliser l'opérateur <xref:System.Linq.Enumerable.Max%2A>.</span><span class="sxs-lookup"><span data-stu-id="627cb-118">Demonstrates how to use the <xref:System.Linq.Enumerable.Max%2A> operator.</span></span>  
  
 [<span data-ttu-id="627cb-119">Comment : rechercher la valeur minimale dans une séquence numérique</span><span class="sxs-lookup"><span data-stu-id="627cb-119">Find the Minimum Value in a Numeric Sequence</span></span>](find-the-minimum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="627cb-120">Montre comment utiliser l'opérateur <xref:System.Linq.Enumerable.Min%2A>.</span><span class="sxs-lookup"><span data-stu-id="627cb-120">Demonstrates how to use the <xref:System.Linq.Enumerable.Min%2A> operator.</span></span>  
  
 [<span data-ttu-id="627cb-121">Comment : calculer la somme de valeurs dans une séquence numérique</span><span class="sxs-lookup"><span data-stu-id="627cb-121">Compute the Sum of Values in a Numeric Sequence</span></span>](compute-the-sum-of-values-in-a-numeric-sequence.md)  
 <span data-ttu-id="627cb-122">Montre comment utiliser l'opérateur <xref:System.Linq.Enumerable.Sum%2A>.</span><span class="sxs-lookup"><span data-stu-id="627cb-122">Demonstrates how to use the <xref:System.Linq.Enumerable.Sum%2A> operator.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="627cb-123">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="627cb-123">Related Sections</span></span>  
 [<span data-ttu-id="627cb-124">Exemples de requêtes</span><span class="sxs-lookup"><span data-stu-id="627cb-124">Query Examples</span></span>](query-examples.md)  
 <span data-ttu-id="627cb-125">Fournit des liens vers les requêtes [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dans Visual Basic et C#.</span><span class="sxs-lookup"><span data-stu-id="627cb-125">Provides links to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries in Visual Basic and C#.</span></span>  
  
 [<span data-ttu-id="627cb-126">Concepts relatifs aux requêtes</span><span class="sxs-lookup"><span data-stu-id="627cb-126">Query Concepts</span></span>](query-concepts.md)  
 <span data-ttu-id="627cb-127">Fournit des liens vers des rubriques qui expliquent les concepts de conception de requêtes LINQ dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="627cb-127">Provides links to topics that explain concepts for designing LINQ queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="627cb-128">Introduction aux requêtes LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="627cb-128">Introduction to LINQ Queries (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 <span data-ttu-id="627cb-129">Explique le fonctionnement des requêtes dans LINQ.</span><span class="sxs-lookup"><span data-stu-id="627cb-129">Explains how queries work in LINQ.</span></span>

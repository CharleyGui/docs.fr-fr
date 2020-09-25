---
title: 'Comment : regrouper des éléments dans une séquence'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d50c8b4-f550-4775-bbb6-eab6e874cb43
ms.openlocfilehash: d11d6f6231c1871cd54f0b0e3f6f862dc10b328b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194338"
---
# <a name="group-elements-in-a-sequence"></a><span data-ttu-id="aa0d3-102">Comment : regrouper des éléments dans une séquence</span><span class="sxs-lookup"><span data-stu-id="aa0d3-102">Group Elements in a Sequence</span></span>

<span data-ttu-id="aa0d3-103">L'opérateur <xref:System.Linq.Enumerable.GroupBy%2A> regroupe les éléments d'une séquence.</span><span class="sxs-lookup"><span data-stu-id="aa0d3-103">The <xref:System.Linq.Enumerable.GroupBy%2A> operator groups the elements of a sequence.</span></span> <span data-ttu-id="aa0d3-104">Les exemples suivants utilisent la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="aa0d3-104">The following examples use the Northwind database.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aa0d3-105">Les valeurs de colonne null dans les requêtes <xref:System.Linq.Enumerable.GroupBy%2A> peuvent parfois lever une exception <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="aa0d3-105">Null column values in <xref:System.Linq.Enumerable.GroupBy%2A> queries can sometimes throw an <xref:System.InvalidOperationException>.</span></span> <span data-ttu-id="aa0d3-106">Pour plus d’informations, consultez la section « GroupBy InvalidOperationException » de la rubrique [Troubleshooting](troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="aa0d3-106">For more information, see the "GroupBy InvalidOperationException" section of [Troubleshooting](troubleshooting.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa0d3-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="aa0d3-107">Example</span></span>  

 <span data-ttu-id="aa0d3-108">L'exemple suivant partitionne `Products` par `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="aa0d3-108">The following example partitions `Products` by `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#27](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#27)]
 [!code-vb[DLinqQueryExamples#27](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#27)]  
  
## <a name="example"></a><span data-ttu-id="aa0d3-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="aa0d3-109">Example</span></span>  

 <span data-ttu-id="aa0d3-110">L'exemple suivant utilise <xref:System.Linq.Enumerable.Max%2A> pour rechercher le prix unitaire maximal pour chaque `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="aa0d3-110">The following example uses <xref:System.Linq.Enumerable.Max%2A> to find the maximum unit price for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#28](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#28)]
 [!code-vb[DLinqQueryExamples#28](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#28)]  
  
## <a name="example"></a><span data-ttu-id="aa0d3-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="aa0d3-111">Example</span></span>  

 <span data-ttu-id="aa0d3-112">L'exemple suivant utilise Average pour rechercher le `UnitPrice` moyen pour chaque `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="aa0d3-112">The following example uses Average to find the average `UnitPrice` for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#29](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#29)]
 [!code-vb[DLinqQueryExamples#29](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="aa0d3-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="aa0d3-113">Example</span></span>  

 <span data-ttu-id="aa0d3-114">L'exemple suivant utilise <xref:System.Linq.Queryable.Sum%2A> pour rechercher le `UnitPrice` total pour chaque `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="aa0d3-114">The following example uses <xref:System.Linq.Queryable.Sum%2A> to find the total `UnitPrice` for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#30](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#30)]
 [!code-vb[DLinqQueryExamples#30](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="aa0d3-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="aa0d3-115">Example</span></span>  

 <span data-ttu-id="aa0d3-116">L'exemple suivant utilise <xref:System.Linq.Queryable.Count%2A> pour rechercher le nombre de `Products` de fin de série dans chaque `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="aa0d3-116">The following example uses <xref:System.Linq.Queryable.Count%2A> to find the number of discontinued `Products` in each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#31](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#31)]
 [!code-vb[DLinqQueryExamples#31](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#31)]  
  
## <a name="example"></a><span data-ttu-id="aa0d3-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="aa0d3-117">Example</span></span>  

 <span data-ttu-id="aa0d3-118">L'exemple suivant utilise une clause `where` pour rechercher toutes les catégories comportant au moins 10 produits.</span><span class="sxs-lookup"><span data-stu-id="aa0d3-118">The following example uses a following `where` clause to find all categories that have at least 10 products.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#32](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#32)]
 [!code-vb[DLinqQueryExamples#32](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#32)]  
  
## <a name="example"></a><span data-ttu-id="aa0d3-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="aa0d3-119">Example</span></span>  

 <span data-ttu-id="aa0d3-120">L'exemple suivant regroupe les produits par `CategoryID` et `SupplierID`.</span><span class="sxs-lookup"><span data-stu-id="aa0d3-120">The following example groups products by `CategoryID` and `SupplierID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#33](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#33)]
 [!code-vb[DLinqQueryExamples#33](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#33)]  
  
## <a name="example"></a><span data-ttu-id="aa0d3-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="aa0d3-121">Example</span></span>  

 <span data-ttu-id="aa0d3-122">L'exemple suivant retourne deux séquences de produits.</span><span class="sxs-lookup"><span data-stu-id="aa0d3-122">The following example returns two sequences of products.</span></span> <span data-ttu-id="aa0d3-123">La première séquence contient des produits dont le prix unitaire est inférieur ou égal à 10.</span><span class="sxs-lookup"><span data-stu-id="aa0d3-123">The first sequence contains products with unit price less than or equal to 10.</span></span> <span data-ttu-id="aa0d3-124">La deuxième séquence contient des produits dont le prix unitaire est supérieur à 10.</span><span class="sxs-lookup"><span data-stu-id="aa0d3-124">The second sequence contains products with unit price greater than 10.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#34](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#34)]
 [!code-vb[DLinqQueryExamples#34](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#34)]  
  
## <a name="example"></a><span data-ttu-id="aa0d3-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="aa0d3-125">Example</span></span>  

 <span data-ttu-id="aa0d3-126">L'opérateur <xref:System.Linq.Queryable.GroupBy%2A> ne peut prendre qu'un argument Key.</span><span class="sxs-lookup"><span data-stu-id="aa0d3-126">The <xref:System.Linq.Queryable.GroupBy%2A> operator can take only a single key argument.</span></span> <span data-ttu-id="aa0d3-127">Pour effectuer un regroupement sur plusieurs clés, vous devez créer un type anonyme, comme dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="aa0d3-127">If you need to group by more than one key, you must create an anonymous type, as in the following example:</span></span>  
  
 [!code-csharp[DLinqQueryExamples#35](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#35)]
 [!code-vb[DLinqQueryExamples#35](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#35)]  
  
## <a name="see-also"></a><span data-ttu-id="aa0d3-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa0d3-128">See also</span></span>

- [<span data-ttu-id="aa0d3-129">Exemples de requêtes</span><span class="sxs-lookup"><span data-stu-id="aa0d3-129">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="aa0d3-130">Téléchargement d’exemples de base de données</span><span class="sxs-lookup"><span data-stu-id="aa0d3-130">Downloading Sample Databases</span></span>](downloading-sample-databases.md)

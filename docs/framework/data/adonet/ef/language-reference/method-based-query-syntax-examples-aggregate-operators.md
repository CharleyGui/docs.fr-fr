---
title: "Exemples de syntaxe de requête fondée sur une méthode : opérateurs d'agrégation"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0e306067-5720-4782-9719-2286570a7e47
ms.openlocfilehash: f8754101e7ec55fe5f9836300de1d077e1db2478
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192124"
---
# <a name="method-based-query-syntax-examples-aggregate-operators"></a><span data-ttu-id="d3f4a-102">Exemples de syntaxe de requête fondée sur une méthode : opérateurs d'agrégation</span><span class="sxs-lookup"><span data-stu-id="d3f4a-102">Method-Based Query Syntax Examples: Aggregate Operators</span></span>

<span data-ttu-id="d3f4a-103">Les exemples de cette rubrique montrent comment utiliser les <xref:System.Linq.Enumerable.Aggregate%2A> méthodes, <xref:System.Linq.Enumerable.Average%2A> , <xref:System.Linq.Enumerable.Count%2A> , <xref:System.Linq.Enumerable.LongCount%2A> , <xref:System.Linq.Enumerable.Max%2A> , <xref:System.Linq.Enumerable.Min%2A> et <xref:System.Linq.Enumerable.Sum%2A> pour interroger le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) à l’aide de la syntaxe de requête fondée sur une méthode.</span><span class="sxs-lookup"><span data-stu-id="d3f4a-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="d3f4a-104">Le modèle de vente AdventureWorks Sales Model utilisé dans ces exemples est construit à partir des tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d3f4a-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="d3f4a-105">Les exemples de cette rubrique utilisent les `using` / `Imports` instructions suivantes :</span><span class="sxs-lookup"><span data-stu-id="d3f4a-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="average"></a><span data-ttu-id="d3f4a-106">Average</span><span class="sxs-lookup"><span data-stu-id="d3f4a-106">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="d3f4a-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="d3f4a-107">Example</span></span>  

 <span data-ttu-id="d3f4a-108">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.Average%2A> pour trouver le prix moyen courant des produits.</span><span class="sxs-lookup"><span data-stu-id="d3f4a-108">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average_mq)]
 [!code-vb[DP L2E Examples#Average_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average_mq)]  
  
### <a name="example"></a><span data-ttu-id="d3f4a-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="d3f4a-109">Example</span></span>  

 <span data-ttu-id="d3f4a-110">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.Average%2A> pour trouver le prix moyen courant des produits de chaque style.</span><span class="sxs-lookup"><span data-stu-id="d3f4a-110">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="d3f4a-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="d3f4a-111">Example</span></span>  

 <span data-ttu-id="d3f4a-112">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.Average%2A> pour trouver le montant total moyen dû.</span><span class="sxs-lookup"><span data-stu-id="d3f4a-112">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageprojection_mq)]
 [!code-vb[DP L2E Examples#AverageProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="d3f4a-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="d3f4a-113">Example</span></span>  

 <span data-ttu-id="d3f4a-114">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.Average%2A> pour obtenir le montant total moyen dû pour chaque ID de contact.</span><span class="sxs-lookup"><span data-stu-id="d3f4a-114">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="d3f4a-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="d3f4a-115">Example</span></span>  

 <span data-ttu-id="d3f4a-116">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.Average%2A> pour obtenir les commandes présentant le montant total moyen dû pour chaque ID de contact.</span><span class="sxs-lookup"><span data-stu-id="d3f4a-116">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the orders with the average total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="d3f4a-117">Count</span><span class="sxs-lookup"><span data-stu-id="d3f4a-117">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="d3f4a-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="d3f4a-118">Example</span></span>  

 <span data-ttu-id="d3f4a-119">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.Count%2A> pour retourner le nombre de produits dans la table Product.</span><span class="sxs-lookup"><span data-stu-id="d3f4a-119">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in the Product table.</span></span>  
  
 [!code-csharp[DP L2E Examples#Count](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#count)]
 [!code-vb[DP L2E Examples#Count](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#count)]  
  
### <a name="example"></a><span data-ttu-id="d3f4a-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="d3f4a-120">Example</span></span>  

 <span data-ttu-id="d3f4a-121">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.Count%2A> pour retourner une liste des ID de contact et du nombre de commandes de chacun d'eux.</span><span class="sxs-lookup"><span data-stu-id="d3f4a-121">The following example uses the <xref:System.Linq.Enumerable.Count%2A> method to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countnested)]
 [!code-vb[DP L2E Examples#CountNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="d3f4a-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="d3f4a-122">Example</span></span>  

 <span data-ttu-id="d3f4a-123">L'exemple ci-dessous regroupe les produits par couleur et utilise la méthode <xref:System.Linq.Enumerable.Count%2A> pour retourner le nombre de produits dans chaque groupe de couleur.</span><span class="sxs-lookup"><span data-stu-id="d3f4a-123">The following example groups products by color and uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="longcount"></a><span data-ttu-id="d3f4a-124">LongCount</span><span class="sxs-lookup"><span data-stu-id="d3f4a-124">LongCount</span></span>  
  
### <a name="example"></a><span data-ttu-id="d3f4a-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="d3f4a-125">Example</span></span>  

 <span data-ttu-id="d3f4a-126">L'exemple ci-dessous obtient le nombre de contacts sous la forme d'un entier long.</span><span class="sxs-lookup"><span data-stu-id="d3f4a-126">The following example gets the contact count as a long integer.</span></span>  
  
 [!code-csharp[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#longcountsimple)]
 [!code-vb[DP L2E Examples#LongCountSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#longcountsimple)]  
  
## <a name="max"></a><span data-ttu-id="d3f4a-127">Max</span><span class="sxs-lookup"><span data-stu-id="d3f4a-127">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="d3f4a-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="d3f4a-128">Example</span></span>  

 <span data-ttu-id="d3f4a-129">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.Max%2A> pour obtenir le montant total dû le plus élevé.</span><span class="sxs-lookup"><span data-stu-id="d3f4a-129">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxprojection_mq)]
 [!code-vb[DP L2E Examples#MaxProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="d3f4a-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="d3f4a-130">Example</span></span>  

 <span data-ttu-id="d3f4a-131">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.Max%2A> pour obtenir le montant total dû le plus élevé pour chaque ID de contact.</span><span class="sxs-lookup"><span data-stu-id="d3f4a-131">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="d3f4a-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="d3f4a-132">Example</span></span>  

 <span data-ttu-id="d3f4a-133">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.Max%2A> pour obtenir les commandes présentant le montant total dû le plus élevé pour chaque ID de contact.</span><span class="sxs-lookup"><span data-stu-id="d3f4a-133">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="d3f4a-134">Min</span><span class="sxs-lookup"><span data-stu-id="d3f4a-134">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="d3f4a-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="d3f4a-135">Example</span></span>  

 <span data-ttu-id="d3f4a-136">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.Min%2A> pour obtenir le montant total dû le plus bas.</span><span class="sxs-lookup"><span data-stu-id="d3f4a-136">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minprojection_mq)]
 [!code-vb[DP L2E Examples#MinProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="d3f4a-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="d3f4a-137">Example</span></span>  

 <span data-ttu-id="d3f4a-138">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.Min%2A> pour obtenir le montant total dû le plus bas pour chaque ID de contact.</span><span class="sxs-lookup"><span data-stu-id="d3f4a-138">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="d3f4a-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="d3f4a-139">Example</span></span>  

 <span data-ttu-id="d3f4a-140">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.Min%2A> pour obtenir les commandes présentant le montant total dû le plus bas pour chaque ID de contact.</span><span class="sxs-lookup"><span data-stu-id="d3f4a-140">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="d3f4a-141">SUM</span><span class="sxs-lookup"><span data-stu-id="d3f4a-141">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="d3f4a-142">Exemple</span><span class="sxs-lookup"><span data-stu-id="d3f4a-142">Example</span></span>  

 <span data-ttu-id="d3f4a-143">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.Sum%2A> pour obtenir le total des quantités commandées de la table SalesOrderDetail.</span><span class="sxs-lookup"><span data-stu-id="d3f4a-143">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total number of order quantities in the SalesOrderDetail table.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumprojection_mq)]
 [!code-vb[DP L2E Examples#SumProjection_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="d3f4a-144">Exemple</span><span class="sxs-lookup"><span data-stu-id="d3f4a-144">Example</span></span>  

 <span data-ttu-id="d3f4a-145">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.Sum%2A> pour obtenir le montant total dû pour chaque ID de contact.</span><span class="sxs-lookup"><span data-stu-id="d3f4a-145">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="d3f4a-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3f4a-146">See also</span></span>

- [<span data-ttu-id="d3f4a-147">Requêtes dans LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="d3f4a-147">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)

---
title: 'Exemples de syntaxe de requête fondée sur une méthode : Opérateurs d’agrégation (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ed5f01d-acb2-4dd4-be60-f04c2d570fa8
ms.openlocfilehash: 348070663e414f2768b6b57d880c41d4da6c7bb2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794932"
---
# <a name="method-based-query-syntax-examples-aggregate-operators-linq-to-dataset"></a><span data-ttu-id="31272-102">Exemples de syntaxe de requête fondée sur une méthode : Opérateurs d’agrégation (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="31272-102">Method-Based Query Syntax Examples: Aggregate Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="31272-103">Les exemples de cette rubrique montrent comment utiliser les opérateurs <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A> et <xref:System.Linq.Enumerable.Sum%2A> pour interroger un <xref:System.Data.DataSet> et agréger des données à l'aide de la syntaxe de requête de méthode.</span><span class="sxs-lookup"><span data-stu-id="31272-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Aggregate%2A>, <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.LongCount%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> operators to query a <xref:System.Data.DataSet> and aggregate data using method query syntax.</span></span>  
  
 <span data-ttu-id="31272-104">La `FillDataSet` méthode utilisée dans ces exemples est spécifiée lors [du chargement des données dans un DataSet](loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="31272-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="31272-105">Les exemples de cette rubrique utilisent les tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="31272-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="31272-106">Les exemples de cette rubrique utilisent les instructions `using` suivantes / `Imports` :</span><span class="sxs-lookup"><span data-stu-id="31272-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="31272-107">Pour plus d’informations, consultez [Guide pratique pour Créez un projet de LINQ to DataSet dans Visual](how-to-create-a-linq-to-dataset-project-in-vs.md)Studio.</span><span class="sxs-lookup"><span data-stu-id="31272-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="aggregate"></a><span data-ttu-id="31272-108">Aggregate</span><span class="sxs-lookup"><span data-stu-id="31272-108">Aggregate</span></span>  
  
### <a name="example"></a><span data-ttu-id="31272-109">Exemples</span><span class="sxs-lookup"><span data-stu-id="31272-109">Example</span></span>  
 <span data-ttu-id="31272-110">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.Aggregate%2A> pour obtenir les cinq premiers contacts de la table `Contact` et créer une liste de noms délimités par des virgules.</span><span class="sxs-lookup"><span data-stu-id="31272-110">This example uses the <xref:System.Linq.Enumerable.Aggregate%2A> method to get the first 5 contacts from the `Contact` table and build a comma-delimited list of the last names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Aggregate_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#aggregate_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Aggregate_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#aggregate_mq)]  
  
## <a name="average"></a><span data-ttu-id="31272-111">Moyenne</span><span class="sxs-lookup"><span data-stu-id="31272-111">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="31272-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="31272-112">Example</span></span>  
 <span data-ttu-id="31272-113">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.Average%2A> pour trouver le prix moyen courant des produits.</span><span class="sxs-lookup"><span data-stu-id="31272-113">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average_mq)]  
  
### <a name="example"></a><span data-ttu-id="31272-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="31272-114">Example</span></span>  
 <span data-ttu-id="31272-115">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.Average%2A> pour trouver le prix moyen courant des produits de chaque style.</span><span class="sxs-lookup"><span data-stu-id="31272-115">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="31272-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="31272-116">Example</span></span>  
 <span data-ttu-id="31272-117">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.Average%2A> pour trouver le montant total moyen dû.</span><span class="sxs-lookup"><span data-stu-id="31272-117">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="31272-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="31272-118">Example</span></span>  
 <span data-ttu-id="31272-119">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.Average%2A> pour obtenir le montant total moyen dû pour chaque ID de contact.</span><span class="sxs-lookup"><span data-stu-id="31272-119">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="31272-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="31272-120">Example</span></span>  
 <span data-ttu-id="31272-121">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.Average%2A> pour obtenir les commandes avec le `TotalDue` moyen pour chaque contact.</span><span class="sxs-lookup"><span data-stu-id="31272-121">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to get the orders with the average `TotalDue` for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="31272-122">Nombre</span><span class="sxs-lookup"><span data-stu-id="31272-122">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="31272-123">Exemples</span><span class="sxs-lookup"><span data-stu-id="31272-123">Example</span></span>  
 <span data-ttu-id="31272-124">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.Count%2A> pour retourner le nombre de produits dans la table `Product`.</span><span class="sxs-lookup"><span data-stu-id="31272-124">This example uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in the `Product` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Count](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#count)]
 [!code-vb[DP LINQ to DataSet Examples#Count](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#count)]  
  
### <a name="example"></a><span data-ttu-id="31272-125">Exemples</span><span class="sxs-lookup"><span data-stu-id="31272-125">Example</span></span>  
 <span data-ttu-id="31272-126">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.Count%2A> pour retourner une liste des ID de contact ID et du nombre de commandes de chaque ID de contact.</span><span class="sxs-lookup"><span data-stu-id="31272-126">This example uses the <xref:System.Linq.Enumerable.Count%2A> method to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countnested)]
 [!code-vb[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="31272-127">Exemples</span><span class="sxs-lookup"><span data-stu-id="31272-127">Example</span></span>  
 <span data-ttu-id="31272-128">Cet exemple regroupe les produits par couleur et utilise la méthode <xref:System.Linq.Enumerable.Count%2A> pour retourner le nombre de produits dans chaque groupe de couleur.</span><span class="sxs-lookup"><span data-stu-id="31272-128">This example groups products by color and uses the <xref:System.Linq.Enumerable.Count%2A> method to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="longcount"></a><span data-ttu-id="31272-129">LongCount</span><span class="sxs-lookup"><span data-stu-id="31272-129">LongCount</span></span>  
  
### <a name="example"></a><span data-ttu-id="31272-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="31272-130">Example</span></span>  
 <span data-ttu-id="31272-131">Cet exemple obtient le nombre de contacts sous la forme d'un entier long.</span><span class="sxs-lookup"><span data-stu-id="31272-131">This example gets the contact count as a long integer.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#LongCountSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#longcountsimple)]
 [!code-vb[DP LINQ to DataSet Examples#LongCountSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#longcountsimple)]  
  
## <a name="max"></a><span data-ttu-id="31272-132">Max</span><span class="sxs-lookup"><span data-stu-id="31272-132">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="31272-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="31272-133">Example</span></span>  
 <span data-ttu-id="31272-134">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.Max%2A> pour obtenir le montant total dû le plus élevé.</span><span class="sxs-lookup"><span data-stu-id="31272-134">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="31272-135">Exemples</span><span class="sxs-lookup"><span data-stu-id="31272-135">Example</span></span>  
 <span data-ttu-id="31272-136">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.Max%2A> pour obtenir le montant total dû le plus élevé pour chaque ID de contact.</span><span class="sxs-lookup"><span data-stu-id="31272-136">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="31272-137">Exemples</span><span class="sxs-lookup"><span data-stu-id="31272-137">Example</span></span>  
 <span data-ttu-id="31272-138">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.Max%2A> pour obtenir les commandes présentant le `TotalDue` le plus élevé pour chaque ID de contact.</span><span class="sxs-lookup"><span data-stu-id="31272-138">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest `TotalDue` for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="31272-139">Min</span><span class="sxs-lookup"><span data-stu-id="31272-139">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="31272-140">Exemples</span><span class="sxs-lookup"><span data-stu-id="31272-140">Example</span></span>  
 <span data-ttu-id="31272-141">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.Min%2A> pour obtenir le montant total dû le plus bas.</span><span class="sxs-lookup"><span data-stu-id="31272-141">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minprojection_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinProjection_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="31272-142">Exemple</span><span class="sxs-lookup"><span data-stu-id="31272-142">Example</span></span>  
 <span data-ttu-id="31272-143">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.Min%2A> pour obtenir le montant total dû le plus bas pour chaque ID de contact.</span><span class="sxs-lookup"><span data-stu-id="31272-143">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="31272-144">Exemples</span><span class="sxs-lookup"><span data-stu-id="31272-144">Example</span></span>  
 <span data-ttu-id="31272-145">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.Min%2A> pour obtenir les commandes présentant le montant total dû le plus bas pour chaque ID de contact.</span><span class="sxs-lookup"><span data-stu-id="31272-145">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="31272-146">Sum</span><span class="sxs-lookup"><span data-stu-id="31272-146">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="31272-147">Exemple</span><span class="sxs-lookup"><span data-stu-id="31272-147">Example</span></span>  
 <span data-ttu-id="31272-148">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.Sum%2A> pour obtenir le total des quantités commandées de la table `SalesOrderDetail`.</span><span class="sxs-lookup"><span data-stu-id="31272-148">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total number of order quantities in the `SalesOrderDetail` table.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumProjection_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumprojection_mq)]  
  
### <a name="example"></a><span data-ttu-id="31272-149">Exemple</span><span class="sxs-lookup"><span data-stu-id="31272-149">Example</span></span>  
 <span data-ttu-id="31272-150">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.Sum%2A> pour obtenir le montant total dû de chaque ID de contact.</span><span class="sxs-lookup"><span data-stu-id="31272-150">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="31272-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31272-151">See also</span></span>

- [<span data-ttu-id="31272-152">Chargement de données dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="31272-152">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="31272-153">Exemples LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="31272-153">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="31272-154">Vue d’ensemble des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="31272-154">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="31272-155">Vue d’ensemble des opérateurs de requête standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31272-155">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)

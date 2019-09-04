---
title: 'Exemples de syntaxe d’expression de requête : Opérateurs d’agrégation'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d729120c-4c1b-4f34-bbe9-33694fca2dde
ms.openlocfilehash: 5090616705c799f2905226b4892fa1fbe50bfbf3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249538"
---
# <a name="query-expression-syntax-examples-aggregate-operators"></a><span data-ttu-id="ff56a-102">Exemples de syntaxe d’expression de requête : Opérateurs d’agrégation</span><span class="sxs-lookup"><span data-stu-id="ff56a-102">Query Expression Syntax Examples: Aggregate Operators</span></span>
<span data-ttu-id="ff56a-103">Les exemples de cette rubrique montrent comment utiliser les méthodes <xref:System.Linq.Enumerable.Average%2A> <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Count%2A>,, <xref:System.Linq.Enumerable.Min%2A>et <xref:System.Linq.Enumerable.Sum%2A> pour interroger le [modèle de vente AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) à l’aide de la syntaxe d’expression de requête.</span><span class="sxs-lookup"><span data-stu-id="ff56a-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using query expression syntax.</span></span> <span data-ttu-id="ff56a-104">Le modèle de vente AdventureWorks Sales Model utilisé dans ces exemples est construit à partir des tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ff56a-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="ff56a-105">Les exemples de cette rubrique utilisent les instructions `using` suivantes / `Imports` :</span><span class="sxs-lookup"><span data-stu-id="ff56a-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="average"></a><span data-ttu-id="ff56a-106">Moyenne</span><span class="sxs-lookup"><span data-stu-id="ff56a-106">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="ff56a-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="ff56a-107">Example</span></span>  
 <span data-ttu-id="ff56a-108">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.Average%2A> pour trouver le prix moyen courant des produits de chaque style.</span><span class="sxs-lookup"><span data-stu-id="ff56a-108">The following example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP L2E Examples#Average2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="ff56a-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="ff56a-109">Example</span></span>  
 <span data-ttu-id="ff56a-110">L'exemple suivant utilise <xref:System.Linq.Enumerable.Average%2A> pour obtenir le montant total moyen dû de chaque ID de contact.</span><span class="sxs-lookup"><span data-stu-id="ff56a-110">The following example uses <xref:System.Linq.Enumerable.Average%2A> to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP L2E Examples#AverageGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="ff56a-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="ff56a-111">Example</span></span>  
 <span data-ttu-id="ff56a-112">L'exemple ci-dessous utilise <xref:System.Linq.Enumerable.Average%2A> pour obtenir les commandes présentant le montant total moyen dû pour chaque ID de contact.</span><span class="sxs-lookup"><span data-stu-id="ff56a-112">The following example uses <xref:System.Linq.Enumerable.Average%2A> to get the orders with the average total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP L2E Examples#AverageElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="ff56a-113">Nombre</span><span class="sxs-lookup"><span data-stu-id="ff56a-113">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="ff56a-114">Exemples</span><span class="sxs-lookup"><span data-stu-id="ff56a-114">Example</span></span>  
 <span data-ttu-id="ff56a-115">L'exemple suivant utilise <xref:System.Linq.Enumerable.Count%2A> pour retourner la liste des ID de contact et du nombre de commandes de chaque ID de contact.</span><span class="sxs-lookup"><span data-stu-id="ff56a-115">The following example uses <xref:System.Linq.Enumerable.Count%2A> to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countnested)]
 [!code-vb[DP L2E Examples#CountNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="ff56a-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="ff56a-116">Example</span></span>  
 <span data-ttu-id="ff56a-117">L'exemple suivant regroupe les produits par couleur et utilise <xref:System.Linq.Enumerable.Count%2A> pour retourner le nombre de produits dans chaque groupe de couleur.</span><span class="sxs-lookup"><span data-stu-id="ff56a-117">The following example groups products by color and uses <xref:System.Linq.Enumerable.Count%2A> to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP L2E Examples#CountGrouped](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="max"></a><span data-ttu-id="ff56a-118">Max</span><span class="sxs-lookup"><span data-stu-id="ff56a-118">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="ff56a-119">Exemples</span><span class="sxs-lookup"><span data-stu-id="ff56a-119">Example</span></span>  
 <span data-ttu-id="ff56a-120">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.Max%2A> pour obtenir le montant total dû le plus élevé pour chaque ID de contact.</span><span class="sxs-lookup"><span data-stu-id="ff56a-120">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP L2E Examples#MaxGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="ff56a-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="ff56a-121">Example</span></span>  
 <span data-ttu-id="ff56a-122">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.Max%2A> pour obtenir les commandes présentant le montant total dû le plus élevé pour chaque ID de contact.</span><span class="sxs-lookup"><span data-stu-id="ff56a-122">The following example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP L2E Examples#MaxElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="ff56a-123">Min</span><span class="sxs-lookup"><span data-stu-id="ff56a-123">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="ff56a-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="ff56a-124">Example</span></span>  
 <span data-ttu-id="ff56a-125">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.Min%2A> pour obtenir le montant total dû le plus bas pour chaque ID de contact.</span><span class="sxs-lookup"><span data-stu-id="ff56a-125">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP L2E Examples#MinGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="ff56a-126">Exemples</span><span class="sxs-lookup"><span data-stu-id="ff56a-126">Example</span></span>  
 <span data-ttu-id="ff56a-127">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.Min%2A> pour obtenir les commandes présentant le montant total dû le plus bas pour chaque ID de contact.</span><span class="sxs-lookup"><span data-stu-id="ff56a-127">The following example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP L2E Examples#MinElements_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="ff56a-128">Sum</span><span class="sxs-lookup"><span data-stu-id="ff56a-128">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="ff56a-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="ff56a-129">Example</span></span>  
 <span data-ttu-id="ff56a-130">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.Sum%2A> pour obtenir le montant total dû pour chaque ID de contact.</span><span class="sxs-lookup"><span data-stu-id="ff56a-130">The following example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP L2E Examples#SumGrouped_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="ff56a-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff56a-131">See also</span></span>

- [<span data-ttu-id="ff56a-132">Requêtes dans LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="ff56a-132">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)

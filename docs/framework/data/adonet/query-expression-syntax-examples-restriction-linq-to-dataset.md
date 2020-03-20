---
title: "Exemples de syntaxe de requête d'expression de requête : restriction (LINQ to DataSet)"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1daf42c2-c9f4-4cda-b291-7641b9c6d3fe
ms.openlocfilehash: 6ec4eac6c0fb2d044e429e88d50c619aa38de4b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149191"
---
# <a name="query-expression-syntax-examples-restriction-linq-to-dataset"></a><span data-ttu-id="0645a-102">Exemples de syntaxe de requête d'expression de requête : restriction (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="0645a-102">Query Expression Syntax Examples: Restriction (LINQ to DataSet)</span></span>
<span data-ttu-id="0645a-103">Les exemples de cette rubrique montrent comment utiliser la méthode <xref:System.Linq.Enumerable.Where%2A> pour interroger un <xref:System.Data.DataSet> à l'aide de la syntaxe d'expression de requête.</span><span class="sxs-lookup"><span data-stu-id="0645a-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Where%2A> method to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="0645a-104">La `FillDataSet` méthode utilisée dans ces exemples est spécifiée dans [les données de chargement dans un ensemble de données](loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="0645a-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="0645a-105">Les exemples de cette rubrique utilisent les tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="0645a-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="0645a-106">Les exemples dans ce `using` / `Imports` sujet utilisent les énoncés suivants :</span><span class="sxs-lookup"><span data-stu-id="0645a-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
[!code-csharp[DP LINQ to DataSetExamples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
  
 <span data-ttu-id="0645a-107">Pour plus d’informations, voir [Comment : Créer un projet LINQ à DataSet Dans Visual Studio.](how-to-create-a-linq-to-dataset-project-in-vs.md)</span><span class="sxs-lookup"><span data-stu-id="0645a-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="where"></a><span data-ttu-id="0645a-108">Where</span><span class="sxs-lookup"><span data-stu-id="0645a-108">Where</span></span>  
  
### <a name="example"></a><span data-ttu-id="0645a-109"> Exemple</span><span class="sxs-lookup"><span data-stu-id="0645a-109">Example</span></span>  
 <span data-ttu-id="0645a-110">Cet exemple retourne toutes les commandes en ligne.</span><span class="sxs-lookup"><span data-stu-id="0645a-110">This example returns all online orders.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)]
  
### <a name="example"></a><span data-ttu-id="0645a-111"> Exemple</span><span class="sxs-lookup"><span data-stu-id="0645a-111">Example</span></span>  
 <span data-ttu-id="0645a-112">Cet exemple retourne les commandes où la quantité commandée est supérieure à 2 et inférieure à 6.</span><span class="sxs-lookup"><span data-stu-id="0645a-112">This example returns the orders where the order quantity is greater than 2 and less than 6.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where2)]  
 [!code-vb[DP LINQ to DataSet Examples#Where2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where2)]
  
### <a name="example"></a><span data-ttu-id="0645a-113"> Exemple</span><span class="sxs-lookup"><span data-stu-id="0645a-113">Example</span></span>  
 <span data-ttu-id="0645a-114">Cet exemple retourne tous les produits de couleur rouge.</span><span class="sxs-lookup"><span data-stu-id="0645a-114">This example returns all red colored products.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]  
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]
  
### <a name="example"></a><span data-ttu-id="0645a-115"> Exemple</span><span class="sxs-lookup"><span data-stu-id="0645a-115">Example</span></span>  
 <span data-ttu-id="0645a-116">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.Where%2A> pour rechercher des commandes qui ont été passées après le 1er décembre 2002, puis utilise la méthode <xref:System.Data.DataRow.GetChildRows%2A> pour obtenir les détails de chaque commande.</span><span class="sxs-lookup"><span data-stu-id="0645a-116">This example uses the <xref:System.Linq.Enumerable.Where%2A> method to find orders that were made after December 1, 2002 and then uses the <xref:System.Data.DataRow.GetChildRows%2A> method to get the details for each order.</span></span>  
  
 [!code-csharp[DP LINQ to DataSetExamples#WhereDrillDown](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#wheredrilldown)]
 [!code-vb[DP LINQ to DataSet Examples#WhereDrillDown](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#wheredrilldown)]  
  
## <a name="see-also"></a><span data-ttu-id="0645a-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0645a-117">See also</span></span>

- [<span data-ttu-id="0645a-118">Chargement de données dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="0645a-118">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="0645a-119">Exemples LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="0645a-119">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="0645a-120">Vue d’ensemble des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="0645a-120">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="0645a-121">Vue d’ensemble des opérateurs de requête standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0645a-121">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)

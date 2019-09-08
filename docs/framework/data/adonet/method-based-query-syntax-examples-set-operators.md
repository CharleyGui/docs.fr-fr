---
title: 'Exemples de syntaxe de requête fondée sur une méthode : Opérateurs de jeu (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa93af15-28af-4b5e-846b-897308410edb
ms.openlocfilehash: 481c0ed7e39b8f958ccdae01e4589d54b3ff2446
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783577"
---
# <a name="method-based-query-syntax-examples-set-operators-linq-to-dataset"></a><span data-ttu-id="f3fb6-102">Exemples de syntaxe de requête fondée sur une méthode : Opérateurs de jeu (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="f3fb6-102">Method-Based Query Syntax Examples: Set Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="f3fb6-103">Les exemples de cette rubrique montrent comment <xref:System.Linq.Enumerable.Distinct%2A>utiliser les opérateurs <xref:System.Linq.Enumerable.Intersect%2A>, <xref:System.Linq.Enumerable.Except%2A>, et <xref:System.Linq.Enumerable.Union%2A> pour effectuer des opérations de comparaison basées sur des valeurs sur des ensembles de lignes de données.[ Le chargement de données dans un DataSet](loading-data-into-a-dataset.md) , consultez [comparaison des DataRows](comparing-datarows-linq-to-dataset.md) pour <xref:System.Data.DataRowComparer>plus d’informations sur.</span><span class="sxs-lookup"><span data-stu-id="f3fb6-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, and <xref:System.Linq.Enumerable.Union%2A> operators to perform value-based comparison operations on sets of data rows.[Loading Data Into a DataSet](loading-data-into-a-dataset.md) See [Comparing DataRows](comparing-datarows-linq-to-dataset.md) for more information on <xref:System.Data.DataRowComparer>.</span></span>  
  
 <span data-ttu-id="f3fb6-104">La `FillDataSet` méthode utilisée dans ces exemples est spécifiée lors [du chargement des données dans un DataSet](loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="f3fb6-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="f3fb6-105">Les exemples de cette rubrique utilisent les tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f3fb6-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="f3fb6-106">Les exemples de cette rubrique utilisent les instructions `using` suivantes / `Imports` :</span><span class="sxs-lookup"><span data-stu-id="f3fb6-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="f3fb6-107">Pour plus d'informations, voir [Procédure : Créez un projet de LINQ to DataSet dans Visual](how-to-create-a-linq-to-dataset-project-in-vs.md)Studio.</span><span class="sxs-lookup"><span data-stu-id="f3fb6-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="distinct"></a><span data-ttu-id="f3fb6-108">distinct</span><span class="sxs-lookup"><span data-stu-id="f3fb6-108">Distinct</span></span>  
  
### <a name="example"></a><span data-ttu-id="f3fb6-109">Exemples</span><span class="sxs-lookup"><span data-stu-id="f3fb6-109">Example</span></span>  
 <span data-ttu-id="f3fb6-110">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.Distinct%2A> pour supprimer des éléments en double dans une séquence.</span><span class="sxs-lookup"><span data-stu-id="f3fb6-110">This example uses the <xref:System.Linq.Enumerable.Distinct%2A> method to remove duplicate elements in a sequence.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#distinctrows)]
 [!code-vb[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#distinctrows)]  
  
## <a name="except"></a><span data-ttu-id="f3fb6-111">À l'exception</span><span class="sxs-lookup"><span data-stu-id="f3fb6-111">Except</span></span>  
  
### <a name="example"></a><span data-ttu-id="f3fb6-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="f3fb6-112">Example</span></span>  
 <span data-ttu-id="f3fb6-113">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.Except%2A> pour retourner les contacts qui apparaissent dans la première table, mais pas dans la seconde.</span><span class="sxs-lookup"><span data-stu-id="f3fb6-113">This example uses the <xref:System.Linq.Enumerable.Except%2A> method to return contacts that appear in the first table but not in the second.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#except2)]
 [!code-vb[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#except2)]  
  
## <a name="intersect"></a><span data-ttu-id="f3fb6-114">Définir une intersection</span><span class="sxs-lookup"><span data-stu-id="f3fb6-114">Intersect</span></span>  
  
### <a name="example"></a><span data-ttu-id="f3fb6-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="f3fb6-115">Example</span></span>  
 <span data-ttu-id="f3fb6-116">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.Intersect%2A> pour retourner les contacts qui apparaissent dans les deux tables.</span><span class="sxs-lookup"><span data-stu-id="f3fb6-116">This example uses the <xref:System.Linq.Enumerable.Intersect%2A> method to return contacts that appear in both tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
## <a name="union"></a><span data-ttu-id="f3fb6-117">Union</span><span class="sxs-lookup"><span data-stu-id="f3fb6-117">Union</span></span>  
  
### <a name="example"></a><span data-ttu-id="f3fb6-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="f3fb6-118">Example</span></span>  
 <span data-ttu-id="f3fb6-119">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.Union%2A> pour retourner des contacts uniques dans l'une ou l'autre des tables.</span><span class="sxs-lookup"><span data-stu-id="f3fb6-119">This example uses the <xref:System.Linq.Enumerable.Union%2A> method to return unique contacts from either of the two tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#union2)]
 [!code-vb[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#union2)]  
  
## <a name="see-also"></a><span data-ttu-id="f3fb6-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3fb6-120">See also</span></span>

- [<span data-ttu-id="f3fb6-121">Chargement de données dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="f3fb6-121">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="f3fb6-122">Exemples LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="f3fb6-122">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="f3fb6-123">Vue d’ensemble des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="f3fb6-123">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="f3fb6-124">Vue d’ensemble des opérateurs de requête standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f3fb6-124">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)

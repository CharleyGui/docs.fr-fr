---
title: Exemples d'opérateurs spécifiques aux DataSets (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fdd64af-6ad0-46cd-91c8-dbe26620eeb1
ms.openlocfilehash: 6a9dc82e0bb065b455c0208daaf2d28a74cd7e34
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784201"
---
# <a name="dataset-specific-operator-examples-linq-to-dataset"></a><span data-ttu-id="76c8b-102">Exemples d'opérateurs spécifiques aux DataSets (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="76c8b-102">DataSet-Specific Operator Examples (LINQ to DataSet)</span></span>
<span data-ttu-id="76c8b-103">Les exemples de cette rubrique montrent comment utiliser la méthode <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> et la classe <xref:System.Data.DataRowComparer>.</span><span class="sxs-lookup"><span data-stu-id="76c8b-103">The examples in this topic demonstrate how to use the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method and the <xref:System.Data.DataRowComparer> class.</span></span>  
  
 <span data-ttu-id="76c8b-104">La `FillDataSet` méthode utilisée dans ces exemples est spécifiée lors [du chargement des données dans un DataSet](loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="76c8b-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="76c8b-105">Les exemples de cette rubrique utilisent les tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="76c8b-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="76c8b-106">Les exemples de cette rubrique utilisent les instructions `using` suivantes / `Imports` :</span><span class="sxs-lookup"><span data-stu-id="76c8b-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="76c8b-107">Pour plus d’informations, consultez [Guide pratique pour Créez un projet de LINQ to DataSet dans Visual](how-to-create-a-linq-to-dataset-project-in-vs.md)Studio.</span><span class="sxs-lookup"><span data-stu-id="76c8b-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="copytodatatable"></a><span data-ttu-id="76c8b-108">CopyToDataTable</span><span class="sxs-lookup"><span data-stu-id="76c8b-108">CopyToDataTable</span></span>  
  
### <a name="example"></a><span data-ttu-id="76c8b-109">Exemples</span><span class="sxs-lookup"><span data-stu-id="76c8b-109">Example</span></span>  
 <span data-ttu-id="76c8b-110">Cet exemple montre comment charger un <xref:System.Data.DataTable> avec les résultats de la requête à l'aide de la méthode <xref:System.Data.DataTableExtensions.CopyToDataTable%2A>.</span><span class="sxs-lookup"><span data-stu-id="76c8b-110">This example loads a <xref:System.Data.DataTable> with query results by using the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#LoadDataTableWithQueryResults](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#loaddatatablewithqueryresults)]
 [!code-vb[DP LINQ to DataSet Examples#LoadDataTableWithQueryResults](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#loaddatatablewithqueryresults)]  
  
## <a name="datarowcomparer"></a><span data-ttu-id="76c8b-111">DataRowComparer</span><span class="sxs-lookup"><span data-stu-id="76c8b-111">DataRowComparer</span></span>  
  
### <a name="example"></a><span data-ttu-id="76c8b-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="76c8b-112">Example</span></span>  
 <span data-ttu-id="76c8b-113">Cet exemple montre comment comparer deux lignes de données différentes à l'aide de <xref:System.Data.DataRowComparer>.</span><span class="sxs-lookup"><span data-stu-id="76c8b-113">This example compares two different data rows by using <xref:System.Data.DataRowComparer>.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CompareDifferentDataRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#comparedifferentdatarows)]  
  
## <a name="see-also"></a><span data-ttu-id="76c8b-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="76c8b-114">See also</span></span>

- [<span data-ttu-id="76c8b-115">Chargement de données dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="76c8b-115">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="76c8b-116">Exemples LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="76c8b-116">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)

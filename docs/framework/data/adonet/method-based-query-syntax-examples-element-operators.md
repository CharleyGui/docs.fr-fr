---
title: "Exemples de syntaxe de requête fondée sur une méthode : opérateurs d'élément (LINQ to DataSet)"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eedf2fbd-f407-4f62-bb1a-c00eb001b1dd
ms.openlocfilehash: 669c6a34d1179caf4ec40eb8db559bdfdc9fc7f5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189277"
---
# <a name="method-based-query-syntax-examples-element-operators-linq-to-dataset"></a><span data-ttu-id="76bb1-102">Exemples de syntaxe de requête fondée sur une méthode : opérateurs d'élément (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="76bb1-102">Method-Based Query Syntax Examples: Element Operators (LINQ to DataSet)</span></span>

<span data-ttu-id="76bb1-103">Les exemples de cette rubrique montrent comment utiliser les méthodes <xref:System.Linq.Enumerable.First%2A> et <xref:System.Linq.Enumerable.ElementAt%2A> pour obtenir des éléments <xref:System.Data.DataRow> à partir d'un <xref:System.Data.DataSet> à l'aide de la syntaxe d'expression de requête.</span><span class="sxs-lookup"><span data-stu-id="76bb1-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="76bb1-104">La `FillDataSet` méthode utilisée dans ces exemples est spécifiée lors [du chargement des données dans un DataSet](loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="76bb1-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="76bb1-105">Les exemples de cette rubrique utilisent les tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="76bb1-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="76bb1-106">Les exemples de cette rubrique utilisent les `using` / `Imports` instructions suivantes :</span><span class="sxs-lookup"><span data-stu-id="76bb1-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
[!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
[!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]

 <span data-ttu-id="76bb1-107">Pour plus d’informations, consultez [Comment : créer un projet LINQ to DataSet dans Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="76bb1-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="elementat"></a><span data-ttu-id="76bb1-108">ElementAt</span><span class="sxs-lookup"><span data-stu-id="76bb1-108">ElementAt</span></span>  
  
### <a name="example"></a><span data-ttu-id="76bb1-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="76bb1-109">Example</span></span>  

 <span data-ttu-id="76bb1-110">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.ElementAt%2A> pour récupérer la cinquième adresse où le `PostalCode` est "M4B 1V7".</span><span class="sxs-lookup"><span data-stu-id="76bb1-110">This example uses the <xref:System.Linq.Enumerable.ElementAt%2A> method to retrieve the fifth address where `PostalCode` == "M4B 1V7".</span></span>  
  
[!code-csharp[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#elementat)]
[!code-vb[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#elementat)]
  
## <a name="first"></a><span data-ttu-id="76bb1-111">Premier</span><span class="sxs-lookup"><span data-stu-id="76bb1-111">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="76bb1-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="76bb1-112">Example</span></span>  

 <span data-ttu-id="76bb1-113">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.First%2A> pour retourner le premier contact dont le prénom est 'Brooke'.</span><span class="sxs-lookup"><span data-stu-id="76bb1-113">This example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is 'Brooke'.</span></span>  
  
[!code-csharp[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#firstsimple)]
[!code-vb[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#firstsimple)]
  
## <a name="see-also"></a><span data-ttu-id="76bb1-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="76bb1-114">See also</span></span>

- [<span data-ttu-id="76bb1-115">Chargement de données dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="76bb1-115">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="76bb1-116">Exemples de LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="76bb1-116">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="76bb1-117">Présentation des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="76bb1-117">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="76bb1-118">Vue d’ensemble des opérateurs de requête standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76bb1-118">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)

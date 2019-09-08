---
title: 'Exemples de syntaxe de requête fondée sur une méthode : Opérateurs de conversion (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a084c16b-9b55-4690-aefd-f8e0810a92c3
ms.openlocfilehash: 3e2a72a2bb0921828bdd90fe437987fddfc995b5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783692"
---
# <a name="method-based-query-syntax-examples-conversion-operators-linq-to-dataset"></a><span data-ttu-id="9e699-102">Exemples de syntaxe de requête fondée sur une méthode : Opérateurs de conversion (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="9e699-102">Method-Based Query Syntax Examples: Conversion Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="9e699-103">Les exemples de cette rubrique montrent comment utiliser les méthodes <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A> et <xref:System.Linq.Enumerable.ToList%2A> pour exécuter immédiatement une expression de requête.</span><span class="sxs-lookup"><span data-stu-id="9e699-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A>, and <xref:System.Linq.Enumerable.ToList%2A> methods to immediately execute a query expression.</span></span>  
  
 <span data-ttu-id="9e699-104">La `FillDataSet` méthode utilisée dans ces exemples est spécifiée lors [du chargement des données dans un DataSet](loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="9e699-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="9e699-105">Les exemples de cette rubrique utilisent les tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="9e699-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="9e699-106">Les exemples de cette rubrique utilisent les instructions `using` suivantes / `Imports` :</span><span class="sxs-lookup"><span data-stu-id="9e699-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="9e699-107">Pour plus d’informations, consultez [Guide pratique pour Créez un projet de LINQ to DataSet dans Visual](how-to-create-a-linq-to-dataset-project-in-vs.md)Studio.</span><span class="sxs-lookup"><span data-stu-id="9e699-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="toarray"></a><span data-ttu-id="9e699-108">ToArray</span><span class="sxs-lookup"><span data-stu-id="9e699-108">ToArray</span></span>  
  
### <a name="example"></a><span data-ttu-id="9e699-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="9e699-109">Example</span></span>  
 <span data-ttu-id="9e699-110">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.ToArray%2A> pour évaluer immédiatement une séquence dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="9e699-110">This example uses the <xref:System.Linq.Enumerable.ToArray%2A> method to immediately evaluate a sequence into an array.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToArray](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#toarray)]
 [!code-vb[DP LINQ to DataSet Examples#ToArray](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a><span data-ttu-id="9e699-111">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="9e699-111">ToDictionary</span></span>  
  
### <a name="example"></a><span data-ttu-id="9e699-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="9e699-112">Example</span></span>  
 <span data-ttu-id="9e699-113">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.ToDictionary%2A> pour évaluer immédiatement une séquence et une expression clé associée dans un dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="9e699-113">This example uses the <xref:System.Linq.Enumerable.ToDictionary%2A> method to immediately evaluate a sequence and a related key expression into a dictionary.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToDictionary](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP LINQ to DataSet Examples#ToDictionary](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a><span data-ttu-id="9e699-114">ToList</span><span class="sxs-lookup"><span data-stu-id="9e699-114">ToList</span></span>  
  
### <a name="example"></a><span data-ttu-id="9e699-115">Exemples</span><span class="sxs-lookup"><span data-stu-id="9e699-115">Example</span></span>  
 <span data-ttu-id="9e699-116">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.ToList%2A> pour évaluer immédiatement une séquence dans une <xref:System.Collections.Generic.List%601> où `T` est de type <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="9e699-116">This example uses the <xref:System.Linq.Enumerable.ToList%2A> method to immediately evaluate a sequence into a <xref:System.Collections.Generic.List%601>, where `T` is of type <xref:System.Data.DataRow>.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToList](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#tolist)]
 [!code-vb[DP LINQ to DataSet Examples#ToList](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a><span data-ttu-id="9e699-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e699-117">See also</span></span>

- [<span data-ttu-id="9e699-118">Chargement de données dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="9e699-118">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="9e699-119">Exemples LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="9e699-119">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="9e699-120">Vue d’ensemble des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="9e699-120">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="9e699-121">Vue d’ensemble des opérateurs de requête standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e699-121">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)

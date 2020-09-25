---
title: "Exemples de syntaxe d'expression de requête : opérateurs de jointure (LINQ to DataSet)"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f4d86667-3392-470d-a076-5ca6cbb660f6
ms.openlocfilehash: 637b815553d7c7f9a5fb4ffe644d2975468e1090
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189095"
---
# <a name="query-expression-syntax-examples-join-operators-linq-to-dataset"></a><span data-ttu-id="92bb2-102">Exemples de syntaxe d'expression de requête : opérateurs de jointure (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="92bb2-102">Query Expression Syntax Examples: Join Operators (LINQ to DataSet)</span></span>

<span data-ttu-id="92bb2-103">La jointure est une opération importante dans les requêtes qui ciblent des sources de données qui n'ont pas de relations explorables les unes avec les autres, comme les tables de base de données relationnelles.</span><span class="sxs-lookup"><span data-stu-id="92bb2-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="92bb2-104">Une jointure de deux sources de données est l'association d'objets dans une source de données avec des objets qui partagent un attribut commun dans l'autre source de données.</span><span class="sxs-lookup"><span data-stu-id="92bb2-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="92bb2-105">Pour plus d’informations, consultez [vue d’ensemble des opérateurs de requête standard (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) ou [vue d’ensemble des opérateurs de requête standard (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="92bb2-105">For more information, see [Standard Query Operators Overview (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
 <span data-ttu-id="92bb2-106">Les exemples de cette rubrique montrent comment utiliser les méthodes <xref:System.Linq.Enumerable.GroupJoin%2A> et <xref:System.Linq.Enumerable.Join%2A> pour interroger un <xref:System.Data.DataSet> à l'aide de la syntaxe d'expression de requête.</span><span class="sxs-lookup"><span data-stu-id="92bb2-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="92bb2-107">La `FillDataSet` méthode utilisée dans ces exemples est spécifiée lors [du chargement des données dans un DataSet](loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="92bb2-107">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="92bb2-108">Les exemples de cette rubrique utilisent les tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="92bb2-108">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="92bb2-109">Les exemples de cette rubrique utilisent les `using` / `Imports` instructions suivantes :</span><span class="sxs-lookup"><span data-stu-id="92bb2-109">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="92bb2-110">Pour plus d’informations, consultez [Comment : créer un projet LINQ to DataSet dans Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="92bb2-110">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="groupjoin"></a><span data-ttu-id="92bb2-111">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="92bb2-111">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="92bb2-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="92bb2-112">Example</span></span>  

 <span data-ttu-id="92bb2-113">Cet exemple effectue une <xref:System.Linq.Enumerable.GroupJoin%2A> sur les tables `SalesOrderHeader` et `SalesOrderDetail` pour trouver le nombre de commandes par client.</span><span class="sxs-lookup"><span data-stu-id="92bb2-113">This example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the `SalesOrderHeader` and `SalesOrderDetail` tables to find the number of orders per customer.</span></span> <span data-ttu-id="92bb2-114">Une jointure de groupe est l'équivalent d'une jointure externe gauche qui retourne chaque élément de la première source de données (gauche), même s'il n'y a pas d'éléments corrélés dans l'autre source de données.</span><span class="sxs-lookup"><span data-stu-id="92bb2-114">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#GroupJoin2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#groupjoin2)]
 [!code-vb[DP LINQ to DataSet Examples#GroupJoin2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#groupjoin2)]  
  
### <a name="example"></a><span data-ttu-id="92bb2-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="92bb2-115">Example</span></span>  

 <span data-ttu-id="92bb2-116">Cet exemple effectue une <xref:System.Linq.Enumerable.GroupJoin%2A> sur les tables `Contact` et `SalesOrderHeader`.</span><span class="sxs-lookup"><span data-stu-id="92bb2-116">This example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the `Contact` and `SalesOrderHeader` tables.</span></span> <span data-ttu-id="92bb2-117">Une jointure de groupe est l'équivalent d'une jointure externe gauche qui retourne chaque élément de la première source de données (gauche), même s'il n'y a pas d'éléments corrélés dans l'autre source de données.</span><span class="sxs-lookup"><span data-stu-id="92bb2-117">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#GroupJoin](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP LINQ to DataSet Examples#GroupJoin](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#groupjoin)]  
  
## <a name="join"></a><span data-ttu-id="92bb2-118">Join</span><span class="sxs-lookup"><span data-stu-id="92bb2-118">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="92bb2-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="92bb2-119">Example</span></span>  

 <span data-ttu-id="92bb2-120">Cet exemple effectue une jointure sur les tables `SalesOrderHeader` et `SalesOrderDetail` pour obtenir les commandes en ligne du mois d'août.</span><span class="sxs-lookup"><span data-stu-id="92bb2-120">This example performs a join over the `SalesOrderHeader` and `SalesOrderDetail` tables to get online orders from the month of August.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a><span data-ttu-id="92bb2-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92bb2-121">See also</span></span>

- [<span data-ttu-id="92bb2-122">Chargement de données dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="92bb2-122">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="92bb2-123">Exemples de LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="92bb2-123">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="92bb2-124">Présentation des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="92bb2-124">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="92bb2-125">Vue d’ensemble des opérateurs de requête standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92bb2-125">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)

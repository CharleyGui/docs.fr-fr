---
title: 'Exemples de syntaxe d’expression de requête : Projection (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48c9f5ed-76bf-4228-ab10-5217bbb295a3
ms.openlocfilehash: 9b8e898ce666b8b443521391eda67318bdf23915
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783001"
---
# <a name="query-expression-syntax-examples-projection--linq-to-dataset"></a><span data-ttu-id="7e7a5-102">Exemples de syntaxe d’expression de requête : Projection (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="7e7a5-102">Query Expression Syntax Examples: Projection  (LINQ to DataSet)</span></span>
<span data-ttu-id="7e7a5-103">Les exemples de cette rubrique montrent comment utiliser les méthodes <xref:System.Linq.Enumerable.Select%2A> et <xref:System.Linq.Enumerable.SelectMany%2A> pour interroger un <xref:System.Data.DataSet> à l'aide de la syntaxe d'expression de requête.</span><span class="sxs-lookup"><span data-stu-id="7e7a5-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="7e7a5-104">La `FillDataSet` méthode utilisée dans ces exemples est spécifiée lors [du chargement des données dans un DataSet](loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="7e7a5-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="7e7a5-105">Les exemples de cette rubrique utilisent les tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="7e7a5-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="7e7a5-106">Les exemples de cette rubrique utilisent les instructions `using` suivantes / `Imports` :</span><span class="sxs-lookup"><span data-stu-id="7e7a5-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="7e7a5-107">Pour plus d'informations, voir [Procédure : Créez un projet de LINQ to DataSet dans Visual](how-to-create-a-linq-to-dataset-project-in-vs.md)Studio.</span><span class="sxs-lookup"><span data-stu-id="7e7a5-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="select"></a><span data-ttu-id="7e7a5-108">Sélectionnez</span><span class="sxs-lookup"><span data-stu-id="7e7a5-108">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="7e7a5-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="7e7a5-109">Example</span></span>  
 <span data-ttu-id="7e7a5-110">Cet exemple utilise la méthode <xref:System.Linq.Enumerable.Select%2A> pour retourner toutes les lignes de la table `Product` et afficher les noms de produits.</span><span class="sxs-lookup"><span data-stu-id="7e7a5-110">This example uses the <xref:System.Linq.Enumerable.Select%2A> method to return all the rows from the `Product` table and display the product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a><span data-ttu-id="7e7a5-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="7e7a5-111">Example</span></span>  
 <span data-ttu-id="7e7a5-112">Cet exemple utilise <xref:System.Linq.Enumerable.Select%2A> pour retourner une séquence comportant uniquement des noms de produits.</span><span class="sxs-lookup"><span data-stu-id="7e7a5-112">This example uses <xref:System.Linq.Enumerable.Select%2A> to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple2)]  
  
## <a name="selectmany"></a><span data-ttu-id="7e7a5-113">SelectMany</span><span class="sxs-lookup"><span data-stu-id="7e7a5-113">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="7e7a5-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="7e7a5-114">Example</span></span>  
 <span data-ttu-id="7e7a5-115">Cet exemple utilise `From …, …` (l'équivalent de la méthode <xref:System.Linq.Enumerable.SelectMany%2A>) pour sélectionner toutes les commandes où le `TotalDue` est inférieur à 500.</span><span class="sxs-lookup"><span data-stu-id="7e7a5-115">This example uses `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a><span data-ttu-id="7e7a5-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="7e7a5-116">Example</span></span>  
 <span data-ttu-id="7e7a5-117">Cet exemple utilise `From …, …` (l'équivalent de la méthode <xref:System.Linq.Enumerable.SelectMany%2A>) pour sélectionner toutes les commandes qui ont été passées le 1er octobre 2002 ou après.</span><span class="sxs-lookup"><span data-stu-id="7e7a5-117">This example uses `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a><span data-ttu-id="7e7a5-118">Exemples</span><span class="sxs-lookup"><span data-stu-id="7e7a5-118">Example</span></span>  
 <span data-ttu-id="7e7a5-119">Cet exemple utilise un `From …, …` (l'équivalent de la méthode <xref:System.Linq.Enumerable.SelectMany%2A>) pour sélectionner toutes les commandes dont le total est supérieur à 10 000 et utilise l'assignation `From` pour éviter de demander deux fois le total.</span><span class="sxs-lookup"><span data-stu-id="7e7a5-119">This example uses a `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order total is greater than 10000.00 and uses `From` assignment to avoid requesting the total twice.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a><span data-ttu-id="7e7a5-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e7a5-120">See also</span></span>

- [<span data-ttu-id="7e7a5-121">Chargement de données dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="7e7a5-121">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="7e7a5-122">Exemples LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="7e7a5-122">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="7e7a5-123">Vue d’ensemble des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="7e7a5-123">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="7e7a5-124">Vue d’ensemble des opérateurs de requête standard (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e7a5-124">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)

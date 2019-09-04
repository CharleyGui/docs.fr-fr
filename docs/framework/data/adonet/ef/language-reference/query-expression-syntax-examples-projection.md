---
title: 'Exemples de syntaxe d’expression de requête : Projection'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 079926c5-e6b5-4fb9-b4cf-9c63886dd626
ms.openlocfilehash: 52681a4035ef55133c6191e7eac2cab7ed36c8fb
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249344"
---
# <a name="query-expression-syntax-examples-projection"></a><span data-ttu-id="9763d-102">Exemples de syntaxe d’expression de requête : Projection</span><span class="sxs-lookup"><span data-stu-id="9763d-102">Query Expression Syntax Examples: Projection</span></span>
<span data-ttu-id="9763d-103">Les exemples de cette rubrique montrent comment utiliser la méthode `Select` et les `From … From …` Mots clés pour interroger le [modèle de vente AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) à l’aide de la syntaxe d’expression de requête.</span><span class="sxs-lookup"><span data-stu-id="9763d-103">The examples in this topic demonstrate how to use the `Select` method and the `From … From …` keywords to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using query expression syntax.</span></span> <span data-ttu-id="9763d-104">`From … From …` est l'équivalent basé sur une requête de la méthode `SelectMany`.</span><span class="sxs-lookup"><span data-stu-id="9763d-104">`From … From …` is the query based equivalent of the `SelectMany` method.</span></span> <span data-ttu-id="9763d-105">Le modèle de vente AdventureWorks Sales Model utilisé dans ces exemples est construit à partir des tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="9763d-105">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="9763d-106">Les exemples de cette rubrique utilisent les instructions `using` suivantes / `Imports` :</span><span class="sxs-lookup"><span data-stu-id="9763d-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a><span data-ttu-id="9763d-107">Sélectionnez</span><span class="sxs-lookup"><span data-stu-id="9763d-107">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="9763d-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="9763d-108">Example</span></span>  
 <span data-ttu-id="9763d-109">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.Select%2A> pour retourner toutes les lignes de la table `Product` et afficher les noms de produits.</span><span class="sxs-lookup"><span data-stu-id="9763d-109">The following example uses the <xref:System.Linq.Enumerable.Select%2A> method to return all the rows from the `Product` table and display the product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a><span data-ttu-id="9763d-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="9763d-110">Example</span></span>  
 <span data-ttu-id="9763d-111">L'exemple ci-dessous utilise <xref:System.Linq.Enumerable.Select%2A> pour retourner une séquence comportant uniquement des noms de produits.</span><span class="sxs-lookup"><span data-stu-id="9763d-111">The following example uses <xref:System.Linq.Enumerable.Select%2A> to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2)]  
  
### <a name="example"></a><span data-ttu-id="9763d-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="9763d-112">Example</span></span>  
 <span data-ttu-id="9763d-113">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Queryable.Select%2A> pour projeter les propriétés `Product.Name` et `Product.ProductID` dans une séquence de types anonymes.</span><span class="sxs-lookup"><span data-stu-id="9763d-113">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to project the `Product.Name` and `Product.ProductID` properties into a sequence of anonymous types.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes)]  
  
## <a name="from--from--selectmany"></a><span data-ttu-id="9763d-114">De...</span><span class="sxs-lookup"><span data-stu-id="9763d-114">From …</span></span> <span data-ttu-id="9763d-115">De...</span><span class="sxs-lookup"><span data-stu-id="9763d-115">From …</span></span> <span data-ttu-id="9763d-116">SelectMany</span><span class="sxs-lookup"><span data-stu-id="9763d-116">(SelectMany)</span></span>  
  
### <a name="example"></a><span data-ttu-id="9763d-117">Exemples</span><span class="sxs-lookup"><span data-stu-id="9763d-117">Example</span></span>  
 <span data-ttu-id="9763d-118">L'exemple ci-dessous utilise `From … From …` (l'équivalent de la méthode <xref:System.Linq.Enumerable.SelectMany%2A>) pour sélectionner toutes les commandes où `TotalDue` est inférieur à 500.</span><span class="sxs-lookup"><span data-stu-id="9763d-118">The following example uses `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a><span data-ttu-id="9763d-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="9763d-119">Example</span></span>  
 <span data-ttu-id="9763d-120">L'exemple ci-dessous utilise `From … From …` (l'équivalent de la méthode <xref:System.Linq.Enumerable.SelectMany%2A>) pour sélectionner toutes les commandes qui ont été passées le 1er octobre 2002 ou après.</span><span class="sxs-lookup"><span data-stu-id="9763d-120">The following example uses `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a><span data-ttu-id="9763d-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="9763d-121">Example</span></span>  
 <span data-ttu-id="9763d-122">L'exemple ci-dessous utilise `From … From …` (l'équivalent de la méthode <xref:System.Linq.Enumerable.SelectMany%2A>) pour sélectionner toutes les commandes dont le total est supérieur à 10 000 et utilise l'assignation `From` pour éviter de demander deux fois le total.</span><span class="sxs-lookup"><span data-stu-id="9763d-122">The following example uses a `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order total is greater than 10000.00 and uses `From` assignment to avoid requesting the total twice.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a><span data-ttu-id="9763d-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9763d-123">See also</span></span>

- [<span data-ttu-id="9763d-124">Requêtes dans LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="9763d-124">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)

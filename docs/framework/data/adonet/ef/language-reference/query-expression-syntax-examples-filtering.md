---
title: 'Exemples de syntaxe d’expression de requête : Filtrage'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c27cb89c-1c1d-4988-9f38-950eda3cb275
ms.openlocfilehash: 4ce4e28df3a09ddf718b000725afb0c9125bdd77
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397105"
---
# <a name="query-expression-syntax-examples-filtering"></a><span data-ttu-id="58cea-102">Exemples de syntaxe d’expression de requête : Filtrage</span><span class="sxs-lookup"><span data-stu-id="58cea-102">Query Expression Syntax Examples: Filtering</span></span>
<span data-ttu-id="58cea-103">Les exemples de cette rubrique montrent comment utiliser les méthodes `Where` et `Where…Contains` pour interroger le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) à l’aide de la syntaxe d’expression de requête.</span><span class="sxs-lookup"><span data-stu-id="58cea-103">The examples in this topic demonstrate how to use the `Where` and `Where…Contains` methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="58cea-104">Remarque : où...`Contains`</span><span class="sxs-lookup"><span data-stu-id="58cea-104">Note, Where…`Contains`</span></span> <span data-ttu-id="58cea-105">ne peut pas être utilisé dans le cadre d’une [requête compilée](compiled-queries-linq-to-entities.md).</span><span class="sxs-lookup"><span data-stu-id="58cea-105">cannot be used as a part of a [compiled query](compiled-queries-linq-to-entities.md).</span></span>  
  
 <span data-ttu-id="58cea-106">Le modèle de vente AdventureWorks Sales Model utilisé dans ces exemples est construit à partir des tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="58cea-106">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="58cea-107">Les exemples de cette rubrique utilisent les instructions `using` suivantes / `Imports` :</span><span class="sxs-lookup"><span data-stu-id="58cea-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="where"></a><span data-ttu-id="58cea-108">Where</span><span class="sxs-lookup"><span data-stu-id="58cea-108">Where</span></span>  
  
### <a name="example"></a><span data-ttu-id="58cea-109">Exemples</span><span class="sxs-lookup"><span data-stu-id="58cea-109">Example</span></span>  
 <span data-ttu-id="58cea-110">L'exemple suivant retourne toutes les commandes en ligne.</span><span class="sxs-lookup"><span data-stu-id="58cea-110">The following example returns all online orders.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where1)]
 [!code-vb[DP L2E Examples#Where1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where1)]  
  
### <a name="example"></a><span data-ttu-id="58cea-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="58cea-111">Example</span></span>  
 <span data-ttu-id="58cea-112">L'exemple suivant retourne les commandes où la quantité commandée est supérieure à 2 et inférieure à 6.</span><span class="sxs-lookup"><span data-stu-id="58cea-112">The following example returns the orders where the order quantity is greater than 2 and less than 6.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where2)]
 [!code-vb[DP L2E Examples#Where2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where2)]  
  
### <a name="example"></a><span data-ttu-id="58cea-113">Exemples</span><span class="sxs-lookup"><span data-stu-id="58cea-113">Example</span></span>  
 <span data-ttu-id="58cea-114">L'exemple suivant retourne tous les produits de couleur rouge.</span><span class="sxs-lookup"><span data-stu-id="58cea-114">The following example returns all red colored products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where3)]
 [!code-vb[DP L2E Examples#Where3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where3)]  
  
### <a name="example"></a><span data-ttu-id="58cea-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="58cea-115">Example</span></span>  
 <span data-ttu-id="58cea-116">L'exemple ci-dessous utilise la méthode `Where` pour rechercher des commandes qui ont été passées après le 1er décembre 2003, puis utilise la propriété de navigation `order.SalesOrderDetail` pour obtenir les détails de chaque commande.</span><span class="sxs-lookup"><span data-stu-id="58cea-116">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="wherecontains"></a><span data-ttu-id="58cea-117">Where…Contains</span><span class="sxs-lookup"><span data-stu-id="58cea-117">Where…Contains</span></span>  
  
### <a name="example"></a><span data-ttu-id="58cea-118">Exemples</span><span class="sxs-lookup"><span data-stu-id="58cea-118">Example</span></span>  
 <span data-ttu-id="58cea-119">L'exemple ci-dessous utilise un tableau dans le cadre d'une clause `Where…Contains` pour rechercher tous les produits qui ont un `ProductModelID` qui correspond à une valeur dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="58cea-119">The following example uses an array as part of a `Where…Contains` clause to find all products that have a `ProductModelID` that matches a value in the array.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#1)]
 [!code-vb[DP L2E ArraysAndListsInQueries#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#1)]  
  
> [!NOTE]
> <span data-ttu-id="58cea-120">Dans le cadre du prédicat dans une clause `Where…Contains`, vous pouvez utiliser un <xref:System.Array>, un <xref:System.Collections.Generic.List%601> ou une collection de type quelconque qui implémente l’interface <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="58cea-120">As part of the predicate in a `Where…Contains` clause, you can use an <xref:System.Array>, a <xref:System.Collections.Generic.List%601>, or a collection of any type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="58cea-121">Vous pouvez également déclarer et initialiser une collection dans une requête LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="58cea-121">You can also declare and initialize a collection within a LINQ to Entities query.</span></span> <span data-ttu-id="58cea-122">Pour plus d'informations, consultez l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="58cea-122">See the next example for more information.</span></span>  
  
### <a name="example"></a><span data-ttu-id="58cea-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="58cea-123">Example</span></span>  
 <span data-ttu-id="58cea-124">L'exemple ci-dessous déclare et initialise des tableaux dans une clause `Where…Contains` pour rechercher tous les produits qui ont un `ProductModelID` ou un `Size` correspondant aux valeurs dans les tableaux.</span><span class="sxs-lookup"><span data-stu-id="58cea-124">The following example declares and initializes arrays in a `Where…Contains` clause to find all products that have a `ProductModelID` or `Size` that match values in the arrays.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#2)]
 [!code-vb[DP L2E ArraysAndListsInQueries#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="58cea-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58cea-125">See also</span></span>

- [<span data-ttu-id="58cea-126">Requêtes dans LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="58cea-126">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)

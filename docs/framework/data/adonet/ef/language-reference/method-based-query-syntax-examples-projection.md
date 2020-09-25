---
title: 'Exemples de syntaxe de requête fondée sur une méthode : projection'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 505491fa-5920-43ce-8a96-c25389e125d8
ms.openlocfilehash: 32db3d0f85e525ad1850df59f0abe66bf82b137b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175783"
---
# <a name="method-based-query-syntax-examples-projection"></a><span data-ttu-id="fd1ce-102">Exemples de syntaxe de requête fondée sur une méthode : projection</span><span class="sxs-lookup"><span data-stu-id="fd1ce-102">Method-Based Query Syntax Examples: Projection</span></span>

<span data-ttu-id="fd1ce-103">Les exemples de cette rubrique montrent comment utiliser les <xref:System.Linq.Enumerable.Select%2A> méthodes et <xref:System.Linq.Enumerable.SelectMany%2A> pour interroger le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) à l’aide de la syntaxe de requête fondée sur une méthode.</span><span class="sxs-lookup"><span data-stu-id="fd1ce-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="fd1ce-104">Le modèle de vente AdventureWorks Sales Model utilisé dans ces exemples est construit à partir des tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="fd1ce-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="fd1ce-105">Les exemples de cette rubrique utilisent les `using` / `Imports` instructions suivantes :</span><span class="sxs-lookup"><span data-stu-id="fd1ce-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a><span data-ttu-id="fd1ce-106">Sélectionnez</span><span class="sxs-lookup"><span data-stu-id="fd1ce-106">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="fd1ce-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="fd1ce-107">Example</span></span>  

 <span data-ttu-id="fd1ce-108">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Queryable.Select%2A> pour projeter les propriétés `Product.Name` et `Product.ProductID` dans une séquence de types anonymes.</span><span class="sxs-lookup"><span data-stu-id="fd1ce-108">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to project the `Product.Name` and `Product.ProductID` properties into a sequence of anonymous types.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
### <a name="example"></a><span data-ttu-id="fd1ce-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="fd1ce-109">Example</span></span>  

 <span data-ttu-id="fd1ce-110">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.Select%2A> pour retourner une séquence comportant uniquement des noms de produits.</span><span class="sxs-lookup"><span data-stu-id="fd1ce-110">The following example uses the <xref:System.Linq.Enumerable.Select%2A> method to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2_mq)]
 [!code-vb[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2_mq)]  
  
## <a name="selectmany"></a><span data-ttu-id="fd1ce-111">SelectMany</span><span class="sxs-lookup"><span data-stu-id="fd1ce-111">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="fd1ce-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="fd1ce-112">Example</span></span>  

 <span data-ttu-id="fd1ce-113">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.SelectMany%2A> pour sélectionner toutes les commandes où `TotalDue` est inférieur à 500,00.</span><span class="sxs-lookup"><span data-stu-id="fd1ce-113">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom_mq)]  
  
### <a name="example"></a><span data-ttu-id="fd1ce-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="fd1ce-114">Example</span></span>  

 <span data-ttu-id="fd1ce-115">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Enumerable.SelectMany%2A> pour sélectionner toutes les commandes qui ont été passées le 1er octobre 2002 ou après.</span><span class="sxs-lookup"><span data-stu-id="fd1ce-115">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="fd1ce-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd1ce-116">See also</span></span>

- [<span data-ttu-id="fd1ce-117">Requêtes dans LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="fd1ce-117">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)

---
title: 'Exemples de syntaxe de requête fondée sur une méthode : groupement'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb23c25c-1075-4cc3-a8ff-4db72e536c0d
ms.openlocfilehash: 2d84e755217878bfa248add37a752224a20d3f84
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191981"
---
# <a name="method-based-query-syntax-examples-grouping"></a><span data-ttu-id="34f6d-102">Exemples de syntaxe de requête fondée sur une méthode : groupement</span><span class="sxs-lookup"><span data-stu-id="34f6d-102">Method-Based Query Syntax Examples: Grouping</span></span>

<span data-ttu-id="34f6d-103">Les exemples de cette rubrique montrent comment utiliser la `GroupBy` méthode pour interroger le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) à l’aide de la syntaxe de requête fondée sur une méthode.</span><span class="sxs-lookup"><span data-stu-id="34f6d-103">The examples in this topic show you how to use the `GroupBy` method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="34f6d-104">Le modèle de vente AdventureWorks Sales Model utilisé dans ces exemples est construit à partir des tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="34f6d-104">The AdventureWorks Sales Model that is used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="34f6d-105">Les exemples de cette rubrique utilisent les `using` / `Imports` instructions suivantes :</span><span class="sxs-lookup"><span data-stu-id="34f6d-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="34f6d-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="34f6d-106">Example</span></span>  

 <span data-ttu-id="34f6d-107">L'exemple suivant utilise la méthode `GroupBy` pour retourner les objets `Address` qui sont regroupés par code postal.</span><span class="sxs-lookup"><span data-stu-id="34f6d-107">The following example uses the `GroupBy` method to return `Address` objects that are grouped by postal code.</span></span> <span data-ttu-id="34f6d-108">Les résultats sont projetés dans un type anonyme.</span><span class="sxs-lookup"><span data-stu-id="34f6d-108">The results are projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3_mq)]  
  
## <a name="example"></a><span data-ttu-id="34f6d-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="34f6d-109">Example</span></span>  

 <span data-ttu-id="34f6d-110">L'exemple suivant utilise la méthode `GroupBy` pour retourner les objets `Contact` qui sont regroupés en fonction de la première lettre du nom de famille des contacts.</span><span class="sxs-lookup"><span data-stu-id="34f6d-110">The following example uses the `GroupBy` method to return `Contact` objects that are grouped by the first letter of the contact's last name.</span></span> <span data-ttu-id="34f6d-111">Les résultats sont également triés selon la première lettre du nom de famille et projetés dans un type anonyme.</span><span class="sxs-lookup"><span data-stu-id="34f6d-111">The results are also sorted by the first letter of the last name and projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2_mq)]  
  
## <a name="example"></a><span data-ttu-id="34f6d-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="34f6d-112">Example</span></span>  

 <span data-ttu-id="34f6d-113">L'exemple suivant utilise la méthode `GroupBy` pour retourner les objets `SalesOrderHeader` qui sont regroupés par code client (Customer ID).</span><span class="sxs-lookup"><span data-stu-id="34f6d-113">The following example uses the `GroupBy` method to return `SalesOrderHeader` objects that are grouped by customer ID.</span></span> <span data-ttu-id="34f6d-114">Le nombre de ventes réalisées pour chaque client est également retourné.</span><span class="sxs-lookup"><span data-stu-id="34f6d-114">The number of sales for each customer is also returned.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount_mq)]
 [!code-vb[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="34f6d-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34f6d-115">See also</span></span>

- [<span data-ttu-id="34f6d-116">Requêtes dans LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="34f6d-116">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)

---
title: Trier les éléments d'une séquence
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d59b93a9-50c8-4770-a114-d902f6a0ea76
ms.openlocfilehash: b594e756b099aa94e1043fd4256da3eff46d0d95
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155755"
---
# <a name="sort-elements-in-a-sequence"></a><span data-ttu-id="16641-102">Trier les éléments d'une séquence</span><span class="sxs-lookup"><span data-stu-id="16641-102">Sort Elements in a Sequence</span></span>

<span data-ttu-id="16641-103">Utilisez l'opérateur <xref:System.Linq.Enumerable.OrderBy%2A> pour trier une séquence selon une ou plusieurs clés.</span><span class="sxs-lookup"><span data-stu-id="16641-103">Use the <xref:System.Linq.Enumerable.OrderBy%2A> operator to sort a sequence according to one or more keys.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="16641-104">est conçu pour prendre en charge le classement par types primitifs simples, tels que `string` , `int` , et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="16641-104">is designed to support ordering by simple primitive types, such as `string`, `int`, and so on.</span></span> <span data-ttu-id="16641-105">Il ne prend pas en charge le classement des classes complexes à valeurs multiples, telles que les types anonymes.</span><span class="sxs-lookup"><span data-stu-id="16641-105">It does not support ordering for complex multi-valued classes, such as anonymous types.</span></span> <span data-ttu-id="16641-106">Il ne prend pas non plus en charge de types de données `byte`.</span><span class="sxs-lookup"><span data-stu-id="16641-106">It also does not support `byte` datatypes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16641-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="16641-107">Example</span></span>  

 <span data-ttu-id="16641-108">L'exemple suivant trie `Employees` par date d'embauche.</span><span class="sxs-lookup"><span data-stu-id="16641-108">The following example sorts `Employees` by date of hire.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#20](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#20)]
 [!code-vb[DLinqQueryExamples#20](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#20)]  
  
## <a name="example"></a><span data-ttu-id="16641-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="16641-109">Example</span></span>  

 <span data-ttu-id="16641-110">L'exemple suivant utilise `where` pour trier des `Orders` expédiées à `London` par fret.</span><span class="sxs-lookup"><span data-stu-id="16641-110">The following example uses `where` to sort `Orders` shipped to `London` by freight.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#21](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#21)]
 [!code-vb[DLinqQueryExamples#21](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#21)]  
  
## <a name="example"></a><span data-ttu-id="16641-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="16641-111">Example</span></span>  

 <span data-ttu-id="16641-112">L'exemple suivant trie les `Products` par prix unitaire du plus élevé au plus bas.</span><span class="sxs-lookup"><span data-stu-id="16641-112">The following example sorts `Products` by unit price from highest to lowest.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#22](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#22)]
 [!code-vb[DLinqQueryExamples#22](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="16641-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="16641-113">Example</span></span>  

 <span data-ttu-id="16641-114">L'exemple suivant utilise un `OrderBy` composé pour trier les `Customers` par ville puis par nom de contact.</span><span class="sxs-lookup"><span data-stu-id="16641-114">The following example uses a compound `OrderBy` to sort `Customers` by city and then by contact name.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#24](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#24)]
 [!code-vb[DLinqQueryExamples#24](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="16641-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="16641-115">Example</span></span>  

 <span data-ttu-id="16641-116">L’exemple suivant trie les commandes de `EmployeeID 1` par, puis de `ShipCountry` fret le plus élevé au plus bas.</span><span class="sxs-lookup"><span data-stu-id="16641-116">The following example sorts Orders from `EmployeeID 1` by `ShipCountry`, and then by highest to lowest freight.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#25](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#25)]
 [!code-vb[DLinqQueryExamples#25](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="16641-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="16641-117">Example</span></span>  

 <span data-ttu-id="16641-118">L'exemple suivant combine les opérateurs <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Max%2A> et <xref:System.Linq.Enumerable.GroupBy%2A> pour rechercher le `Products` qui a le prix unitaire le plus élevé dans chaque catégorie, puis trie le groupe par ID de catégorie.</span><span class="sxs-lookup"><span data-stu-id="16641-118">The following example combines <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Max%2A>, and <xref:System.Linq.Enumerable.GroupBy%2A> operators to find the `Products` that have the highest unit price in each category, and then sorts the group by category id.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#26](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#26)]
 [!code-vb[DLinqQueryExamples#26](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#26)]  
  
 <span data-ttu-id="16641-119">Si vous exécutez la requête précédente sur l'exemple de base de données Northwind, les résultats se présenteront comme suit :</span><span class="sxs-lookup"><span data-stu-id="16641-119">If you run the previous query against the Northwind sample database, the results will resemble the following:</span></span>  
  
 `1`  
  
 `Côte de Blaye`  
  
 `2`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `4`  
  
 `Raclette Courdavault`  
  
 `5`  
  
 `Gnocchi di nonna Alice`  
  
 `6`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Carnarvon Tigers`  
  
## <a name="see-also"></a><span data-ttu-id="16641-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16641-120">See also</span></span>

- [<span data-ttu-id="16641-121">Exemples de requêtes</span><span class="sxs-lookup"><span data-stu-id="16641-121">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="16641-122">Téléchargement d’exemples de base de données</span><span class="sxs-lookup"><span data-stu-id="16641-122">Downloading Sample Databases</span></span>](downloading-sample-databases.md)

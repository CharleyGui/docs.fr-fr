---
title: Trier les éléments d'une séquence
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d59b93a9-50c8-4770-a114-d902f6a0ea76
ms.openlocfilehash: 21fa2f9e1dc2f255fe94f2420ba90a809ab5b05e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792663"
---
# <a name="sort-elements-in-a-sequence"></a><span data-ttu-id="7dee5-102">Trier les éléments d'une séquence</span><span class="sxs-lookup"><span data-stu-id="7dee5-102">Sort Elements in a Sequence</span></span>
<span data-ttu-id="7dee5-103">Utilisez l'opérateur <xref:System.Linq.Enumerable.OrderBy%2A> pour trier une séquence selon une ou plusieurs clés.</span><span class="sxs-lookup"><span data-stu-id="7dee5-103">Use the <xref:System.Linq.Enumerable.OrderBy%2A> operator to sort a sequence according to one or more keys.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="7dee5-104">est conçu pour prendre en charge le classement par types primitifs `string`simples `int`, tels que,, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="7dee5-104">is designed to support ordering by simple primitive types, such as `string`, `int`, and so on.</span></span> <span data-ttu-id="7dee5-105">Il ne prend pas en charge le classement des classes complexes à valeurs multiples, telles que les types anonymes.</span><span class="sxs-lookup"><span data-stu-id="7dee5-105">It does not support ordering for complex multi-valued classes, such as anonymous types.</span></span> <span data-ttu-id="7dee5-106">Il ne prend pas non plus en charge de types de données `byte`.</span><span class="sxs-lookup"><span data-stu-id="7dee5-106">It also does not support `byte` datatypes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7dee5-107">Exemples</span><span class="sxs-lookup"><span data-stu-id="7dee5-107">Example</span></span>  
 <span data-ttu-id="7dee5-108">L'exemple suivant trie `Employees` par date d'embauche.</span><span class="sxs-lookup"><span data-stu-id="7dee5-108">The following example sorts `Employees` by date of hire.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#20](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#20)]
 [!code-vb[DLinqQueryExamples#20](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#20)]  
  
## <a name="example"></a><span data-ttu-id="7dee5-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="7dee5-109">Example</span></span>  
 <span data-ttu-id="7dee5-110">L'exemple suivant utilise `where` pour trier des `Orders` expédiées à `London` par fret.</span><span class="sxs-lookup"><span data-stu-id="7dee5-110">The following example uses `where` to sort `Orders` shipped to `London` by freight.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#21](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#21)]
 [!code-vb[DLinqQueryExamples#21](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#21)]  
  
## <a name="example"></a><span data-ttu-id="7dee5-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="7dee5-111">Example</span></span>  
 <span data-ttu-id="7dee5-112">L'exemple suivant trie les `Products` par prix unitaire du plus élevé au plus bas.</span><span class="sxs-lookup"><span data-stu-id="7dee5-112">The following example sorts `Products` by unit price from highest to lowest.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#22](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#22)]
 [!code-vb[DLinqQueryExamples#22](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="7dee5-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="7dee5-113">Example</span></span>  
 <span data-ttu-id="7dee5-114">L'exemple suivant utilise un `OrderBy` composé pour trier les `Customers` par ville puis par nom de contact.</span><span class="sxs-lookup"><span data-stu-id="7dee5-114">The following example uses a compound `OrderBy` to sort `Customers` by city and then by contact name.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#24](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#24)]
 [!code-vb[DLinqQueryExamples#24](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="7dee5-115">Exemples</span><span class="sxs-lookup"><span data-stu-id="7dee5-115">Example</span></span>  
 <span data-ttu-id="7dee5-116">L’exemple suivant trie les commandes `EmployeeID 1` de `ShipCountry`par, puis de fret le plus élevé au plus bas.</span><span class="sxs-lookup"><span data-stu-id="7dee5-116">The following example sorts Orders from `EmployeeID 1` by `ShipCountry`, and then by highest to lowest freight.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#25](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#25)]
 [!code-vb[DLinqQueryExamples#25](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="7dee5-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="7dee5-117">Example</span></span>  
 <span data-ttu-id="7dee5-118">L'exemple suivant combine les opérateurs <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Max%2A> et <xref:System.Linq.Enumerable.GroupBy%2A> pour rechercher le `Products` qui a le prix unitaire le plus élevé dans chaque catégorie, puis trie le groupe par ID de catégorie.</span><span class="sxs-lookup"><span data-stu-id="7dee5-118">The following example combines <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Max%2A>, and <xref:System.Linq.Enumerable.GroupBy%2A> operators to find the `Products` that have the highest unit price in each category, and then sorts the group by category id.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#26](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#26)]
 [!code-vb[DLinqQueryExamples#26](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#26)]  
  
 <span data-ttu-id="7dee5-119">Si vous exécutez la requête précédente sur l'exemple de base de données Northwind, les résultats se présenteront comme suit :</span><span class="sxs-lookup"><span data-stu-id="7dee5-119">If you run the previous query against the Northwind sample database, the results will resemble the following:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7dee5-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7dee5-120">See also</span></span>

- [<span data-ttu-id="7dee5-121">Exemples de requêtes</span><span class="sxs-lookup"><span data-stu-id="7dee5-121">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="7dee5-122">Téléchargement d’exemples de base de données</span><span class="sxs-lookup"><span data-stu-id="7dee5-122">Downloading Sample Databases</span></span>](downloading-sample-databases.md)

---
title: 'Comment : formuler des jointures et des requêtes de produit croisé'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
ms.openlocfilehash: 002a644ff5d48b25351228dcd74330707491d6c8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782097"
---
# <a name="formulate-joins-and-cross-product-queries"></a><span data-ttu-id="18764-102">Comment : formuler des jointures et des requêtes de produit croisé</span><span class="sxs-lookup"><span data-stu-id="18764-102">Formulate Joins and Cross-Product Queries</span></span>
<span data-ttu-id="18764-103">Les exemples suivants expliquent comment combiner les résultats de plusieurs tables.</span><span class="sxs-lookup"><span data-stu-id="18764-103">The following examples show how to combine results from multiple tables.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18764-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="18764-104">Example</span></span>  
 <span data-ttu-id="18764-105">L’exemple suivant utilise la navigation de clé étrangère `From` dans la clause dans`from` Visual Basic ( C#clause dans) pour sélectionner toutes les commandes pour les clients de Londres.</span><span class="sxs-lookup"><span data-stu-id="18764-105">The following example uses foreign key navigation in the `From` clause in Visual Basic (`from` clause in C#) to select all orders for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## <a name="example"></a><span data-ttu-id="18764-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="18764-106">Example</span></span>  
 <span data-ttu-id="18764-107">L’exemple suivant utilise la navigation de clé étrangère `Where` dans la clause dans`where` Visual Basic ( C#clause dans) pour filtrer les ruptures de `Products` stock `Supplier` dont se trouve dans le États-Unis.</span><span class="sxs-lookup"><span data-stu-id="18764-107">The following example uses foreign key navigation in the `Where` clause in Visual Basic (`where` clause in C#) to filter for out-of-stock `Products` whose `Supplier` is in the United States.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## <a name="example"></a><span data-ttu-id="18764-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="18764-108">Example</span></span>  
 <span data-ttu-id="18764-109">L’exemple suivant utilise la navigation de clé étrangère `From` dans la clause dans`from` Visual Basic ( C#clause dans) pour filtrer les employés de Seattle et répertorier leurs territoires.</span><span class="sxs-lookup"><span data-stu-id="18764-109">The following example uses foreign key navigation in the `From` clause in Visual Basic (`from` clause in C#) to filter for employees in Seattle and to list their territories.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## <a name="example"></a><span data-ttu-id="18764-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="18764-110">Example</span></span>  
 <span data-ttu-id="18764-111">L’exemple suivant utilise la navigation de clé étrangère `Select` dans la clause dans`select` Visual Basic ( C#clause dans) pour filtrer les paires d’employés où un employé est reporté à l’autre et où les `City`deux employés sont de la même.</span><span class="sxs-lookup"><span data-stu-id="18764-111">The following example uses foreign key navigation in the `Select` clause in Visual Basic (`select` clause in C#) to filter for pairs of employees where one employee reports to the other and where both employees are from the same `City`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## <a name="example"></a><span data-ttu-id="18764-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="18764-112">Example</span></span>  
 <span data-ttu-id="18764-113">L’exemple de Visual Basic suivant recherche tous les clients et les commandes, vérifie que les commandes sont mises en correspondance avec les clients et garantit que pour chaque client de cette liste, un nom de contact est fourni.</span><span class="sxs-lookup"><span data-stu-id="18764-113">The following Visual Basic example looks for all customers and orders, makes sure that the orders are matched to customers, and guarantees that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## <a name="example"></a><span data-ttu-id="18764-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="18764-114">Example</span></span>  
 <span data-ttu-id="18764-115">L'exemple suivant joint explicitement deux tables et projette les résultats des deux tables.</span><span class="sxs-lookup"><span data-stu-id="18764-115">The following example explicitly joins two tables and projects results from both tables.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## <a name="example"></a><span data-ttu-id="18764-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="18764-116">Example</span></span>  
 <span data-ttu-id="18764-117">L'exemple suivant joint explicitement trois tables et projette les résultats de chacune d'elles.</span><span class="sxs-lookup"><span data-stu-id="18764-117">The following example explicitly joins three tables and projects results from each of them.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## <a name="example"></a><span data-ttu-id="18764-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="18764-118">Example</span></span>  
 <span data-ttu-id="18764-119">L'exemple suivant indique comment réaliser une `LEFT OUTER JOIN` en utilisant `DefaultIfEmpty()`.</span><span class="sxs-lookup"><span data-stu-id="18764-119">The following example shows how to achieve a `LEFT OUTER JOIN` by using `DefaultIfEmpty()`.</span></span> <span data-ttu-id="18764-120">La méthode `DefaultIfEmpty()` retourne null en l'absence de `Order` pour l'`Employee`.</span><span class="sxs-lookup"><span data-stu-id="18764-120">The `DefaultIfEmpty()` method returns null when there is no `Order` for the `Employee`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## <a name="example"></a><span data-ttu-id="18764-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="18764-121">Example</span></span>  
 <span data-ttu-id="18764-122">L'exemple suivant projette une expression `let` qui résulte d'une jointure.</span><span class="sxs-lookup"><span data-stu-id="18764-122">The following example projects a `let` expression resulting from a join.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## <a name="example"></a><span data-ttu-id="18764-123">Exemples</span><span class="sxs-lookup"><span data-stu-id="18764-123">Example</span></span>  
 <span data-ttu-id="18764-124">L'exemple suivant affiche une `join` avec une clé composite.</span><span class="sxs-lookup"><span data-stu-id="18764-124">The following example shows a `join` with a composite key.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## <a name="example"></a><span data-ttu-id="18764-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="18764-125">Example</span></span>  
 <span data-ttu-id="18764-126">L'exemple suivant indique comment construire une `join` où un côté est Nullable et l'autre ne l'est pas.</span><span class="sxs-lookup"><span data-stu-id="18764-126">The following example shows how to construct a `join` where one side is nullable and the other is not.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="18764-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18764-127">See also</span></span>

- [<span data-ttu-id="18764-128">Exemples de requêtes</span><span class="sxs-lookup"><span data-stu-id="18764-128">Query Examples</span></span>](query-examples.md)

---
title: Retourner le premier élément d'une séquence
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: 4506ef1a79c8f7e77160df4d55d0f93ee79f5a41
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200340"
---
# <a name="return-the-first-element-in-a-sequence"></a><span data-ttu-id="f533f-102">Retourner le premier élément d'une séquence</span><span class="sxs-lookup"><span data-stu-id="f533f-102">Return the First Element in a Sequence</span></span>

<span data-ttu-id="f533f-103">Utilisez l'opérateur <xref:System.Linq.Enumerable.First%2A> pour retourner le premier élément d'une séquence.</span><span class="sxs-lookup"><span data-stu-id="f533f-103">Use the <xref:System.Linq.Enumerable.First%2A> operator to return the first element in a sequence.</span></span> <span data-ttu-id="f533f-104">Les requêtes qui utilisent <xref:System.Linq.Enumerable.First%2A> sont exécutées immédiatement.</span><span class="sxs-lookup"><span data-stu-id="f533f-104">Queries that use <xref:System.Linq.Enumerable.First%2A> are executed immediately.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="f533f-105">ne prend pas en charge l'opérateur <xref:System.Linq.Enumerable.Last%2A>.</span><span class="sxs-lookup"><span data-stu-id="f533f-105">does not support the <xref:System.Linq.Enumerable.Last%2A> operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f533f-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="f533f-106">Example</span></span>  

 <span data-ttu-id="f533f-107">Le code suivant recherche le premier `Shipper` dans une table :</span><span class="sxs-lookup"><span data-stu-id="f533f-107">The following code finds the first `Shipper` in a table:</span></span>  
  
 <span data-ttu-id="f533f-108">Si vous exécutez cette requête sur l'exemple de base de données Northwind, vous obtenez le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="f533f-108">If you run this query against the Northwind sample database, the results are</span></span>  
  
 <span data-ttu-id="f533f-109">`ID = 1, Company = Speedy Express`.</span><span class="sxs-lookup"><span data-stu-id="f533f-109">`ID = 1, Company = Speedy Express`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="f533f-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="f533f-110">Example</span></span>  

 <span data-ttu-id="f533f-111">Le code suivant recherche le seul `Customer` qui a BONAP comme `CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="f533f-111">The following code finds the single `Customer` that has the `CustomerID` BONAP.</span></span>  
  
 <span data-ttu-id="f533f-112">Si vous exécutez cette requête sur l'exemple de base de données Northwind, vous obtenez `ID = BONAP, Contact = Laurence Lebihan`.</span><span class="sxs-lookup"><span data-stu-id="f533f-112">If you run this query against the Northwind sample database, the results are `ID = BONAP, Contact = Laurence Lebihan`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="f533f-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f533f-113">See also</span></span>

- [<span data-ttu-id="f533f-114">Exemples de requêtes</span><span class="sxs-lookup"><span data-stu-id="f533f-114">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="f533f-115">Téléchargement d’exemples de base de données</span><span class="sxs-lookup"><span data-stu-id="f533f-115">Downloading Sample Databases</span></span>](downloading-sample-databases.md)

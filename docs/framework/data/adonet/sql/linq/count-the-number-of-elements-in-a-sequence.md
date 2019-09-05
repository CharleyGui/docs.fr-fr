---
title: Dénombrer les éléments d'une séquence
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
ms.openlocfilehash: 74e24aeb64b0097cba3975e76475034e6bb9544d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247703"
---
# <a name="count-the-number-of-elements-in-a-sequence"></a><span data-ttu-id="4110b-102">Dénombrer les éléments d'une séquence</span><span class="sxs-lookup"><span data-stu-id="4110b-102">Count the Number of Elements in a Sequence</span></span>
<span data-ttu-id="4110b-103">Utilisez l'opérateur <xref:System.Linq.Enumerable.Count%2A> pour compter le nombre d'éléments dans une séquence.</span><span class="sxs-lookup"><span data-stu-id="4110b-103">Use the <xref:System.Linq.Enumerable.Count%2A> operator to count the number of elements in a sequence.</span></span>  
  
 <span data-ttu-id="4110b-104">L'exécution de cette requête sur la base de données Northwind génère le résultat suivant : `91`.</span><span class="sxs-lookup"><span data-stu-id="4110b-104">Running this query against the Northwind sample database produces an output of `91`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4110b-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="4110b-105">Example</span></span>  
 <span data-ttu-id="4110b-106">L'exemple suivant compte le nombre de `Customers` dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="4110b-106">The following example counts the number of `Customers` in the database.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="4110b-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="4110b-107">Example</span></span>  
 <span data-ttu-id="4110b-108">L'exemple suivant compte le nombre de produits dans la base de données qui n'ont pas été arrêtés.</span><span class="sxs-lookup"><span data-stu-id="4110b-108">The following example counts the number of products in the database that have not been discontinued.</span></span>  
  
 <span data-ttu-id="4110b-109">L'exécution de cet exemple sur la base de données Northwind génère le résultat suivant : `69`.</span><span class="sxs-lookup"><span data-stu-id="4110b-109">Running this example against the Northwind sample database produces an output of `69`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="4110b-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4110b-110">See also</span></span>

- [<span data-ttu-id="4110b-111">Requêtes d’agrégation</span><span class="sxs-lookup"><span data-stu-id="4110b-111">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="4110b-112">Téléchargement d’exemples de base de données</span><span class="sxs-lookup"><span data-stu-id="4110b-112">Downloading Sample Databases</span></span>](downloading-sample-databases.md)

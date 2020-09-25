---
title: 'Procédure : Récupérer plusieurs objets à la fois'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 18aff4d8-bde8-461b-9960-ccabb24e9d22
ms.openlocfilehash: 98827989f72b7922a325a9e13b5f46cb18ac5395
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197311"
---
# <a name="how-to-retrieve-many-objects-at-once"></a><span data-ttu-id="e5c2e-102">Procédure : Récupérer plusieurs objets à la fois</span><span class="sxs-lookup"><span data-stu-id="e5c2e-102">How to: Retrieve Many Objects At Once</span></span>

<span data-ttu-id="e5c2e-103">Vous pouvez récupérer plusieurs objets dans une requête en utilisant <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span><span class="sxs-lookup"><span data-stu-id="e5c2e-103">You can retrieve many objects in one query by using <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5c2e-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="e5c2e-104">Example</span></span>  

 <span data-ttu-id="e5c2e-105">Le code suivant utilise la méthode <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> pour récupérer des objets `Customer` et `Order`.</span><span class="sxs-lookup"><span data-stu-id="e5c2e-105">The following code uses the <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method to retrieve both `Customer` and `Order` objects.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#9)]
 [!code-vb[DLinqQueryConcepts#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="e5c2e-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5c2e-106">See also</span></span>

- [<span data-ttu-id="e5c2e-107">Concepts relatifs aux requêtes</span><span class="sxs-lookup"><span data-stu-id="e5c2e-107">Query Concepts</span></span>](query-concepts.md)

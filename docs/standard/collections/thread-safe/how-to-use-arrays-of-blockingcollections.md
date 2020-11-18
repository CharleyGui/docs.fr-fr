---
title: 'Procédure : utiliser des tableaux de collections de blocage dans un pipeline'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking collections in pipeline
ms.assetid: a39c7ec3-3ad7-4f4d-8fe4-b3e9dbabe2ed
ms.openlocfilehash: a79cd13af19a8f67fd5a96ce80dc899ca6f07516
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824998"
---
# <a name="how-to-use-arrays-of-blocking-collections-in-a-pipeline"></a><span data-ttu-id="80987-102">Procédure : utiliser des tableaux de collections de blocage dans un pipeline</span><span class="sxs-lookup"><span data-stu-id="80987-102">How to: Use Arrays of Blocking Collections in a Pipeline</span></span>
<span data-ttu-id="80987-103">L’exemple suivant montre comment utiliser des tableaux d’objets <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> avec des méthodes statiques telles que <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> et <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> pour implémenter le transfert de données rapide et flexible entre des composants.</span><span class="sxs-lookup"><span data-stu-id="80987-103">The following example shows how to use arrays of <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> objects with static methods such as <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> to implement fast and flexible data transfer between components.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80987-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="80987-104">Example</span></span>  
 <span data-ttu-id="80987-105">L’exemple suivant montre une implémentation de pipeline de base dans laquelle chaque objet prend simultanément des données dans la collection d’entrée, les transforme et les passe à la collection de sortie.</span><span class="sxs-lookup"><span data-stu-id="80987-105">The following example demonstrates a basic pipeline implementation in which each object is concurrently taking data from the input collection, transforming it, and passing it to the output collection.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)]
 [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]  
  
## <a name="see-also"></a><span data-ttu-id="80987-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="80987-106">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="80987-107">Collections thread-safe</span><span class="sxs-lookup"><span data-stu-id="80987-107">Thread-Safe Collections</span></span>](index.md)

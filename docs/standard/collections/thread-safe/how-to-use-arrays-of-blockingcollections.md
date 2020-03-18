---
title: 'Comment : utiliser des tableaux de collections de blocage dans un pipeline'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking collections in pipeline
ms.assetid: a39c7ec3-3ad7-4f4d-8fe4-b3e9dbabe2ed
ms.openlocfilehash: 397c438bacd1cfed1613efef61e9d7266d55ea47
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711257"
---
# <a name="how-to-use-arrays-of-blocking-collections-in-a-pipeline"></a><span data-ttu-id="aaf91-102">Comment : utiliser des tableaux de collections de blocage dans un pipeline</span><span class="sxs-lookup"><span data-stu-id="aaf91-102">How to: Use Arrays of Blocking Collections in a Pipeline</span></span>
<span data-ttu-id="aaf91-103">L’exemple suivant montre comment utiliser des tableaux d’objets <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> avec des méthodes statiques telles que <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> et <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> pour implémenter le transfert de données rapide et flexible entre des composants.</span><span class="sxs-lookup"><span data-stu-id="aaf91-103">The following example shows how to use arrays of <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> objects with static methods such as <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> to implement fast and flexible data transfer between components.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aaf91-104"> Exemple</span><span class="sxs-lookup"><span data-stu-id="aaf91-104">Example</span></span>  
 <span data-ttu-id="aaf91-105">L’exemple suivant montre une implémentation de pipeline de base dans laquelle chaque objet prend simultanément des données dans la collection d’entrée, les transforme et les passe à la collection de sortie.</span><span class="sxs-lookup"><span data-stu-id="aaf91-105">The following example demonstrates a basic pipeline implementation in which each object is concurrently taking data from the input collection, transforming it, and passing it to the output collection.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)]
 [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]  
  
## <a name="see-also"></a><span data-ttu-id="aaf91-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aaf91-106">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="aaf91-107">Thread-Safe Collections</span><span class="sxs-lookup"><span data-stu-id="aaf91-107">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)

---
title: "Guide pratique : créer un pool d'objets à l'aide d'un ConcurrentBag"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object pool, in .NET Framework
ms.assetid: 0480e7ff-b6f9-480e-a889-2ed4264d8372
ms.openlocfilehash: 888521eb5c3c3169c4b39a26e82fef2e35c286d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711270"
---
# <a name="how-to-create-an-object-pool-by-using-a-concurrentbag"></a><span data-ttu-id="f6546-102">Guide pratique : créer un pool d'objets à l'aide d'un ConcurrentBag</span><span class="sxs-lookup"><span data-stu-id="f6546-102">How to: Create an Object Pool by Using a ConcurrentBag</span></span>
<span data-ttu-id="f6546-103">L’exemple suivant montre comment utiliser un conteneur simultané pour implémenter un pool d’objets.</span><span class="sxs-lookup"><span data-stu-id="f6546-103">This example shows how to use a concurrent bag to implement an object pool.</span></span> <span data-ttu-id="f6546-104">Les pools d’objet peuvent améliorer les performances de l’application dans les cas où vous avez besoin de plusieurs instances d’une classe et que la création ou la destruction de la classe est coûteuse.</span><span class="sxs-lookup"><span data-stu-id="f6546-104">Object pools can improve application performance in situations where you require multiple instances of a class and the class is expensive to create or destroy.</span></span> <span data-ttu-id="f6546-105">Quand un programme client demande un nouvel objet, le pool d’objets tente d’abord d’en fournir un qui a été créé et retourné au pool.</span><span class="sxs-lookup"><span data-stu-id="f6546-105">When a client program requests a new object, the object pool first attempts to provide one that has already been created and returned to the pool.</span></span> <span data-ttu-id="f6546-106">Si aucun n’est disponible, et uniquement dans ce cas, un nouvel objet est créé.</span><span class="sxs-lookup"><span data-stu-id="f6546-106">If none is available, only then is a new object created.</span></span>  
  
 <span data-ttu-id="f6546-107"><xref:System.Collections.Concurrent.ConcurrentBag%601> est utilisé pour stocker les objets, car il prend en charge l’insertion et la suppression rapides, en particulier quand le même thread ajoute et supprime des éléments.</span><span class="sxs-lookup"><span data-stu-id="f6546-107"><xref:System.Collections.Concurrent.ConcurrentBag%601> is used to store the objects because it supports fast insertion and removal, especially when the same thread is both adding and removing items.</span></span> <span data-ttu-id="f6546-108">Cet exemple peut être augmenté davantage pour être généré autour d’un <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, que la structure de données de conteneur implémente, comme le font <xref:System.Collections.Concurrent.ConcurrentQueue%601> et <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span><span class="sxs-lookup"><span data-stu-id="f6546-108">This example could be further augmented to be built around a <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, which the bag data structure implements, as do <xref:System.Collections.Concurrent.ConcurrentQueue%601> and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6546-109"> Exemple</span><span class="sxs-lookup"><span data-stu-id="f6546-109">Example</span></span>  
 [!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
 [!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="f6546-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6546-110">See also</span></span>

- [<span data-ttu-id="f6546-111">Thread-Safe Collections</span><span class="sxs-lookup"><span data-stu-id="f6546-111">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)

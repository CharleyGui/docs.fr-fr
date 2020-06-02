---
title: Créer un pool d’objets à l’aide d’un ConcurrentBag
ms.date: 05/01/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object pool, in .NET Framework
ms.assetid: 0480e7ff-b6f9-480e-a889-2ed4264d8372
ms.openlocfilehash: 64d91162b27eba80fba63761d0a926e441b63440
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287859"
---
# <a name="create-an-object-pool-by-using-a-concurrentbag"></a><span data-ttu-id="5a5e6-102">Créer un pool d’objets à l’aide d’un ConcurrentBag</span><span class="sxs-lookup"><span data-stu-id="5a5e6-102">Create an object pool by using a ConcurrentBag</span></span>

<span data-ttu-id="5a5e6-103">Cet exemple montre comment utiliser un <xref:System.Collections.Concurrent.ConcurrentBag%601> pour implémenter un pool d’objets.</span><span class="sxs-lookup"><span data-stu-id="5a5e6-103">This example shows how to use a <xref:System.Collections.Concurrent.ConcurrentBag%601> to implement an object pool.</span></span> <span data-ttu-id="5a5e6-104">Les pools d’objet peuvent améliorer les performances de l’application dans les cas où vous avez besoin de plusieurs instances d’une classe et que la création ou la destruction de la classe est coûteuse.</span><span class="sxs-lookup"><span data-stu-id="5a5e6-104">Object pools can improve application performance in situations where you require multiple instances of a class and the class is expensive to create or destroy.</span></span> <span data-ttu-id="5a5e6-105">Quand un programme client demande un nouvel objet, le pool d’objets tente d’abord d’en fournir un qui a été créé et retourné au pool.</span><span class="sxs-lookup"><span data-stu-id="5a5e6-105">When a client program requests a new object, the object pool first attempts to provide one that has already been created and returned to the pool.</span></span> <span data-ttu-id="5a5e6-106">Si aucun n’est disponible, et uniquement dans ce cas, un nouvel objet est créé.</span><span class="sxs-lookup"><span data-stu-id="5a5e6-106">If none is available, only then is a new object created.</span></span>

<span data-ttu-id="5a5e6-107">Le <xref:System.Collections.Concurrent.ConcurrentBag%601> est utilisé pour stocker les objets, car il prend en charge l’insertion et la suppression rapides, en particulier lorsque le même thread ajoute et supprime des éléments.</span><span class="sxs-lookup"><span data-stu-id="5a5e6-107">The <xref:System.Collections.Concurrent.ConcurrentBag%601> is used to store the objects because it supports fast insertion and removal, especially when the same thread is both adding and removing items.</span></span> <span data-ttu-id="5a5e6-108">Cet exemple peut être augmenté davantage pour être généré autour d’un <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, que la structure de données de conteneur implémente, comme le font <xref:System.Collections.Concurrent.ConcurrentQueue%601> et <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span><span class="sxs-lookup"><span data-stu-id="5a5e6-108">This example could be further augmented to be built around a <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, which the bag data structure implements, as do <xref:System.Collections.Concurrent.ConcurrentQueue%601> and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>

> [!TIP]
> <span data-ttu-id="5a5e6-109">Cet article définit comment écrire votre propre implémentation d’un pool d’objets avec un type simultané sous-jacent pour stocker des objets en vue de les réutiliser.</span><span class="sxs-lookup"><span data-stu-id="5a5e6-109">This article defines how to write your own implementation of an object pool with an underlying concurrent type to store objects for reuse.</span></span> <span data-ttu-id="5a5e6-110">Toutefois, le <xref:Microsoft.Extensions.ObjectPool.ObjectPool%601?displayProperty=nameWithType> type existe déjà sous l' <xref:Microsoft.Extensions.ObjectPool?displayProperty=fullName> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="5a5e6-110">However, the <xref:Microsoft.Extensions.ObjectPool.ObjectPool%601?displayProperty=nameWithType> type already exists under the <xref:Microsoft.Extensions.ObjectPool?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="5a5e6-111">Envisagez d’utiliser le type disponible avant de créer votre propre implémentation, qui comprend de nombreuses fonctionnalités supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="5a5e6-111">Consider using the available type before creating your own implementation, which includes many additional features.</span></span>

## <a name="example"></a><span data-ttu-id="5a5e6-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="5a5e6-112">Example</span></span>

[!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
[!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]

## <a name="see-also"></a><span data-ttu-id="5a5e6-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a5e6-113">See also</span></span>

- [<span data-ttu-id="5a5e6-114">Collections thread-safe</span><span class="sxs-lookup"><span data-stu-id="5a5e6-114">Thread-Safe Collections</span></span>](index.md)

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
# <a name="create-an-object-pool-by-using-a-concurrentbag"></a>Créer un pool d’objets à l’aide d’un ConcurrentBag

Cet exemple montre comment utiliser un <xref:System.Collections.Concurrent.ConcurrentBag%601> pour implémenter un pool d’objets. Les pools d’objet peuvent améliorer les performances de l’application dans les cas où vous avez besoin de plusieurs instances d’une classe et que la création ou la destruction de la classe est coûteuse. Quand un programme client demande un nouvel objet, le pool d’objets tente d’abord d’en fournir un qui a été créé et retourné au pool. Si aucun n’est disponible, et uniquement dans ce cas, un nouvel objet est créé.

Le <xref:System.Collections.Concurrent.ConcurrentBag%601> est utilisé pour stocker les objets, car il prend en charge l’insertion et la suppression rapides, en particulier lorsque le même thread ajoute et supprime des éléments. Cet exemple peut être augmenté davantage pour être généré autour d’un <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>, que la structure de données de conteneur implémente, comme le font <xref:System.Collections.Concurrent.ConcurrentQueue%601> et <xref:System.Collections.Concurrent.ConcurrentStack%601>.

> [!TIP]
> Cet article définit comment écrire votre propre implémentation d’un pool d’objets avec un type simultané sous-jacent pour stocker des objets en vue de les réutiliser. Toutefois, le <xref:Microsoft.Extensions.ObjectPool.ObjectPool%601?displayProperty=nameWithType> type existe déjà sous l' <xref:Microsoft.Extensions.ObjectPool?displayProperty=fullName> espace de noms. Envisagez d’utiliser le type disponible avant de créer votre propre implémentation, qui comprend de nombreuses fonctionnalités supplémentaires.

## <a name="example"></a>Exemple

[!code-csharp[CDS#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/objectpool.cs#04)]
[!code-vb[CDS#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/objectpool04.vb#04)]

## <a name="see-also"></a>Voir aussi

- [Collections thread-safe](index.md)

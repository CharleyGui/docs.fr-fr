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
# <a name="how-to-use-arrays-of-blocking-collections-in-a-pipeline"></a>Procédure : utiliser des tableaux de collections de blocage dans un pipeline
L’exemple suivant montre comment utiliser des tableaux d’objets <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> avec des méthodes statiques telles que <xref:System.Collections.Concurrent.BlockingCollection%601.TryAddToAny%2A> et <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%2A> pour implémenter le transfert de données rapide et flexible entre des composants.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une implémentation de pipeline de base dans laquelle chaque objet prend simultanément des données dans la collection d’entrée, les transforme et les passe à la collection de sortie.  
  
 [!code-csharp[CDS_BlockingCollection#07](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example07.cs#07)]
 [!code-vb[CDS_BlockingCollection#07](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/bcpipeline.vb#07)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Collections thread-safe](index.md)

---
title: 'Comment : convertir une séquence en liste générique'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab76d93-6898-4e75-b76f-290a66ecead8
ms.openlocfilehash: 43960d100cde7f746a56c023d305795e13bc04e7
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247866"
---
# <a name="convert-a-sequence-to-a-generic-list"></a>Comment : convertir une séquence en liste générique
Utilisez <xref:System.Linq.Enumerable.ToList%2A> pour créer une liste générique à partir d'une séquence.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise <xref:System.Linq.Enumerable.ToList%2A> pour évaluer immédiatement une requête dans un <xref:System.Collections.Generic.List%601>générique.  
  
 [!code-csharp[DLinqQueryExamples#45](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#45)]
 [!code-vb[DLinqQueryExamples#45](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#45)]  
  
## <a name="see-also"></a>Voir aussi

- [Exemples de requêtes](query-examples.md)

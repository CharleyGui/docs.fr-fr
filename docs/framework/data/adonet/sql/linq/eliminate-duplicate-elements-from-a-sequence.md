---
title: "Comment : éliminer des éléments en double d'une séquence"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b224a84-bad5-4843-adcc-14e784d280f5
ms.openlocfilehash: 0dca1a635fd1cc6e48e8ad914909769b2cf0e66d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161371"
---
# <a name="eliminate-duplicate-elements-from-a-sequence"></a>Comment : éliminer des éléments en double d'une séquence

Utilisez l'opérateur <xref:System.Linq.Queryable.Distinct%2A> pour éliminer des éléments en double d'une séquence.  
  
## <a name="example"></a>Exemple  

 L'exemple suivant utilise <xref:System.Linq.Queryable.Distinct%2A> pour sélectionner une séquence des villes uniques qui comportent des clients.  
  
 [!code-csharp[DLinqQueryExamples#36](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#36)]
 [!code-vb[DLinqQueryExamples#36](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#36)]  
  
## <a name="see-also"></a>Voir aussi

- [Exemples de requêtes](query-examples.md)

---
title: 'Procédure : Désactiver le chargement différé'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: b2193e7e8bda396451274d2da96e7cb86774fd03
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91196960"
---
# <a name="how-to-turn-off-deferred-loading"></a>Procédure : Désactiver le chargement différé

Vous pouvez désactiver le chargement différé en affectant la valeur <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> à `false`. Pour plus d’informations, consultez [différé et chargement immédiat](deferred-versus-immediate-loading.md).  
  
> [!NOTE]
> Le chargement différé est désactivé lorsque le suivi d'objet est désactivé. Pour plus d’informations, consultez [Comment : récupérer des informations en lecture seule](how-to-retrieve-information-as-read-only.md).  
  
## <a name="example"></a>Exemple  

 L'exemple suivant montre comment désactiver le chargement différé en affectant la valeur <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> à `false`.  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Voir aussi

- [Concepts relatifs aux requêtes](query-concepts.md)
- [Interrogation de la base de données](querying-the-database.md)

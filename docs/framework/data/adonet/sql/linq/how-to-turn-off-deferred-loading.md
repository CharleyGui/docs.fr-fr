---
title: 'Procédure : Désactiver le chargement différé'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: 6559392527bb02afe9cea61e704f1f371c6d5470
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781655"
---
# <a name="how-to-turn-off-deferred-loading"></a>Procédure : Désactiver le chargement différé
Vous pouvez désactiver le chargement différé en affectant la valeur <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> à `false`. Pour plus d’informations, consultez [différé et chargement immédiat](deferred-versus-immediate-loading.md).  
  
> [!NOTE]
> Le chargement différé est désactivé lorsque le suivi d'objet est désactivé. Pour plus d’informations, consultez [Guide pratique pour Récupérez les informations en lecture](how-to-retrieve-information-as-read-only.md)seule.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment désactiver le chargement différé en affectant la valeur <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> à `false`.  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Voir aussi

- [Concepts relatifs aux requêtes](query-concepts.md)
- [Interrogation de la base de données](querying-the-database.md)

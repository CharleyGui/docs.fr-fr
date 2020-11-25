---
title: 'Procédure : Dissocier des blocs de flux de données'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow blocks, unlinking in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, unlinking dataflow blocks
ms.assetid: 40f0208d-4618-47f7-85cf-4913d07d2d7d
ms.openlocfilehash: e981d1b9b3adc638a84de1c119ad849ec533d16e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722370"
---
# <a name="how-to-unlink-dataflow-blocks"></a>Procédure : Dissocier des blocs de flux de données

Ce document explique comment dissocier un bloc de flux de données cible de sa source.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Exemple  

 L’exemple suivant crée trois objets <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, dont chacun appelle la méthode `TrySolution` pour calculer une valeur. Cet exemple n’a besoin que du résultat du premier appel à `TrySolution` pour se terminer.  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 Pour recevoir la valeur du premier objet <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> qui se termine, cet exemple définit la méthode `ReceiveFromAny(T)`. La méthode `ReceiveFromAny(T)` accepte un tableau d’objets <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> et lie chacun de ces objets à un objet <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>. Si vous utilisez la méthode <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> pour lier un bloc source de flux de données à un bloc cible, le premier propage les messages auprès du second au fil de l’arrivée des données. Étant donné que la classe <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> accepte uniquement le premier message proposé, la méthode `ReceiveFromAny(T)` produit ses résultats en appelant la méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A>. Cela génère le premier message proposé à l’objet <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>. La méthode <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> a une version surchargée acceptant un objet <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> avec une propriété <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.MaxMessages> qui, définie à la valeur `1`, impose au bloc source de se dissocier du bloc cible dès que ce dernier a reçu un message provenant du bloc source. Il est important que l’objet <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> se dissocie de ses sources, car la relation qu’il entretient avec le tableau de sources n’est plus nécessaire dès lors qu’il a reçu un message<xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601><xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>.  
  
 Pour permettre aux appels restants à `TrySolution` de se terminer dès que l’un d’eux a calculé une valeur, la méthode `TrySolution` prend un objet <xref:System.Threading.CancellationToken> qui est annulé après que l’appel à `ReceiveFromAny(T)` a produit une sortie. La méthode <xref:System.Threading.SpinWait.SpinUntil%2A> produit une sortie quand cet objet <xref:System.Threading.CancellationToken> est annulé.  
  
## <a name="see-also"></a>Voir aussi

- [Dataflow](dataflow-task-parallel-library.md)

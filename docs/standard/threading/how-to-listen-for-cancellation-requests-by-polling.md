---
title: 'Procédure : écouter les requêtes d’annulation par interrogation'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, how to poll for requests
ms.assetid: c7f2f022-d08e-4e00-b4eb-ae84844cb1bc
ms.openlocfilehash: a527fb7f0f9e3c78b3161fdfed0f1d9f3d52798b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723725"
---
# <a name="how-to-listen-for-cancellation-requests-by-polling"></a>Procédure : écouter les requêtes d’annulation par interrogation

L’exemple suivant montre une manière dont un code utilisateur peut interroger un jeton d’annulation à intervalles réguliers pour voir si une annulation a été demandée à partir du thread appelant. Cet exemple utilise le type <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, mais le même modèle s’applique aux opérations asynchrones créées directement par le type <xref:System.Threading.ThreadPool?displayProperty=nameWithType> ou par le type <xref:System.Threading.Thread?displayProperty=nameWithType>.  
  
## <a name="example"></a>Exemple  

 L’interrogation requiert une boucle ou un code récursif qui peut lire régulièrement la valeur de la propriété booléenne <xref:System.Threading.CancellationToken.IsCancellationRequested%2A>. Si vous utilisez le type <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> et que vous attendez que la tâche se termine sur le thread appelant, vous pouvez utiliser la méthode <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> pour vérifier la propriété et lever l’exception. En utilisant cette méthode, vous garantissez que la bonne exception est levée en réponse à une requête. Si vous utilisez un <xref:System.Threading.Tasks.Task>, il vaudra alors mieux appeler cette méthode plutôt que de lever manuellement un <xref:System.OperationCanceledException>. Si vous ne devez pas lever l’exception, vous pouvez simplement vérifier la propriété et le retour de la méthode si la propriété est `true`.  
  
 [!code-csharp[Cancellation#11](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#11)]
 [!code-vb[Cancellation#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#11)]  
  
 L’appel de <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> est extrêmement rapide et n’introduit pas de surcharge importante dans les boucles.  
  
 Si vous appelez <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, vous avez uniquement à vérifier explicitement la propriété <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> si, en plus de lever l’exception, vous avez un autre travail à faire en réponse à l’annulation. Dans cet exemple, vous pouvez voir qu’en fait, le code accède deux fois à la propriété : une fois dans l’accès explicite et une autre fois dans la méthode <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>. Cependant, étant donné que l’opération de lecture de la propriété <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> implique une seule instruction de lecture volatile par accès, le double accès n’est pas significatif du point de vue des performances. Il est toujours préférable d’appeler la méthode plutôt que de lever manuellement le <xref:System.OperationCanceledException>.  
  
## <a name="see-also"></a>Voir aussi

- [Annulation dans les threads managés](cancellation-in-managed-threads.md)

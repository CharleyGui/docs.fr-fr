---
title: Annulation de tâches
description: Comprendre l’annulation de tâches, qui est prise en charge dans les classes Task et Task <TResult> à l’aide de jetons d’annulation dans .net.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, cancellation
- asynchronous task cancellation
ms.assetid: 3ecf1ea9-e399-4a6a-a0d6-8475f48dcb28
ms.openlocfilehash: 1d9b7b35341961c27107f007e0eafa51ef49e232
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768662"
---
# <a name="task-cancellation"></a>Annulation de tâches
Les classes <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> prennent en charge l'annulation via l'utilisation de jetons d'annulation dans .NET Framework. Pour plus d’informations, consultez [annulation dans les threads managés](../threading/cancellation-in-managed-threads.md). Dans les classes de tâche, l'annulation implique une coopération entre le délégué d'utilisateur, qui représente une opération annulable et le code qui a demandé l'annulation.  Une annulation réussie implique la demande du code appelant la méthode <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType>, et le délégué d'utilisateur terminant l'opération dans le délai imparti. Vous pouvez terminer l'opération à l'aide de l'une des options suivantes :  
  
- Par un retour du délégué. Cela suffit dans la plupart des scénarios ; toutefois, une instance de tâche annulée de cette façon passe à l'état <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType> , et non à l'état <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> .  
  
- En levant une <xref:System.OperationCanceledException> et en lui passant le jeton sur lequel l'annulation a été demandée. La meilleure façon de faire cela est d'utiliser la méthode <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> . Une tâche annulée de cette façon passe à l'état Canceled, ce que le code appelant peut utiliser pour vérifier que la tâche a répondu à sa requête d'annulation.  
  
 L'exemple suivant montre le modèle de base d'annulation de tâche qui lève l'exception. Notez que le jeton est passé au délégué utilisateur et à l'instance de tâche.  
  
 [!code-csharp[TPL_Cancellation#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/snippet02.cs#02)]
 [!code-vb[TPL_Cancellation#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/module1.vb#02)]  
  
 Pour obtenir un exemple plus complet, consultez [Comment : annuler une tâche et ses enfants](how-to-cancel-a-task-and-its-children.md).  
  
 Lorsqu'une instance de tâche observe une <xref:System.OperationCanceledException> levée par le code utilisateur, elle compare le jeton de l'exception à son jeton associé (celui passé à l'API ayant créé la tâche). S'ils sont identiques et si la propriété <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> du jeton retourne la valeur true, la tâche l'interprète comme une acceptation d'annulation et passe à l'état Canceled. Si vous n'utilisez pas une méthode <xref:System.Threading.Tasks.Task.Wait%2A> ou <xref:System.Threading.Tasks.Task.WaitAll%2A> pour attendre la tâche, la tâche définit uniquement son état sur <xref:System.Threading.Tasks.TaskStatus.Canceled>.  
  
 Si vous attendez une tâche qui passe à l’état Canceled, une exception <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> (enveloppée dans une exception <xref:System.AggregateException> ) est levée. Notez que cette exception indique une annulation réussie et non une défaillance. Ainsi, la propriété <xref:System.Threading.Tasks.Task.Exception%2A> de la tâche retourne `null`.  
  
 Si la propriété <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> du jeton retourne la valeur false ou si le jeton de l'exception ne correspond pas au jeton de la tâche, <xref:System.OperationCanceledException> est traitée comme une exception normale, entraînant ainsi le passage de la tâche à l'état Faulted. Notez également que la présence d'autres exceptions entraînera le passage de la tâche à l'état Faulted. Vous pouvez obtenir l'état de la tâche terminée dans la propriété <xref:System.Threading.Tasks.Task.Status%2A> .  
  
 Il est possible qu'une tâche puisse continuer à traiter certains éléments après la demande d'annulation.  
  
## <a name="see-also"></a>Voir aussi

- [Annulation dans les threads managés](../threading/cancellation-in-managed-threads.md)
- [Procédure : annuler une tâche et ses enfants](how-to-cancel-a-task-and-its-children.md)

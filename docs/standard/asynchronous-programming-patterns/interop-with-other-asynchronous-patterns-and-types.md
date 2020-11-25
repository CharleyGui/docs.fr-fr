---
title: Interopérabilité avec d’autres types et modèles asynchrones
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous design patterns, .NET
- TAP, .NET support for
- Task-based Asynchronous Pattern, .NET support for
- .NET, asynchronous design patterns
ms.assetid: f120a5d9-933b-4d1d-acb6-f034a57c3749
ms.openlocfilehash: 2ae1c514185152dd709fe06018df513fb54b874b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726715"
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a>Interopérabilité avec d’autres types et modèles asynchrones

Bref historique des modèles asynchrones dans .NET :

- .NET Framework 1,0 a introduit le <xref:System.IAsyncResult> modèle, également connu sous le nom de [modèle de programmation asynchrone (APM)](asynchronous-programming-model-apm.md), ou le modèle `Begin/End` .
- .NET Framework 2,0 a ajouté le [modèle asynchrone basé sur les événements (EAP)](event-based-asynchronous-pattern-eap.md).
- .NET Framework 4 a introduit le [modèle asynchrone basé sur des tâches (TAP)](task-based-asynchronous-pattern-tap.md), qui remplace à la fois APM et EAP et fournit la possibilité de créer facilement des routines de migration à partir des modèles précédents.
  
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a>Tâches et APM

### <a name="from-apm-to-tap"></a>APM vers modèle asynchrone basé sur les tâches (TAP, Task-based Asynchronous Pattern)  

 Étant donné que le modèle [APM (Asynchronous Programming Model)](asynchronous-programming-model-apm.md) est structuré, il est assez facile de créer un wrapper pour exposer une implémentation APM en tant qu’implémentation TAP. .NET Framework 4 et versions ultérieures incluent des routines d’assistance sous la forme de <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> surcharges de méthode pour fournir cette traduction.  
  
 Imaginez la classe <xref:System.IO.Stream> et ses méthodes <xref:System.IO.Stream.BeginRead%2A> et <xref:System.IO.Stream.EndRead%2A> , qui représentent la contrepartie AMP de méthode <xref:System.IO.Stream.Read%2A> synchrone :  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 Vous pouvez utiliser la méthode <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> pour implémenter un wrapper TAP pour cette opération, comme le montre l’exemple ci-dessous :  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 Cette implémentation est similaire à ce qui suit :  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
### <a name="from-tap-to-apm"></a>TAP vers APM  

 Si votre infrastructure existante attend le modèle APM, vous voudrez également prendre une implémentation TAP et l’utiliser lorsque l’implémentation APM est attendue.  Étant donné que les tâches peuvent être composées et que la classe <xref:System.Threading.Tasks.Task> implémente <xref:System.IAsyncResult>, vous pouvez utiliser une fonction d’assistance simple pour effectuer cette opération. Le code suivant utilise une extension de la classe <xref:System.Threading.Tasks.Task%601> , mais vous pouvez utiliser une fonction presque identique pour les tâches non génériques.  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 À présent, imaginez une situation dans laquelle vous avez l’implémentation TAP suivante :  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 et que vous souhaitez fournir cette implémentation APM :  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 L’exemple suivant montre une migration vers APM :  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a>Tâches et EAP  

 Envelopper une implémentation [Event-based Asynchronous Pattern (EAP)](event-based-asynchronous-pattern-eap.md) est plus complexe qu’envelopper un modèle APM, car le modèle EAP est plus variable et moins structuré qu’un modèle APM.  Par exemple, le code suivant enveloppe la méthode `DownloadStringAsync` .  `DownloadStringAsync` accepte un URI, déclenche l’événement `DownloadProgressChanged` lors du téléchargement afin de générer plusieurs statistiques sur la progression et déclenche l’événement `DownloadStringCompleted` lorsque l’événement précédent est terminé.  Le résultat final est une chaîne qui détient le contenu de la page au niveau de l’URI spécifié.  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
## <a name="tasks-and-wait-handles"></a>Tâches et handles d’attente  
  
### <a name="from-wait-handles-to-tap"></a>handles d’attente vers TAP  

 Bien que les handles d’attente n’implémentent pas un modèle asynchrone, les développeurs expérimentés peuvent utiliser la classe <xref:System.Threading.WaitHandle> et la méthode <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> pour recevoir des notifications asynchrones lorsqu’un handle d’attente est défini.  Vous pouvez envelopper la méthode <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> pour autoriser une alternative basée sur les tâches pour toute attente synchrone sur un handle d’attente :  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 Cette méthode vous permet d’utiliser les implémentations <xref:System.Threading.WaitHandle> existantes dans les méthodes asynchrones.  Par exemple, si vous souhaitez limiter le nombre d’opérations asynchrones en cours d’exécution à un moment donné, vous pouvez utiliser un sémaphore (un objet <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType>).  Vous pouvez limiter à *n* le nombre d’opérations qui s’exécutent simultanément en initialisant le nombre du sémaphore à *n*, en attendant le sémaphore chaque fois que vous souhaitez effectuer une opération, puis libérer le sémaphore lorsque vous avez terminé une opération :  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 Vous pouvez également créer un sémaphore asynchrone qui ne repose pas sur les handles d’attente, mais sur les tâches. Pour ce faire, vous pouvez utiliser des techniques telles que celles abordées dans [Consuming the Task-based Asynchronous Pattern](consuming-the-task-based-asynchronous-pattern.md) pour la création de structures de données sur <xref:System.Threading.Tasks.Task>.  
  
### <a name="from-tap-to-wait-handles"></a>TAP vers handles d’attente  

 Comme mentionné précédemment, la classe <xref:System.Threading.Tasks.Task> implémente <xref:System.IAsyncResult>, et cette implémentation expose une propriété <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> qui renvoie un handle d’attente qui sera défini une fois la <xref:System.Threading.Tasks.Task> terminée.  Vous pouvez obtenir un <xref:System.Threading.WaitHandle> pour une <xref:System.Threading.Tasks.Task> comme suit :  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a>Voir aussi

- [Modèle asynchrone basé sur les tâches (TAP, Task-based Asynchronous Pattern)](task-based-asynchronous-pattern-tap.md)
- [Implémentation du modèle asynchrone basé sur des tâches](implementing-the-task-based-asynchronous-pattern.md)
- [Utilisation du modèle asynchrone basé sur les tâches](consuming-the-task-based-asynchronous-pattern.md)

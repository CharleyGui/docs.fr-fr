---
title: Tâches enfants attachées et détachées
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, child tasks
ms.assetid: c95788bf-90a6-4e96-b7bc-58e36a228cc5
ms.openlocfilehash: c8a5d2c1ccb8bb2d272c2582cd416cdfd75506d8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84285688"
---
# <a name="attached-and-detached-child-tasks"></a>Tâches enfants attachées et détachées
Une *tâche enfant* (ou *tâche imbriquée*) est une instance <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> créée dans le délégué utilisateur d’une autre tâche, appelée *tâche parent*. Une tâche enfant peut être détachée ou attachée. Une *tâche enfant détachée* est une tâche qui s’exécute indépendamment de son parent. Une *tâche enfant attachée* est une tâche imbriquée créée avec l’option <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> dont le parent ne l’empêche pas explicitement ou par défaut d’être attachée. Une tâche peut créer autant de tâches enfants attachées et détachées que le permettent les ressources système.  
  
 Le tableau suivant répertorie les principales différences entre les deux types de tâches enfants.  
  
|Category|Tâches enfants détachées|Tâches enfants attachées|  
|--------------|--------------------------|--------------------------|  
|Le parent attend que les tâches enfants soient terminées.|Non|Oui|  
|Le parent propage les exceptions levées par les tâches enfants.|Non|Oui|  
|Le statut du parent dépend du statut de l'enfant.|Non|Oui|  
  
 Dans la plupart des scénarios, nous vous recommandons d’utiliser des tâches enfants détachées, car leurs relations avec les autres tâches sont moins complexes. C'est pourquoi les tâches créées à l'intérieur de tâches parentes sont détachées par défaut et vous devez spécifier explicitement l'option <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> pour créer une tâche enfant attachée.  
  
## <a name="detached-child-tasks"></a>Tâches enfants détachées  
 Même si une tâche enfant est créée par une tâche parente, par défaut, elle est indépendante de celle-ci. Dans l'exemple suivant, une tâche parente crée une tâche enfant simple. Si vous exécutez l'exemple de code plusieurs fois, vous pouvez remarquer que la sortie de l'exemple diffère de celle indiquée et éventuellement d'une exécution à l'autre. En effet, la tâche parente et les tâches enfants s'exécutent indépendamment les unes des autres ; l'enfant est une tâche détachée. L'exemple attend seulement que la tâche parente se termine, et la tâche enfant ne peut pas s'exécuter ou s'achever avant la fin de l'application console.  
  
 [!code-csharp[TPL_ChildTasks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/nested1.cs#1)]
 [!code-vb[TPL_ChildTasks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/nested1.vb#1)]  
  
 Si la tâche enfant est représentée par un objet <xref:System.Threading.Tasks.Task%601> plutôt que par un objet <xref:System.Threading.Tasks.Task>, vous pouvez vous assurer que la tâche parente attend la fin de la tâche enfant en accédant à la propriété <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> de celle-ci, même s'il s'agit d'une tâche enfant détachée. La propriété <xref:System.Threading.Tasks.Task%601.Result%2A> bloque jusqu’à ce que sa tâche se termine, comme le montre l’exemple suivant.  
  
 [!code-csharp[TPL_ChildTasks#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/childtasks.cs#4)]
 [!code-vb[TPL_ChildTasks#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/tpl_childtasks.vb#4)]  
  
## <a name="attached-child-tasks"></a>Tâches enfants attachées  
 Contrairement aux tâches enfants détachées, les tâches enfants attachées sont étroitement synchronisées avec le parent. Vous pouvez convertir la tâche enfant détachée dans l'exemple précédent en tâche enfant attachée à l'aide de l'option <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> dans l'instruction de création de tâche, comme illustré dans l'exemple suivant. Dans ce code, la tâche enfant attachée se termine avant son parent. La sortie de l'exemple est donc la même chaque fois que vous exécutez le code.  
  
 [!code-csharp[TPL_ChildTasks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/child1.cs#2)]
 [!code-vb[TPL_ChildTasks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/child1.vb#2)]  
  
 Vous pouvez utiliser des tâches enfants attachées pour créer des graphiques étroitement synchronisés d’opérations asynchrones.  
  
 Toutefois, une tâche enfant ne peut s’attacher à son parent que si celui-ci n’interdit pas les tâches enfants attachées. Pour empêcher explicitement l’attachement de tâches enfants à une tâche parente, vous devez spécifier l’option <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> dans le constructeur de classe de la tâche parente ou la méthode <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType>. Pour une interdiction implicite, vous devez créer les tâches parentes en appelant la méthode <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType>. L'exemple suivant illustre ce comportement. Il est identique à l’exemple précédent, même si la tâche parente est créée en appelant la méthode <xref:System.Threading.Tasks.Task.Run%28System.Action%29?displayProperty=nameWithType> plutôt que la méthode <xref:System.Threading.Tasks.TaskFactory.StartNew%28System.Action%29?displayProperty=nameWithType>. Étant donné que la tâche enfant n’est pas en mesure de s’attacher à son parent, la sortie de l’exemple est imprévisible. Étant donné que les options de création de tâches par défaut pour les surcharges <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> incluent <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>, cet exemple est fonctionnellement équivalent au premier exemple dans la section « Tâches enfants détachées ».  
  
 [!code-csharp[TPL_ChildTasks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/child1a.cs#3)]
 [!code-vb[TPL_ChildTasks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/child1a.vb#3)]  
  
## <a name="exceptions-in-child-tasks"></a>Exceptions dans les tâches enfants  
 Si une tâche enfant détachée lève une exception, celle-ci doit être observée ou gérée directement dans la tâche parente, comme dans le cas de n’importe quelle tâche non imbriquée. Si une tâche enfant attachée lève une exception, celle-ci est automatiquement propagée vers la tâche parente, puis vers le thread qui attend ou essaie d’accéder à la propriété <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> de la tâche. Ainsi, en utilisant des tâches enfants attachées, vous pouvez gérer toutes les exceptions en un seul point dans l’appel à <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> sur le thread appelant. Pour plus d’informations, consultez l’article [Gestion des exceptions](exception-handling-task-parallel-library.md).  
  
## <a name="cancellation-and-child-tasks"></a>Annulation et tâches enfants  
 L'annulation de tâche est coopérative. Autrement dit, pour être annulable, chaque tâche enfant attachée ou détachée doit surveiller l'état du jeton d'annulation. Pour annuler un parent et tous ses enfants à l'aide d'une demande d'annulation, vous passez le même jeton en tant qu'argument à toutes les tâches et fournissez dans chaque tâche la logique pour répondre à la demande. Pour plus d’informations, consultez [Annulation de tâches](task-cancellation.md) et [Comment : annuler une tâche et ses enfants](how-to-cancel-a-task-and-its-children.md).  
  
### <a name="when-the-parent-cancels"></a>Annulation d'un parent  
 Si un parent s’annule avant le démarrage de sa tâche enfant, celle-ci ne démarre jamais. Si un parent s’annule une fois que sa tâche enfant a démarré, celle-ci s’exécute jusqu’à son terme sauf si elle possède sa propre logique d’annulation. Pour plus d'informations, consultez [Task Cancellation](task-cancellation.md).  
  
### <a name="when-a-detached-child-task-cancels"></a>Annulation d’une tâche enfant détachée  
 Si une tâche enfant détachée s’annule à l’aide du jeton passé au parent et que celui-ci n’attend pas la tâche enfant, aucune exception n’est propagée, car l’exception est traitée comme une annulation de coopération bénigne. Ce comportement est identique à celui de toute tâche de niveau supérieur.  
  
### <a name="when-an-attached-child-task-cancels"></a>Annulation d’une tâche enfant attachée  
 Quand une tâche enfant attachée s’annule à l’aide du jeton passé à sa tâche parente, une <xref:System.Threading.Tasks.TaskCanceledException> est propagée vers le thread intermédiaire à l’intérieur d’une <xref:System.AggregateException>. Vous devez attendre la tâche parente pour pouvoir gérer toutes les exceptions bénignes, en plus de toute exception d’erreur propagée vers un graphique de tâches enfants attachées.  
  
 Pour plus d’informations, consultez l’article [Gestion des exceptions](exception-handling-task-parallel-library.md).  
  
## <a name="preventing-a-child-task-from-attaching-to-its-parent"></a>Empêcher qu'une tâche enfant ne s'attache à son parent  
 Une exception non gérée levée par une tâche enfant est propagée vers la tâche parente. Vous pouvez vous baser sur ce comportement pour observer toutes les exceptions de tâche enfant à partir d'une seule tâche racine au lieu de parcourir une arborescence de tâches. Toutefois, la propagation d’exception peut être problématique quand une tâche parente n’attend pas d’attachement de la part d’un autre code. Par exemple, imaginez une application qui appelle un composant de bibliothèque tierce à partir d'un objet <xref:System.Threading.Tasks.Task>. Si ce composant crée également un objet <xref:System.Threading.Tasks.Task> et spécifie <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> pour l’attacher à la tâche parente, les exceptions non gérées qui se produisent dans la tâche enfant se propagent vers le parent. Cela peut entraîner un comportement inattendu dans l'application principale.  
  
 Pour empêcher une tâche enfant de s'attacher à sa tâche parente, spécifiez l'option <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> quand vous créez l'objet <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> parent. Si une tâche enfant tente de s’attacher à son parent alors que celui-ci spécifie l’option <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>, elle échoue et s’exécute comme si l’option <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> n’était pas spécifiée.  
  
 Vous pourriez également empêcher une tâche enfant de s'attacher à son parent quand la tâche enfant ne se termine pas en temps voulu. Étant donné qu’une tâche parente ne se termine pas tant que toutes les tâches enfants ne sont pas achevées, une tâche enfant à exécution longue peut entraîner des performances médiocres de la part de l’application globale. Pour obtenir un exemple qui montre comment améliorer les performances de l’application en empêchant une tâche de s’attacher à sa tâche parente, consultez [Procédure : empêcher une tâche enfant de s’attacher à son parent](how-to-prevent-a-child-task-from-attaching-to-its-parent.md).  
  
## <a name="see-also"></a>Voir aussi

- [Programmation parallèle](index.md)
- [Parallélisme des données](data-parallelism-task-parallel-library.md)

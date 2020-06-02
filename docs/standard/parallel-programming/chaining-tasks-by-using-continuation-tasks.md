---
title: Chaînage des tâches à l’aide de tâches de continuation
ms.date: 02/11/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, continuations
ms.assetid: 0b45e9a2-de28-46ce-8212-1817280ed42d
ms.openlocfilehash: c6952b4b341a76e15d9699a06cd64ae7b6b4f047
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84285610"
---
# <a name="chaining-tasks-by-using-continuation-tasks"></a>Chaînage des tâches à l’aide de tâches de continuation
En programmation asynchrone, il est courant pour une opération asynchrone, une fois terminée, d’appeler une deuxième opération et de lui passer des données. Habituellement, les continuations se faisaient à l’aide de méthodes de rappel. Dans la bibliothèque parallèle de tâches, les mêmes fonctionnalités sont fournies par les *tâches de continuation*. Une tâche de continuation (également appelée continuation) est une tâche asynchrone appelée par une autre tâche, appelée *antécédent*, quand ce dernier est terminé.  
  
 Les continuations sont relativement faciles à utiliser, tout en étant puissantes et flexibles. Vous pouvez par exemple :  
  
- passer des données de l'antécédent à la continuation ;  
  
- spécifier les conditions précises sous lesquelles la continuation doit être ou non appelée ;  
  
- annuler une continuation avant qu'elle ne soit lancée ou pendant son exécution de manière coopérative ;  
  
- fournir des conseils sur la manière de planifier la continuation ;  
  
- appeler plusieurs continuations depuis le même antécédent ;  
  
- appeler une continuation quand certains ou tous les antécédents se terminent ;  
  
- chaîner des continuations les unes à la suite des autres à une longueur arbitraire ;  
  
- utiliser une continuation pour gérer des exceptions levées par l'antécédent.  
  
## <a name="about-continuations"></a>À propos des continuations  
 Une continuation est une tâche qui est créée dans l'état <xref:System.Threading.Tasks.TaskStatus.WaitingForActivation> . Elle est automatiquement activée à la fin de la tâche ou des tâches de son antécédent. Appeler <xref:System.Threading.Tasks.Task.Start%2A?displayProperty=nameWithType> sur une continuation dans le code utilisateur lève une exception <xref:System.InvalidOperationException?displayProperty=nameWithType> .  
  
 Une continuation est un <xref:System.Threading.Tasks.Task> et ne bloque pas le thread sur lequel elle a démarré. Appelez la méthode <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> pour bloquer jusqu'à ce que la tâche de continuation se termine.  
  
## <a name="creating-a-continuation-for-a-single-antecedent"></a>Création d‘une continuation pour un seul antécédent  
 Vous créez une continuation qui s'exécute quand son antécédent est terminé en appelant la méthode <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> . L’exemple suivant montre le modèle de base (pour plus de clarté, la gestion des exceptions a été omise). Il exécute une tâche d'antécédent, `taskA`, qui retourne un objet <xref:System.DayOfWeek> indiquant le jour actuel de la semaine. Quand l’antécédent termine, la tâche de continuation, `continuation`, le récupère et affiche une chaîne qui comprend son résultat.

> [!NOTE]
> Les exemples en C# fournis dans cet article utilisent le modificateur `async` sur la méthode `Main`. Cette fonctionnalité est disponible dans les versions 7.1 et ultérieures de C#. Les versions précédentes ont été générées [`CS5001`](../../csharp/misc/cs5001.md) lors de la compilation de cet exemple de code. Vous devez définir la version du langage sur C# 7.1 ou une version ultérieure. Pour savoir comment configurer la version du langage, consultez l’article sur la [configuration de la version du langage](../../csharp/language-reference/configure-language-version.md).
  
 [!code-csharp[TPL_Continuations#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/simple1.cs#1)]
 [!code-vb[TPL_Continuations#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/simple1.vb#1)]  
  
## <a name="creating-a-continuation-for-multiple-antecedents"></a>Création d‘une continuation pour plusieurs antécédents  
 Vous pouvez également créer une continuation qui s’exécute quand tout ou partie d’un groupe de tâches est terminé. Pour exécuter une continuation quand toutes les tâches d'antécédent sont terminées, vous appelez la méthode statique`Shared` ( <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> en Visual Basic) ou la méthode <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> d'instance. Pour exécuter une continuation quand n'importe quelle tâche d'antécédent est terminée, vous appelez la méthode statique`Shared` ( <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> en Visual Basic) ou la méthode <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A?displayProperty=nameWithType> d'instance.  
  
 Sachez que les appels aux surcharges <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> ne bloquent pas le thread appelant.  Cependant, vous appelez généralement toutes les méthodes, sauf <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> et  <xref:System.Threading.Tasks.Task.WhenAll%28System.Threading.Tasks.Task%5B%5D%29?displayProperty=nameWithType> , pour extraire la propriété  <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> retournée, ce qui bloque le thread appelant.  
  
 L’exemple suivant appelle la méthode <xref:System.Threading.Tasks.Task.WhenAll%28System.Collections.Generic.IEnumerable%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> pour créer une tâche de continuation qui reflète les résultats de ses dix tâches d’antécédent. Chaque tâche d’antécédent élève au carré une valeur d’index allant de 1 à 10. Si les antécédents se terminent correctement (leur propriété <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> vaut <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType>), la propriété <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> de la continuation est un tableau de valeurs <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> retournées par chaque antécédent. L’exemple les ajoute pour calculer la somme des carrés de tous les nombres compris entre 1 et 10.  
  
 [!code-csharp[TPL_Continuations#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/whenall1.cs#5)]
 [!code-vb[TPL_Continuations#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/whenall1.vb#5)]  
  
## <a name="continuation-options"></a>Options de continuation  
 Quand vous créez une continuation de tâche unique, vous pouvez utiliser une surcharge <xref:System.Threading.Tasks.Task.ContinueWith%2A> qui prend une valeur d'énumération <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> pour spécifier les conditions sous lesquelles la continuation doit se lancer. Par exemple, vous pouvez spécifier que la continuation doit être exécutée uniquement si l‘antécédent se termine correctement ou uniquement s‘il se termine avec un état d‘erreur. Si cette condition n’est pas remplie quand l’antécédent est prêt à appeler la continuation, la continuation passe directement à l’état <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> et ne peut donc pas être lancée.  
  
 Plusieurs méthodes de continuation multitâche, telles que les surcharges de la méthode <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> , incluent également un paramètre <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> . Seul un sous-ensemble des membres de l'énumération <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> est valide, toutefois. Vous pouvez spécifier des valeurs <xref:System.Threading.Tasks.TaskContinuationOptions?displayProperty=nameWithType> qui ont des équivalents dans l'énumération <xref:System.Threading.Tasks.TaskCreationOptions?displayProperty=nameWithType> , telles que <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType>, <xref:System.Threading.Tasks.TaskContinuationOptions.LongRunning?displayProperty=nameWithType>et <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness?displayProperty=nameWithType>. Si vous spécifiez n'importe laquelle des options `NotOn` ou `OnlyOn` avec une continuation multitâche, une exception <xref:System.ArgumentOutOfRangeException> est levée au moment de l'exécution.  
  
 Pour plus d'informations sur les options de continuation de tâche, consultez la rubrique <xref:System.Threading.Tasks.TaskContinuationOptions> .  
  
## <a name="passing-data-to-a-continuation"></a>Passage de données à une continuation  
 La méthode <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> passe une référence à l'antécédent au délégué d'utilisateur de la continuation en tant qu'argument. Si l'antécédent est un objet <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> et que la tâche s'est exécutée normalement jusqu'à son terme, la continuation peut accéder à la propriété <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> de la tâche.  
  
 La propriété <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> se bloque jusqu'à ce que la tâche soit terminée. Toutefois, si la tâche a été annulée ou a rencontré une erreur, toute tentative d'accéder à la propriété <xref:System.Threading.Tasks.Task%601.Result%2A> lève une exception <xref:System.AggregateException> . Vous pouvez éviter ce problème à l'aide de l'option <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnRanToCompletion> , comme indiqué dans l'exemple suivant.  
  
 [!code-csharp[TPL_Continuations#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result1.cs#2)]
 [!code-vb[TPL_Continuations#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result1.vb#2)]  
  
 Si vous voulez que la continuation s‘exécute même si l‘exécution de l‘antécédent n‘est pas correctement terminée, vous devez vous attendre à des exceptions. Une approche consiste à tester la propriété <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> de l'antécédent et à n'essayer d'accéder à la propriété <xref:System.Threading.Tasks.Task%601.Result%2A> que si l'état n'est pas <xref:System.Threading.Tasks.TaskStatus.Faulted> ou <xref:System.Threading.Tasks.TaskStatus.Canceled>. Vous pouvez également examiner la propriété <xref:System.Threading.Tasks.Task.Exception%2A> de l'antécédent. Pour plus d’informations, consultez l’article [Gestion des exceptions](exception-handling-task-parallel-library.md). L'exemple suivant modifie l'exemple précédent de manière à n'accéder à la propriété <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> de l'antécédent que si son état est <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType>.  
  
 [!code-csharp[TPL_Continuations#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/result2.cs#7)]
 [!code-vb[TPL_Continuations#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/result2.vb#7)]  
  
## <a name="canceling-a-continuation"></a>Annulation d'une continuation  
 La propriété <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=nameWithType> d'une continuation est définie sur <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> dans les situations suivantes :  
  
- Elle lève une exception <xref:System.OperationCanceledException> en réponse à une demande d'annulation. Comme pour toute tâche, si l’exception contient le même jeton qui a été passé à la continuation, il est traité comme un accusé de réception de l’annulation coopérative.  
  
- La continuation récupère un <xref:System.Threading.CancellationToken?displayProperty=nameWithType> dont la propriété <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> a pour valeur `true`. Dans ce cas, la continuation ne démarre pas, et elle passe à l'état <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> .  
  
- La continuation ne s'exécute jamais, car la condition définie par son argument <xref:System.Threading.Tasks.TaskContinuationOptions> n'a pas été remplie. Par exemple, si un antécédent passe à l'état <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> , sa continuation qui a reçu l'option <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnFaulted?displayProperty=nameWithType> ne s'exécute pas, mais passe à l'état <xref:System.Threading.Tasks.TaskStatus.Canceled> .  
  
 Si une tâche et sa continuation représentent deux parties de la même opération logique, vous pouvez passer le même jeton d’annulation aux deux tâches, comme illustré dans l’exemple suivant. Ce dernier comprend un antécédent qui génère une liste d'entiers divisibles par 33, transmise ensuite à la continuation. À son tour, la continuation affiche la liste. L‘antécédent et la continuation marquent régulièrement des pauses de durée aléatoire. En outre, un objet <xref:System.Threading.Timer?displayProperty=nameWithType> est utilisé pour exécuter la méthode `Elapsed` après un délai de cinq secondes. Cet exemple appelle la méthode <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType>, ce qui amène la tâche en cours d’exécution à appeler la méthode <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A?displayProperty=nameWithType>. La durée des pauses générées de manière aléatoire détermine si la méthode <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> est appelée pendant l'exécution de l'antécédent ou de sa continuation. Si l‘antécédent est annulé, la continuation ne démarre pas. Si l‘antécédent n‘est pas annulé, le jeton peut toujours être utilisé pour annuler la continuation.  
  
 [!code-csharp[TPL_Continuations#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation1.cs#3)]
 [!code-vb[TPL_Continuations#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation1.vb#3)]  
  
 Vous pouvez également empêcher une continuation de s'exécuter si son antécédent est annulé en spécifiant l'option <xref:System.Threading.Tasks.TaskContinuationOptions.NotOnCanceled?displayProperty=nameWithType> quand vous créez la continuation, ce qui vous évite de lui fournir un jeton d'annulation. Voici un exemple simple.  
  
 [!code-csharp[TPL_Continuations#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/cancellation2.cs#8)]
 [!code-vb[TPL_Continuations#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/cancellation2.vb#8)]  
  
 Une fois la continuation à l'état <xref:System.Threading.Tasks.TaskStatus.Canceled> , elle peut affecter les continuations suivantes, selon les <xref:System.Threading.Tasks.TaskContinuationOptions> spécifiés pour ces continuations.  
  
 Les continuations supprimées ne seront pas lancées.  
  
## <a name="continuations-and-child-tasks"></a>Continuations et tâches enfants  
 Une continuation ne s'exécute pas tant que l'antécédent et toutes ses tâches enfants attachées ne sont pas terminés. La continuation n'attend pas la fin des tâches enfants détachées. Les deux exemples suivants illustrent des tâches enfants attachées à un antécédent qui crée une continuation, et détachées de celui-ci. Dans l’exemple suivant, la continuation ne s’exécute qu’une fois toutes les tâches enfants terminées. L’exécution de l’exemple à plusieurs reprise génère systématiquement la même sortie. L’exemple lance l’antécédent en appelant la méthode <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType>, car par défaut la méthode <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> crée une tâche parente dont l’option de création de tâche par défaut est <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>.  
  
 [!code-csharp[TPL_Continuations#9](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/attached1.cs#9)]
 [!code-vb[TPL_Continuations#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/attached1.vb#9)]  
  
 Toutefois, si des tâches enfants sont détachées de l'antécédent, la continuation s'exécute dès que l'antécédent a terminé, indépendamment de l'état des tâches enfants. Ainsi, différentes exécutions de l'exemple suivant peuvent générer différentes sorties en fonction de la façon dont le Planificateur de tâches a géré chaque tâche enfant.  
  
 [!code-csharp[TPL_Continuations#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/detached1.cs#10)]
 [!code-vb[TPL_Continuations#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/detached1.vb#10)]  
  
 L’état final de la tâche d’antécédent dépend de l’état final des tâches enfants attachées. L’état des tâches enfants détachées n’affecte pas le parent. Pour plus d'informations, consultez [Tâches enfants attachées et détachées](attached-and-detached-child-tasks.md).  
  
## <a name="associating-state-with-continuations"></a>Association d'un état à une continuation  
 Vous pouvez associer un état arbitraire à une continuation de tâche. La méthode <xref:System.Threading.Tasks.Task.ContinueWith%2A> fournit des versions surchargées prenant chacune une valeur <xref:System.Object> qui représente l'état de la continuation. Vous pouvez ensuite accéder à cet objet d'état à l'aide de la propriété <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType> . Cet objet d'état est `null` si vous ne fournissez pas de valeur.  
  
 L'état de continuation est utile quand vous convertissez du code existant qui recourt au [modèle de programmation asynchrone (APM)](../asynchronous-programming-patterns/asynchronous-programming-model-apm.md) pour utiliser la bibliothèque parallèle de tâches. Dans l’APM, vous fournissez généralement l’état de l’objet dans la méthode **Begin**_Method_, puis vous accédez à cet état à l’aide de la propriété <xref:System.IAsyncResult.AsyncState%2A?displayProperty=nameWithType>. À l'aide de la méthode <xref:System.Threading.Tasks.Task.ContinueWith%2A> , vous pouvez conserver cet état quand vous convertissez du code qui recourt à l'APM pour utiliser la bibliothèque parallèle de tâches.  
  
 L'état de continuation peut également être utile si vous employez des objets <xref:System.Threading.Tasks.Task> dans le débogueur Visual Studio. Par exemple, dans la fenêtre **Tâches parallèles** , la colonne **Tâche** affiche la représentation sous forme de chaîne de l'objet d'état pour chaque tâche. Pour plus d’informations sur la fenêtre **Tâches parallèles**, consultez [Utilisation de la fenêtre Tâches](/visualstudio/debugger/using-the-tasks-window).  
  
 L'exemple suivant montre comment utiliser l'état de continuation. Il crée une chaîne de tâches de continuation. Chaque tâche fournit l'heure actuelle, sous la forme d'un objet <xref:System.DateTime> , pour le paramètre `state` de la méthode <xref:System.Threading.Tasks.Task.ContinueWith%2A> . Chaque objet <xref:System.DateTime> représente l'heure de création de la tâche de continuation. Chaque tâche génère un deuxième objet <xref:System.DateTime> qui représente l'heure à laquelle la tâche se termine. Une fois toutes les tâches terminées, cet exemple affiche les heures de création et de fin de chaque tâche de continuation.  
  
 [!code-csharp[TPL_ContinuationState#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuationstate/cs/continuationstate.cs#1)]
 [!code-vb[TPL_ContinuationState#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuationstate/vb/continuationstate.vb#1)]  
  
## <a name="handling-exceptions-thrown-from-continuations"></a>Gestion d'exceptions levées par des continuations  
 Une relation antécédent-continuation n'est pas une relation parent-enfant. Les exceptions levées par les continuations ne sont pas propagées à l'antécédent. Vous pouvez ainsi gérer les exceptions levées par les continuations de la même manière qu’avec une autre tâche, comme suit :  
  
- Vous pouvez utiliser la méthode <xref:System.Threading.Tasks.Task.Wait%2A>, <xref:System.Threading.Tasks.Task.WaitAll%2A>, ou <xref:System.Threading.Tasks.Task.WaitAny%2A> , ou son équivalent générique, pour attendre la continuation. Vous pouvez attendre un antécédent et ses continuations dans la même instruction `try` , comme indiqué dans l'exemple suivant.  
  
     [!code-csharp[TPL_Continuations#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception1.cs#6)]
     [!code-vb[TPL_Continuations#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception1.vb#6)]  
  
- Vous pouvez utiliser une deuxième continuation pour observer la propriété <xref:System.Threading.Tasks.Task.Exception%2A> de la première continuation. Dans l’exemple suivant, une tâche tente de lire un fichier inexistant. La continuation affiche ensuite des informations sur l'exception dans la tâche d'antécédent.  
  
     [!code-csharp[TPL_Continuations#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#4)]
     [!code-vb[TPL_Continuations#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#4)]  
  
     Ayant été lancée avec l'option <xref:System.Threading.Tasks.TaskContinuationOptions.OnlyOnFaulted?displayProperty=nameWithType> , la continuation ne s'exécute que si une exception se produit dans l'antécédent et peut donc supposer que la propriété <xref:System.Threading.Tasks.Task.Exception%2A> de l'antécédent n'a pas pour valeur `null`. Si la continuation s'exécute indépendamment du fait qu'une exception soit levée ou non dans l'antécédent, elle doit vérifier si la propriété <xref:System.Threading.Tasks.Task.Exception%2A> de l'antécédent n'est pas définie sur `null` avant de gérer l'exception, comme le montre le fragment de code suivant.  
  
     [!code-csharp[TPL_Continuations#11](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_continuations/cs/exception2.cs#11)]
     [!code-vb[TPL_Continuations#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_continuations/vb/exception2.vb#11)]  
  
     Pour plus d’informations, consultez l’article [Gestion des exceptions](exception-handling-task-parallel-library.md).  
  
- Si la continuation est une tâche enfant attachée qui a été créée à l'aide de l'option <xref:System.Threading.Tasks.TaskContinuationOptions.AttachedToParent?displayProperty=nameWithType> , ses exceptions sont de nouveau propagées par le parent au thread appelant, comme dans le cas de tout autre enfant attaché. Pour plus d'informations, consultez [Tâches enfants attachées et détachées](attached-and-detached-child-tasks.md).  
  
## <a name="see-also"></a>Voir aussi

- [Bibliothèque parallèle de tâches](task-parallel-library-tpl.md)

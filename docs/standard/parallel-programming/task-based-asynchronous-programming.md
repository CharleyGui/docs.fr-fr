---
title: Programmation asynchrone basée sur les tâches - .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallelism, task
ms.assetid: 458b5e69-5210-45e5-bc44-3888f86abd6f
ms.openlocfilehash: 66904a24817eee0161d877ace7f4584d58fe30f0
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507570"
---
# <a name="task-based-asynchronous-programming"></a>Programmation asynchrone basée sur les tâches

La bibliothèque parallèle de tâches (TPL) est basée sur le concept de *tâche*, qui représente une opération asynchrone. À certains égards, une tâche ressemble à un thread ou à un élément de travail <xref:System.Threading.ThreadPool>, mais à un niveau d’abstraction supérieur. Le terme *parallélisme des tâches* fait référence à une ou plusieurs tâches indépendantes qui s’exécutent simultanément. Les tâches présentent deux grands avantages :

- Une utilisation plus efficace et évolutive des ressources système.

     En arrière-plan, les tâches sont mises en file d’attente dans le <xref:System.Threading.ThreadPool>, amélioré au moyen d’algorithmes qui déterminent le nombre de threads (et s’y ajustent) et qui fournissent l’équilibrage de charge afin d’optimiser le débit. Cela rend les tâches relativement simples et vous permet d’en créer de nombreuses pour un parallélisme affiné.

- Davantage de contrôle par programmation qu'avec un thread ou un élément de travail.

     Les tâches et l'infrastructure construites autour de ces algorithmes fournissent un ensemble riche d'API prenant en charge l'attente, l'annulation, les continuations, la gestion fiable des exceptions, l'état détaillé, la planification personnalisée, et bien plus encore.

Pour ces raisons, la bibliothèque parallèle de tâches est l'API privilégiée pour l'écriture du code multithread, asynchrone et parallèle dans .NET Framework.

## <a name="creating-and-running-tasks-implicitly"></a>Création et exécution implicites de tâches

La méthode <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> offre un moyen pratique d'exécuter simultanément un nombre d'instructions arbitraires. Pour cela, passez un délégué <xref:System.Action> pour chaque élément de travail. La façon la plus facile de créer ces délégués est d’utiliser des expressions lambda. L’expression lambda peut appeler une méthode nommée ou fournir le code inline. L'exemple suivant montre un appel <xref:System.Threading.Tasks.Parallel.Invoke%2A> de base qui crée et démarre deux tâches qui s'exécutent simultanément. La première tâche est représentée par une expression lambda qui appelle une méthode nommée `DoSomeWork` et la seconde tâche est représentée par une expression lambda qui appelle une méthode nommée `DoSomeOtherWork`.

> [!NOTE]
> Cette documentation utilise les expressions lambda pour définir les délégués de la bibliothèque parallèle de tâches. Si les expressions lambda en C# ou Visual Basic ne vous sont pas familières, consultez la page [Expressions lambda en PLINQ et dans la bibliothèque parallèle de tâches](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

[!code-csharp[TPL#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#21)]
[!code-vb[TPL#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#21)]

> [!NOTE]
> Le nombre d'instances <xref:System.Threading.Tasks.Task> créées en arrière-plan par <xref:System.Threading.Tasks.Parallel.Invoke%2A> n'est pas nécessairement égal au nombre de délégués fournis. La bibliothèque parallèle de tâches peut utiliser différentes optimisations, surtout avec un grand nombre de délégués.

Pour plus d’informations, consultez [Comment : utiliser parallel_invoke pour exécuter des opérations parallèles](../../../docs/standard/parallel-programming/how-to-use-parallel-invoke-to-execute-parallel-operations.md).

Pour un plus grand contrôle de l’exécution de tâches ou pour retourner une valeur à partir de la tâche, vous devez utiliser les objets <xref:System.Threading.Tasks.Task> de manière plus explicite.

## <a name="creating-and-running-tasks-explicitly"></a>Création et exécution explicites de tâches

Une tâche qui ne retourne pas de valeur est représentée par la classe <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>. Une tâche qui retourne une valeur est représentée par la classe <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>, qui hérite de <xref:System.Threading.Tasks.Task>. L’objet de tâche gère les détails de l’infrastructure et fournit des méthodes et des propriétés accessibles depuis le thread appelant pendant la durée de vie de la tâche. Par exemple, vous pouvez accéder à la propriété <xref:System.Threading.Tasks.Task.Status%2A> d'une tâche à tout moment pour déterminer si son exécution a commencé, est terminée, a été annulée ou a levé une exception. Le statut est représenté par une énumération <xref:System.Threading.Tasks.TaskStatus>.

Lorsque vous créez une tâche, vous lui donnez un délégué utilisateur qui encapsule le code que la tâche exécutera. Le délégué peut être exprimé en tant que délégué nommé, méthode anonyme ou expression lambda. Les expressions lambda peuvent contenir un appel à une méthode nommée, comme indiqué dans l’exemple suivant. Notez que l’exemple inclut un appel à la méthode <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> pour garantir que l’exécution de la tâche se termine avant la fin de l’application en mode console.

[!code-csharp[TPL_TaskIntro#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/lambda1.cs#1)]
[!code-vb[TPL_TaskIntro#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/lambda1.vb#1)]

Vous pouvez également utiliser les méthodes <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> pour créer et lancer une tâche dans une opération. Pour gérer la tâche, les méthodes <xref:System.Threading.Tasks.Task.Run%2A> utilisent le planificateur de tâches par défaut, quel que soit le planificateur de tâches associé au thread actuel. Les méthodes <xref:System.Threading.Tasks.Task.Run%2A> représentent la meilleure façon de créer et de lancer des tâches lorsqu’un plus grand contrôle sur la création et la planification de la tâche n’est pas nécessaire.

[!code-csharp[TPL_TaskIntro#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/run1.cs#2)]
[!code-vb[TPL_TaskIntro#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/run1.vb#2)]

Vous pouvez également utiliser la méthode <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> pour créer et lancer une tâche dans une opération. Utilisez cette méthode quand la création et la planification n’ont pas besoin d’être séparées et que vous avez besoin d’options supplémentaires de création de tâches ou d’utiliser un planificateur spécifique, ou lorsque vous devez obtenir l’état supplémentaire dans la tâche via sa propriété <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType>, comme indiqué dans l’exemple suivant.

[!code-csharp[TPL_TaskIntro#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/asyncstate.cs#23)]
[!code-vb[TPL_TaskIntro#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/asyncstate.vb#23)]

<xref:System.Threading.Tasks.Task> et <xref:System.Threading.Tasks.Task%601> exposent tous deux une propriété <xref:System.Threading.Tasks.Task.Factory%2A> statique qui retourne une instance par défaut de <xref:System.Threading.Tasks.TaskFactory>, afin que vous puissiez appeler la méthode en tant que `Task.Factory.StartNew()`. De plus, dans l’exemple suivant, parce que les tâches sont de type <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>, chacune d’elle a une propriété <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> publique contenant le résultat du calcul. Les tâches sont exécutées de façon asynchrone et peuvent se terminer dans n’importe quel ordre. Si la propriété <xref:System.Threading.Tasks.Task%601.Result%2A> est accessible avant la fin du calcul, la propriété bloque le thread appelant jusqu'à ce que la valeur soit disponible.

[!code-csharp[TPL_TaskIntro#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/result1.cs#4)]
[!code-vb[TPL_TaskIntro#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/result1.vb#4)]

Pour plus d’informations, consultez [Comment : retourner une valeur à partir d’une tâche](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md).

Lorsque vous utilisez une expression lambda pour créer le délégué d’une tâche, vous avez accès à toutes les variables qui sont visibles à ce stade dans votre code source. Toutefois, dans certains cas, notamment dans les boucles, une expression lambda ne capture pas la variable comme prévu. Elle capture uniquement la valeur finale, pas la valeur qui change au cours de chaque itération. L'exemple de code suivant illustre le problème. Il passe un compteur de boucles à une expression lambda qui instancie un objet `CustomData` et utilise le compteur de boucles comme identificateur de l'objet. Comme le montre la sortie de l'exemple, chaque objet `CustomData` a un identificateur identique.

[!code-csharp[TPL_TaskIntro#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/iteration1b.cs#22)]
[!code-vb[TPL_TaskIntro#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/iteration1b.vb#22)]

Vous pouvez accéder à la valeur de chaque itération en fournissant un objet d’état à une tâche via son constructeur. L'exemple suivant modifie l'exemple précédent en utilisant le compteur de boucles lors de la création de l'objet `CustomData` qui, à son tour, est passé à l'expression lambda.  Comme le montre la sortie de l'exemple, chaque objet `CustomData` possède maintenant un identificateur unique basé sur la valeur du compteur de boucle au moment où l'objet a été instancié.

[!code-csharp[TPL_TaskIntro#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/iteration1a.cs#21)]
[!code-vb[TPL_TaskIntro#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/iteration1a.vb#21)]

Cet état est passé comme argument au délégué de tâche et est accessible dans l'objet de tâche à l'aide de la propriété <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=nameWithType>.  L'exemple suivant est une variante de l'exemple précédent. Il utilise la propriété <xref:System.Threading.Tasks.Task.AsyncState%2A> pour afficher des informations sur les objets `CustomData` passés à l’expression lambda.

[!code-csharp[TPL_TaskIntro#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/asyncstate.cs#23)]
[!code-vb[TPL_TaskIntro#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/asyncstate.vb#23)]

## <a name="task-id"></a>ID de la tâche

Chaque tâche reçoit un ID d'entier qui l'identifie de façon unique dans un domaine d'application et peut être accessible à l'aide de la propriété <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=nameWithType>. L’ID est utile pour la consultation des informations de tâche dans les fenêtres **Piles parallèles** et **Tâches** du débogueur Visual Studio. L’ID est créé de manière différée, ce qui signifie qu’il n’est pas créé tant que cela n’est pas demandé ; par conséquent, une tâche peut avoir un ID différent à chaque exécution du programme. Pour plus d’informations sur l’affichage des ID de tâche dans le débogueur, consultez [Utilisation de la fenêtre Tâches](/visualstudio/debugger/using-the-tasks-window) et [Utilisation de la fenêtre Piles parallèles](/visualstudio/debugger/using-the-parallel-stacks-window).

## <a name="task-creation-options"></a>Options de création de tâches

La plupart des API qui créent des tâches fournissent des surcharges qui acceptent un paramètre <xref:System.Threading.Tasks.TaskCreationOptions>. En spécifiant l’une de ces options, vous indiquez au planificateur de tâches la manière de planifier la tâche dans le pool de threads. Le tableau suivant répertorie les différentes options de création de tâches.

|Valeur du paramètre <xref:System.Threading.Tasks.TaskCreationOptions>|Description|
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|
|<xref:System.Threading.Tasks.TaskCreationOptions.None>|Valeur par défaut lorsqu'aucune option n'est spécifiée. Le planificateur utilise ses méthodes heuristiques par défaut pour planifier la tâche.|
|<xref:System.Threading.Tasks.TaskCreationOptions.PreferFairness>|Spécifie que la tâche doit être planifiée afin que les tâches créées précédemment soient susceptibles d’être exécutées plus tôt et que les tâches créées ultérieurement soient susceptibles d’être exécutées plus tard.|
|<xref:System.Threading.Tasks.TaskCreationOptions.LongRunning>|Spécifie que la tâche représente une opération de longue durée.|
|<xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent>|Spécifie qu’une tâche doit être créée en tant qu’enfant attaché à la tâche actuelle, s’il en existe une. Pour plus d'informations, consultez [Tâches enfants attachées et détachées](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).|
|<xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach>|Indique que si une tâche interne spécifie l'option `AttachedToParent`, cette tâche ne sera pas une tâche enfant attachée.|
|<xref:System.Threading.Tasks.TaskCreationOptions.HideScheduler>|Spécifie que le planificateur de tâches pour les tâches créées en appelant des méthodes comme <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> ou <xref:System.Threading.Tasks.Task%601.ContinueWith%2A?displayProperty=nameWithType> à partir d'une tâche particulière est le planificateur par défaut au lieu du planificateur sur lequel cette tâche s'exécute.|

Les options peuvent être combinées avec une opération de bits **OR**. L’exemple suivant montre une tâche avec les options <xref:System.Threading.Tasks.TaskCreationOptions.LongRunning> et <xref:System.Threading.Tasks.TaskContinuationOptions.PreferFairness>.

[!code-csharp[TPL_TaskIntro#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#03)]
[!code-vb[TPL_TaskIntro#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#03)]

## <a name="tasks-threads-and-culture"></a>Tâches, threads et culture

Chaque thread possède une culture associée et une culture d'interface utilisateur, respectivement définies par les propriétés <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> et <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType>. La culture d'un thread est utilisée dans des opérations telles que la mise en forme, l'analyse, le tri et la comparaison de chaînes. La culture d'interface utilisateur d'un thread est utilisée dans la recherche de ressources. En règle générale, sauf si vous spécifiez une culture par défaut pour tous les threads dans un domaine d'application à l'aide des propriétés <xref:System.Globalization.CultureInfo.DefaultThreadCurrentCulture%2A?displayProperty=nameWithType> et <xref:System.Globalization.CultureInfo.DefaultThreadCurrentUICulture%2A?displayProperty=nameWithType>, la culture par défaut et la culture d'interface utilisateur d'un thread sont définies par la culture du système. Si vous définissez explicitement la culture d'un thread et lancez un nouveau thread, ce dernier n'hérite pas de la culture du thread appelant ; au lieu de cela, sa culture est la culture du système par défaut. Le modèle de programmation basé sur les tâches pour les applications qui ciblent des versions du .NET Framework antérieures à .NET Framework 4.6 respecte cette pratique.

> [!IMPORTANT]
> Notez que la culture du thread appelant dans le cadre du contexte d’une tâche s’applique aux applications qui *ciblent* .NET Framework 4.6, et non celles qui *s’exécutent sous* .NET Framework 4.6. Vous pouvez cibler une version particulière du .NET Framework quand vous créez votre projet dans Visual Studio en sélectionnant une version dans la liste déroulante située en haut de la boîte de dialogue **Nouveau projet**. Sinon, en dehors de Visual Studio, vous pouvez utiliser l’attribut <xref:System.Runtime.Versioning.TargetFrameworkAttribute>. Pour les applications qui ciblent des versions du .NET Framework antérieures à .NET Framework 4.6, ou qui ne ciblent pas une version spécifique du .NET Framework, la culture d’une tâche demeure déterminée par la culture du thread sur lequel la tâche s’exécute.

À compter des applications qui ciblent .NET Framework 4.6, la culture du thread appelant est héritée par chaque tâche, même si la tâche s’exécute de façon asynchrone sur un thread de pool de threads.

L'exemple suivant illustre cette situation de façon simple. Il utilise l’attribut <xref:System.Runtime.Versioning.TargetFrameworkAttribute> pour cibler .NET Framework 4.6 et définit la culture actuelle de l’application sur Français (France) ou, si Français (France) est déjà la culture actuelle, sur Anglais (États-Unis). Il appelle ensuite un délégué nommé `formatDelegate` qui retourne des nombres mis en forme en tant que valeurs de devise dans la nouvelle culture. Que le délégué exécute une tâche de manière synchrone ou asynchrone, il retourne le résultat attendu, car la culture du thread appelant est héritée par la tâche asynchrone.

[!code-csharp[System.Globalization.CultureInfo.Class.Async#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.globalization.cultureinfo.class.async/cs/asyncculture1.cs#5)]
[!code-vb[System.Globalization.CultureInfo.Class.Async#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.globalization.cultureinfo.class.async/vb/asyncculture1.vb#5)]

Si vous utilisez Visual Studio, vous pouvez omettre l'attribut <xref:System.Runtime.Versioning.TargetFrameworkAttribute>. Pour cela, vous devez sélectionner le .NET Framework 4.6 comme cible au moment de la création du projet dans la boîte de dialogue **Nouveau projet**.

Pour la sortie qui reflète le comportement des applications ciblant des versions du .NET Framework antérieures à .NET Framework 4.6, supprimez l’attribut <xref:System.Runtime.Versioning.TargetFrameworkAttribute> du code source. La sortie reflète les conventions de mise en forme de la culture du système par défaut, pas de la culture du thread appelant.

Pour plus d'informations sur les tâches asynchrones et la culture, consultez la section « Culture et opérations asynchrones basées sur les tâches » dans la rubrique <xref:System.Globalization.CultureInfo>.

## <a name="creating-task-continuations"></a>Création de continuations de tâches

Les méthodes <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Task%601.ContinueWith%2A?displayProperty=nameWithType> vous permettent de spécifier une tâche à démarrer lorsque l’*antécédent* est terminé. Une référence à la tâche antécédente est passée au délégué de la tâche de continuation afin qu’il puisse examiner l’état de la tâche antécédente et, en récupérant la valeur de la propriété <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType>, utiliser la sortie de l’antécédent comme entrée pour la continuation.

Dans l'exemple suivant, la tâche `getData` est démarrée par un appel à la méthode <xref:System.Threading.Tasks.TaskFactory.StartNew%60%601%28System.Func%7B%60%600%7D%29?displayProperty=nameWithType>. La tâche `processData` démarre automatiquement lorsque `getData` est terminé, et `displayData` commence lorsque `processData` est terminé. `getData` produit un tableau d'entiers, accessible à la tâche `processData` via la propriété `getData` de la tâche <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType>. La tâche `processData` traite ce tableau et retourne un résultat dont le type est déduit du type de retour de l'expression lambda passée à la méthode <xref:System.Threading.Tasks.Task%601.ContinueWith%60%601%28System.Func%7BSystem.Threading.Tasks.Task%7B%600%7D%2C%60%600%7D%29?displayProperty=nameWithType>. La tâche `displayData` s'exécute automatiquement lorsque `processData` est terminé, et l'objet <xref:System.Tuple%603> retourné par l'expression lambda `processData` est accessible à la tâche `displayData` via la propriété `processData` de la tâche <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType>. La tâche `displayData` prend le résultat de la tâche `processData` et produit un résultat dont le type est déduit de façon semblable et mis à disposition du programme dans la propriété <xref:System.Threading.Tasks.Task%601.Result%2A>.

[!code-csharp[TPL_TaskIntro#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/continuations1.cs#5)]
[!code-vb[TPL_TaskIntro#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/continuations1.vb#5)]

Comme <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> est une méthode d‘instance, vous pouvez concaténer les appels de méthode ensemble au lieu d‘instancier un objet <xref:System.Threading.Tasks.Task%601> pour chaque antécédent. L'exemple suivant est fonctionnellement identique à l'exemple précédent, sauf qu'il chaîne ensemble les appels à la méthode <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>. Notez que l'objet <xref:System.Threading.Tasks.Task%601> retourné par la chaîne d'appels de méthode est la tâche de continuation finale.

[!code-csharp[TPL_TaskIntro#24](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/continuations2.cs#24)]
[!code-vb[TPL_TaskIntro#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/continuations2.vb#24)]

Les méthodes <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> et <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> vous permettent de continuer avec plusieurs tâches.

Pour plus d’informations, consultez [Chaînage des tâches à l’aide de tâches de continuation](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).

## <a name="creating-detached-child-tasks"></a>Création de tâches enfants détachées

Lorsque le code utilisateur qui s'exécute dans une tâche crée une tâche sans spécifier l'option <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent>, la nouvelle tâche n'est pas synchronisée avec la tâche parent externe. Ce type de tâche non synchronisée est appelé *tâche imbriquée détachée* ou *tâche enfant détachée*. L’exemple suivant montre une tâche qui crée une tâche enfant détachée.

[!code-csharp[TPL_TaskIntro#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#07)]
[!code-vb[TPL_TaskIntro#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#07)]

Notez que la tâche parent n’attend pas que la tâche enfant détachée soit terminée.

## <a name="creating-child-tasks"></a>Création de tâches enfants

Lorsque le code utilisateur qui s’exécute dans une tâche crée une tâche avec l’option <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent>, la nouvelle tâche est une *tâche enfant attachée* de la tâche d’origine, appelée tâche parent. Vous pouvez utiliser l’option <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> pour exprimer le parallélisme des tâches structuré, car la tâche parent attend implicitement que toutes les tâches enfants attachées soient terminées. L’exemple suivant affiche une tâche parent qui crée dix tâches enfants attachées. Notez que l'exemple appelle la méthode <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> pour attendre la fin de la tâche parente, il ne doit pas explicitement attendre la fin des tâches enfants attachées.

[!code-csharp[TPL_TaskIntro#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/child1.cs#8)]
[!code-vb[TPL_TaskIntro#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/child1.vb#8)]

Une tâche parent peut utiliser l’option <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> pour empêcher d’autres tâches de s’attacher à la tâche parent. Pour plus d'informations, consultez [Tâches enfants attachées et détachées](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md).

## <a name="waiting-for-tasks-to-finish"></a>Attente de fin d’exécution de tâches

Les types <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> fournissent plusieurs surcharges des méthodes <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> qui vous permettent d’attendre qu’une tâche soit terminée. De plus, les surcharges des méthodes statiques <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> vous permettent d’attendre que certaines ou toutes les tâches soient terminées.

En général, il est nécessaire d’attendre une tâche pour l’une des raisons suivantes :

- Le thread principal dépend du résultat final calculé par une tâche.

- Vous devez gérer les exceptions pouvant être levées depuis la tâche.

- L'application peut se fermer avant que l'exécution de toutes les tâches ne soit terminée. Par exemple, les applications de console s'arrêtent dès que l'intégralité du code synchrone dans `Main` (point d'entrée de l'application) est exécutée.

L’exemple suivant affiche le modèle de base qui n’implique pas la gestion des exceptions.

[!code-csharp[TPL_TaskIntro#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_taskintro/cs/taskintro.cs#06)]
[!code-vb[TPL_TaskIntro#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_taskintro/vb/tpl_intro.vb#06)]

Pour obtenir un exemple illustrant la gestion des exceptions, consultez [Gestion des exceptions](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).

Certaines surcharges vous permettent de spécifier un délai d'attente, et d'autres prennent un <xref:System.Threading.CancellationToken> supplémentaire en tant que paramètre d'entrée, afin que l'attente puisse être annulée soit par programmation, soit en réponse à l'entrée utilisateur.

Lorsque vous attendez une tâche, vous attendez implicitement tous les enfants de cette tâche créés à l'aide de l'option <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType>. <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> est retourné immédiatement si la tâche est déjà terminée. Toutes les exceptions déclenchées par une tâche seront levées par une méthode <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, même si la méthode <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> a été appelée une fois la tâche terminée.

## <a name="composing-tasks"></a>Composition des tâches

Les classes <xref:System.Threading.Tasks.Task> et <xref:System.Threading.Tasks.Task%601> fournissent plusieurs méthodes qui peuvent vous aider à composer plusieurs tâches pour implémenter des modèles courants et améliorer l’utilisation des fonctionnalités de langage asynchrones fournies par C#, Visual Basic et F#. Cette section décrit les méthodes <xref:System.Threading.Tasks.Task.WhenAll%2A>, <xref:System.Threading.Tasks.Task.WhenAny%2A>, <xref:System.Threading.Tasks.Task.Delay%2A> et <xref:System.Threading.Tasks.Task.FromResult%2A>.

### <a name="taskwhenall"></a>Task.WhenAll

La méthode <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> attend de façon asynchrone que plusieurs objets <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> se terminent. Elle fournit des versions surchargées qui vous permettent d’attendre des ensembles de tâches non-uniformes. Par exemple, vous pouvez attendre que plusieurs objets <xref:System.Threading.Tasks.Task> et <xref:System.Threading.Tasks.Task%601> soient terminés à partir d'un appel de méthode.

### <a name="taskwhenany"></a>Task.WhenAny

La méthode <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> attend de façon asynchrone qu'un des objets <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> se termine. À l’instar de la méthode <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>, cette méthode fournit des versions surchargées qui vous permettent d’attendre des jeux de tâches non-uniformes. La méthode <xref:System.Threading.Tasks.Task.WhenAny%2A> est spécialement utile dans les scénarios suivants.

- Opérations redondantes. Considérez un algorithme ou une opération pouvant être exécutée plusieurs façons. Vous pouvez utiliser la méthode <xref:System.Threading.Tasks.Task.WhenAny%2A> pour sélectionner l'opération qui se termine en premier et annuler les opérations restantes.

- Opérations entrelacées. Vous pouvez démarrer plusieurs opérations qui doivent toutes se terminer et utiliser la méthode <xref:System.Threading.Tasks.Task.WhenAny%2A> pour traiter les résultats à mesure que chaque opération se termine. Lorsqu’une opération se termine, vous pouvez démarrer une ou plusieurs autres tâches.

- Opérations limitées. Vous pouvez utiliser la méthode <xref:System.Threading.Tasks.Task.WhenAny%2A> pour étendre le scénario précédent en limitant le nombre d'opérations simultanées.

- Opérations expirées. Vous pouvez utiliser la méthode <xref:System.Threading.Tasks.Task.WhenAny%2A> pour sélectionner entre une ou plusieurs tâches et une tâche qui se termine après une heure spécifique, telle qu’une tâche retournée par la méthode <xref:System.Threading.Tasks.Task.Delay%2A>. La méthode <xref:System.Threading.Tasks.Task.Delay%2A> est décrite dans la section suivante.

### <a name="taskdelay"></a>Task.Delay

La méthode <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> produit un objet <xref:System.Threading.Tasks.Task> qui se termine après le délai spécifié. Vous pouvez utiliser cette méthode pour générer des boucles qui, occasionnellement, sondent les données, introduisent des délais, diffèrent la gestion des entrées d'utilisateur pendant une durée prédéterminé, et ainsi de suite.

### <a name="tasktfromresult"></a>Task(T).FromResult

En utilisant la méthode <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType>, vous pouvez créer un objet <xref:System.Threading.Tasks.Task%601> qui contient un résultat précalculé. Cette méthode est utile lorsque vous exécutez une opération asynchrone qui retourne un objet <xref:System.Threading.Tasks.Task%601>, et que le résultat de cet objet <xref:System.Threading.Tasks.Task%601> est déjà calculé. Pour obtenir un exemple qui utilise <xref:System.Threading.Tasks.Task.FromResult%2A> pour récupérer les résultats des opérations de téléchargement asynchrones qui sont conservées dans un cache, consultez [Procédure : création de tâches précalculées](../../../docs/standard/parallel-programming/how-to-create-pre-computed-tasks.md).

## <a name="handling-exceptions-in-tasks"></a>Gestion des exceptions des tâches

Lorsqu’une tâche lève une ou plusieurs exceptions, les exceptions sont encapsulées dans une exception <xref:System.AggregateException>. Cette exception est propagée vers le thread joint à la tâche, qui est en général le thread qui attend la fin de la tâche, ou le thread qui accède à la propriété <xref:System.Threading.Tasks.Task%601.Result%2A>. Ce comportement permet d'appliquer la stratégie .NET Framework selon laquelle toutes les exceptions non gérées doivent par défaut détruire le processus. Le code appelant peut gérer les exceptions en utilisant l’un des éléments suivants dans un bloc `try`/`catch` :

- Méthode <xref:System.Threading.Tasks.Task.Wait%2A>

- Méthode <xref:System.Threading.Tasks.Task.WaitAll%2A>

- Méthode <xref:System.Threading.Tasks.Task.WaitAny%2A>

- La propriété <xref:System.Threading.Tasks.Task%601.Result%2A>

Le thread joint peut également gérer des exceptions en accédant à la propriété <xref:System.Threading.Tasks.Task.Exception%2A> avant que la tâche ne soit récupérée par le garbage collector. En accédant à cette propriété, vous empêchez l'exception non gérée de déclencher le comportement de propagation de l'exception qui termine le processus lorsque l'objet est finalisé.

Pour plus d’informations sur les exceptions et les tâches, consultez [Gestion des exceptions](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).

## <a name="canceling-tasks"></a>Annulation des tâches

La classe <xref:System.Threading.Tasks.Task> prend en charge l'annulation coopérative et s'intègre pleinement aux classes <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> et <xref:System.Threading.CancellationToken?displayProperty=nameWithType>, qui ont été introduites dans .NET Framework 4. De nombreux constructeurs de la classe <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> prennent un objet <xref:System.Threading.CancellationToken> en tant que paramètre d'entrée. La plupart des surcharges <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> et <xref:System.Threading.Tasks.Task.Run%2A> incluent également un paramètre <xref:System.Threading.CancellationToken>.

Vous pouvez créer le jeton et la requête d'annulation ultérieurement, à l'aide de la classe <xref:System.Threading.CancellationTokenSource>. Passez le jeton au <xref:System.Threading.Tasks.Task> en tant qu'argument et référencez ce même jeton dans votre délégué d'utilisateur, qui répond à une requête d'annulation.

Pour plus d’informations, consultez [Annulation de tâches](../../../docs/standard/parallel-programming/task-cancellation.md) et [Comment : annuler une tâche et ses enfants](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).

## <a name="the-taskfactory-class"></a>Classe TaskFactory

La classe <xref:System.Threading.Tasks.TaskFactory> fournit des méthodes statiques qui encapsulent des modèles communs pour la création et le lancement des tâches et des tâches de continuation.

- Le modèle le plus commun est <xref:System.Threading.Tasks.TaskFactory.StartNew%2A>, qui crée et lance une tâche dans une instruction.

- Lorsque vous créez des tâches de continuation à partir de plusieurs antécédents, utilisez la méthode <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> ou <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A>, ou leurs équivalents de la classe <xref:System.Threading.Tasks.Task%601>. Pour plus d’informations, consultez [Chaînage des tâches à l’aide de tâches de continuation](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).

- Pour encapsuler le modèle de programmation asynchrone `BeginX` et des méthodes `EndX` dans une instance <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>, utilisez les méthodes <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A>. Pour plus d’informations, consultez [Bibliothèque parallèle de tâches (TPL) et programmation asynchrone](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md).

<xref:System.Threading.Tasks.TaskFactory> par défaut est accessible en tant que propriété statique dans la classe <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>. Vous pouvez également instancier directement un <xref:System.Threading.Tasks.TaskFactory> et spécifier différentes options qui incluent une option <xref:System.Threading.CancellationToken>, <xref:System.Threading.Tasks.TaskCreationOptions>, <xref:System.Threading.Tasks.TaskContinuationOptions> ou <xref:System.Threading.Tasks.TaskScheduler>. Toutes les options spécifiées lors de la création de la fabrique de tâches seront appliquées à toutes les tâches qu'elle crée, à moins que la tâche <xref:System.Threading.Tasks.Task> ne soit créée à l'aide de l'énumération <xref:System.Threading.Tasks.TaskCreationOptions>, auquel cas les options de la tâche remplacent celles de la fabrique de tâches.

## <a name="tasks-without-delegates"></a>Tâches sans délégués

Dans certains cas, vous pouvez utiliser un <xref:System.Threading.Tasks.Task> pour encapsuler une opération asynchrone exécutée par un composant externe au lieu de votre propre délégué utilisateur. Si l’opération est basée sur le modèle de programmation asynchrone Begin/End, vous pouvez utiliser les méthodes <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A>. Si ce n’est pas le cas, vous pouvez utiliser l’objet <xref:System.Threading.Tasks.TaskCompletionSource%601> pour encapsuler l’opération dans une tâche et, de cette façon, bénéficier de certains des avantages de programmabilité <xref:System.Threading.Tasks.Task>, comme par exemple, la prise en charge de la propagation et des continuations d’exceptions. Pour plus d’informations, consultez <xref:System.Threading.Tasks.TaskCompletionSource%601>.

## <a name="custom-schedulers"></a>Planificateurs personnalisés

La plupart des développeurs d'applications ou de bibliothèques ne se soucient pas du processeur sur lequel s'exécute la tâche, ni de la manière dont il synchronise son travail avec d'autres tâches ou de la façon dont il est planifié sur le <xref:System.Threading.ThreadPool?displayProperty=nameWithType>. Ils demandent simplement à ce qu'il s'exécute aussi efficacement que possible sur l'ordinateur hôte. Si vous avez besoin d’un contrôle plus affiné sur les détails de la planification, la bibliothèque parallèle de tâches vous permet de configurer des paramètres dans le planificateur de tâches par défaut et vous permet même de fournir un planificateur personnalisé. Pour plus d’informations, consultez <xref:System.Threading.Tasks.TaskScheduler>.

## <a name="related-data-structures"></a>Structures de données associées

La bibliothèque parallèle de tâches possède plusieurs nouveaux types publics qui sont utiles dans les scénarios parallèles et séquentiels. Ces derniers incluent plusieurs classes de collection thread-safe, rapides et évolutives dans l'espace de noms <xref:System.Collections.Concurrent?displayProperty=nameWithType>, et plusieurs nouveaux types de synchronisation, tels que <xref:System.Threading.Semaphore?displayProperty=nameWithType> et <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, qui sont plus efficaces que leurs prédécesseurs pour certains genres de charges de travail. D'autres types nouveaux dans .NET Framework 4, tels que <xref:System.Threading.Barrier?displayProperty=nameWithType> et <xref:System.Threading.SpinLock?displayProperty=nameWithType>, fournissent des fonctionnalités qui n'étaient pas disponibles dans les versions précédentes. Pour plus d’informations, consultez [Structures de données pour la programmation parallèle](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md).

## <a name="custom-task-types"></a>Types de tâches personnalisés

Nous vous recommandons de ne pas hériter de <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> ou <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>. Nous vous recommandons d'utiliser plutôt la propriété <xref:System.Threading.Tasks.Task.AsyncState%2A> pour associer d'autres données ou états à un objet <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>. Vous pouvez également utiliser des méthodes d'extension pour étendre les fonctionnalités des classes <xref:System.Threading.Tasks.Task> et <xref:System.Threading.Tasks.Task%601>. Pour plus d’informations sur les méthodes d’extension, consultez [Méthodes d’extension](../../csharp/programming-guide/classes-and-structs/extension-methods.md) et [Méthodes d’extension](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).

Si vous devez hériter <xref:System.Threading.Tasks.Task> de <xref:System.Threading.Tasks.Task%601>ou, vous ne <xref:System.Threading.Tasks.Task.Run%2A>pouvez pas utiliser <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType>, <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType>ou les <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType> classes, ou pour créer des instances de votre type de tâche personnalisée, <xref:System.Threading.Tasks.Task> car <xref:System.Threading.Tasks.Task%601> ces mécanismes créent uniquement des objets et. En outre, vous ne pouvez pas utiliser les mécanismes de continuation des tâches fournis par <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601><xref:System.Threading.Tasks.TaskFactory> et <xref:System.Threading.Tasks.TaskFactory%601> pour créer des instances de votre type de tâche personnalisé parce que ces mécanismes créent également uniquement des objets <xref:System.Threading.Tasks.Task> et <xref:System.Threading.Tasks.Task%601>.

## <a name="related-topics"></a>Rubriques connexes

|Intitulé|Description|
|-|-|
|[Chaînage des tâches à l’aide de tâches de continuation](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md)|Décrit le fonctionnement des continuations.|
|[Tâches enfants attachées et détachées](../../../docs/standard/parallel-programming/attached-and-detached-child-tasks.md)|Décrit la différence entre les tâches enfants attachées et les tâches enfants détachées.|
|[Annulation de tâches](../../../docs/standard/parallel-programming/task-cancellation.md)|Décrit la prise en charge de l'annulation intégrée dans l'objet <xref:System.Threading.Tasks.Task>.|
|[Gestion des exceptions](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md)|Décrit comment les exceptions sur les threads simultanés sont gérées.|
|[Procédure : utiliser Parallel_Invoke pour exécuter des opérations parallèles](../../../docs/standard/parallel-programming/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Explique comment utiliser <xref:System.Threading.Tasks.Parallel.Invoke%2A>.|
|[Procédure : retourner une valeur à partir d’une tâche](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md)|Décrit comment retourner des valeurs à partir de tâches.|
|[Procédure : annuler une tâche et ses enfants](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)|Décrit comment annuler des tâches.|
|[Procédure : créer des tâches précalculées](../../../docs/standard/parallel-programming/how-to-create-pre-computed-tasks.md)|Décrit comment utiliser la méthode <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> pour récupérer les résultats d'opérations de téléchargement asynchrones qui sont conservées dans un cache.|
|[Procédure : parcourir un arbre binaire avec des tâches parallèles](../../../docs/standard/parallel-programming/how-to-traverse-a-binary-tree-with-parallel-tasks.md)|Décrit comment utiliser des tâches pour parcourir un arbre binaire.|
|[Procédure : désencapsuler une tâche imbriquée](../../../docs/standard/parallel-programming/how-to-unwrap-a-nested-task.md)|Montre également comment utiliser la méthode d'extension <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>.|
|[Parallélisme des données](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)|Décrit comment utiliser <xref:System.Threading.Tasks.Parallel.For%2A> et <xref:System.Threading.Tasks.Parallel.ForEach%2A> pour créer des boucles parallèles sur des données.|
|[Programmation parallèle](../../../docs/standard/parallel-programming/index.md)|Nœud de niveau supérieur pour la programmation parallèle .NET Framework.|

## <a name="see-also"></a>Voir aussi

- [Programmation parallèle](../../../docs/standard/parallel-programming/index.md)
- [Exemples de programmation parallèle avec .NET Core & .NET Standard](/samples/browse/?products=dotnet-core%2Cdotnet-standard&term=parallel)

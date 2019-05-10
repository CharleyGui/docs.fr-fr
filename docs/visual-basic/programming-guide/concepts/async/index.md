---
title: Programmation asynchrone avec Async et Await (Visual Basic)
ms.date: 07/20/2015
ms.assetid: bd7e462b-583b-4395-9c36-45aa9e61072c
ms.openlocfilehash: ebdec0e165902e2904ab3fcc7008a73d273354a1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64751380"
---
# <a name="asynchronous-programming-with-async-and-await-visual-basic"></a>Programmation asynchrone avec Async et Await (Visual Basic)

Vous pouvez éviter des goulots d'étranglement de performance et améliorer la réactivité globale de votre application à l'aide de la programmation asynchrone. Toutefois, les techniques traditionnelles pour écrire des applications asynchrones peuvent être complexes et rendre ces applications difficiles à écrire, déboguer et mettre à jour.

Visual Studio 2012 a introduit une approche simplifiée, la programmation async, qui tire parti de la prise en charge asynchrone de .NET Framework 4.5 et des versions ultérieures ainsi que de Windows Runtime. Le compilateur effectue le travail difficile dont se chargeait le développeur jusqu’à maintenant. En outre, votre application conserve une structure logique qui ressemble à du code synchrone. Par conséquent, vous obtenez tous les avantages de la programmation asynchrone avec peu d'effort.

Cette rubrique fournit une vue d'ensemble sur quand et comment utiliser la programmation asynchrone, et inclut des liens vers des rubriques du support, qui contiennent des informations et des exemples.

## <a name="BKMK_WhentoUseAsynchrony"></a> Async améliore la réactivité

Le comportement asynchrone est essentiel pour les activités qui sont potentiellement bloquantes, par exemple lorsque votre application accède au Web. L'accès à une ressource Web est parfois lent ou différé. Si cette activité est bloquée dans un processus synchrone, l'application entière doit attendre. Dans un processus asynchrone, l'application peut poursuivre une autre tâche qui ne dépend pas de la ressource Web jusqu'à ce que la tâche potentiellement bloquante soit terminée.

Le tableau suivant indique les zones classiques où la programmation asynchrone améliore la réactivité. Les API répertoriées de .NET Framework 4.5 et de Windows Runtime contiennent des méthodes qui prennent en charge la programmation async.

|Domaine d'application|API de prise en charge qui contiennent des méthodes async|
|----------------------|------------------------------------------------|
|Accès Web|<xref:System.Net.Http.HttpClient>, <xref:Windows.Web.Syndication.SyndicationClient>|
|Utilisation de fichiers|<xref:Windows.Storage.StorageFile>, <xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader>, <xref:System.Xml.XmlReader>|
|Utilisation d'images|<xref:Windows.Media.Capture.MediaCapture>, <xref:Windows.Graphics.Imaging.BitmapEncoder>, <xref:Windows.Graphics.Imaging.BitmapDecoder>|
|Programmation WCF|[Opérations synchrones et asynchrones](../../../../framework/wcf/synchronous-and-asynchronous-operations.md)|
|||

Le comportement asynchrone est particulièrement utile pour les applications qui accèdent au thread d'interface utilisateur, car toute activité liée à l'interface utilisateur partage généralement un thread. Si un processus est bloqué dans une application synchrone, tous les processus sont bloqués. Votre application ne répond plus et vous pouvez conclure qu'elle a rencontré une défaillance, alors qu'elle attend simplement.

Lorsque vous utilisez des méthodes asynchrones, l'application continue à répondre à l'interface utilisateur. Vous pouvez redimensionner ou réduire une fenêtre, par exemple, ou vous pouvez fermer l'application si vous ne souhaitez pas attendre qu'elle se termine.

L'approche basée sur async ajoute l'équivalent d'une transmission automatique à la liste d'options dont vous disposez pour concevoir des opérations asynchrones. En d'autres termes, vous obtenez tous les avantages de la programmation asynchrone classique mais avec beaucoup moins d'efforts du point de vue du développeur.

## <a name="BKMK_HowtoWriteanAsyncMethod"></a> Les méthodes Async sont plus faciles à écrire

Les mots clés [async](../../../../visual-basic/language-reference/modifiers/async.md) et [await](../../../../visual-basic/language-reference/modifiers/async.md) en Visual Basic sont au cœur de la programmation async. Avec ces deux mots clés, vous pouvez utiliser des ressources dans .NET Framework ou Windows Runtime pour créer une méthode asynchrone presque aussi facilement qu’une méthode synchrone. Les méthodes asynchrones définies avec `Async` et `Await` sont appelées méthodes async.

L'exemple suivant illustre une méthode async. Presque tous les éléments du code doivent vous sembler familiers. Les commentaires indiquent les fonctionnalités que vous ajoutez pour créer le comportement asynchrone.

Le fichier d’exemple complet Windows Presentation Foundation (WPF) se trouve à la fin de cette rubrique. Vous pouvez télécharger l’exemple sur [Exemple async : exemple de « Programmation asynchrone avec Async et Await »](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c).

```vb
' Three things to note in the signature:
'  - The method has an Async modifier.
'  - The return type is Task or Task(Of T). (See "Return Types" section.)
'    Here, it is Task(Of Integer) because the return statement returns an integer.
'  - The method name ends in "Async."
Async Function AccessTheWebAsync() As Task(Of Integer)

    ' You need to add a reference to System.Net.Http to declare client.
    Dim client As HttpClient = New HttpClient()

    ' GetStringAsync returns a Task(Of String). That means that when you await the
    ' task you'll get a string (urlContents).
    Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")

    ' You can do work here that doesn't rely on the string from GetStringAsync.
    DoIndependentWork()

    ' The Await operator suspends AccessTheWebAsync.
    '  - AccessTheWebAsync can't continue until getStringTask is complete.
    '  - Meanwhile, control returns to the caller of AccessTheWebAsync.
    '  - Control resumes here when getStringTask is complete.
    '  - The Await operator then retrieves the string result from getStringTask.
    Dim urlContents As String = Await getStringTask

    ' The return statement specifies an integer result.
    ' Any methods that are awaiting AccessTheWebAsync retrieve the length value.
    Return urlContents.Length
End Function
```

Si `AccessTheWebAsync` n'a aucun travail qu'il peut effectuer entre l'appel de `GetStringAsync` et l'attente de son achèvement, vous pouvez simplifier votre code en appelant et attendant dans l'instruction unique suivante.

```vb
Dim urlContents As String = Await client.GetStringAsync()
```

 Les caractéristiques suivantes résument ce qui fait de l'exemple précédent une méthode async.

- La signature de la méthode inclut un modificateur `Async`.

- Le nom d'une méthode async, par convention, se termine par un suffixe « Async ».

- Le type de retour est l'un des types suivants :

  - <xref:System.Threading.Tasks.Task%601> si votre méthode a une instruction de retour dans laquelle l'opérande a le type TResult.

  - <xref:System.Threading.Tasks.Task> si votre méthode n'a aucune instruction de retour, ou si elle a une instruction de retour sans opérande.

  - [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) si vous écrivez un gestionnaire d’événements async.

  Pour plus d’informations, consultez « Types et paramètres de retour » dans la suite de cette rubrique.

- La méthode inclut généralement au moins une expression await, qui marque le point au-delà duquel la méthode ne peut pas poursuivre son exécution tant que l'opération asynchrone attendue n'est pas terminée. Dans le même temps, la méthode est interrompue, et le contrôle retourne à l'appelant de la méthode. La section suivante de cette rubrique illustre ce qui se produit au point d'interruption.

Dans les méthodes async, vous utilisez les mots clés et les types fournis pour indiquer ce que vous souhaitez faire, et le compilateur effectue le reste, notamment le suivi de ce qui doit se produire lorsque le contrôle retourne à un point d'attente dans une méthode interrompue. Il peut être difficile de gérer des processus de routine, tels que les boucles et la gestion des exceptions, dans le code asynchrone traditionnel. Dans une méthode async, vous écrivez ces éléments comme vous l’auriez fait dans une solution synchrone, et le problème est résolu.

Pour plus d’informations sur le comportement asynchrone dans les versions antérieures de .NET Framework, consultez la page [Programmation asynchrone .NET Framework traditionnelle et TPL](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md).

## <a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a> Ce qui se produit dans une méthode Async

La chose la plus importante à comprendre en programmation asynchrone est le déplacement du flux de contrôle d'une méthode à l'autre. Le diagramme suivant vous guide à travers le processus.

![Diagramme illustrant le suivi d’un programme asynchrone.](./media/index/navigation-trace-async-program.png)

Les numéros du diagramme correspondent aux étapes suivantes.

1. Un gestionnaire d'événements appelle et attend la méthode async `AccessTheWebAsync`.

2. `AccessTheWebAsync` crée une instance <xref:System.Net.Http.HttpClient> et appelle la méthode asynchrone <xref:System.Net.Http.HttpClient.GetStringAsync%2A> pour télécharger le contenu d'un site Web comme une chaîne.

3. Quelque chose se produit dans `GetStringAsync` et suspend sa progression. Elle peut être obligée d'attendre la fin d'un téléchargement sur un site Web ou de toute autre activité bloquante. Pour éviter de bloquer les ressources, `GetStringAsync` cède le contrôle à son appelant, `AccessTheWebAsync`.

     `GetStringAsync` retourne un <xref:System.Threading.Tasks.Task%601> où TResult est une chaîne et `AccessTheWebAsync` assigne la tâche à la variable `getStringTask`. La tâche représente le processus en cours de l'appel de `GetStringAsync`, avec l'engagement de produire une valeur de chaîne réelle lorsque le travail est terminé.

4. Étant donné que `getStringTask` n'a pas encore été attendu, `AccessTheWebAsync` peut continuer avec un autre travail qui ne dépend pas du résultat final issu de `GetStringAsync`. Cette opération est représentée par un appel à la méthode synchrone `DoIndependentWork`.

5. `DoIndependentWork` est une méthode synchrone qui effectue son travail et retourne à son appelant.

6. `AccessTheWebAsync` n'a plus de travail à exécuter sans un résultat de `getStringTask`. `AccessTheWebAsync` veut ensuite calculer et retourner la longueur de la chaîne téléchargée, mais la méthode ne peut pas calculer cette valeur avant d'avoir la chaîne.

     Par conséquent, `AccessTheWebAsync` utilise un opérateur await pour interrompre sa progression et pour céder le contrôle à la méthode ayant appelé `AccessTheWebAsync`. `AccessTheWebAsync`Retourne un `Task<int>` (`Task(Of Integer)` en Visual Basic) à l’appelant. La tâche représente la promesse de produire un résultat entier qui est la longueur de la chaîne téléchargée.

    > [!NOTE]
    > Si `GetStringAsync` (et donc `getStringTask`) est terminé avant que `AccessTheWebAsync` ne l'attende, le contrôle reste dans `AccessTheWebAsync`. Le fait de suspendre, puis de retourner à `AccessTheWebAsync` ne sert à rien si le processus asynchrone appelé (`getStringTask`) s'est déjà effectué et si AccessTheWebSync n'a pas à attendre le résultat final.

     Dans l'appelant (le gestionnaire d'événements dans cet exemple), le modèle de traitement continue. L'appelant peut effectuer d'autres tâches qui ne dépendent pas du résultat de `AccessTheWebAsync` avant d'attendre ce résultat, ou l'appelant peut attendre immédiatement.   Le gestionnaire d'événements attend `AccessTheWebAsync`, et `AccessTheWebAsync` attend `GetStringAsync`.

7. `GetStringAsync` se termine et génère un résultat de chaîne. Le résultat de chaîne n'est pas retourné par l'appel de `GetStringAsync` de la façon à laquelle vous pourriez vous attendre. N’oubliez pas que la méthode a déjà retourné une tâche à l’étape 3. Au lieu de cela, la chaîne résultante est stockée dans la tâche qui représente l’achèvement de la méthode, `getStringTask`. L'opérateur await récupère le résultat de `getStringTask`. L'instruction d'assignation assigne le résultat récupéré à `urlContents`.

8. Lorsque `AccessTheWebAsync` a le résultat de chaîne, la méthode peut calculer la longueur de la chaîne. Puis, le travail d'`AccessTheWebAsync` est également interrompu, et le gestionnaire d'événements en attente peut reprendre. Dans l'exemple complet à la fin de la rubrique, vous pouvez vérifier que le gestionnaire d'événements récupère et imprime la valeur du résultat de la longueur.

Si vous débutez en programmation asynchrone, prenez une minute pour déterminer la différence entre le comportement synchrone et le comportement asynchrone. Une méthode synchrone retourne une fois son travail terminé (étape 5), mais une méthode asynchrone retourne une valeur de tâche lorsque son travail est interrompu (étapes 3 et 6). Lorsque la méthode async termine finalement son travail, la tâche est marquée comme terminée et le résultat, le cas échéant, est stocké dans la tâche.

Pour plus d’informations sur le flux de contrôle, consultez la page [Flux de contrôle dans les programmes async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).

## <a name="BKMK_APIAsyncMethods"></a> Méthodes async d’API

Vous pouvez vous demander où rechercher les méthodes telles que `GetStringAsync` qui prennent en charge la programmation async. .NET Framework 4.5 ou version ultérieure contient de nombreux membres qui fonctionnent avec `Async` et `Await`. Vous pouvez identifier ces membres par le suffixe « Async » joint au nom de membre et un type de retour <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>. Par exemple, la classe `System.IO.Stream` contient des méthodes telles que <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A> et <xref:System.IO.Stream.WriteAsync%2A> en même temps que les méthodes synchrones <xref:System.IO.Stream.CopyTo%2A>, <xref:System.IO.Stream.Read%2A> et <xref:System.IO.Stream.Write%2A>.

Windows Runtime contient également de nombreuses méthodes utilisables avec `Async` et `Await` dans les applications Windows. Pour plus d’informations et des exemples de méthodes, consultez [appeler les API asynchrones dans C# ou Visual Basic](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic), [programmation asynchrone (applications Windows Runtime)](https://docs.microsoft.com/previous-versions/windows/apps/hh464924(v=win.10)), et [WhenAny : Combler l’écart entre le .NET Framework et le Runtime Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120)).

## <a name="BKMK_Threads"></a> Threads

Les méthodes Async sont conçues pour être des opérations non bloquantes. Une expression `Await` dans une méthode async ne bloque pas le thread actuel lors de l’exécution de la tâche attendue. Au lieu de cela, l'expression inscrit le reste de la méthode comme continuation et retourne le contrôle à l'appelant de la méthode async.

Les mots clés `Async` et `Await` n’entraînent pas la création de threads supplémentaires. Les méthodes Async ne requièrent pas de multithreading, car une méthode async ne fonctionne pas sur son propre thread. La méthode s'exécute sur le contexte de synchronisation actuel et utilise du temps sur le thread uniquement lorsqu'elle est active. Vous pouvez utiliser <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> pour déplacer le travail lié au processeur vers un thread d'arrière-plan, mais un thread d'arrière-plan ne permet pas à un processus qui attend simplement les résultats de devenir disponible.

L’approche basée sur async en matière de programmation asynchrone est préférable aux approches existantes, dans presque tous les cas. En particulier, cette approche est préférable à <xref:System.ComponentModel.BackgroundWorker> pour les opérations d’e/S, car le code est plus simple et vous n’êtes pas obligé de se prémunir contre des conditions de concurrence. Combinée à <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType>, la programmation asynchrone est meilleure que <xref:System.ComponentModel.BackgroundWorker> pour les opérations utilisant le processeur de manière intensive car la programmation asynchrone sépare les détails de coordination de l'exécution de votre code à partir du travail que `Task.Run` transfère au pool de threads.

## <a name="BKMK_AsyncandAwait"></a> Async et Await

Si vous spécifiez qu’une méthode est une méthode async en utilisant un modificateur [Async](../../../../visual-basic/language-reference/modifiers/async.md), vous activez les deux fonctionnalités suivantes.

- La méthode async marquée peut utiliser [Await](../../../../visual-basic/language-reference/operators/await-operator.md) pour indiquer des points d’interruption. L'opérateur await indique au compilateur que la méthode async ne peut pas continuer au-delà de ce point, tant que le processus asynchrone attendu n'est pas terminé. Entre-temps, le contrôle retourne à l'appelant de la méthode async.

  L’interruption d’une méthode async dans une expression `Await` ne constitue pas une sortie de la méthode et les blocs `Finally` ne s’exécutent pas.

- La méthode async marquée peut elle-même être attendue par les méthodes qui l'appellent.

La méthode async contient généralement une ou plusieurs occurrences d’un opérateur `Await`, mais l’absence des expressions `Await` ne provoque pas d’erreur du compilateur. Si une méthode async n’utilise pas un opérateur `Await` pour marquer un point de sélection, elle s’exécute comme le fait une méthode synchrone, en dépit du modificateur `Async`. Le compilateur émet un avertissement pour ces méthodes.

`Async` et `Await` sont des mots clés contextuels. Pour plus d'informations et des exemples, consultez les rubriques suivantes :

- [Async](../../../../visual-basic/language-reference/modifiers/async.md)

- [Await (opérateur)](../../../../visual-basic/language-reference/operators/await-operator.md)

## <a name="BKMK_ReturnTypesandParameters"></a> Paramètres et types de retour

Dans la programmation .NET Framework, une méthode async retourne généralement un <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>. Dans une méthode async, un opérateur `Await` est appliqué à une tâche retournée à partir d’un appel à une autre méthode async.

Vous spécifiez <xref:System.Threading.Tasks.Task%601> comme type de retour si la méthode contient une instruction [Return](../../../../visual-basic/language-reference/statements/return-statement.md) qui spécifie un opérande de type `TResult`.

Vous utilisez `Task` comme type de retour si la méthode n'a aucune instruction return ou une instruction return qui ne retourne pas d'opérande.

L'exemple suivant montre comment déclarer et appeler une méthode qui retourne <xref:System.Threading.Tasks.Task%601> ou <xref:System.Threading.Tasks.Task>.

```vb
' Signature specifies Task(Of Integer)
Async Function TaskOfTResult_MethodAsync() As Task(Of Integer)

    Dim hours As Integer
    ' . . .
    ' Return statement specifies an integer result.
    Return hours
End Function

' Calls to TaskOfTResult_MethodAsync
Dim returnedTaskTResult As Task(Of Integer) = TaskOfTResult_MethodAsync()
Dim intResult As Integer = Await returnedTaskTResult
' or, in a single statement
Dim intResult As Integer = Await TaskOfTResult_MethodAsync()

' Signature specifies Task
Async Function Task_MethodAsync() As Task

    ' . . .
    ' The method has no return statement.
End Function

' Calls to Task_MethodAsync
Task returnedTask = Task_MethodAsync()
Await returnedTask
' or, in a single statement
Await Task_MethodAsync()
```

Chaque tâche retournée représente le travail en cours. Une tâche encapsule des informations sur l’état du processus asynchrone et, éventuellement, le résultat final du processus ou l’exception que le processus déclenche s’il ne réussit pas.

Une méthode async peut également être une méthode `Sub`. Ce type de retour est essentiellement utilisé pour définir les gestionnaires d’événements, où un type de retour est obligatoire. Les gestionnaires d'événements asynchrones servent souvent de point de départ aux programmes asynchrones.

Une méthode async qui est une procédure `Sub` ne peut pas être attendue, et l’appelant ne peut capturer aucune exception levée par la méthode.

Une méthode async ne peut pas déclarer de paramètres [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), mais elle peut appeler des méthodes qui comportent ces paramètres.

Pour plus d’informations ainsi que des exemples, consultez la page [Types de retour Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md). Pour plus d’informations sur l’interception des exceptions dans les méthodes async, consultez la page [Instruction Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).

Les API asynchrones dans la programmation Windows Runtime ont l’un des types de retour suivants, qui sont semblables aux tâches :

- <xref:Windows.Foundation.IAsyncOperation%601>, qui correspond à <xref:System.Threading.Tasks.Task%601>

- <xref:Windows.Foundation.IAsyncAction>, qui correspond à <xref:System.Threading.Tasks.Task>

- <xref:Windows.Foundation.IAsyncActionWithProgress%601>

- <xref:Windows.Foundation.IAsyncOperationWithProgress%602>

Pour plus d’informations et un exemple, consultez [appeler les API asynchrones en c# ou Visual Basic](/windows/uwp/threading-async/call-asynchronous-apis-in-csharp-or-visual-basic).

## <a name="BKMK_NamingConvention"></a> Convention d’affectation de noms

Par convention, on ajoute « Async » aux noms des méthodes qui possèdent un modificateur `Async`.

Vous pouvez ignorer la convention où un événement, une classe de base, ou un contrat d'interface suggère un nom différent. Par exemple, vous ne devez pas renommer les gestionnaires d'événements communs, tels que `Button1_Click`.

## <a name="BKMK_RelatedTopics"></a> Rubriques connexes et exemples (Visual Studio)

|Titre|Description|Exemple|
|-----------|-----------------|------------|
|[Procédure pas à pas : Accès Web à l’aide d’Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)|Montre comment convertir une solution WPF synchrone en une solution WPF asynchrone. L’application télécharge une série de sites web.|[Exemple Async : Accès à la procédure web](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)|
|[Guide pratique pour Étendre la procédure pas à pas Async à l’aide de Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|Ajoute <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> à la procédure précédente. L'utilisation de `WhenAll` démarre tous les téléchargements en même temps.||
|[Guide pratique pour Effectuer plusieurs requêtes Web en parallèle en utilisant Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|Explique comment démarrer plusieurs tâches en même temps.|[Exemple Async : Effectuer plusieurs requêtes web en parallèle](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)|
|[Types de retour Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)|Décrit les types que les méthodes async peuvent retourner et explique quand chaque type est approprié.||
|[Flux de contrôle dans les programmes Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)|Effectue le suivi en détail du flux de contrôle via une série d'expressions await dans un programme asynchrone.|[Exemple Async : Flux de contrôle dans les programmes Async](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)|
|[Ajuster une application Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)|Indique comment ajouter les fonctionnalités suivantes à votre solution async :<br /><br /> - [Annuler une tâche Asynch ou une liste de tâches (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)<br />- [Annuler des tâches Asynch après une période spécifique (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)<br />- [Annuler les tâches Asynch restantes lorsque l’une d’elles est terminée (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)<br />- [Démarrer plusieurs tâches Asynch et les traiter une fois terminées (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)|[Exemple Async : Réglage de votre application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)|
|[Gérer la réentrance dans Async Apps (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md)|Montre comment traiter les cas où une opération asynchrone active redémarre pendant son exécution.||
|[WhenAny : transition entre .NET Framework et Windows Runtime](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|Montre comment établir un pont entre les types de tâches du .NET Framework et IAsyncOperations dans [!INCLUDE[wrt](~/includes/wrt-md.md)] pour pouvoir utiliser <xref:System.Threading.Tasks.Task.WhenAny%2A> avec une méthode [!INCLUDE[wrt](~/includes/wrt-md.md)].|[Exemple Async : transition entre .NET et Windows Runtime (AsTask et WhenAny)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|
|Annulation Async : transition entre .NET Framework et Windows Runtime|Montre comment établir un pont entre les types de tâches du .NET Framework et IAsyncOperations dans [!INCLUDE[wrt](~/includes/wrt-md.md)] pour pouvoir utiliser <xref:System.Threading.CancellationTokenSource> avec une méthode [!INCLUDE[wrt](~/includes/wrt-md.md)].|[Exemple Async : transition entre .NET et Windows Runtime (AsTask & Annulation)](https://code.msdn.microsoft.com/Async-Sample-Bridging-9479eca3)|
|[Utiliser async pour l’accès aux fichiers (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/using-async-for-file-access.md)|Répertorie et explique les avantages de l'utilisation d'async et d'await pour accéder aux fichiers.||
|[Modèle asynchrone basé sur les tâches (TAP, Task-based Asynchronous Pattern)](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|Décrit un nouveau modèle pour le comportement asynchrone dans le .NET Framework. Le modèle est basé sur les types <xref:System.Threading.Tasks.Task> et <xref:System.Threading.Tasks.Task%601>.||
|[Vidéos Async sur Channel 9](https://channel9.msdn.com/search?term=async+&type=All)|Fournit des liens vers diverses vidéos sur la programmation asynchrone.||

## <a name="BKMK_CompleteExample"></a> Exemple complet

Le code suivant est le fichier MainWindow.xaml.vb de l’application WPF (Windows Presentation Foundation) traitée dans cette rubrique. Vous pouvez télécharger l’exemple à partir de [Exemple Async : exemple de « Programmation asynchrone avec Async et Await »](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c).

```vb
' Add an Imports statement and a reference for System.Net.Http
Imports System.Net.Http

Class MainWindow

    ' Mark the event handler with async so you can use Await in it.
    Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)

        ' Call and await separately.
        'Task<int> getLengthTask = AccessTheWebAsync();
        '' You can do independent work here.
        'int contentLength = await getLengthTask;

        Dim contentLength As Integer = Await AccessTheWebAsync()

        ResultsTextBox.Text &=
            String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)
    End Sub

    ' Three things to note in the signature:
    '  - The method has an Async modifier.
    '  - The return type is Task or Task(Of T). (See "Return Types" section.)
    '    Here, it is Task(Of Integer) because the return statement returns an integer.
    '  - The method name ends in "Async."
    Async Function AccessTheWebAsync() As Task(Of Integer)

        ' You need to add a reference to System.Net.Http to declare client.
        Dim client As HttpClient = New HttpClient()

        ' GetStringAsync returns a Task(Of String). That means that when you await the
        ' task you'll get a string (urlContents).
        Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")

        ' You can do work here that doesn't rely on the string from GetStringAsync.
        DoIndependentWork()

        ' The Await operator suspends AccessTheWebAsync.
        '  - AccessTheWebAsync can't continue until getStringTask is complete.
        '  - Meanwhile, control returns to the caller of AccessTheWebAsync.
        '  - Control resumes here when getStringTask is complete.
        '  - The Await operator then retrieves the string result from getStringTask.
        Dim urlContents As String = Await getStringTask

        ' The return statement specifies an integer result.
        ' Any methods that are awaiting AccessTheWebAsync retrieve the length value.
        Return urlContents.Length
    End Function

    Sub DoIndependentWork()
        ResultsTextBox.Text &= "Working . . . . . . ." & vbCrLf
    End Sub
End Class

' Sample Output:

' Working . . . . . . .

' Length of the downloaded string: 41763.
```

## <a name="see-also"></a>Voir aussi

- [Await (opérateur)](../../../../visual-basic/language-reference/operators/await-operator.md)
- [Async](../../../../visual-basic/language-reference/modifiers/async.md)

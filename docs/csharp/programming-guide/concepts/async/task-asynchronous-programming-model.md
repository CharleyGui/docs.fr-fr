---
title: Le modèle de programmation asynchrone de tâche (TAP) avec Async et await (C#)
description: Découvrez quand et comment utiliser la programmation asynchrone basée sur des tâches, une approche simplifiée de la programmation asynchrone en C#.
ms.date: 08/19/2020
ms.assetid: 9bcf896a-5826-4189-8c1a-3e35fa08243a
ms.openlocfilehash: 5e85b99025b31e205c66468d4bd886701cbaea17
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812084"
---
# <a name="task-asynchronous-programming-model"></a>Modèle de programmation asynchrone des tâches

Vous pouvez éviter des goulots d'étranglement de performance et améliorer la réactivité globale de votre application à l'aide de la programmation asynchrone. Toutefois, les techniques traditionnelles pour écrire des applications asynchrones peuvent être complexes et rendre ces applications difficiles à écrire, déboguer et mettre à jour.

[C# 5](../../../whats-new/csharp-version-history.md#c-version-50) a introduit une approche simplifiée, la programmation asynchrone, qui tire parti de la prise en charge asynchrone de .NET Framework 4.5 et des versions ultérieures, de .NET Core, ainsi que de Windows Runtime. Le compilateur effectue le travail difficile dont se chargeait le développeur jusqu’à maintenant. En outre, votre application conserve une structure logique qui ressemble à du code synchrone. Par conséquent, vous obtenez tous les avantages de la programmation asynchrone avec peu d'effort.

Cette rubrique fournit une vue d'ensemble sur quand et comment utiliser la programmation asynchrone, et inclut des liens vers des rubriques du support, qui contiennent des informations et des exemples.

## <a name="async-improves-responsiveness"></a><a name="BKMK_WhentoUseAsynchrony"></a> Async améliore la réactivité

Le comportement asynchrone est essentiel pour les activités qui sont potentiellement bloquantes, par exemple l’accès au web. L'accès à une ressource Web est parfois lent ou différé. Si cette activité est bloquée dans un processus synchrone, toute l’application doit attendre. Dans un processus asynchrone, l'application peut poursuivre une autre tâche qui ne dépend pas de la ressource Web jusqu'à ce que la tâche potentiellement bloquante soit terminée.

Le tableau suivant indique les zones classiques où la programmation asynchrone améliore la réactivité. Les API répertoriées de .NET et de Windows Runtime contiennent des méthodes qui prennent en charge la programmation asynchrone.

| Domaine d'application | Types .NET avec les méthodes async | Types Windows Runtime avec les méthodes async |
|--|--|--|
| Accès Web | <xref:System.Net.Http.HttpClient> | <xref:Windows.Web.Http.HttpClient?displayProperty=nameWithType> <br> <xref:Windows.Web.Syndication.SyndicationClient> |
| Utilisation de fichiers | <xref:System.Text.Json.JsonSerializer> <br> <xref:System.IO.StreamReader> <br> <xref:System.IO.StreamWriter> <br> <xref:System.Xml.XmlReader> <br> <xref:System.Xml.XmlWriter> | <xref:Windows.Storage.StorageFile> |
| Utilisation des images |  | <xref:Windows.Media.Capture.MediaCapture> <br> <xref:Windows.Graphics.Imaging.BitmapEncoder> <br> <xref:Windows.Graphics.Imaging.BitmapDecoder> |
| Programmation WCF | [Opérations synchrones et asynchrones](../../../../framework/wcf/synchronous-and-asynchronous-operations.md) |  |

Le comportement asynchrone est particulièrement utile pour les applications qui accèdent au thread d'interface utilisateur, car toute activité liée à l'interface utilisateur partage généralement un thread. Si un processus est bloqué dans une application synchrone, tous les processus sont bloqués. Votre application ne répond plus et vous pouvez conclure qu'elle a rencontré une défaillance, alors qu'elle attend simplement.

Lorsque vous utilisez des méthodes asynchrones, l'application continue à répondre à l'interface utilisateur. Vous pouvez redimensionner ou réduire une fenêtre, par exemple, ou vous pouvez fermer l'application si vous ne souhaitez pas attendre qu'elle se termine.

L'approche basée sur async ajoute l'équivalent d'une transmission automatique à la liste d'options dont vous disposez pour concevoir des opérations asynchrones. En d'autres termes, vous obtenez tous les avantages de la programmation asynchrone classique mais avec beaucoup moins d'efforts du point de vue du développeur.

## <a name="async-methods-are-easy-to-write"></a><a name="BKMK_HowtoWriteanAsyncMethod"></a> Les méthodes Async sont faciles à écrire

Les mots clés [async](../../../language-reference/keywords/async.md) et [await](../../../language-reference/operators/await.md) en C# sont au cœur de la programmation async. En utilisant ces deux mots clés, vous pouvez utiliser des ressources dans .NET Framework, .NET Core ou le Windows Runtime pour créer une méthode asynchrone presque aussi facilement que vous créez une méthode synchrone. Les méthodes asynchrones définies avec mot clé `async` sont appelées *méthodes asynchrones*.

L'exemple suivant illustre une méthode async. Presque tous les éléments du code doivent vous sembler familiers.

Vous trouverez un exemple complet de Windows Presentation Foundation (WPF) disponible en téléchargement à partir de la [programmation asynchrone avec Async et await en C#](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-cs).

:::code language="csharp" source="snippets/access-web/Program.cs" id="ControlFlow":::

Vous pouvez tirer plusieurs enseignements à partir de l’exemple précédent. Démarrez par la signature de la méthode. Elle inclut le modificateur `async`. Le type de retour est `Task<int>` (consultez la section « Types de retour » pour découvrir d’autres options). Le nom de la méthode se termine dans `Async`. Dans le corps de la méthode, `GetStringAsync` retourne un `Task<string>`. Cela signifie que quand vous attendez (`await`) la tâche, vous obtenez un `string` (`contents`). Avant d’attendre la tâche, vous pouvez effectuer tout travail qui ne repose pas sur le `string` de `GetStringAsync`.

Faites particulièrement attention à l’opérateur `await`. Il s’interrompt `GetUrlContentLengthAsync` :

- `GetUrlContentLengthAsync` ne peut pas continuer tant que `getStringTask` n’est pas terminé.
- Pendant ce temps, le contrôle retourne à l’appelant de `GetUrlContentLengthAsync`.
- Le contrôle reprend ici quand `getStringTask` est terminé.
- L’opérateur `await` récupère alors le résultat `string` auprès de `getStringTask`.

L’instruction return spécifie un résultat entier. Toutes les méthodes qui attendent `GetUrlContentLengthAsync` récupèrent la valeur de longueur.

Si `GetUrlContentLengthAsync` n'a aucun travail qu'il peut effectuer entre l'appel de `GetStringAsync` et l'attente de son achèvement, vous pouvez simplifier votre code en appelant et attendant dans l'instruction unique suivante.

```csharp
string contents = await client.GetStringAsync("https://docs.microsoft.com/dotnet");
```

Les caractéristiques suivantes résument ce qui fait de l’exemple précédent une méthode Async :

- La signature de la méthode inclut un modificateur `async`.
- Le nom d'une méthode async, par convention, se termine par un suffixe « Async ».
- Le type de retour est l’un des types suivants :

  - <xref:System.Threading.Tasks.Task%601> si votre méthode a une instruction return dans laquelle l'opérande est de type `TResult`.
  - <xref:System.Threading.Tasks.Task> si votre méthode n'a aucune instruction de retour, ou si elle a une instruction de retour sans opérande.
  - `void` si vous écrivez un gestionnaire d’événements async.
  - Tous les autres types ayant une méthode `GetAwaiter` (à compter de C# 7.0).

  Pour plus d’informations, consultez la section [types de retour et paramètres](#BKMK_ReturnTypesandParameters) .

- La méthode inclut généralement au moins une expression `await`, qui marque le point au-delà duquel la méthode ne peut pas poursuivre son exécution tant que l’opération asynchrone attendue n’est pas terminée. Dans le même temps, la méthode est interrompue, et le contrôle retourne à l'appelant de la méthode. La section suivante de cette rubrique illustre ce qui se produit au point d'interruption.

Dans les méthodes async, vous utilisez les mots clés et les types fournis pour indiquer ce que vous souhaitez faire, et le compilateur effectue le reste, notamment le suivi de ce qui doit se produire lorsque le contrôle retourne à un point d'attente dans une méthode interrompue. Il peut être difficile de gérer des processus de routine, tels que les boucles et la gestion des exceptions, dans le code asynchrone traditionnel. Dans une méthode async, vous écrivez ces éléments comme vous l’auriez fait dans une solution synchrone, et le problème est résolu.

Pour plus d’informations sur l’asynchronie dans les versions précédentes de .NET Framework, consultez [tpl et programmation asynchrone .NET Framework traditionnelle](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md).

## <a name="what-happens-in-an-async-method"></a><a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a> Ce qui se passe dans une méthode Async

La chose la plus importante à comprendre en programmation asynchrone est le déplacement du flux de contrôle d'une méthode à l'autre. Le diagramme suivant présente le processus :

:::image type="content" source="media/task-asynchronous-programming-model/navigation-trace-async-program.png" alt-text="Traçage de la navigation dans le contrôle du workflow asynchrone" lightbox="media/task-asynchronous-programming-model/navigation-trace-async-program.png":::

Les nombres dans le diagramme correspondent aux étapes suivantes, initiées lorsqu’une méthode d’appel appelle la méthode Async.

1. Une méthode d’appel appelle et attend la `GetUrlContentLengthAsync` méthode Async.

1. `GetUrlContentLengthAsync` crée une instance <xref:System.Net.Http.HttpClient> et appelle la méthode asynchrone <xref:System.Net.Http.HttpClient.GetStringAsync%2A> pour télécharger le contenu d'un site Web comme une chaîne.

1. Quelque chose se produit dans `GetStringAsync` et suspend sa progression. Elle peut être obligée d'attendre la fin d'un téléchargement sur un site Web ou de toute autre activité bloquante. Pour éviter de bloquer les ressources, `GetStringAsync` cède le contrôle à son appelant, `GetUrlContentLengthAsync`.

     `GetStringAsync` retourne un <xref:System.Threading.Tasks.Task%601>, où `TResult` est une chaîne, et `GetUrlContentLengthAsync` assigne la tâche à la variable `getStringTask`. La tâche représente le processus en cours de l'appel de `GetStringAsync`, avec l'engagement de produire une valeur de chaîne réelle lorsque le travail est terminé.

1. Étant donné que `getStringTask` n'a pas encore été attendu, `GetUrlContentLengthAsync` peut continuer avec un autre travail qui ne dépend pas du résultat final issu de `GetStringAsync`. Cette opération est représentée par un appel à la méthode synchrone `DoIndependentWork`.

1. `DoIndependentWork` est une méthode synchrone qui effectue son travail et retourne à son appelant.

1. `GetUrlContentLengthAsync` n'a plus de travail à exécuter sans un résultat de `getStringTask`. `GetUrlContentLengthAsync` veut ensuite calculer et retourner la longueur de la chaîne téléchargée, mais la méthode ne peut pas calculer cette valeur avant d'avoir la chaîne.

    Par conséquent, `GetUrlContentLengthAsync` utilise un opérateur await pour interrompre sa progression et pour céder le contrôle à la méthode ayant appelé `GetUrlContentLengthAsync`. `GetUrlContentLengthAsync` retourne un `Task<int>` à l’appelant. La tâche représente la promesse de produire un résultat entier qui est la longueur de la chaîne téléchargée.

    > [!NOTE]
    > Si `GetStringAsync` (et donc `getStringTask`) se termine avant que `GetUrlContentLengthAsync` ne l’attende, le contrôle reste dans `GetUrlContentLengthAsync`. Le coût de la suspension et du retour à est `GetUrlContentLengthAsync` gaspillé si le processus asynchrone appelé `getStringTask` est déjà terminé et `GetUrlContentLengthAsync` n’a pas besoin d’attendre le résultat final.

    À l’intérieur de la méthode d’appel, le modèle de traitement continue. L'appelant peut effectuer d'autres tâches qui ne dépendent pas du résultat de `GetUrlContentLengthAsync` avant d'attendre ce résultat, ou l'appelant peut attendre immédiatement. La méthode appelante attend `GetUrlContentLengthAsync` , et `GetUrlContentLengthAsync` attend `GetStringAsync` .

1. `GetStringAsync` se termine et génère un résultat de chaîne. Le résultat de chaîne n'est pas retourné par l'appel de `GetStringAsync` de la façon à laquelle vous pourriez vous attendre. (N'oubliez pas que la méthode a déjà retourné une tâche à l'étape 3.) Au lieu de cela, le résultat chaîne est stocké dans la tâche qui représente l'achèvement de la méthode, `getStringTask`. L'opérateur await récupère le résultat de `getStringTask`. L'instruction d'assignation assigne le résultat récupéré à `contents`.

1. Lorsque `GetUrlContentLengthAsync` a le résultat de chaîne, la méthode peut calculer la longueur de la chaîne. Puis, le travail d'`GetUrlContentLengthAsync` est également interrompu, et le gestionnaire d'événements en attente peut reprendre. Dans l'exemple complet à la fin de la rubrique, vous pouvez vérifier que le gestionnaire d'événements récupère et imprime la valeur du résultat de la longueur.
Si vous débutez en programmation asynchrone, prenez une minute pour déterminer la différence entre le comportement synchrone et le comportement asynchrone. Une méthode synchrone retourne une fois son travail terminé (étape 5), mais une méthode asynchrone retourne une valeur de tâche lorsque son travail est interrompu (étapes 3 et 6). Lorsque la méthode async termine finalement son travail, la tâche est marquée comme terminée et le résultat, le cas échéant, est stocké dans la tâche.

## <a name="api-async-methods"></a><a name="BKMK_APIAsyncMethods"></a> Méthodes Async d’API

Vous pouvez vous demander où rechercher les méthodes telles que `GetStringAsync` qui prennent en charge la programmation async. .NET Framework 4,5 ou version ultérieure et .NET Core contiennent de nombreux membres qui fonctionnent avec `async` et `await` . Vous pouvez les reconnaître par le suffixe « Async » qui est ajouté au nom de membre et par leur type de retour <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> . Par exemple, la classe `System.IO.Stream` contient des méthodes telles que <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A> et <xref:System.IO.Stream.WriteAsync%2A> en même temps que les méthodes synchrones <xref:System.IO.Stream.CopyTo%2A>, <xref:System.IO.Stream.Read%2A> et <xref:System.IO.Stream.Write%2A>.

Windows Runtime contient également de nombreuses méthodes utilisables avec `async` et `await` dans les applications Windows. Pour plus d’informations, consultez [Programmation thread et asynchrone](/windows/uwp/threading-async/) pour le développement UWP, et [Programmation asynchrone (applications Windows Store)](https://docs.microsoft.com/previous-versions/windows/apps/hh464924(v=win.10)) et [Démarrage rapide : appel d’API asynchrones en C# ou Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/hh452713(v=win.10)) si vous utilisez des versions antérieures de Windows Runtime.

## <a name="threads"></a><a name="BKMK_Threads"></a> Thèmes

Les méthodes Async sont conçues pour être des opérations non bloquantes. Une `await` expression dans une méthode Async ne bloque pas le thread actuel pendant que la tâche attendue est en cours d’exécution. Au lieu de cela, l'expression inscrit le reste de la méthode comme continuation et retourne le contrôle à l'appelant de la méthode async.

Les mots clés `async` et `await` n’entraînent pas la création de threads supplémentaires. Les méthodes Async ne requièrent pas de multithreading, car une méthode async ne fonctionne pas sur son propre thread. La méthode s'exécute sur le contexte de synchronisation actuel et utilise du temps sur le thread uniquement lorsqu'elle est active. Vous pouvez utiliser <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> pour déplacer le travail lié au processeur vers un thread d'arrière-plan, mais un thread d'arrière-plan ne permet pas à un processus qui attend simplement les résultats de devenir disponible.

L’approche basée sur async en matière de programmation asynchrone est préférable aux approches existantes, dans presque tous les cas. En particulier, cette approche est préférable à la classe <xref:System.ComponentModel.BackgroundWorker> pour les opérations utilisant de nombreuses E/S, car le code est plus simple et il est inutile de vous protéger contre des conditions de concurrence. En association avec la <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> méthode, la programmation asynchrone est meilleure que <xref:System.ComponentModel.BackgroundWorker> pour les opérations liées au processeur, car la programmation asynchrone sépare les détails de coordination de l’exécution de votre code du travail qui `Task.Run` transfère vers le pool de threads.

## <a name="async-and-await"></a><a name="BKMK_AsyncandAwait"></a> Async et await

Si vous spécifiez qu’une méthode est une méthode async en utilisant le modificateur [async](../../../language-reference/keywords/async.md), vous activez les deux fonctionnalités suivantes.

- La méthode async marquée peut utiliser [await](../../../language-reference/operators/await.md) pour indiquer des points d’interruption. L'opérateur`await` indique au compilateur que la méthode asynchrone ne peut pas continuer au-delà de ce point, tant que le processus asynchrone attendu n'est pas terminé. Entre-temps, le contrôle retourne à l'appelant de la méthode async.

     La suspension d’une méthode Async au niveau d’une `await` expression ne constitue pas une sortie de la méthode et les `finally` blocs ne s’exécutent pas.

- La méthode async marquée peut elle-même être attendue par les méthodes qui l'appellent.

Une méthode Async contient généralement une ou plusieurs occurrences d’un `await` opérateur, mais l’absence d' `await` expressions ne provoque pas d’erreur du compilateur. Si une méthode Async n’utilise pas un `await` opérateur pour marquer un point de suspension, la méthode s’exécute en tant que méthode synchrone, en dépit du `async` modificateur. Le compilateur émet un avertissement pour ces méthodes.

`async` et `await` sont des mots clés contextuels. Pour plus d'informations et pour obtenir des exemples, consultez les rubriques suivantes :

- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)

## <a name="return-types-and-parameters"></a><a name="BKMK_ReturnTypesandParameters"></a> Types de retour et paramètres

Une méthode async retourne généralement un <xref:System.Threading.Tasks.Task> ou un <xref:System.Threading.Tasks.Task%601>. Dans une méthode async, un opérateur `await` est appliqué à une tâche retournée à partir d’un appel à une autre méthode async.

Vous spécifiez <xref:System.Threading.Tasks.Task%601> comme type de retour si la méthode contient une [`return`](../../../language-reference/keywords/return.md) instruction qui spécifie un opérande de type `TResult` .

Vous utilisez <xref:System.Threading.Tasks.Task> comme type de retour si la méthode n’a aucune instruction return ou une instruction return qui ne retourne pas d’opérande.

À compter de C# 7.0, vous pouvez également spécifier n’importe quel autre type de retour, sous réserve que ce type inclue une méthode `GetAwaiter`. <xref:System.Threading.Tasks.ValueTask%601> est un exemple d’un tel type. Il est disponible dans le package NuGet [System.Threading.Tasks.Extension](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/).

L’exemple suivant montre comment déclarer et appeler une méthode qui retourne un <xref:System.Threading.Tasks.Task%601> ou un <xref:System.Threading.Tasks.Task> :

```csharp
async Task<int> GetTaskOfTResultAsync()
{
    int hours = 0;
    await Task.Delay(0);

    return hours;
}


Task<int> returnedTaskTResult = GetTaskOfTResultAsync();
int intResult = await returnedTaskTResult;
// Single line
// int intResult = await GetTaskOfTResultAsync();

async Task GetTaskAsync()
{
    await Task.Delay(0);
    // No return statement needed
}

Task returnedTask = GetTaskAsync();
await returnedTask;
// Single line
await GetTaskAsync();
```

Chaque tâche retournée représente le travail en cours. Une tâche encapsule des informations sur l’état du processus asynchrone et, éventuellement, le résultat final du processus ou l’exception que le processus déclenche s’il ne réussit pas.

Une méthode async peut également avoir un type de retour `void`. Ce type de retour est essentiellement utilisé pour définir les gestionnaires d'événements, où un type de retour `void` est obligatoire. Les gestionnaires d'événements asynchrones servent souvent de point de départ aux programmes asynchrones.

Une méthode Async qui a un `void` type de retour ne peut pas être attendue, et l’appelant d’une méthode retournant void ne peut pas intercepter les exceptions levées par la méthode.

Une méthode async ne peut pas déclarer de paramètres [in](../../../language-reference/keywords/in-parameter-modifier.md), [ref](../../../language-reference/keywords/ref.md) ou [out](../../../language-reference/keywords/out-parameter-modifier.md), mais elle peut appeler des méthodes qui ont ces paramètres. De même, une méthode async ne peut pas retourner une valeur par référence, bien qu’elle puisse appeler des méthodes avec des valeurs de retour de référence.

Pour plus d’informations et d’exemples, consultez [types de retour Async (C#)](async-return-types.md). Pour plus d’informations sur l’interception des exceptions dans les méthodes async, consultez la page [try-catch](../../../language-reference/keywords/try-catch.md).

Les API asynchrones dans la programmation Windows Runtime ont l’un des types de retour suivants, qui sont semblables aux tâches :

- <xref:Windows.Foundation.IAsyncOperation%601>, qui correspond à <xref:System.Threading.Tasks.Task%601>
- <xref:Windows.Foundation.IAsyncAction>, qui correspond à <xref:System.Threading.Tasks.Task>
- <xref:Windows.Foundation.IAsyncActionWithProgress%601>
- <xref:Windows.Foundation.IAsyncOperationWithProgress%602>

## <a name="naming-convention"></a><a name="BKMK_NamingConvention"></a> Convention d’affectation de noms

Par Convention, les méthodes qui retournent des types habituellement await (par exemple,,, `Task` `Task<T>` `ValueTask` `ValueTask<T>` ) doivent avoir des noms qui se terminent par « Async ». Les méthodes qui démarrent une opération asynchrone, mais qui ne retournent pas un type awaitable ne doivent pas avoir un nom qui se termine par « Async ». Cependant, leur nom peut commencer par « Begin », « Start » ou un autre mot suggérant que cette méthode ne retourne pas ou ne lève pas le résultat de l’opération.

Vous pouvez ignorer la convention où un événement, une classe de base, ou un contrat d'interface suggère un nom différent. Par exemple, vous ne devez pas renommer les gestionnaires d’événements communs, tels que `OnButtonClick` .

## <a name="related-topics-and-samples-visual-studio"></a><a name="BKMK_RelatedTopics"></a> Rubriques connexes et exemples (Visual Studio)

| Titre | Description | Exemple |
|--|--|--|
| [Comment effectuer plusieurs requêtes Web en parallèle en utilisant Async et await (C#)](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) | Explique comment démarrer plusieurs tâches en même temps. | [Exemple Async : effectuer plusieurs requêtes web en parallèle](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e) |
| [Types de retour Async (C#)](async-return-types.md) | Illustre les types que les méthodes Async peuvent retourner et explique quand chaque type est approprié. |  |
| Annuler les tâches avec un jeton d’annulation en tant que mécanisme de signalisation. | Indique comment ajouter les fonctionnalités suivantes à votre solution async :<br><br> - [Annuler une liste de tâches (C#)](cancel-an-async-task-or-a-list-of-tasks.md)<br>- [Annuler des tâches après une période de temps (C#)](cancel-async-tasks-after-a-period-of-time.md)<br>- [Traiter la tâche asynchrone à mesure qu’elle se termine (C#)](start-multiple-async-tasks-and-process-them-as-they-complete.md) |  |
| [Utilisation d’Async pour l’accès aux fichiers (C#)](using-async-for-file-access.md) | Répertorie et explique les avantages de l'utilisation d'async et d'await pour accéder aux fichiers. |  |
| [Modèle asynchrone basé sur les tâches (TAP)](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) | Décrit un modèle asynchrone, le modèle est basé sur les <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> types et. |  |
| [Vidéos Async sur Channel 9](https://channel9.msdn.com/search?term=async%20&type=All#pubDate=year&ch9Search&lang-en=en) | Fournit des liens vers diverses vidéos sur la programmation asynchrone. |  |

## <a name="see-also"></a>Voir aussi

- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
- [Programmation asynchrone](../../../async.md)
- [Vue d’ensemble Async](../../../../standard/async.md)

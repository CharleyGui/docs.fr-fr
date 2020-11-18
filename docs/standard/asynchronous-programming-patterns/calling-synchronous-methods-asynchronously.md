---
title: Appel de méthodes synchrones de façon asynchrone
description: Découvrez comment appeler des méthodes synchrones de façon asynchrone dans .NET, à l’aide des méthodes BeginInvoke et EndInvoke.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- asynchronous programming, delegates
- asynchronous delegates
- AsyncWaitHandle property
- callback methods
- calling synchronous methods in asynchronous manner
- WaitHandle class, code examples
- asynchronous programming, status polling
- polling asynchronous operation status
- delegates [.NET], asynchronous
- synchronous calling in asynchronous manner
- waiting for asynchronous calls
- status information [.NET], asynchronous operations
ms.assetid: 41972034-92ed-450a-9664-ab93fcc6f1fb
ms.openlocfilehash: 668ac7552289a9d1015b62ed9e68f53415dd6211
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830439"
---
# <a name="calling-synchronous-methods-asynchronously"></a>Appel de méthodes synchrones de façon asynchrone

.NET vous permet d’appeler n’importe quelle méthode de façon asynchrone. Pour ce faire, vous définissez un délégué avec la même signature que la méthode que vous souhaitez appeler. Le common language runtime définit automatiquement `BeginInvoke` les `EndInvoke` méthodes et pour ce délégué, avec les signatures appropriées.

> [!NOTE]
> Les appels de délégués asynchrones, en particulier les méthodes `BeginInvoke` et `EndInvoke` , ne sont pas pris en charge dans le .NET Compact Framework.

La méthode `BeginInvoke` lance l’appel asynchrone. Elle possède les mêmes paramètres que la méthode que vous voulez exécuter de façon asynchrone, plus deux paramètres facultatifs supplémentaires. Le premier paramètre est un délégué <xref:System.AsyncCallback> qui fait référence à une méthode appelée à la fin de l’appel asynchrone. Le deuxième paramètre est un objet défini par l’utilisateur qui transmet les informations dans la méthode de rappel. `BeginInvoke` retourne immédiatement et n’attend pas la fin de l’appel asynchrone. `BeginInvoke` retourne un <xref:System.IAsyncResult>, qui peut être utilisé pour surveiller la progression de l’appel asynchrone.

La méthode `EndInvoke` récupère les résultats de l’appel asynchrone. Elle peut être appelée à tout moment après `BeginInvoke`. Si l’appel asynchrone n’est pas terminé, `EndInvoke` bloque le thread appelant jusqu’à la fin. Les paramètres de `EndInvoke` incluent les `out` `ref` paramètres et ( `<Out>` `ByRef` et `ByRef` dans Visual Basic) de la méthode que vous souhaitez exécuter de façon asynchrone, plus le <xref:System.IAsyncResult> retourné par `BeginInvoke` .

> [!NOTE]
> La fonctionnalité IntelliSense dans Visual Studio affiche les paramètres de `BeginInvoke` et `EndInvoke`. Si vous n’utilisez pas Visual Studio ou un outil similaire, ou si vous utilisez C# avec Visual Studio, consultez [Modèle de programmation asynchrone](asynchronous-programming-model-apm.md) pour une description des paramètres définis pour ces méthodes.

Les exemples de code de cette rubrique illustrent quatre façons courantes d’utiliser `BeginInvoke` et `EndInvoke` pour effectuer des appels asynchrones. Vous pouvez effectuer les opérations suivantes après l’appel de `BeginInvoke` :

- Effectuez quelques tâches, puis appelez `EndInvoke` pour bloquer l’exécution jusqu’à la fin de l’appel.

- Obtenez un <xref:System.Threading.WaitHandle> à l’aide de la propriété <xref:System.IAsyncResult.AsyncWaitHandle%2A?displayProperty=nameWithType> , utilisez sa méthode <xref:System.Threading.WaitHandle.WaitOne%2A> pour bloquer l’exécution jusqu’à ce que <xref:System.Threading.WaitHandle> soit signalé, puis appelez `EndInvoke`.

- Interrogez le <xref:System.IAsyncResult> retourné par `BeginInvoke` pour déterminer quand l’appel asynchrone s’est terminé, puis appelez `EndInvoke`.

- Passez un délégué d’une méthode de rappel à `BeginInvoke`. La méthode est exécutée sur un thread <xref:System.Threading.ThreadPool> à la fin de l’appel asynchrone. La méthode de rappel appelle `EndInvoke`.

> [!IMPORTANT]
> Quelle que soit la technique utilisée, appelez toujours `EndInvoke` pour terminer votre appel asynchrone.

## <a name="defining-the-test-method-and-asynchronous-delegate"></a>Définition de la méthode de test et du délégué asynchrone
 Les exemples de code suivants illustrent différentes façons d’appeler la même méthode longue, `TestMethod`, de façon asynchrone. La méthode `TestMethod` affiche un message de console pour indiquer qu’elle a commencé le traitement, se met en veille pendant quelques secondes, puis se termine. `TestMethod` possède un paramètre `out` pour illustrer la façon dont ces paramètres sont ajoutés aux signatures de `BeginInvoke` et `EndInvoke`. Vous pouvez gérer les paramètres `ref` de la même façon.

 L’exemple de code suivant illustre la définition de `TestMethod` et le délégué nommé `AsyncMethodCaller` qui peut être utilisé pour appeler `TestMethod` de manière asynchrone. Pour compiler les exemples de code, vous devez inclure les définitions de `TestMethod` et le délégué `AsyncMethodCaller` .

 [!code-cpp[AsyncDelegateExamples#1](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/TestMethod.cpp#1)]
 [!code-csharp[AsyncDelegateExamples#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/TestMethod.cs#1)]
 [!code-vb[AsyncDelegateExamples#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/TestMethod.vb#1)]

## <a name="waiting-for-an-asynchronous-call-with-endinvoke"></a>Attente d’un appel asynchrone avec EndInvoke
 Le moyen le plus simple d’exécuter une méthode de manière asynchrone est de démarrer l’exécution de la méthode en appelant la méthode `BeginInvoke` du délégué, d’effectuer quelques tâches sur le thread principal, puis d’appeler la méthode `EndInvoke` du délégué. `EndInvoke` peut bloquer le thread appelant, car il ne retourne de pas résultat avant la fin de l’appel asynchrone. Cette technique est utile pour les opérations de fichier ou de réseau.

> [!IMPORTANT]
> Étant donné que `EndInvoke` peut bloquer l’exécution, ne l’appelez jamais à partir de threads qui gèrent l’interface utilisateur.

 [!code-cpp[AsyncDelegateExamples#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/EndInvoke.cpp#2)]
 [!code-csharp[AsyncDelegateExamples#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/EndInvoke.cs#2)]
 [!code-vb[AsyncDelegateExamples#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/EndInvoke.vb#2)]

## <a name="waiting-for-an-asynchronous-call-with-waithandle"></a>Attente d’un appel asynchrone avec WaitHandle
 Vous pouvez obtenir un <xref:System.Threading.WaitHandle> à l’aide de la propriété <xref:System.IAsyncResult.AsyncWaitHandle%2A> du <xref:System.IAsyncResult> retourné par `BeginInvoke`. Le <xref:System.Threading.WaitHandle> est signalé quand l’appel asynchrone se termine et vous pouvez l’attendre en appelant la méthode <xref:System.Threading.WaitHandle.WaitOne%2A> .

 Si vous utilisez un <xref:System.Threading.WaitHandle>, vous pouvez effectuer un traitement supplémentaire avant ou après la fin de l’appel asynchrone, mais avant d’appeler `EndInvoke` pour récupérer les résultats.

> [!NOTE]
> Le handle d’attente n’est pas fermé automatiquement quand vous appelez `EndInvoke`. Si vous libérez toutes les références au handle d’attente, les ressources système sont libérées quand le garbage collection récupère le handle d’attente. Pour libérer les ressources système dès que vous avez terminé d’utiliser le handle d’attente, supprimez-le en appelant la méthode <xref:System.Threading.WaitHandle.Close%2A?displayProperty=nameWithType>. Le garbage collection fonctionne plus efficacement quand les objets à supprimer le sont explicitement.

 [!code-cpp[AsyncDelegateExamples#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/waithandle.cpp#3)]
 [!code-csharp[AsyncDelegateExamples#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/waithandle.cs#3)]
 [!code-vb[AsyncDelegateExamples#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/WaitHandle.vb#3)]

## <a name="polling-for-asynchronous-call-completion"></a>Interrogation pour connaître l’état d’avancement de l’appel asynchrone
 Vous pouvez utiliser la propriété <xref:System.IAsyncResult.IsCompleted%2A> du <xref:System.IAsyncResult> retourné par `BeginInvoke` pour déterminer la fin de l’appel asynchrone. Cela est possible quand vous effectuez l’appel asynchrone à partir d’un thread qui gère l’interface utilisateur. L’interrogation pour connaître l’état d’avancement permet au thread appelant de continuer à s’exécuter pendant que l’appel asynchrone s’exécute sur un thread <xref:System.Threading.ThreadPool> .

 [!code-cpp[AsyncDelegateExamples#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/polling.cpp#4)]
 [!code-csharp[AsyncDelegateExamples#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/polling.cs#4)]
 [!code-vb[AsyncDelegateExamples#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/polling.vb#4)]

## <a name="executing-a-callback-method-when-an-asynchronous-call-completes"></a>Exécution d’une méthode de rappel à la fin d’un appel asynchrone
 Si le thread qui lance l’appel asynchrone ne doit pas nécessairement être le thread qui traite les résultats, vous pouvez exécuter une méthode de rappel à la fin de l’appel. La méthode de rappel est exécutée sur un thread <xref:System.Threading.ThreadPool> .

 Pour utiliser une méthode de rappel, vous devez transmettre `BeginInvoke` et le délégué <xref:System.AsyncCallback> qui représente la méthode de rappel. Vous pouvez également transmettre un objet contenant les informations que la méthode de rappel doit utiliser. Dans la méthode de rappel, vous pouvez convertir le <xref:System.IAsyncResult>, qui est le seul paramètre de la méthode de rappel, en objet <xref:System.Runtime.Remoting.Messaging.AsyncResult> . Vous pouvez ensuite utiliser la propriété <xref:System.Runtime.Remoting.Messaging.AsyncResult.AsyncDelegate%2A?displayProperty=nameWithType> pour obtenir le délégué utilisé pour lancer l’appel, afin de pouvoir appeler `EndInvoke`.

 Remarques sur l’exemple :

- Le `threadId` paramètre de `TestMethod` est un `out` paramètre ([ `<Out>` `ByRef` dans Visual Basic), donc sa valeur d’entrée n’est jamais utilisée par `TestMethod` . Une variable factice est transmise à l’appel `BeginInvoke` . Si le paramètre `threadId` était un paramètre `ref` (`ByRef` en Visual Basic), la variable doit être un champ de niveau classe pour pouvoir être transmise à `BeginInvoke` et `EndInvoke`.

- Les informations d’état transmises à `BeginInvoke` sont une chaîne de format, que la méthode de rappel utilise pour mettre en forme un message de sortie. Parce qu’elles sont transmises en tant que type <xref:System.Object>, les informations d’état doivent être converties en leur propre type avant de pouvoir être utilisées.

- Le rappel est effectué sur un thread <xref:System.Threading.ThreadPool> . Les threads<xref:System.Threading.ThreadPool> sont des threads d’arrière-plan qui arrêtent l’exécution de l’application si le thread principal s’arrête. Ainsi, le thread principal de l’exemple doit se mettre en veille suffisamment longtemps pour que le rappel puisse se terminer.

 [!code-cpp[AsyncDelegateExamples#5](../../../samples/snippets/cpp/VS_Snippets_CLR/AsyncDelegateExamples/cpp/callback.cpp#5)]
 [!code-csharp[AsyncDelegateExamples#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDelegateExamples/CS/callback.cs#5)]
 [!code-vb[AsyncDelegateExamples#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDelegateExamples/VB/callback.vb#5)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Delegate>
- [Modèle asynchrone basé sur les événements (EAP)](event-based-asynchronous-pattern-eap.md)

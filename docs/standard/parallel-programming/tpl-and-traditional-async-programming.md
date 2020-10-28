---
title: Bibliothèque parallèle de tâches et programmation asynchrone .NET traditionnelle
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, with other asynchronous models
ms.assetid: e7b31170-a156-433f-9f26-b1fc7cd1776f
ms.openlocfilehash: 498bde82d05259bdc561d08819d024090b0417f0
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92688015"
---
# <a name="tpl-and-traditional-net-asynchronous-programming"></a>Bibliothèque parallèle de tâches et programmation asynchrone .NET traditionnelle

.NET fournit les deux modèles standard suivants pour l’exécution d’opérations asynchrones liées aux e/s et liées aux calculs :  
  
- Modèle de programmation asynchrone (APM), dans lequel les opérations asynchrones sont représentées par une paire de méthodes Begin/End. Par exemple : <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> et <xref:System.IO.Stream.EndRead%2A?displayProperty=nameWithType>.  
  
- Le modèle asynchrone basé sur les événements (EAP), dans lequel les opérations asynchrones sont représentées par une paire méthode/événement qui sont nommées `<OperationName>Async` et `<OperationName>Completed` . Par exemple : <xref:System.Net.WebClient.DownloadStringAsync%2A?displayProperty=nameWithType> et <xref:System.Net.WebClient.DownloadStringCompleted?displayProperty=nameWithType>.
  
La bibliothèque parallèle de tâches peut être utilisée de plusieurs façons conjointement à l'un ou l'autre des modèles asynchrones. Vous pouvez exposer des opérations APM et EAP en tant qu' `Task` objets aux consommateurs de bibliothèque, ou vous pouvez exposer les modèles APM, mais utiliser des `Task` objets pour les implémenter en interne. Dans les deux scénarios, en utilisant des `Task` objets, vous pouvez simplifier le code et tirer parti des fonctionnalités utiles suivantes :  
  
- Enregistrer des rappels sous la forme de continuations de tâches, à tout moment après le lancement de la tâche.  
  
- Coordonner plusieurs opérations qui s’exécutent en réponse à une `Begin_` méthode à l’aide des <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> méthodes et, ou des <xref:System.Threading.Tasks.Task.WaitAll%2A> <xref:System.Threading.Tasks.Task.WaitAny%2A> méthodes et.  
  
- Encapsuler les opérations asynchrones d’e/s et liées au calcul dans le même `Task` objet.  
  
- Surveiller l’état de l' `Task` objet.  
  
- Marshaler l’état d’une opération vers un `Task` objet à l’aide de <xref:System.Threading.Tasks.TaskCompletionSource%601> .  
  
## <a name="wrap-apm-operations-in-a-task"></a>Encapsuler des opérations APM dans une tâche  

 Les <xref:System.Threading.Tasks.TaskFactory?displayProperty=nameWithType> classes et <xref:System.Threading.Tasks.TaskFactory%601?displayProperty=nameWithType> fournissent plusieurs surcharges des <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> méthodes et qui vous permettent d’encapsuler une paire de méthodes de programmation APM Begin/End dans une <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> instance ou. Les différentes surcharges s’adaptent à n’importe quelle paire de méthodes Begin/End comprise entre zéro et trois paramètres d’entrée.  
  
 Pour les paires qui ont des `End` méthodes qui retournent une valeur ( `Function` en Visual Basic), utilisez les méthodes de <xref:System.Threading.Tasks.TaskFactory%601> qui créent un <xref:System.Threading.Tasks.Task%601> . Pour les `End` méthodes qui retournent void (a `Sub` dans Visual Basic), utilisez les méthodes de <xref:System.Threading.Tasks.TaskFactory> qui créent un <xref:System.Threading.Tasks.Task> .  
  
 Pour les rares cas dans lesquels la méthode `Begin` a plus de trois paramètres ou contient les paramètres `ref` ou `out`, les surcharges `FromAsync` supplémentaires qui encapsulent uniquement la méthode `End` sont fournies.  
  
 L'exemple suivant montre la signature de la surcharge `FromAsync` qui correspond aux méthodes <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> et <xref:System.IO.FileStream.EndRead%2A?displayProperty=nameWithType>.
  
 [!code-csharp[FromAsync#01](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#01)]
 [!code-vb[FromAsync#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#01)]  
  
Cette surcharge prend trois paramètres d'entrée, comme suit. Le premier paramètre est un délégué <xref:System.Func%606> qui correspond à la signature de la méthode <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType>. Le deuxième paramètre est un délégué <xref:System.Func%602> qui prend un <xref:System.IAsyncResult> et retourne un `TResult`. Étant donné que <xref:System.IO.FileStream.EndRead%2A> retourne un entier, le compilateur déduit le type de `TResult` en tant que <xref:System.Int32> et le type de la tâche en tant que <xref:System.Threading.Tasks.Task>. Les quatre derniers paramètres sont identiques à ceux de la méthode <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> :  
  
- Tampon dans lequel stocker les données de fichiers.  
  
- Dans le tampon, offset à partir duquel commencer l'écriture des données.  
  
- Quantité maximale de données à lire dans le fichier.  
  
- Objet facultatif qui stocke les données d'état définies par l'utilisateur à passer au rappel.  
  
### <a name="use-continuewith-for-the-callback-functionality"></a>Utiliser ContinueWith pour la fonctionnalité de rappel

 Si vous devez accéder aux données d'un fichier, et non juste au nombre d'octets, la méthode <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> n'est pas suffisante. Utilisez plutôt <xref:System.Threading.Tasks.Task>, dont la propriété `Result` contient les données de fichier. Pour cela, ajoutez une continuation à la tâche d’origine. La continuation exécute le travail généralement effectué par le délégué <xref:System.AsyncCallback>. Elle est appelée quand l'antécédent est terminé et que le tampon de données est rempli. (L'objet <xref:System.IO.FileStream> doit être fermé avant le retour.)  
  
 L’exemple suivant montre comment retourner un <xref:System.Threading.Tasks.Task> qui encapsule la `BeginRead` / `EndRead` paire de la <xref:System.IO.FileStream> classe.  
  
 [!code-csharp[FromAsync#03](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#03)]
 [!code-vb[FromAsync#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#03)]  
  
 La méthode peut ensuite être appelée, comme suit.  
  
 [!code-csharp[FromAsync#04](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#04)]
 [!code-vb[FromAsync#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#04)]  
  
### <a name="provide-custom-state-data"></a>Fournir des données d’état personnalisées

 Dans les opérations <xref:System.IAsyncResult> typiques, si votre délégué <xref:System.AsyncCallback> a besoin de certaines données d'état personnalisées, vous devez les passer via le dernier paramètre de la méthode `Begin`, afin que les données puissent être empaquetées dans l'objet <xref:System.IAsyncResult> qui est finalement passé à la méthode de rappel. Cela n'est en général pas obligatoire quand les méthodes `FromAsync` sont utilisées. Si les données personnalisées sont connues de la continuation, elles peuvent être capturées directement dans le délégué de continuation. L'exemple suivant ressemble au précédent, mais au lieu d'examiner la propriété `Result` de la tâche antérieure, la continuation examine les données d'état personnalisées directement accessibles au délégué utilisateur de la continuation.  
  
 [!code-csharp[FromAsync#05](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#05)]
 [!code-vb[FromAsync#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#05)]  
  
### <a name="synchronize-multiple-fromasync-tasks"></a>Synchroniser plusieurs tâches FromAsync

 Les méthodes <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A> et <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAny%2A> statiques offrent une flexibilité supplémentaire en cas d'utilisation avec les méthodes `FromAsync`. L'exemple suivant montre comment initialiser plusieurs opérations d'E/S asynchrones et attendre qu'elles soient toutes terminées avant d'exécuter la continuation.  
  
 [!code-csharp[FromAsync#06](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#06)]
 [!code-vb[FromAsync#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#06)]  
  
### <a name="fromasync-tasks-for-only-the-end-method"></a>Tâches FromAsync pour la méthode end uniquement

 Pour les rares cas dans lesquels la `Begin` méthode requiert plus de trois paramètres d’entrée ou possède des `ref` `out` paramètres ou, vous pouvez utiliser les `FromAsync` surcharges, par exemple, <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%600%7D%29?displayProperty=nameWithType> qui représentent uniquement la `End` méthode. Ces méthodes peuvent également être utilisées dans n’importe quel scénario dans lequel vous avez passé un <xref:System.IAsyncResult> et souhaitez l’encapsuler dans une tâche.  
  
 [!code-csharp[FromAsync#07](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#07)]
 [!code-vb[FromAsync#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#07)]  
  
### <a name="start-and-cancel-fromasync-tasks"></a>Démarrer et annuler des tâches FromAsync

 La tâche retournée par une `FromAsync` méthode a l’état `WaitingForActivation` et est démarrée par le système à un moment donné après la création de la tâche. Si vous essayez d’appeler Start pour une telle tâche, une exception sera levée.  
  
 Vous ne pouvez pas annuler une `FromAsync` tâche, car les API .net sous-jacentes ne prennent pas en charge l’annulation en cours des e/s de fichier ou réseau. Vous pouvez ajouter des fonctionnalités d’annulation à une méthode qui encapsule un appel `FromAsync`, mais vous pouvez répondre uniquement à l’annulation avant que `FromAsync` soit appelé ou terminé (par exemple, dans une tâche de continuation).  
  
 Certaines classes prenant en charge le modèle asynchrone basé sur des événements, comme <xref:System.Net.WebClient>, prennent en charge l'annulation et vous pouvez intégrer ces fonctionnalités d'annulation native à l'aide de jetons d'annulation.  
  
## <a name="expose-complex-eap-operations-as-tasks"></a>Exposer des opérations EAP complexes en tant que tâches

 La bibliothèque parallèle de tâches ne fournit pas de méthodes conçues spécifiquement pour encapsuler une opération asynchrone basée sur des événements de la même façon que la famille `FromAsync` de méthodes encapsule le modèle <xref:System.IAsyncResult>. Toutefois, la bibliothèque parallèle de tâches fournit la classe <xref:System.Threading.Tasks.TaskCompletionSource%601?displayProperty=nameWithType>, qui peut être utilisée pour représenter tout ensemble d'opérations arbitraire tel qu'un <xref:System.Threading.Tasks.Task%601>. Les opérations peuvent être synchrones ou asynchrones et peuvent être liées aux E/S ou orientées calcul, ou les deux.  
  
 L'exemple suivant montre comment utiliser un <xref:System.Threading.Tasks.TaskCompletionSource%601> pour exposer un ensemble d'opérations <xref:System.Net.WebClient> asynchrones à du code client en tant que <xref:System.Threading.Tasks.Task%601> de base. Cette méthode vous permet d'entrer un tableau d'URL web et un terme ou nom à rechercher, puis retourne le nombre d'occurrences de ce terme ou nom sur chaque site.  
  
 [!code-csharp[FromAsync#10](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/snippet10.cs#10)]
 [!code-vb[FromAsync#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/snippet10.vb#10)]  
  
 Pour obtenir un exemple plus complet incluant une gestion supplémentaire des exceptions et indiquant comment appeler la méthode depuis le code client, consultez [Guide pratique pour exposer des modèles EAP dans une tâche](how-to-wrap-eap-patterns-in-a-task.md).  
  
 N’oubliez pas que toute tâche créée par un <xref:System.Threading.Tasks.TaskCompletionSource%601> sera démarrée par `TaskCompletionSource` et, par conséquent, le code utilisateur ne doit pas appeler la `Start` méthode sur cette tâche.  
  
## <a name="implement-the-apm-pattern-by-using-tasks"></a>Implémenter le modèle APM à l’aide de tâches

 Dans certains scénarios, il peut être souhaitable d’exposer directement le <xref:System.IAsyncResult> modèle à l’aide de paires de méthodes Begin/End dans une API. Vous pouvez, par exemple, maintenir la cohérence avec les API existantes ou posséder des outils automatisés qui nécessitent ce modèle. Dans ce cas, vous pouvez utiliser des `Task` objets pour simplifier l’implémentation en interne du modèle APM.  
  
 L’exemple suivant montre comment utiliser des tâches pour implémenter une paire de méthodes de programmation APM Begin/End pour une méthode liée à un calcul de longue durée.  
  
 [!code-csharp[FromAsync#09](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#09)]
 [!code-vb[FromAsync#09](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#09)]  
  
## <a name="use-the-streamextensions-sample-code"></a>Utiliser l’exemple de code StreamExtensions

 Le fichier *StreamExtensions.cs* , dans le référentiel [.NET standard Parallel Extensions extras](/samples/dotnet/samples/parallel-programming-extensions-extras-cs/) , contient plusieurs implémentations de référence qui utilisent `Task` des objets pour les e/s de fichier et de réseau asynchrones.
  
## <a name="see-also"></a>Voir aussi

- [Bibliothèque parallèle de tâches](task-parallel-library-tpl.md)

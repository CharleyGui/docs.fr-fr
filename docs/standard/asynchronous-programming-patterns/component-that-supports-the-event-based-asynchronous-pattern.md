---
title: 'Procédure : implémenter un composant qui prend en charge le modèle asynchrone basé sur des événements'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET], asynchronous features
- components [.NET], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 61f676b5-936f-40f6-83ce-f22805ec9c2f
ms.openlocfilehash: ef7363cd1c5161217fa4cf74dbfae9dee86fa76f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697738"
---
# <a name="how-to-implement-a-component-that-supports-the-event-based-asynchronous-pattern"></a>Procédure : implémenter un composant qui prend en charge le modèle asynchrone basé sur des événements

Si vous écrivez une classe qui comporte certaines opérations pouvant entraîner d’importants ralentissements, pensez à lui affecter des fonctionnalités asynchrones en implémentant la [Vue d’ensemble du modèle asynchrone basé sur les événements](event-based-asynchronous-pattern-overview.md).  
  
 Cette procédure pas à pas montre comment créer un composant qui applique le modèle asynchrone basé sur les événements. Il est implémenté à l’aide de classes d’assistance provenant de l’espace de noms <xref:System.ComponentModel?displayProperty=nameWithType>, ce qui garantit son bon fonctionnement quel que soit le modèle d’application, notamment ASP.NET, les applications console et les applications Windows Forms. Vous pouvez également le concevoir avec un contrôle <xref:System.Windows.Forms.PropertyGrid> et vos propres concepteurs personnalisés.  
  
 À la fin, vous disposerez d’une application qui calcule les nombres premiers de manière asynchrone. Votre application aura un thread d’interface utilisateur (IU) principal et un thread pour chaque calcul de nombres premiers. Bien qu’il puisse être long de tester si un grand nombre est un nombre premier, le thread d’UI principal ne sera pas interrompu par ce ralentissement, et le formulaire restera réactif tout au long des calculs. Vous pourrez lancer autant de calculs que vous le souhaiterez simultanément, et annuler de manière sélective des calculs en attente.  
  
 Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
- Création du composant  
  
- Définir des délégués et des événements asynchrones publics  
  
- Définir des délégués privés  
  
- Implémenter des événements publics  
  
- Implémenter la méthode d’achèvement  
  
- Implémenter les méthodes de travail  
  
- Implémenter des méthodes de démarrage et d’annulation  
  
 Pour copier le code dans cette rubrique sous la forme d’une liste unique, consultez [Comment : implémenter un client du modèle asynchrone basé sur les événements](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
## <a name="creating-the-component"></a>Création du composant  

 La première étape consiste à créer le composant qui implémentera le modèle asynchrone basé sur les événements.  
  
### <a name="to-create-the-component"></a>Pour créer le composant :  
  
- Créez une classe nommée `PrimeNumberCalculator` qui hérite de <xref:System.ComponentModel.Component>.  
  
## <a name="defining-public-asynchronous-events-and-delegates"></a>Définir des délégués et des événements asynchrones publics  

 Votre composant communique avec les clients à l’aide d’événements. L’événement _MethodName_**Completed** avertit les clients de l’achèvement d’une tâche asynchrone, et l’événement _MethodName_**ProgressChanged** les informe de la progression d’une tâche asynchrone.  
  
### <a name="to-define-asynchronous-events-for-clients-of-your-component"></a>Pour définir des événements asynchrones pour les clients de votre composant :  
  
1. Importer les espaces de noms <xref:System.Threading?displayProperty=nameWithType> et <xref:System.Collections.Specialized?displayProperty=nameWithType> en haut de votre fichier.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#11](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#11)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#11](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#11)]  
  
2. Avant la définition de la classe `PrimeNumberCalculator`, déclarez des délégués pour les événements de progression et d’achèvement.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#7](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#7)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#7](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#7)]  
  
3. Dans la définition de la classe `PrimeNumberCalculator`, déclarez des événements signalant la progression et l’achèvement aux clients.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#8](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#8)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#8](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#8)]  
  
4. Après la définition de la classe `PrimeNumberCalculator`, dérivez la classe `CalculatePrimeCompletedEventArgs` pour signaler le résultat de chaque calcul au gestionnaire d’événements du client pour l’événement `CalculatePrimeCompleted`. Outre les propriétés `AsyncCompletedEventArgs`, cette classe permet au client déterminer quel nombre a été testé, s’il est premier et, si ce n’est pas le cas, quel est le premier diviseur.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#6](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#6)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#6](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#6)]  
  
## <a name="checkpoint"></a>Point de contrôle  

 Vous pouvez maintenant générer le composant.  
  
### <a name="to-test-your-component"></a>Pour tester le composant :  
  
- Compilez le composant.  
  
     Vous recevrez deux avertissements du compilateur :  
  
    ```console  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.ProgressChanged' is never used  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.CalculatePrimeCompleted' is never used  
    ```  
  
     Ces avertissements seront effacés dans la section suivante.  
  
## <a name="defining-private-delegates"></a>Définir des délégués privés  

 Les aspects asynchrones du composant `PrimeNumberCalculator` sont implémentés en interne avec un délégué spécial appelé <xref:System.Threading.SendOrPostCallback>. <xref:System.Threading.SendOrPostCallback> représente une méthode de rappel qui s’exécute sur un thread <xref:System.Threading.ThreadPool>. Elle doit avoir une signature qui prend un seul paramètre de type <xref:System.Object>, ce qui signifie qu’il vous faudra transmettre l’état entre les délégués dans une classe wrapper. Pour plus d’informations, consultez <xref:System.Threading.SendOrPostCallback>.  
  
### <a name="to-implement-your-components-internal-asynchronous-behavior"></a>Pour implémenter le comportement asynchrone interne du composant :  
  
1. Déclarez et créez le délégué <xref:System.Threading.SendOrPostCallback> dans la classe `PrimeNumberCalculator`. Créez les objets <xref:System.Threading.SendOrPostCallback> dans une méthode utilitaire nommée `InitializeDelegates`.  
  
     Vous aurez besoin de deux délégués : un pour signaler la progression au client, l’autre pour lui signaler l’achèvement.  

     [!code-csharp[System.ComponentModel.AsyncOperationManager#9](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#9)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#9](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#9)]  
    [!code-csharp[System.ComponentModel.AsyncOperationManager#20](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#20)]
    [!code-vb[System.ComponentModel.AsyncOperationManager#20](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#20)]  
  
2. Appelez la méthode `InitializeDelegates` dans le constructeur de votre composant.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#21](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#21)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#21](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#21)]  
  
3. Déclarez un délégué dans la classe `PrimeNumberCalculator` qui gère concrètement le travail à faire de façon asynchrone. Il inclut dans un wrapper la méthode de travail qui teste si un nombre est premier. Le délégué prend un paramètre <xref:System.ComponentModel.AsyncOperation>, qui sera utilisé pour effectuer le suivi de la durée de vie de l’opération asynchrone.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#22](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#22)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#22](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#22)]  
  
4. Créez une collection pour gérer la durée de vie des opérations asynchrones en attente. Le client a besoin d’un moyen d’effectuer le suivi des opérations à l’exécution et à l’achèvement, en transmettant un ID de tâche ou un jeton unique lorsqu’il effectue l’appel à la méthode asynchrone. Le composant `PrimeNumberCalculator` doit garder la trace de chaque appel en associant l’ID de tâche à l’appel correspondant. Si le client transmet un ID de tâche non unique, le composant `PrimeNumberCalculator` doit lever une exception.  
  
     Le composant `PrimeNumberCalculator` garde la trace de l’ID de tâche à l’aide d’une classe de collection spéciale appelée <xref:System.Collections.Specialized.HybridDictionary>. Dans la définition de classe, créez un <xref:System.Collections.Specialized.HybridDictionary> nommé `userTokenToLifetime`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#23](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#23)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#23](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#23)]  
  
## <a name="implementing-public-events"></a>Implémenter des événements publics  

 Les composants qui implémentent le modèle asynchrone basé sur les événements communiquent avec les clients à l’aide d’événements. Ces événements sont appelés sur le thread adéquat à l’aide de la classe <xref:System.ComponentModel.AsyncOperation>.  
  
### <a name="to-raise-events-to-your-components-clients"></a>Pour déclencher des événements sur les clients du composant :  
  
1. Implémentez des événements publics permettant d’informer les clients. Vous aurez besoin d’un événement pour signaler la progression et d’un autre pour signaler l’achèvement.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#24](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#24)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#24](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#24)]  
  
## <a name="implementing-the-completion-method"></a>Implémenter la méthode d’achèvement  

 Le délégué d’achèvement est la méthode qui appelle le comportement asynchrone à threads libres sous-jacent lorsque l’opération asynchrone aboutit correctement, se termine par une erreur ou est annulée. Cet appel a lieu sur un thread arbitraire.  
  
 C’est dans cette méthode que l’ID de tâche du client est supprimé de la collection interne de jetons de clients uniques. Cette méthode met également fin à la durée de vie d’une opération asynchrone en particulier en appelant la méthode <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> sur la <xref:System.ComponentModel.AsyncOperation> correspondante. Cet appel déclenche l’événement d’achèvement sur le thread adapté au modèle d’application. Une fois que la méthode <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> a été appelée, cette instance de <xref:System.ComponentModel.AsyncOperation> n’est plus utilisable, et toute tentative ultérieure de l’utiliser lèvera une exception.  
  
 La signature `CompletionMethod` doit contenir tout l’état nécessaire pour décrire le résultat de l’opération asynchrone. Elle conserve l’état du nombre qui a été testé par cette opération asynchrone en particulier, l’information consistant à savoir si le nombre est premier ou non et la valeur de son premier diviseur si ce n’est pas le cas. Elle renferme également l’état décrivant les exceptions qui sont produites, et la <xref:System.ComponentModel.AsyncOperation> correspondant à cette tâche particulière.  
  
### <a name="to-complete-an-asynchronous-operation"></a>Pour achever une opération asynchrone :  
  
- Implémentez la méthode d’achèvement. Elle prend six paramètres, qu’elle utilise pour remplir un `CalculatePrimeCompletedEventArgs` qui est retourné au client par le biais du `CalculatePrimeCompletedEventHandler` du client. Elle supprime le jeton d’ID tâche du client de la collection interne et met fin à la durée de vie de l’opération asynchrone par un appel à <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>. La <xref:System.ComponentModel.AsyncOperation> marshale l’appel au thread ou au contexte adapté au modèle d'application.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#26](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#26)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#26](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#26)]  
  
## <a name="checkpoint"></a>Point de contrôle  

 Vous pouvez maintenant générer le composant.  
  
### <a name="to-test-your-component"></a>Pour tester le composant :  
  
- Compilez le composant.  
  
     Vous recevrez un avertissement du compilateur :  
  
    ```console  
    warning CS0169: The private field 'AsynchronousPatternExample.PrimeNumberCalculator.workerDelegate' is never used  
    ```  
  
     Cet avertissement sera résolu dans la section suivante.  
  
## <a name="implementing-the-worker-methods"></a>Implémenter les méthodes de travail  

 Pour le moment, vous avez implémenté le code asynchrone d’accompagnement du composant `PrimeNumberCalculator`. Vous pouvez maintenant écrire le code qui effectue concrètement le travail. Vous allez implémenter trois méthodes : `CalculateWorker`, `BuildPrimeNumberList` et `IsPrime`. Ensemble, `BuildPrimeNumberList` et `IsPrime` composent un algorithme connu, appelé le crible d'Ératosthène, qui détermine si un nombre est premier en recherchant tous les nombres premiers jusqu'à la racine carrée du nombre testé. Si aucun diviseur n’est trouvé jusque-là, le numéro testé est un nombre premier.  
  
 Si ce composant était écrit dans une optique d’efficacité maximale, il mémoriserait tous les nombres premiers découverts par différents appels sur différents nombres testés. Il vérifierait également les diviseurs triviaux, comme 2, 3 et 5. Cependant, l’objectif de cet exemple est de montrer comment exécuter des opérations longues de façon asynchrone ; nous vous laissons donc le soin d’implémenter ces optimisations pour vous exercer.  
  
 La méthode `CalculateWorker` est incluse dans un délégué et invoquée de façon asynchrone avec un appel à `BeginInvoke`.  
  
> [!NOTE]
> Le signalement de la progression est implémenté dans la méthode `BuildPrimeNumberList`. Sur les ordinateurs rapides, il est possible de déclencher les événements `ProgressChanged` à courts intervalles. Le thread du client, sur lequel ces événements sont déclenchés, doit être en mesure de gérer cette situation. Le code de l’interface utilisateur pourrait être submergé par les messages et incapable de suivre le rythme, ce qui provoquerait une absence de réponse. Vous trouverez un exemple de client qui gère cette situation sur la page [Guide pratique : implémenter un client du modèle asynchrone basé sur les événements](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
### <a name="to-execute-the-prime-number-calculation-asynchronously"></a>Pour exécuter de façon asynchrone le calcul de nombres premiers :  
  
1. Implémentez la méthode utilitaire `TaskCanceled`. Elle recherche la collection de durée de vie de la tâche pour l’ID de tâche donné, et retourne `true` si l’ID de tâche est introuvable.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#32](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#32)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#32](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#32)]  
  
2. Implémentez la méthode `CalculateWorker`. Elle prend deux paramètres : un nombre à tester et une <xref:System.ComponentModel.AsyncOperation>.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#27](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#27)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#27](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#27)]  
  
3. Implémentez `BuildPrimeNumberList`. Elle prend deux paramètres : le nombre à tester et une <xref:System.ComponentModel.AsyncOperation>. Elle utilise la <xref:System.ComponentModel.AsyncOperation> pour signaler la progression et les résultats incrémentiels. Cela garantit que les gestionnaires d’événements du client sont appelés sur le thread ou le contexte adapté au modèle d’application. Lorsque `BuildPrimeNumberList` trouve un nombre premier, elle le signale comme un résultat incrémentiel au gestionnaire d’événements du client pour l’événement `ProgressChanged`. Cela requiert une classe dérivée de <xref:System.ComponentModel.ProgressChangedEventArgs>, appelée `CalculatePrimeProgressChangedEventArgs`, possédant une propriété supplémentaire nommée `LatestPrimeNumber`.  
  
     Par ailleurs, la méthode `BuildPrimeNumberList` appelle périodiquement la méthode `TaskCanceled` et s’arrête si celle-ci retourne `true`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#5](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#5)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#5](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#5)]  
  
4. Implémentez `IsPrime`. Elle prend trois paramètres : une liste de nombres premiers connus, le nombre à tester et un paramètre de sortie pour le premier diviseur trouvé. Étant donné la liste de nombres premiers, elle détermine si le nombre testé est premier.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#28](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#28)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#28](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#28)]  
  
5. Dérivez `CalculatePrimeProgressChangedEventArgs` de <xref:System.ComponentModel.ProgressChangedEventArgs>. Cette classe est nécessaire pour signaler des résultats incrémentiels au gestionnaire d’événements du client pour l’événement `ProgressChanged`. Elle possède une propriété supplémentaire nommée `LatestPrimeNumber`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#29](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#29)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#29](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#29)]  
  
## <a name="checkpoint"></a>Point de contrôle  

 Vous pouvez maintenant générer le composant.  
  
### <a name="to-test-your-component"></a>Pour tester le composant :  
  
- Compilez le composant.  
  
     Il ne reste plus qu’à écrire les méthodes permettant de démarrer et d’annuler des opérations asynchrones, `CalculatePrimeAsync` et `CancelAsync`.  
  
## <a name="implementing-the-start-and-cancel-methods"></a>Implémenter les méthodes de démarrage et d’annulation  

 Pour démarrer la méthode de travail sur son propre thread, appelez `BeginInvoke` sur le délégué qui l’inclut. Pour gérer la durée de vie d’une opération asynchrone en particulier, vous appellerez la méthode <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> sur la classe d’assistance <xref:System.ComponentModel.AsyncOperationManager>. Cela retourne un <xref:System.ComponentModel.AsyncOperation>, qui marshale les appels sur les gestionnaires d'événements du client au thread ou au contexte adéquat.  
  
 Pour annuler une opération en attente donnée, appelez <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> sur la <xref:System.ComponentModel.AsyncOperation> correspondante. Cela met fin à cette opération, et tous les appels ultérieurs à son <xref:System.ComponentModel.AsyncOperation> lèveront une exception.  
  
### <a name="to-implement-start-and-cancel-functionality"></a>Pour implémenter les fonctionnalités de démarrage et d’annulation :  
  
1. Implémentez la méthode `CalculatePrimeAsync`. Vérifiez que le jeton fourni par le client (ID de tâche) est unique parmi tous les jetons représentant des tâches actuellement en attente. Si le client transmet un jeton non unique, `CalculatePrimeAsync` lève une exception. Sinon, le jeton est ajouté à la collection d’ID de tâche.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#3](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#3)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#3](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#3)]  
  
2. Implémentez la méthode `CancelAsync`. Si le paramètre `taskId` existe dans la collection de jetons, il est supprimé. Cela empêche l’exécution des tâches annulées qui n’ont pas démarré. Si la tâche est en cours d’exécution, la méthode `BuildPrimeNumberList` se termine lorsqu’elle détecte que l’ID de tâche a été supprimé de la collection de durées de vie.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#4](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#4)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#4](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#4)]  
  
## <a name="checkpoint"></a>Point de contrôle  

 Vous pouvez maintenant générer le composant.  
  
### <a name="to-test-your-component"></a>Pour tester le composant :  
  
- Compilez le composant.  
  
 Le composant `PrimeNumberCalculator` est maintenant terminé et prêt à être utilisé.  
  
 Vous trouverez un exemple de client qui utilise le composant `PrimeNumberCalculator` sur la page [Guide pratique : implémenter un client du modèle asynchrone basé sur les événements](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
## <a name="next-steps"></a>Étapes suivantes  

 Vous pouvez remplir cet exemple en écrivant `CalculatePrime`, l’équivalent synchrone de la méthode `CalculatePrimeAsync`. Cela rendra le composant `PrimeNumberCalculator` entièrement compatible avec le modèle asynchrone basé sur les événements.  
  
 Vous pouvez améliorer cet exemple en conservant la liste de tous les nombres premiers découverts par différents appels pour différents nombres testés. Grâce à cette approche, chaque tâche bénéficiera du travail effectué par les tâches précédentes. Veillez à protéger cette liste par des régions `lock`, afin de sérialiser l’accès à la liste par différents threads.  
  
 Vous pouvez également améliorer cet exemple en testant des diviseurs triviaux comme 2, 3 et 5.  
  
## <a name="see-also"></a>Voir aussi

- [Procédure : exécuter une opération en arrière-plan](/dotnet/desktop/winforms/controls/how-to-run-an-operation-in-the-background)
- [Vue d’ensemble du modèle asynchrone basé sur des événements](event-based-asynchronous-pattern-overview.md)
- [Modèle asynchrone basé sur les événements (EAP)](event-based-asynchronous-pattern-eap.md)

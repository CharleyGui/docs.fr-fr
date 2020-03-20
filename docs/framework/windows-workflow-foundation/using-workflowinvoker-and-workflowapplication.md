---
title: Utilisation de WorkflowInvoker et WorkflowApplication
ms.date: 03/30/2017
ms.assetid: cd0e583c-a3f9-4fa2-b247-c7b3368c48a7
ms.openlocfilehash: 5d09fc3c902b1993b32edf3e9f92393433281636
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182704"
---
# <a name="using-workflowinvoker-and-workflowapplication"></a>Utilisation de WorkflowInvoker et WorkflowApplication
Windows Workflow Foundation (WF) fournit plusieurs méthodes d’hébergement des flux de travail. <xref:System.Activities.WorkflowInvoker> offre un moyen simple pour appeler un workflow comme s'il s'agissait d'un appel de méthode et ne peut être utilisé que pour les workflows qui n'utilisent pas la persistance. <xref:System.Activities.WorkflowApplication> fournit un modèle plus riche pour exécuter des workflows, qui inclut la notification des événements de cycle de vie, le contrôle d'exécution, la modification de signet et la persistance. <xref:System.ServiceModel.Activities.WorkflowServiceHost> fournit la prise en charge des activités de messagerie et est principalement utilisé avec les services de workflow. Cette rubrique vous présente l'hébergement de workflow avec <xref:System.Activities.WorkflowInvoker> et <xref:System.Activities.WorkflowApplication>. Pour plus d’informations sur <xref:System.ServiceModel.Activities.WorkflowServiceHost>l’hébergement des flux de travail avec , voir [Workflow Services](../wcf/feature-details/workflow-services.md) et [Hosting Workflow Services Aperçu](../wcf/feature-details/hosting-workflow-services-overview.md).  
  
## <a name="using-workflowinvoker"></a>Utilisation de WorkflowInvoker  
 <xref:System.Activities.WorkflowInvoker> fournit un modèle pour l'exécution d'un workflow comme s'il s'agissait d'un appel de méthode. Pour appeler un workflow à l'aide de <xref:System.Activities.WorkflowInvoker>, appelez la méthode <xref:System.Activities.WorkflowInvoker.Invoke%2A> et passez la définition du workflow à appeler. Dans cet exemple, une activité <xref:System.Activities.Statements.WriteLine> est appelée à l'aide de <xref:System.Activities.WorkflowInvoker>.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#1)]  
  
 Lorsqu'un workflow est appelé à l'aide de <xref:System.Activities.WorkflowInvoker>, le workflow est exécuté sur le thread appelant et la méthode <xref:System.Activities.WorkflowInvoker.Invoke%2A> est bloquée jusqu'à ce que l'exécution du workflow soit terminée, durées d'inactivité comprises. Pour configurer un intervalle de délai d'attente au cours duquel le workflow doit être exécuté, utilisez l'une des surcharges de <xref:System.Activities.WorkflowInvoker.Invoke%2A> acceptant un paramètre <xref:System.TimeSpan>. Dans cet exemple, un workflow est appelé deux fois avec deux intervalles de délai d'attente différents. Le premier workflow se termine, mais pas le second.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#50](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#50)]  
  
> [!NOTE]
> <xref:System.TimeoutException> est levée uniquement si l'intervalle de délai d'attente est écoulé et que le workflow devient inactif pendant l'exécution. Un flux de travail dont le délai d'exécution dépasse l'intervalle de délai d'attente spécifié se termine correctement s'il ne devient pas inactif.  
  
 <xref:System.Activities.WorkflowInvoker> fournit également des versions asynchrones de la méthode invoke. Pour plus d’informations, consultez <xref:System.Activities.WorkflowInvoker.InvokeAsync%2A> et <xref:System.Activities.WorkflowInvoker.BeginInvoke%2A>.  
  
### <a name="setting-input-arguments-of-a-workflow"></a>Définition des arguments d’entrée d’un workflow  
 Les données peuvent être passées dans un workflow à l’aide d’un dictionnaire de paramètres d’entrée, indexés par nom d’argument, qui correspondent aux arguments d’entrée du workflow. Dans cet exemple, un <xref:System.Activities.Statements.WriteLine> est appelé et la valeur de son argument <xref:System.Activities.Statements.WriteLine.Text%2A> est spécifiée à l’aide du dictionnaire de paramètres d’entrée.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#3)]  
  
### <a name="retrieving-output-arguments-of-a-workflow"></a>Récupération des arguments de sortie d’un workflow  
 Les paramètres de sortie d'un workflow peuvent être obtenus à l'aide du dictionnaire de sorties retourné à partir de l'appel à <xref:System.Activities.WorkflowInvoker.Invoke%2A>. L’exemple suivant appelle un workflow composé d’une activité `Divide` unique qui a deux arguments d’entrée et deux arguments de sortie. Lorsque le workflow est appelé, le dictionnaire d'arguments (`arguments`) est passé ; il contient les valeurs de chaque argument d'entrée, indexées par nom d'argument. Lors du retour de l'appel à `Invoke`, chaque argument de sortie, également indexé par nom d'argument, est retourné dans le dictionnaire `outputs`.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#120](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#120)]  
  
 [!code-csharp[CFX_WorkflowInvokerExample#20](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#20)]  
  
 Si le workflow dérive de <xref:System.Activities.ActivityWithResult>, par exemple `CodeActivity<TResult>` ou `Activity<TResult>`, et qu’il existe des arguments de sortie en plus des arguments de sortie <xref:System.Activities.Activity%601.Result%2A> correctement définis, une surcharge non générique de `Invoke` doit être utilisée pour récupérer les arguments supplémentaires. Pour ce faire, la définition de workflow passée dans `Invoke` doit être de type <xref:System.Activities.Activity>. Dans cet exemple l'activité `Divide` dérive de `CodeActivity<int>`, mais est déclarée comme <xref:System.Activities.Activity> afin qu'une surcharge non générique de `Invoke` soit utilisée, qui retourne un dictionnaire d'arguments au lieu d'une valeur de retour unique.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#121](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#121)]  
  
 [!code-csharp[CFX_WorkflowInvokerExample#21](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#21)]  
  
## <a name="using-workflowapplication"></a>Utilisation de WorkflowApplication  
 <xref:System.Activities.WorkflowApplication> fournit un ensemble complet de fonctionnalités pour la gestion d'instance du workflow. <xref:System.Activities.WorkflowApplication> joue le rôle d'un proxy thread-safe pour le <xref:System.Activities.Hosting.WorkflowInstance> réel, qui encapsule l'exécution et fournit des méthodes pour la création et le chargement d'instances de workflow, l'interruption et la reprise, l'arrêt et la notification des événements du cycle de vie. Pour exécuter un workflow à l'aide de <xref:System.Activities.WorkflowApplication>, créez le <xref:System.Activities.WorkflowApplication>, abonnez-vous à tous les événements de cycle de vie souhaités, démarrez le workflow, puis attendez la fin de son exécution. Dans cet exemple, une définition de workflow constituée d'une activité <xref:System.Activities.Statements.WriteLine> est créée et un <xref:System.Activities.WorkflowApplication> est créé en utilisant la définition spécifiée de workflow. <xref:System.Activities.WorkflowApplication.Completed%2A> est géré afin que l'hôte soit informé lorsque le workflow se termine, le workflow démarre par un appel à <xref:System.Activities.WorkflowApplication.Run%2A>, puis l'hôte attend que le workflow se termine. Lorsque le workflow est terminé, le <xref:System.Threading.AutoResetEvent> est défini et l'application hôte peut reprendre l'exécution, comme indiqué dans l'exemple suivant.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#31](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#31)]  
  
### <a name="workflowapplication-lifecycle-events"></a>Événements de cycle de vie WorkflowApplication  
 En plus de <xref:System.Activities.WorkflowApplication.Completed%2A>, les auteurs d'hôte peuvent être avertis lorsqu'un workflow est déchargé (<xref:System.Activities.WorkflowApplication.Unloaded%2A>), est abandonné (<xref:System.Activities.WorkflowApplication.Aborted%2A>), devient inactif (<xref:System.Activities.WorkflowApplication.Idle%2A> et <xref:System.Activities.WorkflowApplication.PersistableIdle%2A>), ou qu'une exception non gérée se produit (<xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>). Les développeurs d'applications de workflow peuvent gérer ces notifications et agir en conséquence, comme indiqué dans l'exemple suivant.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#32](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#32)]  
  
### <a name="setting-input-arguments-of-a-workflow"></a>Définition des arguments d’entrée d’un workflow  
 Les données peuvent être passées dans un workflow comme il est démarré à l'aide d'un dictionnaire de paramètres, de la même façon que les données sont passées lors de l'utilisation de <xref:System.Activities.WorkflowInvoker>. Chaque élément dans le dictionnaire correspond à un argument d’entrée du workflow spécifié. Dans cet exemple, un workflow qui consiste en une activité <xref:System.Activities.Statements.WriteLine> est appelé et son argument <xref:System.Activities.Statements.WriteLine.Text%2A> est spécifié à l’aide du dictionnaire de paramètres d’entrée.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#30](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#30)]  
  
### <a name="retrieving-output-arguments-of-a-workflow"></a>Récupération des arguments de sortie d’un workflow  
 Lorsque l’exécution d’un workflow est terminée, tous les arguments de sortie peuvent être récupérés dans le gestionnaire <xref:System.Activities.WorkflowApplication.Completed%2A> en accédant au dictionnaire <xref:System.Activities.WorkflowApplicationCompletedEventArgs.Outputs%2A?displayProperty=nameWithType>. L'exemple suivant héberge un workflow à l'aide de <xref:System.Activities.WorkflowApplication>. Une <xref:System.Activities.WorkflowApplication> instance est construite à l’aide `DiceRoll` d’une définition de flux de travail consistant en une seule activité. L’activité `DiceRoll` a deux arguments de sortie qui représentent les résultats du jet de dés. Lorsque le workflow se termine, les sorties sont récupérées dans le gestionnaire <xref:System.Activities.WorkflowApplication.Completed%2A>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#130](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#130)]  
  
 [!code-csharp[CFX_WorkflowApplicationExample#21](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#21)]  
  
> [!NOTE]
> <xref:System.Activities.WorkflowApplication> et <xref:System.Activities.WorkflowInvoker> prennent un dictionnaire d'arguments d'entrée et retournent un dictionnaire d'arguments `out`. Ces paramètres de dictionnaire, propriétés et valeurs de retour sont de type `IDictionary<string, object>`. L'instance réelle de la classe de dictionnaire qui est passée peut être toute classe qui implémente `IDictionary<string, object>`. Dans ces exemples, `Dictionary<string, object>` est utilisé. Pour plus d’informations sur <xref:System.Collections.Generic.IDictionary%602> <xref:System.Collections.Generic.Dictionary%602>les dictionnaires, voir et .  
  
### <a name="passing-data-into-a-running-workflow-using-bookmarks"></a>Passage de données dans un workflow en cours d'exécution à l'aide de signets  
 Les signets sont le mécanisme par lequel une activité peut attendre passivement d'être reprise et un mécanisme pour le passage de données dans une instance de workflow en cours d'exécution. Si une activité attend des données, elle peut créer un <xref:System.Activities.Bookmark> et inscrire une méthode de rappel à appeler lorsque le <xref:System.Activities.Bookmark> est repris, comme indiqué dans l'exemple suivant.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
 Lors de l'exécution, l'activité `ReadLine` crée un <xref:System.Activities.Bookmark>, inscrit un rappel, puis attend la reprise du <xref:System.Activities.Bookmark>. Lors de la reprise, l'activité `ReadLine` affecte les données passées avec le <xref:System.Activities.Bookmark> à son argument <xref:System.Activities.Activity%601.Result%2A>. Dans cet exemple, un workflow qui utilise l'activité `ReadLine` pour rassembler le nom de l'utilisateur et l'afficher dans la fenêtre de console est créé.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#22](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#22)]  
  
 Lorsque l'activité `ReadLine` est exécutée, elle crée un <xref:System.Activities.Bookmark> nommé `UserName`, puis attend la reprise du signet. L'hôte recueille les données voulues, puis reprend le <xref:System.Activities.Bookmark>. Le workflow reprend, affiche le nom, puis se termine.  
  
 L'application hôte peut inspecter le workflow pour déterminer la présence de signets actifs. Pour ce faire, elle peut appeler la méthode <xref:System.Activities.WorkflowApplication.GetBookmarks%2A> d'une instance <xref:System.Activities.WorkflowApplication> ou inspecter le <xref:System.Activities.WorkflowApplicationIdleEventArgs> dans le gestionnaire <xref:System.Activities.WorkflowApplication.Idle%2A>.  
  
 L'exemple de code suivant est semblable à l'exemple précédent, mais les signets actifs sont énumérés avant la reprise du signet. Le workflow démarre et, une fois que <xref:System.Activities.Bookmark> est créé et que le workflow est inactif, la méthode <xref:System.Activities.WorkflowApplication.GetBookmarks%2A> est appelée. Lorsque le flux de travail est terminé, la sortie suivante s'affiche sur la console.  
  
 **Comment vous appelez-vous ?**  
**BookmarkName: UserName - OwnerDisplayName: ReadLine**
**Steve**
**Hello, Steve**

[!code-csharp[CFX_WorkflowApplicationExample#14](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#14)]  
  
 L'exemple de code suivant inspecte l'objet <xref:System.Activities.WorkflowApplicationIdleEventArgs> passé dans le gestionnaire <xref:System.Activities.WorkflowApplication.Idle%2A> d'une instance de <xref:System.Activities.WorkflowApplication>. Dans cet exemple, le workflow qui devient inactif comporte un <xref:System.Activities.Bookmark> portant le nom `EnterGuess` et appartenant à une activité nommée `ReadInt`. Cet exemple de code est basé sur [How to: Run a Workflow](how-to-run-a-workflow.md), qui fait partie du [tutoriel Getting Started](getting-started-tutorial.md). Si le gestionnaire <xref:System.Activities.WorkflowApplication.Idle%2A> utilisé dans cette étape est modifié de façon à contenir le code de cet exemple, la sortie suivante s'affiche.  
  
 **BookmarkName: EnterGuess - OwnerDisplayName: ReadInt**

 [!code-csharp[CFX_WorkflowApplicationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#2)]  
  
## <a name="summary"></a>Résumé  
 <xref:System.Activities.WorkflowInvoker> offre un moyen simplifié d'appeler des workflows et, bien qu'il fournisse des méthodes pour le passage des données au début d'un workflow et l'extraction de données d'un workflow terminé, il ne prévoit pas de scénarios plus complexes dans lesquels <xref:System.Activities.WorkflowApplication> peut être utilisé.

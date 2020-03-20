---
title: Modélisation du comportement d'annulation dans les workflows
ms.date: 03/30/2017
ms.assetid: d48f6cf3-cdde-4dd3-8265-a665acf32a03
ms.openlocfilehash: 8738afa838f1d0ca36b7fd6def00f0794bcf47ac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143042"
---
# <a name="modeling-cancellation-behavior-in-workflows"></a>Modélisation du comportement d'annulation dans les workflows
Les activités peuvent être annulées à l’intérieur d’un workflow, par exemple par une activité <xref:System.Activities.Statements.Parallel> qui annule des branches incomplètes lorsque son <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> a la valeur `true`, ou à l’extérieur du workflow, si l’hôte appelle <xref:System.Activities.WorkflowApplication.Cancel%2A>. Pour fournir la gestion des annulations, les auteurs de workflow peuvent utiliser l'activité <xref:System.Activities.Statements.CancellationScope>, l'activité <xref:System.Activities.Statements.CompensableActivity> ou créer des activités personnalisées qui fournissent la logique d'annulation. Cette rubrique fournit une vue d'ensemble de l'annulation dans les workflows.  
  
## <a name="cancellation-compensation-and-transactions"></a>Annulation, compensation et transactions  
 Les transactions permettent à votre application d'annuler (restaurer) toute modification exécutée dans une transaction en cas d'erreur au cours du processus de transaction. Toutefois, le travail qui peut devoir être annulé n’est pas dans sa totalité approprié pour les transactions, tel que le travail de longue durée ou le travail qui n’implique pas de ressources transactionnelles. La compensation fournit un modèle pour l'annulation de travail non transactionnel précédemment effectué en cas d'échec ultérieur dans le workflow. L’annulation fournit un modèle pour les auteurs de workflow et d’activité pour gérer le travail non transactionnel qui n’a pas été effectué. Si une activité n'a pas terminé son exécution et est annulée, sa logique d'annulation sera appelée si elle est disponible.  
  
> [!NOTE]
> Pour plus d’informations sur les transactions et la rémunération, voir [Transactions](workflow-transactions.md) et [Rémunération](compensation.md).  
  
## <a name="using-cancellationscope"></a>Utilisation de CancellationScope  
 L'activité <xref:System.Activities.Statements.CancellationScope> a deux sections qui peuvent contenir des activités enfants : <xref:System.Activities.Statements.CancellationScope.Body%2A> et <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>. Le <xref:System.Activities.Statements.CancellationScope.Body%2A> est l'endroit où les activités qui composent la logique de l'activité sont placées et le <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> est l'endroit où les activités qui fournissent la logique d'annulation pour l'activité sont placées. Une activité peut être annulée uniquement si elle n'est pas terminée. Dans le cas de l'activité <xref:System.Activities.Statements.CancellationScope>, l'achèvement fait référence à l'achèvement des activités dans le <xref:System.Activities.Statements.CancellationScope.Body%2A>. Si une demande d'annulation est planifiée et que les activités dans le <xref:System.Activities.Statements.CancellationScope.Body%2A> ne sont pas terminées, le <xref:System.Activities.Statements.CancellationScope> sera marqué comme <xref:System.Activities.ActivityInstanceState.Canceled> et les activités <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> seront exécutées.  
  
### <a name="canceling-a-workflow-from-the-host"></a>Annulation d'un workflow à partir de l'hôte  
 Un hôte peut annuler un workflow en appelant la méthode <xref:System.Activities.WorkflowApplication.Cancel%2A> de l'instance <xref:System.Activities.WorkflowApplication> qui héberge le workflow. Dans l'exemple suivant, un workflow avec un <xref:System.Activities.Statements.CancellationScope> est créé. Le workflow est appelé, puis l'hôte passe un appel au <xref:System.Activities.WorkflowApplication.Cancel%2A>. L'exécution principale du workflow est arrêtée, le <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> du <xref:System.Activities.Statements.CancellationScope> est appelé, puis le workflow se termine avec l'état <xref:System.Activities.ActivityInstanceState.Canceled>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#35](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#35)]  
  
 Lorsque ce workflow est appelé, la sortie suivante s'affiche sur la console.  
  
 **Démarrage du flux de travail.**  
**AnnulationHandler invoqué.** 
 **Workflow b30ebb30-df46-4d90-a211-e31c38d8db3c Annulé.**
> [!NOTE]
> Lorsqu'une activité <xref:System.Activities.Statements.CancellationScope> est annulée et que le <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> est appelé, il incombe à l'auteur de workflow de déterminer la progression effectuée par l'activité avant son annulation afin de fournir la logique d'annulation appropriée. Le <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> ne fournit aucune information sur la progression de l'activité annulée.  
  
 Un workflow peut également être annulé à partir de l'hôte si une exception non gérée est propagée au-delà de la racine du workflow et que le gestionnaire <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> retourne <xref:System.Activities.UnhandledExceptionAction.Cancel>. Dans cet exemple, le workflow démarre, puis lève un <xref:System.ApplicationException>. Cette exception n'étant pas prise en charge par le workflow, le gestionnaire <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> est appelé. Le gestionnaire indique à l'exécution d'annuler le workflow et le <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> de l'activité <xref:System.Activities.Statements.CancellationScope> actuellement en cours d'exécution est appelé.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#36](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#36)]  
  
 Lorsque ce workflow est appelé, la sortie suivante s'affiche sur la console.  
  
 **Démarrage du flux de travail.**  
**OnUnhandledException in Workflow 6bb2d5d6-f49a-4c6d-a988-478afb86dbe9**
**An ApplicationException was thrown.** 
 **AnnulationHandler invoqué.** 
 **Workflow 6bb2d5d6-f49a-4c6d-a988-478afb86dbe9 Annulé.**
### <a name="canceling-an-activity-from-inside-a-workflow"></a>Annulation d'une activité à l'intérieur d'un workflow  
 Une activité peut également être annulée par son parent. Par exemple, si une activité <xref:System.Activities.Statements.Parallel> a plusieurs branches en cours d’exécution et que son <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> a la valeur `true`, ses branches incomplètes seront annulées. Dans cet exemple, une activité <xref:System.Activities.Statements.Parallel> avec deux branches est créée. Son <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> ayant la valeur `true`, le <xref:System.Activities.Statements.Parallel> est effectué dès que l’une de ses branches est terminée. Dans cet exemple, la branche 2 étant terminée, la branche 1 est annulée.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#37](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#37)]  
  
 Lorsque ce workflow est appelé, la sortie suivante s'affiche sur la console.  
  
 **Branche 1 à partir.**  
**Branche 2 complète.** 
 **Branche 1 annulée.** 
 **Workflow e0685e24-18ef-4a47-acf3-5c638732f3be Terminé.**  Les activités sont également annulées si une exception est propagée au-delà de la racine de l'activité, mais est gérée à un niveau supérieur dans le workflow. Dans cet exemple, la logique principale du workflow se compose d'une activité <xref:System.Activities.Statements.Sequence>. Le <xref:System.Activities.Statements.Sequence> est spécifié comme <xref:System.Activities.Statements.CancellationScope.Body%2A> d'une activité <xref:System.Activities.Statements.CancellationScope> contenue dans une activité <xref:System.Activities.Statements.TryCatch>. Une exception est levée à partir du corps du <xref:System.Activities.Statements.Sequence>, est gérée par l'activité <xref:System.Activities.Statements.TryCatch> parente et le <xref:System.Activities.Statements.Sequence> est annulé.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#39](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#39)]  
  
 Lorsque ce workflow est appelé, la sortie suivante s'affiche sur la console.  
  
 **Sequence starting.**  
**Séquence annulée.** 
 **Exception attrapée.** 
 **Workflow e3c18939-121e-4c43-af1c-ba1ce977ce55 Terminé.**
### <a name="throwing-exceptions-from-a-cancellationhandler"></a>Levée d'exceptions à partir d'un CancellationHandler  
 Toutes les exceptions levées à partir du <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> d'un <xref:System.Activities.Statements.CancellationScope> sont irrécupérables pour le workflow. S'il existe une possibilité pour les exceptions d'échapper à un <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>, utilisez un <xref:System.Activities.Statements.TryCatch> dans le <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> pour intercepter et gérer ces exceptions.  
  
### <a name="cancellation-using-compensableactivity"></a>Annulation à l'aide de CompensableActivity  
 Comme l'activité <xref:System.Activities.Statements.CancellationScope>, le <xref:System.Activities.Statements.CompensableActivity> a un <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>. Si un <xref:System.Activities.Statements.CompensableActivity> est annulé, toutes les activités dans son <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> sont appelées. Cela peut être utile pour l'annulation de travail compensable partiellement effectué. Pour plus d’informations sur la façon d’utiliser <xref:System.Activities.Statements.CompensableActivity> pour l’indemnisation et l’annulation, voir [Compensation](compensation.md).  
  
## <a name="cancellation-using-custom-activities"></a>Annulation à l'aide d'activités personnalisées  
 Les auteurs d'activités personnalisés peuvent implémenter une logique d'annulation dans leurs activités personnalisées de plusieurs façons différentes. Les activités personnalisées qui dérivent de <xref:System.Activities.Activity> peuvent implémenter la logique d'annulation en plaçant <xref:System.Activities.Statements.CancellationScope> ou une autre activité personnalisée qui contient la logique d'annulation dans le corps de l'activité. Les activités dérivées <xref:System.Activities.AsyncCodeActivity> et <xref:System.Activities.NativeActivity> peuvent remplacer leur méthode correspondante <xref:System.Activities.NativeActivity.Cancel%2A> et fournir la logique d'annulation à cet endroit. Les activités dérivées <xref:System.Activities.CodeActivity> ne fournissent aucune configuration pour l'annulation parce que tout leur travail est effectué dans une rafale unique d'exécution lorsque l'exécution appelle la méthode <xref:System.Activities.CodeActivity.Execute%2A>. Si la méthode d'exécution n'a pas encore été appelée et qu'une activité basée sur <xref:System.Activities.CodeActivity> est annulée, l'activité est fermée avec l'état <xref:System.Activities.ActivityInstanceState.Canceled> et la méthode <xref:System.Activities.CodeActivity.Execute%2A> n'est pas appelée.  
  
### <a name="cancellation-using-nativeactivity"></a>Annulation à l'aide de NativeActivity  
 Les activités dérivées <xref:System.Activities.NativeActivity> peuvent substituer la méthode <xref:System.Activities.NativeActivity.Cancel%2A> pour fournir une logique d'annulation personnalisée. Si cette méthode n'est pas substituée, la logique d'annulation du workflow par défaut est appliquée. L’annulation par défaut est <xref:System.Activities.NativeActivity> le processus qui <xref:System.Activities.NativeActivity.Cancel%2A> se <xref:System.Activities.NativeActivity.Cancel%2A> produit pour <xref:System.Activities.NativeActivity> <xref:System.Activities.NativeActivity.Cancel%2A> un qui ne remplace pas la méthode ou dont la méthode appelle la méthode de base. Lorsqu'une activité est annulée, l'exécution signale l'activité pour annulation et gère automatiquement un certain nettoyage. Si l'activité a seulement des signets en attente, les signets seront supprimés et l'activité sera marquée comme <xref:System.Activities.ActivityInstanceState.Canceled>. Toutes les activités enfants en attente de l'activité annulée seront à leur tour annulées. Toute tentative de planifier des activités enfants supplémentaires aura pour conséquence que la tentative sera ignorée et l'activité sera marquée comme <xref:System.Activities.ActivityInstanceState.Canceled>. Si une activité enfant en attente se termine dans l'état <xref:System.Activities.ActivityInstanceState.Canceled> ou <xref:System.Activities.ActivityInstanceState.Faulted>, l'activité sera marquée comme <xref:System.Activities.ActivityInstanceState.Canceled>. Notez qu'une demande d'annulation peut être ignorée. Si une activité n'a pas de signets en attente ou d'activités enfants en cours d'exécution et ne planifie pas d'éléments de travail supplémentaires après avoir été signalée pour annulation, son exécution sera réussie. Cette annulation par défaut suffit pour de nombreux scénarios mais, si une logique d'annulation supplémentaire est nécessaire, les activités d'annulation intégrées ou activités personnalisées peuvent être utilisées.  
  
 Dans l'exemple suivant, la substitution <xref:System.Activities.NativeActivity.Cancel%2A> d'une activité <xref:System.Activities.NativeActivity> personnalisée basée sur `ParallelForEach` est définie. Lorsque l'activité est annulée, cette substitution gère la logique d'annulation pour l'activité. Cet exemple fait partie de l’échantillon [parallèle non génériqueforEach.](./samples/non-generic-parallelforeach.md)  
  
```csharp  
protected override void Cancel(NativeActivityContext context)  
{  
    // If we do not have a completion condition then we can just  
    // use default logic.  
    if (this.CompletionCondition == null)  
    {  
        base.Cancel(context);  
    }  
    else  
    {  
        context.CancelChildren();  
    }  
}  
```  
  
 Les activités dérivées <xref:System.Activities.NativeActivity> peuvent déterminer si l'annulation a été demandée en inspectant la propriété <xref:System.Activities.NativeActivityContext.IsCancellationRequested%2A>, puis se marquer comme annulées en appelant la méthode <xref:System.Activities.NativeActivityContext.MarkCanceled%2A>. L'appel de <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> ne met pas immédiatement fin à l'activité. Comme habituellement, l'exécution termine l'activité lorsque plus aucun travail n'est en attente, mais si <xref:System.Activities.NativeActivityContext.MarkCanceled%2A> est appelé, l'état définitif sera <xref:System.Activities.ActivityInstanceState.Canceled> au lieu de <xref:System.Activities.ActivityInstanceState.Closed>.  
  
### <a name="cancellation-using-asynccodeactivity"></a>Annulation à l'aide d'AsyncCodeActivity  
 Les activités basées sur <xref:System.Activities.AsyncCodeActivity> peuvent également fournir une logique d'annulation personnalisée en substituant la méthode <xref:System.Activities.AsyncCodeActivity.Cancel%2A>. Si cette méthode n'est pas substituée, aucune gestion des annulations n'est effectuée si l'activité est annulée. Dans l'exemple suivant, la substitution <xref:System.Activities.AsyncCodeActivity.Cancel%2A> d'une activité <xref:System.Activities.AsyncCodeActivity> personnalisée basée sur `ExecutePowerShell` est définie. Lorsque l'activité est annulée, elle exécute le comportement d'annulation voulu.
  
 [!code-csharp[CFX_WorkflowApplicationExample#1020](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#1020)]  
  
 Les activités dérivées <xref:System.Activities.AsyncCodeActivity> peuvent déterminer si l'annulation a été demandée en inspectant la propriété <xref:System.Activities.AsyncCodeActivityContext.IsCancellationRequested%2A>, puis se marquer comme annulées en appelant la méthode <xref:System.Activities.AsyncCodeActivityContext.MarkCanceled%2A>.

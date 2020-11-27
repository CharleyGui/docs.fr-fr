---
title: Exceptions
ms.date: 03/30/2017
ms.assetid: 065205cc-52dd-4f30-9578-b17d8d113136
ms.openlocfilehash: 53cc8e3e27e131c5c2a9f8271851a0d8d7e0cbd7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280206"
---
# <a name="exceptions"></a>Exceptions

Les flux de travail peuvent utiliser l'activité <xref:System.Activities.Statements.TryCatch> pour gérer des exceptions déclenchées lors de leur exécution. Ces exceptions peuvent être gérées ou être à nouveau levées à l'aide de l'activité <xref:System.Activities.Statements.Rethrow>. Les activités de la section <xref:System.Activities.Statements.TryCatch.Finally%2A> sont exécutées lorsque soit la section <xref:System.Activities.Statements.TryCatch.Try%2A>, soit la section <xref:System.Activities.Statements.TryCatch.Catches%2A> est terminée. Les flux de travail hébergés par une <xref:System.Activities.WorkflowApplication> instance peuvent également utiliser le <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> Gestionnaire d’événements pour gérer les exceptions qui ne sont pas gérées par une <xref:System.Activities.Statements.TryCatch> activité.  
  
## <a name="causes-of-exceptions"></a>Raisons des exceptions  

 Dans un workflow, les exceptions peuvent être générées des différentes manières suivantes :  
  
- délai d'expiration de transactions dans l'objet <xref:System.Activities.Statements.TransactionScope> ;  
  
- exception explicite levée par le flux de travail à l'aide de l'activité <xref:System.Activities.Statements.Throw> ;  
  
- exception [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] levée depuis une activité ;  
  
- exception levée par un code externe, tel que les bibliothèques, composants ou services utilisés dans le flux de travail.  
  
## <a name="handling-exceptions"></a>Gestion des exceptions  

 Si une exception est levée par une activité et n'est pas gérée, le comportement par défaut consiste à arrêter l'instance de flux de travail. En cas de présence d'un gestionnaire <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> personnalisé, il peut substituer ce comportement par défaut. Ce gestionnaire permet à l’auteur hôte du workflow de fournir la gestion appropriée, englobant par exemple l’enregistrement personnalisé, l’abandon de workflow, l’annulation de workflow ou l’arrêt de workflow.  Si un workflow lève une exception qui n'est pas gérée, le gestionnaire <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> est appelé. Il existe trois actions possibles retournées depuis <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> qui déterminent les résultats finaux du flux de travail.  
  
- **Annuler** : une instance de workflow annulée est une sortie normale d’une exécution de branche. Vous pouvez modéliser le comportement d'annulation (par exemple, en utilisant une activité CancellationScope). Le gestionnaire Completed est appelé lorsque le processus d'annulation se termine. Un flux de travail annulé est dans un état d'annulation.  
  
- **Terminate** -une instance de workflow terminée ne peut pas être reprise ou redémarrée.  Cela déclenche l'événement Completed dans lequel vous pouvez fournir une exception comme la raison de l'arrêt. Le gestionnaire Terminated est appelé lorsque le processus d'arrêt se termine. Un flux de travail terminé est dans l'état d'erreur.  
  
- **Abandonner** -une instance de workflow abandonnée peut être reprise uniquement si elle a été configurée pour être persistante.  Sans persistance, un flux de travail ne peut pas être repris.  Au stade où un flux de travail est abandonné, les tâches effectuées (en mémoire) depuis le dernier point de persistance sont perdues. Pour un workflow abandonné, le gestionnaire Aborted est appelé en utilisant l'exception comme raison lorsque le processus d'abandon est terminé. Toutefois, contrairement aux gestionnaires Cancelled et Terminated, le gestionnaire Completed n'est pas appelé. Un flux de travail abandonné est dans un état d'abandon.  
  
 L'exemple suivant appelle un workflow qui lève une exception. L'exception n'est pas prise en charge par le workflow et le gestionnaire <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> est appelé. L'objet <xref:System.Activities.WorkflowApplicationUnhandledExceptionEventArgs> est inspecté de façon à fournir des informations sur l'exception, et le workflow est arrêté.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#1)]  
  
### <a name="handling-exceptions-with-the-trycatch-activity"></a>Gestion des exceptions avec l'activité TryCatch  

 La gestion des exceptions au sein d'un workflow est effectuée avec l'activité <xref:System.Activities.Statements.TryCatch>. L’activité <xref:System.Activities.Statements.TryCatch> possède une collection <xref:System.Activities.Statements.TryCatch.Catches%2A> des activités <xref:System.Activities.Statements.Catch> qui sont toutes associées à un type <xref:System.Exception> spécifique. Si l'exception levée par une activité contenue dans la section <xref:System.Activities.Statements.TryCatch.Try%2A> d'une activité <xref:System.Activities.Statements.TryCatch> correspond à l'exception d'une activité <xref:System.Activities.Statements.Catch%601> dans la collection <xref:System.Activities.Statements.TryCatch.Catches%2A>, elle est gérée. L'exception passe à l'activité parente si elle est explicitement à nouveau levée ou si une nouvelle exception est levée. L'exemple de code suivant illustre une activité <xref:System.Activities.Statements.TryCatch> qui gère un objet <xref:System.ApplicationException> levé dans la section <xref:System.Activities.Statements.TryCatch.Try%2A> par une activité <xref:System.Activities.Statements.Throw>. Le message de l'exception est écrit sur la console par l'activité <xref:System.Activities.Statements.Catch%601>, puis un message est écrit sur la console dans la section <xref:System.Activities.Statements.TryCatch.Finally%2A>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#33](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#33)]  
  
 Les activités dans la section <xref:System.Activities.Statements.TryCatch.Finally%2A> sont exécutées lorsque soit la section <xref:System.Activities.Statements.TryCatch.Try%2A>, soit la section <xref:System.Activities.Statements.TryCatch.Catches%2A> est terminée correctement. La section <xref:System.Activities.Statements.TryCatch.Try%2A> se termine correctement si aucune exception n'est levée, et la section <xref:System.Activities.Statements.TryCatch.Catches%2A> se termine correctement si aucune exception n'est levée ou à nouveau levée. Si une exception est levée dans la section <xref:System.Activities.Statements.TryCatch.Try%2A> d'un <xref:System.Activities.Statements.TryCatch> et n'est pas gérée par <xref:System.Activities.Statements.Catch%601> dans la section <xref:System.Activities.Statements.TryCatch.Catches%2A>, ou est à nouveau levée dans <xref:System.Activities.Statements.TryCatch.Catches%2A>, les activités dans <xref:System.Activities.Statements.TryCatch.Finally%2A> ne seront pas exécutées à moins qu'une des opérations suivantes se produise.  
  
- L'exception est interceptée par une activité <xref:System.Activities.Statements.TryCatch> de plus haut niveau dans le flux de travail, qu'elle soit levée de nouveau ou non à partir de cette activité <xref:System.Activities.Statements.TryCatch> de niveau supérieur.  
  
- L'exception n'est pas gérée par une activité <xref:System.Activities.Statements.TryCatch> de niveau supérieur, s'échappe de la racine du flux de travail et le flux de travail est configuré de sorte à annuler au lieu de terminer ou abandonner. Les flux de travail hébergés à l'aide de <xref:System.Activities.WorkflowApplication> peuvent configurer cela en gérant <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> et en retournant <xref:System.Activities.UnhandledExceptionAction.Cancel>. Un exemple de gestion <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> est disponible précédemment dans cette rubrique. Les services de flux de travail peuvent configurer cette opération à l'aide de <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> et en spécifiant <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Cancel>. Pour obtenir un exemple de configuration de, consultez la page extensibilité de l' <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> [hôte du service de workflow](../wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="exception-handling-versus-compensation"></a>Gestion des exceptions et compensation  

 La différence entre la gestion des exceptions et la compensation réside dans le fait que la gestion des exceptions a lieu lors de l'exécution d'une activité. La compensation a lieu une fois une activité terminée correctement. La gestion des exceptions permet de nettoyer une fois l'exception levée par l'activité, tandis que la compensation fournit un mécanisme permettant d'annuler un travail correctement terminé d'une activité précédemment terminée. Pour plus d’informations, consultez [compensation](compensation.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Activities.Statements.TryCatch>
- <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>
- <xref:System.Activities.Statements.CompensableActivity>

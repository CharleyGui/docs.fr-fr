---
title: Utilisation du suivi pour résoudre les problèmes posés par les applications
ms.date: 03/30/2017
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
ms.openlocfilehash: b07e850810734082568ddca9776a72575c986094
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837556"
---
# <a name="using-tracking-to-troubleshoot-applications"></a>Utilisation du suivi pour résoudre les problèmes posés par les applications
Windows Workflow Foundation (WF) vous permet de suivre les informations relatives au flux de travail pour fournir des détails sur l’exécution d’une application ou d’un service Windows Workflow Foundation. Windows Workflow Foundation hôtes sont en mesure de capturer des événements de workflow pendant l’exécution d’une instance de Workflow. Si votre workflow génère des erreurs ou des exceptions, vous pouvez utiliser les détails du suivi Windows Workflow Foundation pour résoudre les problèmes liés à son traitement.  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a>Dépannage d'un WF à l'aide du suivi WF  
 Pour détecter les erreurs dans le traitement d’une activité Windows Workflow Foundation, vous pouvez activer le suivi avec un modèle de suivi qui recherche un <xref:System.Activities.Tracking.ActivityStateRecord> avec l’état Faulted. La requête correspondante est spécifiée dans le code suivant.  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 Si une erreur est propagée et gérée dans un gestionnaire d'erreur (tel qu'une activité <xref:System.Activities.Statements.TryCatch>), cette erreur peut être détectée à l'aide d'un <xref:System.Activities.Tracking.FaultPropagationRecord>. <xref:System.Activities.Tracking.FaultPropagationRecord> indique l'activité source de l'erreur et le nom du gestionnaire d'erreur. Le <xref:System.Activities.Tracking.FaultPropagationRecord> contient les détails de l’erreur sous forme de la pile d’exception pour l’erreur. La requête pour s’abonner à un <xref:System.Activities.Tracking.FaultPropagationRecord> est présentée dans l’exemple suivant.  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 Si une erreur n'est pas gérée dans le workflow, cela génère une exception non prise en charge au niveau de l'instance du workflow et l'instance du workflow est abandonnée. Pour comprendre les détails de l'exception non prise en charge, le modèle de suivi doit interroger l'enregistrement de l'instance du workflow dont l'état est `state name="UnhandledException"`, comme spécifié dans l'exemple suivant.  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 Lorsqu’une instance de workflow rencontre une exception non gérée, un objet <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> est émis si Windows Workflow Foundation suivi a été activé.  
  
 Cet enregistrement de suivi contient les détails de l'erreur sous la forme d'une pile d'exception. Il contient les détails de la source de l’erreur (par exemple, l’activité) qui a généré une erreur et a généré l’exception non gérée. Pour vous abonner aux événements d’erreur à partir d’un Windows Workflow Foundation, activez le suivi en ajoutant un participant de suivi. Configurez ce participant avec un modèle de suivi qui recherche `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord> et `WorkflowInstanceQuery (state="UnhandledException")`.  
  
 Si le suivi est activé à l'aide du participant de suivi ETW, les événements d'erreur sont émis sur une session ETW. Les événements peuvent être visualisés à l'aide de l'Observateur d'événements. Cela se trouve sous le nœud **observateur d’événements > journaux des applications et des services-> serveur d’applications Microsoft > Windows->-applications** dans le canal analytique.  
  
## <a name="see-also"></a>Voir aussi

- [Analyse Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))
- [Surveillance des applications avec application Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))

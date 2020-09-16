---
title: Utilisation du suivi pour résoudre les problèmes posés par les applications
ms.date: 03/30/2017
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
ms.openlocfilehash: fc9427d0c06ed67ea69669cab2aae64f39f7c10c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551286"
---
# <a name="using-tracking-to-troubleshoot-applications"></a><span data-ttu-id="62b3a-102">Utilisation du suivi pour résoudre les problèmes posés par les applications</span><span class="sxs-lookup"><span data-stu-id="62b3a-102">Using Tracking to Troubleshoot Applications</span></span>
<span data-ttu-id="62b3a-103">Windows Workflow Foundation (WF) vous permet de suivre les informations relatives au flux de travail pour fournir des détails sur l’exécution d’une application ou d’un service Windows Workflow Foundation.</span><span class="sxs-lookup"><span data-stu-id="62b3a-103">Windows Workflow Foundation (WF) enables you to track workflow-related information to give details into the execution of a Windows Workflow Foundation application or service.</span></span> <span data-ttu-id="62b3a-104">Windows Workflow Foundation hôtes sont en mesure de capturer des événements de workflow pendant l’exécution d’une instance de Workflow.</span><span class="sxs-lookup"><span data-stu-id="62b3a-104">Windows Workflow Foundation hosts are able to capture workflow events during the execution of a workflow instance.</span></span> <span data-ttu-id="62b3a-105">Si votre workflow génère des erreurs ou des exceptions, vous pouvez utiliser les détails du suivi Windows Workflow Foundation pour résoudre les problèmes liés à son traitement.</span><span class="sxs-lookup"><span data-stu-id="62b3a-105">If your workflow generates faults or exceptions, you can use the Windows Workflow Foundation tracking details to troubleshooting its processing.</span></span>  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a><span data-ttu-id="62b3a-106">Dépannage d'un WF à l'aide du suivi WF</span><span class="sxs-lookup"><span data-stu-id="62b3a-106">Troubleshooting a WF using WF Tracking</span></span>  
 <span data-ttu-id="62b3a-107">Pour détecter les erreurs dans le traitement d’une activité de Windows Workflow Foundation, vous pouvez activer le suivi avec un modèle de suivi qui recherche un <xref:System.Activities.Tracking.ActivityStateRecord> avec l’état d’erreur.</span><span class="sxs-lookup"><span data-stu-id="62b3a-107">To detect faults within the processing of a Windows Workflow Foundation activity, you can enable tracking with a tracking profile that queries for an <xref:System.Activities.Tracking.ActivityStateRecord> with the state of Faulted.</span></span> <span data-ttu-id="62b3a-108">La requête correspondante est spécifiée dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="62b3a-108">The corresponding query is specified in the following code.</span></span>  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 <span data-ttu-id="62b3a-109">Si une erreur est propagée et gérée dans un gestionnaire d'erreur (tel qu'une activité <xref:System.Activities.Statements.TryCatch>), cette erreur peut être détectée à l'aide d'un <xref:System.Activities.Tracking.FaultPropagationRecord>.</span><span class="sxs-lookup"><span data-stu-id="62b3a-109">If a fault is propagated and handled within a fault handler (such as a <xref:System.Activities.Statements.TryCatch> activity) this can be detected using a <xref:System.Activities.Tracking.FaultPropagationRecord>.</span></span> <span data-ttu-id="62b3a-110"><xref:System.Activities.Tracking.FaultPropagationRecord> indique l'activité source de l'erreur et le nom du gestionnaire d'erreur.</span><span class="sxs-lookup"><span data-stu-id="62b3a-110">The <xref:System.Activities.Tracking.FaultPropagationRecord> indicates the source activity of the fault and the name of the fault handler.</span></span> <span data-ttu-id="62b3a-111">Contient les détails de l' <xref:System.Activities.Tracking.FaultPropagationRecord> erreur sous forme de la pile d’exception pour l’erreur.</span><span class="sxs-lookup"><span data-stu-id="62b3a-111">The <xref:System.Activities.Tracking.FaultPropagationRecord> contains fault details in form of the exception stack for the fault.</span></span> <span data-ttu-id="62b3a-112">La requête pour s’abonner à un <xref:System.Activities.Tracking.FaultPropagationRecord> est présentée dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="62b3a-112">The query to subscribe for a <xref:System.Activities.Tracking.FaultPropagationRecord> is shown in the following example.</span></span>  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 <span data-ttu-id="62b3a-113">Si une erreur n'est pas gérée dans le workflow, cela génère une exception non prise en charge au niveau de l'instance du workflow et l'instance du workflow est abandonnée.</span><span class="sxs-lookup"><span data-stu-id="62b3a-113">If a fault is not handled within the workflow it results in an unhandled exception at the workflow instance and the workflow instance is aborted.</span></span> <span data-ttu-id="62b3a-114">Pour comprendre les détails de l'exception non prise en charge, le modèle de suivi doit interroger l'enregistrement de l'instance du workflow dont l'état est `state name="UnhandledException"`, comme spécifié dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="62b3a-114">To understand the details of the unhandled exception, the tracking profile must query the workflow instance record with `state name="UnhandledException"` as specified in the following example.</span></span>  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 <span data-ttu-id="62b3a-115">Lorsqu’une instance de workflow rencontre une exception non gérée, un <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> objet est émis si Windows Workflow Foundation le suivi a été activé.</span><span class="sxs-lookup"><span data-stu-id="62b3a-115">When a workflow instance encounters an unhandled exception, a <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> object is emitted if Windows Workflow Foundation tracking has been enabled.</span></span>  
  
 <span data-ttu-id="62b3a-116">Cet enregistrement de suivi contient les détails de l'erreur sous la forme d'une pile d'exception.</span><span class="sxs-lookup"><span data-stu-id="62b3a-116">This tracking record contains the fault details in the form of the exception stack.</span></span> <span data-ttu-id="62b3a-117">Il contient les détails de la source de l’erreur (par exemple, l’activité) qui a généré une erreur et a généré l’exception non gérée. Pour vous abonner aux événements d’erreur à partir d’un Windows Workflow Foundation, activez le suivi en ajoutant un participant de suivi.</span><span class="sxs-lookup"><span data-stu-id="62b3a-117">It has details of the source of the fault (for example, the activity) that faulted and resulted in the unhandled exception.To subscribe to fault events from a Windows Workflow Foundation, enable tracking by adding a tracking participant.</span></span> <span data-ttu-id="62b3a-118">Configurez ce participant avec un modèle de suivi qui recherche `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord> et `WorkflowInstanceQuery (state="UnhandledException")`.</span><span class="sxs-lookup"><span data-stu-id="62b3a-118">Configure this participant with a tracking profile that queries for `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, and `WorkflowInstanceQuery (state="UnhandledException")`.</span></span>  
  
 <span data-ttu-id="62b3a-119">Si le suivi est activé à l'aide du participant de suivi ETW, les événements d'erreur sont émis sur une session ETW.</span><span class="sxs-lookup"><span data-stu-id="62b3a-119">If tracking is enabled using the ETW tracking participant, the fault events are emitted to an ETW session.</span></span> <span data-ttu-id="62b3a-120">Les événements peuvent être visualisés à l'aide de l'Observateur d'événements.</span><span class="sxs-lookup"><span data-stu-id="62b3a-120">The events can be viewed using the Event Viewer event viewer.</span></span> <span data-ttu-id="62b3a-121">Cela se trouve sous le nœud **observateur d’événements >journaux des applications et des services->serveur d’applications Microsoft >Windows->-applications** dans le canal analytique.</span><span class="sxs-lookup"><span data-stu-id="62b3a-121">This can be found under the node **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications** in the analytic channel.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62b3a-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62b3a-122">See also</span></span>

- <span data-ttu-id="62b3a-123">[Analyse Windows Server App Fabric](/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="62b3a-123">[Windows Server App Fabric Monitoring](/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="62b3a-124">[Surveillance des applications avec application Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="62b3a-124">[Monitoring Applications with App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span></span>

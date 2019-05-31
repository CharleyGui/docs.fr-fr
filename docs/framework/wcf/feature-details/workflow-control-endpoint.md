---
title: Point de terminaison de contrôle de workflow
ms.date: 03/30/2017
ms.assetid: 1b883334-1590-4fbb-b0d6-65197efe0700
ms.openlocfilehash: 781a7cefaeeb8cd9cd21298471c59de2e7815244
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66424018"
---
# <a name="workflow-control-endpoint"></a>Point de terminaison de contrôle de workflow
Le point de terminaison de contrôle de workflow permet aux développeurs d'appeler des opérations de contrôle qui permettent de contrôler à distance des instances de workflow hébergées à l'aide de <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Cette fonctionnalité peut être utilisée pour effectuer par programme des opérations de contrôle, comme interrompre, continuer et terminer.  
  
> [!WARNING]
>  Si en utilisant le point de terminaison de contrôle de flux de travail au sein d’une transaction et le workflow contrôlé contient un <xref:System.Activities.Statements.Persist> activité, l’instance de workflow se bloque jusqu'à ce que la transaction n’expire.  
  
## <a name="workflow-instance-management"></a>Gestion de l'instance de workflow  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] définit un nouveau contrat appelé <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement>. Ce contrat définit une série d'opérations de contrôle qui vous permettent de contrôler à distance les instances de workflow hébergées par <xref:System.ServiceModel.Activities.WorkflowServiceHost>. <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> est un point de terminaison standard qui fournit une implémentation du contrat <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement>. <xref:System.ServiceModel.Activities.WorkflowControlClient> est une classe utilisée pour envoyer les opérations de contrôle au <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.  
  
 Les instances de workflow peuvent se trouver dans l'un des états suivants :  
  
 Actif  
 État d'une instance de workflow avant qu'elle atteigne l'état terminé et lorsqu'elle n'est pas dans l'état interrompu. Dans cet état, l'instance de workflow s'exécute et traite des messages d'application.  
  
 Suspendu  
 Dans cet état, l'instance de workflow ne s'exécute pas, même si des activités n'ont pas démarré leur exécution ou se sont partiellement exécutées.  
  
 Terminé  
 Dernier état d'une instance de workflow. L'instance de workflow ne peut pas s'exécuter après avoir atteint l'état terminé.  
  
## <a name="iworkflowinstancemanagement"></a>IWorkflowInstanceManagement  
 L’interface <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> définit un jeu d’opérations de contrôle avec des versions synchrones et asynchrones. Les versions avec transaction requièrent l'utilisation d'une liaison prenant en compte les transactions. Le tableau suivant répertorie les opérations de contrôle prises en charge.  
  
|Opération de contrôle|Description|  
|-----------------------|-----------------|  
|Abandonner|Entraîne l'arrêt forcé de l'exécution de l'instance de workflow.|  
|Annuler|Fait passer une instance de workflow de l'état actif ou interrompu à l'état terminé.|  
|Exécuter|Offre à une instance de workflow la possibilité de s'exécuter.|  
|Interrompre|Fait passer une instance de workflow de l'état actif à l'état interrompu.|  
|Terminer|Fait passer une instance de workflow de l'état actif ou interrompu à l'état terminé.|  
|Annuler l'interruption|Fait passer une instance de workflow de l'état interrompu à l'état actif.|  
|TransactedCancel|Effectue l'opération Annuler dans le cadre d'une transaction (transmise à partir du client ou créée localement). Si le système maintient l'état durable de l'instance de workflow, celle-ci doit être persistante pendant l'exécution de cette opération.|  
|TransactedRun|Effectue l'opération Exécuter dans le cadre d'une transaction (transmise à partir du client ou créée localement). Si le système maintient l'état durable de l'instance de workflow, celle-ci doit être persistante pendant l'exécution de cette opération.|  
|TransactedSuspend|Effectue l'opération Interrompre dans le cadre d'une transaction (transmise à partir du client ou créée localement). Si le système maintient l'état durable de l'instance de workflow, celle-ci doit être persistante pendant l'exécution de cette opération.|  
|TransactedTerminate|Effectue l’opération Arrêter dans le cadre d’une transaction (transmise à partir du client ou créée localement). Si le système maintient l'état durable de l'instance de workflow, celle-ci doit être persistante pendant l'exécution de cette opération.|  
|TransactedUnsuspend|Effectue l’opération Annuler l’interruption dans le cadre d’une transaction (transmise à partir du client ou créée localement). Si le système maintient l'état durable de l'instance de workflow, celle-ci doit être persistante pendant l'exécution de cette opération.|  
  
 Le contrat <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> ne permet pas de créer une nouvelle instance de workflow, mais seulement de gérer des instances de workflow existantes. Pour plus d’informations sur la création d’une nouvelle instance de flux de travail à distance, consultez [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="workflowcontrolendpoint"></a>WorkflowControlEndpoint  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> est un point de terminaison standard avec un contrat fixe, <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement>. Lorsqu'il est ajouté à une instance <xref:System.ServiceModel.Activities.WorkflowServiceHost>, ce point de terminaison peut être utilisé pour envoyer des opérations de commande à n'importe quelle instance de workflow hébergée par l'instance hôte. Pour plus d’informations sur les points de terminaison standard, consultez [points de terminaison Standard](../../../../docs/framework/wcf/feature-details/standard-endpoints.md).  
  
## <a name="workflowcontrolclient"></a>WorkflowControlClient  
 <xref:System.ServiceModel.Activities.WorkflowControlClient> est une classe qui vous permet d'envoyer des messages de contrôle à un <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> sur un <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Elle contient une méthode pour chacune des opérations prises en charge par le contrat <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> à l'exception des opérations avec transaction. <xref:System.ServiceModel.Activities.WorkflowControlClient> utilise la transaction ambiante pour déterminer si une opération avec transaction doit être utilisée.

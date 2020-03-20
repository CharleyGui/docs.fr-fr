---
title: Éléments internes de l'hôte du service de workflow
ms.date: 03/30/2017
ms.assetid: af44596f-bf6a-4149-9f04-08d8e8f45250
ms.openlocfilehash: b95a59b0e1715b3cc18ccfea44d6c4ccd04ca5ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184175"
---
# <a name="workflow-service-host-internals"></a>Éléments internes de l'hôte du service de workflow
<xref:System.ServiceModel.WorkflowServiceHost> fournit un hôte pour les services basés sur des workflows. Elle est chargée d'écouter les messages entrants et de les router vers l'instance de service de workflow appropriée, contrôle le déchargement et la persistance des workflows inactifs, et plus encore. Cette rubrique explique comment WorkflowServiceHost traite les messages entrants.  
  
## <a name="workflowservicehost-overview"></a>Vue d'ensemble WorkflowServiceHost  

La classe <xref:System.ServiceModel.WorkflowServiceHost> permet d'héberger des services de workflow. Elle écoute les messages entrants et les route vers l'instance de service appropriée, en créant de nouvelles instances ou en chargeant des instances existantes à partir d'un stockage durable, selon les besoins. Le diagramme suivant illustre à <xref:System.ServiceModel.WorkflowServiceHost> un niveau élevé comment fonctionne :
  
 ![Diagramme qui montre un aperçu de l’hôte du service workflow.](./media/workflow-service-host-internals/workflow-service-host-high-level-overview.gif)  
  
 Ce diagramme montre que la classe <xref:System.ServiceModel.WorkflowServiceHost> charge les définitions de service de workflow à partir de fichiers .xamlx et les informations de configuration à partir d'un fichier de configuration. Elle charge aussi la configuration du suivi à partir du profil de suivi. <xref:System.ServiceModel.WorkflowServiceHost> expose un point de terminaison de contrôle de workflow qui vous permet d'envoyer des opérations de contrôle à des instances de workflow.  Pour plus d’informations, consultez [l’échantillon De point de terminaison de contrôle de flux de travail.](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)  
  
 <xref:System.ServiceModel.WorkflowServiceHost> expose aussi des points de terminaison d'application qui écoutent les messages d'application entrants. Un message entrant qui arrive est envoyé à l'instance de service de workflow appropriée (si celle-ci est actuellement chargée). Au besoin, une nouvelle instance de workflow est créée. Cependant, si une instance existante a été rendue persistante, elle est chargée à partir du magasin de persistance.  
  
## <a name="workflowservicehost-details"></a>Détails de WorkflowServiceHost  
 Le diagramme suivant <xref:System.ServiceModel.WorkflowServiceHost> montre comment gère les messages un peu plus en détail :  
  
 ![Diagramme qui affiche le flux de messages Workflow Service Host.](./media/workflow-service-host-internals/workflow-service-host-message-flow.gif)  
  
 Ce diagramme présente trois points de terminaison distincts : un point de terminaison d'application, un point de terminaison de contrôle de workflow et un point de terminaison d'hébergement de workflow. Le point de terminaison d'application reçoit les messages liés à une instance de workflow spécifique. Le point de terminaison de contrôle de workflow écoute les opérations de contrôle. Le point de terminaison d'hébergement de workflow écoute les messages qui entraînent le chargement et l'exécution par <xref:System.ServiceModel.WorkflowServiceHost> de workflows sans service. Comme le montre le diagramme, tous les messages sont traités via le runtime WCF.  La limitation d'instance de service de workflow s'effectue à l'aide de la propriété <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A>. Cette propriété limite le nombre d'instances de service de workflow. En cas de dépassement de cette limite, les demandes supplémentaires de nouvelle instance de service de workflow ou les demandes d'activation d'instances de workflow persistantes seront mises en file d'attente. Les demandes mises en file d'attente sont traitées dans l'ordre FIFO (premier entré, premier sorti) qu'il s'agisse de demandes de nouvelle instance ou d'une instance en cours d'exécution, persistante. Des informations de stratégie d'hôte qui déterminent le mode de traitement des exceptions non gérées et la façon dont les services de workflow inactifs sont déchargés et rendus persistants sont chargées. Pour plus d’informations sur ces sujets voir [Comment configurer Workflow Unhandled Exception Behavior with WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md) et [How to: Configurer Idle Behavior with WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/how-to-configure-idle-behavior-with-workflowservicehost.md). Les instances de workflow sont rendues persistantes conformément aux stratégies d'hôte, puis rechargées selon les besoins. Pour plus d’informations sur la persistance du flux de travail voir: [Comment configurer la persistance avec WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/how-to-configure-persistence-with-workflowservicehost.md), [La création d’un service de flux de travail à long terme](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md), et [Workflow Persistence](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md).  
  
 L’illustration suivante montre le flux lorsque WorkflowServiceHost.Open est appelé:  
  
 ![Diagramme qui affiche le flux lorsque WorkflowServiceHost.Open est appelé.](./media/workflow-service-host-internals/workflow-service-host-open.gif)  
  
 Le workflow est chargé à partir du XAML et l’arborescence d’activité est créée. <xref:System.ServiceModel.WorkflowServiceHost> parcourt l'arborescence d'activité et crée la description du service. La configuration est appliquée à l'hôte. Enfin, l'hôte commence à écouter les messages entrants.  
  
 L’illustration suivante <xref:System.ServiceModel.WorkflowServiceHost> montre ce que le fait quand il reçoit un message lié `true`pour une activité Recevoir qui a CanCreateInstance mis à:  
  
 ![Arbre de décision utilisé par l’hôte WFS quand il reçoit un message et CanCreateInstance est vrai.](./media/workflow-service-host-internals/workflow-service-host-receive-message-cancreateinstance.gif)  
  
 Le message arrive et est traité par la pile de canaux WCF. Les limitations sont vérifiées et les requêtes de corrélation exécutées. Si le message est lié à une instance existante, il est remis. Si une nouvelle instance doit être créée, la propriété CanCreateInstance de l'activité Receive est vérifiée. Si sa valeur est true, une nouvelle instance est créée et le message est remis.  
  
 L'illustration suivante montre ce que fait <xref:System.ServiceModel.WorkflowServiceHost> à réception d'un message lié à une activité Receive dont CanCreateInstance a la valeur false.  
  
 ![Arbre de décision utilisé par l’hôte WFS quand il reçoit un message et CanCreateInstance est faux.](./media/workflow-service-host-internals/workflow-service-host-receive-message.gif)  
  
 Le message arrive et est traité par la pile de canaux WCF. Les limitations sont vérifiées et les requêtes de corrélation exécutées. Le message est lié à une instance existante (puisque CanCreateInstance a la valeur false), de sorte que l'instance est chargée à partir du magasin de persistance, le signet est repris et le workflow s'exécute.  
  
> [!WARNING]
> Si SQL Server est configuré de façon à n'écouter que le protocole NamedPipe, l'ouverture de l'hôte du service de workflow échoue.  
  
## <a name="see-also"></a>Voir aussi

- [Services de flux de travail](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Hébergement de services de workflow](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)
- [Point de terminaison de contrôle de workflow](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)
- [Procédure : configurer le comportement des exceptions non gérées du workflow avec WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md)
- [Création d'un service de workflow de longue durée](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)
- [Persistance du workflow](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)

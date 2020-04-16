---
title: Extensibilité de l'hôte du service de workflow
ms.date: 03/30/2017
ms.assetid: c0e8f7bb-cb13-49ec-852f-b85d7c23972f
ms.openlocfilehash: eb35b9211bc55ee66f5bb5600ef86f40d4145191
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463998"
---
# <a name="workflow-service-host-extensibility"></a>Extensibilité de l'hôte du service de workflow
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] fournit la classe <xref:System.ServiceModel.Activities.WorkflowServiceHost> pour l'hébergement de services de workflow. Cette classe est utilisée lorsque vous auto-hébergez un service de workflow dans une application managée ou un service Windows. Cette classe est également utilisée lors de l'hébergement d'un service de workflow dans les services IIS (Internet Information Services) ou WAS (Windows Process Activation Service). La classe <xref:System.ServiceModel.Activities.WorkflowServiceHost> fournit des points d’extension qui vous permettent d’ajouter des extensions personnalisées, de modifier le comportement inactif et d’héberger des workflows sans service (workflows qui n’utilisent aucune activité de messagerie).  
  
## <a name="workflow-service-host-extensions"></a>Extensions de l'hôte du service de workflow  
 Le <xref:System.ServiceModel.Activities.WorkflowServiceHost> contient une propriété <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> de type <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager> qui fournit des méthodes pour ajouter des extensions au <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Utilisez la méthode <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager.Add%2A> pour ajouter une extension pour chaque instance du service de workflow. Le délégué spécifié est appelé pour créer une extension lorsqu’une instance du service de workflow est créée ou chargée à partir d’un magasin de persistance. Utilisez la méthode <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager.Add%2A> pour ajouter une extension pour chaque hôte du service de workflow. Une instance de l'extension est partagée pour toutes les instances du service de workflow.  
  
## <a name="react-to-unhandled-exceptions"></a>Réagir aux exceptions non gérées  
 Le <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> vous permet de spécifier l'action à entreprendre si une exception non gérée est levée dans un service de workflow. La propriété <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior.Action%2A> spécifie l'une des valeurs de <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction> :  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Abandon> : abandonne l'instance de service de workflow.  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.AbandonAndSuspend> : restaure le dernier état persistant et interrompt l'instance du service de workflow. Cela ne se produit que si le workflow a déjà été persistant au moins une fois. Dans le cas contraire, l'instance de workflow est annulée.  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Cancel> : annule l'instance.  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Terminate> : met fin à l'instance.  
  
 Ce comportement peut être configuré dans le code, comme indiqué dans l'exemple suivant.  
  
```csharp  
host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.Abandon });  
```  
  
 Il peut également être configuré dans un fichier de configuration, comme illustré dans l'exemple suivant.  
  
```xml
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <workflowUnhandledExceptionBehavior action="Abandon" />
        </behavior>  
      </serviceBehaviors>  
</behaviors>
```  
  
## <a name="hosting-non-service-workflows"></a>Hébergement de workflows sans service  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost> peut être utilisé pour héberger des workflows sans service, ou des workflows qui ne commencent pas non plus par une activité <xref:System.ServiceModel.Activities.Receive> ou qui n'utilisent pas les activités de messagerie. Les services de workflow commencent normalement par une activité <xref:System.ServiceModel.Activities.Receive>. Lorsque le <xref:System.ServiceModel.Activities.WorkflowServiceHost> reçoit un message pour un service de workflow, si celui-ci n'est pas déjà en cours d'exécution (ou persistant), une nouvelle instance du service de workflow est créée. Si un workflow ne commence pas par une activité Receive, il ne peut pas être démarré par l'envoi d'un message parce qu'il n'existe aucune activité pour recevoir le message. Pour héberger un workflow sans service, dérivez une classe à partir de <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> et substituez les méthodes <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A>, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> et <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnResolveBookmark%2A>. Substituez <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> si vous souhaitez fournir un ID d'instance préféré. Substituez la méthode <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> pour créer un contexte de création de workflow personnalisé ou remplir une instance du <xref:System.ServiceModel.Activities.WorkflowCreationContext> existant. Substituez la méthode <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnResolveBookmark%2A> pour extraire manuellement le signet du message entrant. Si vous remplacez cette méthode, vous devez invoquer <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> dans son corps pour qu'il réponde au message envoyé au WorkflowHostingEndpoint. Faute de cela, la limite <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> sera peut-être dépassée. Dans les contrats duplex, vous pouvez détecter votre échec d'appel de <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> car le client ne reçoit pas de réponse. Dans les contrats unidirectionnels, vous pouvez ne détecter l'échec de l'appel de <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> qu'une fois qu'il est trop tard, c'est-à-dire après le dépassement de la valeur limite <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>. Pour plus d’informations, veuillez consulter le [carnet de cv WorkflowHostingEndpoint](../../../../docs/framework/windows-workflow-foundation/samples/workflowhostingendpoint-resume-bookmark.md)Pour créer une nouvelle instance d’un flux de travail non-service, déclarer un contrat de service qui définit une opération qui crée une nouvelle instance. L’opération de création doit\<prendre une chaîne IDictionary, objet> pour passer tous les paramètres de flux de travail requis. Ce contrat est implémenté de manière implicite par la classe dérivée de <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>. Lorsque vous hébergez le workflow, ajoutez à l'hôte une instance de la classe dérivée de <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> en appelant la méthode <xref:System.ServiceModel.Activities.WorkflowServiceHost.AddServiceEndpoint%2A>, puis appelez <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Pour créer une instance du workflow, créez un objet <xref:System.ServiceModel.ChannelFactory%601> de votre type de contrat de service et appelez <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>. Vous pouvez ensuite appeler l'opération de création définie dans votre contrat de service.  
  
## <a name="see-also"></a>Voir aussi

- [Services de flux de travail](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Activités de messagerie](../../../../docs/framework/wcf/feature-details/messaging-activities.md)

---
title: 'Procédure : configurer le suivi avec WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: 5781878270272f5ef894c68dc23b9433029e1d41
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968493"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a>Procédure : configurer le suivi avec WorkflowServiceHost
Cette rubrique explique comment configurer le suivi pour un workflow [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] hébergé dans <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Il est configuré via un fichier Web.config en spécifiant un comportement de service.  
  
### <a name="configure-tracking-in-configuration"></a>Configurer le suivi dans le fichier de configuration  
  
1. Ajoutez le <xref:System.Activities.Tracking.EtwTrackingParticipant> à l’aide`behavior`de l’élément < > dans un fichier de configuration, comme indiqué dans l’exemple suivant.  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior>  
           <etwTracking profileName="Sample Tracking Profile" />  
         </behavior>              
       </serviceBehaviors>  
    <behaviors>  
    ```  
  
    > [!NOTE]
    > L'exemple de configuration précédent utilise la configuration simplifiée. Pour plus d’informations, consultez [configuration simplifiée](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     L'exemple de configuration précédent ajoute un objet <xref:System.Activities.Tracking.EtwTrackingParticipant> et spécifie un nom de modèle de suivi. Les profils de suivi sont créés dans`trackingProfile`un élément < > au`tracking`sein d’un élément < >. Le modèle de suivi contient des requêtes de suivi qui permettent à un participant de suivi de s'abonner à des événements de workflow émis lorsque l'état d'une instance de workflow change au moment de l'exécution. L'exemple suivant montre comment créer un modèle de suivi.  
  
    ```xml  
    <system.serviceModel>  
        <tracking>   
         <trackingProfile name="Sample Tracking Profile">  
            <workflow activityDefinitionId="*">  
               <workflowInstanceQueries>  
                 <workflowInstanceQuery>  
                    <states>  
                       <state name="Started"/>  
                       <state name="Completed"/>  
                    </states>  
                </workflowInstanceQuery>  
             </workflowInstanceQueries>  
           </workflow>  
         </trackingProfile>   
       </tracking>  
    </system.serviceModel>  
    ```  
  
     Pour plus d’informations sur les profils de suivi, consultez [suivi des profils](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     Pour plus d’informations sur le suivi en général, consultez [suivi et traçage de workflow](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).  
  
### <a name="configure-tracking-in-code"></a>Configurer le suivi dans le code  
  
1. Ajoutez le <xref:System.Activities.Tracking.EtwTrackingParticipant> à l'aide du comportement <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> dans le code, comme indiqué dans l'exemple suivant.  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     L'exemple de code précédent ajoute un objet <xref:System.Activities.Tracking.EtwTrackingParticipant> et spécifie un nom de modèle de suivi. Les profils de suivi sont créés dans`trackingProfile`un élément < > au`tracking`sein d’un élément < > comme indiqué dans la section précédente.  
  
     Pour plus d’informations sur les profils de suivi, consultez [suivi des profils](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     Pour plus d’informations sur le suivi en général, consultez [suivi et traçage de workflow](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md). Pour obtenir un exemple de configuration du suivi par programme, consultez [configuration du suivi d’un workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).  
  
## <a name="see-also"></a>Voir aussi

- [Configuration simplifiée pour les services WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)
- [Services de workflow](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Profils de suivi](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)

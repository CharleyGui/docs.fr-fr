---
title: 'Procédure : configurer le suivi avec WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: cf30ace90f86e282d72c4da5f2c3707905360aeb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96257351"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a>Procédure : configurer le suivi avec WorkflowServiceHost

Cette rubrique explique comment configurer le suivi pour un workflow [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] hébergé dans <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Il est configuré via un fichier Web.config en spécifiant un comportement de service.  
  
### <a name="configure-tracking-in-configuration"></a>Configurer le suivi dans le fichier de configuration  
  
1. Ajoutez le <xref:System.Activities.Tracking.EtwTrackingParticipant> à l’aide de l' `behavior` élément <> dans un fichier de configuration, comme indiqué dans l’exemple suivant.  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior>  
           <etwTracking profileName="Sample Tracking Profile" />  
         </behavior>
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
    > [!NOTE]
    > L'exemple de configuration précédent utilise la configuration simplifiée. Pour plus d’informations, consultez [configuration simplifiée](../simplified-configuration.md).  
  
     L'exemple de configuration précédent ajoute un objet <xref:System.Activities.Tracking.EtwTrackingParticipant> et spécifie un nom de modèle de suivi. Les profils de suivi sont créés dans un `trackingProfile` élément <> au sein d’un `tracking` élément <>. Le modèle de suivi contient des requêtes de suivi qui permettent à un participant de suivi de s'abonner à des événements de workflow émis lorsque l'état d'une instance de workflow change au moment de l'exécution. L'exemple suivant montre comment créer un modèle de suivi.  
  
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
  
     Pour plus d’informations sur les profils de suivi, consultez [suivi des profils](../../windows-workflow-foundation/tracking-profiles.md).  
  
     Pour plus d’informations sur le suivi en général, consultez [suivi et traçage de workflow](../../windows-workflow-foundation/workflow-tracking-and-tracing.md).  
  
### <a name="configure-tracking-in-code"></a>Configurer le suivi dans le code  
  
1. Ajoutez le <xref:System.Activities.Tracking.EtwTrackingParticipant> à l'aide du comportement <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> dans le code, comme indiqué dans l'exemple suivant.  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     L'exemple de code précédent ajoute un objet <xref:System.Activities.Tracking.EtwTrackingParticipant> et spécifie un nom de modèle de suivi. Les profils de suivi sont créés dans un `trackingProfile` élément <> au sein d’un `tracking` élément <> comme indiqué dans la section précédente.  
  
     Pour plus d’informations sur les profils de suivi, consultez [suivi des profils](../../windows-workflow-foundation/tracking-profiles.md).  
  
     Pour plus d’informations sur le suivi en général, consultez [suivi et traçage de workflow](../../windows-workflow-foundation/workflow-tracking-and-tracing.md). Pour obtenir un exemple de configuration du suivi par programme, consultez [configuration du suivi d’un workflow](../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).  
  
## <a name="see-also"></a>Voir aussi

- [Configuration simplifiée pour WCF Services](../samples/simplified-configuration-for-wcf-services.md)
- [Services de workflow](workflow-services.md)
- [Modèles de suivi](../../windows-workflow-foundation/tracking-profiles.md)

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
# <a name="how-to-configure-tracking-with-workflowservicehost"></a><span data-ttu-id="3f68c-102">Procédure : configurer le suivi avec WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="3f68c-102">How to: Configure Tracking with WorkflowServiceHost</span></span>
<span data-ttu-id="3f68c-103">Cette rubrique explique comment configurer le suivi pour un workflow [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] hébergé dans <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="3f68c-103">This topic explains how to configure tracking for a [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="3f68c-104">Il est configuré via un fichier Web.config en spécifiant un comportement de service.</span><span class="sxs-lookup"><span data-stu-id="3f68c-104">It is configured through a Web.config file by specifying a service behavior.</span></span>  
  
### <a name="configure-tracking-in-configuration"></a><span data-ttu-id="3f68c-105">Configurer le suivi dans le fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="3f68c-105">Configure Tracking in Configuration</span></span>  
  
1. <span data-ttu-id="3f68c-106">Ajoutez le <xref:System.Activities.Tracking.EtwTrackingParticipant> à l’aide`behavior`de l’élément < > dans un fichier de configuration, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="3f68c-106">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>  
  
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
    > <span data-ttu-id="3f68c-107">L'exemple de configuration précédent utilise la configuration simplifiée.</span><span class="sxs-lookup"><span data-stu-id="3f68c-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="3f68c-108">Pour plus d’informations, consultez [configuration simplifiée](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="3f68c-108">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="3f68c-109">L'exemple de configuration précédent ajoute un objet <xref:System.Activities.Tracking.EtwTrackingParticipant> et spécifie un nom de modèle de suivi.</span><span class="sxs-lookup"><span data-stu-id="3f68c-109">The preceding configuration sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="3f68c-110">Les profils de suivi sont créés dans`trackingProfile`un élément < > au`tracking`sein d’un élément < >.</span><span class="sxs-lookup"><span data-stu-id="3f68c-110">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element.</span></span> <span data-ttu-id="3f68c-111">Le modèle de suivi contient des requêtes de suivi qui permettent à un participant de suivi de s'abonner à des événements de workflow émis lorsque l'état d'une instance de workflow change au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="3f68c-111">The tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="3f68c-112">L'exemple suivant montre comment créer un modèle de suivi.</span><span class="sxs-lookup"><span data-stu-id="3f68c-112">The following example shows how to create a tracking profile.</span></span>  
  
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
  
     <span data-ttu-id="3f68c-113">Pour plus d’informations sur les profils de suivi, consultez [suivi des profils](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="3f68c-113">For more information about tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="3f68c-114">Pour plus d’informations sur le suivi en général, consultez [suivi et traçage de workflow](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="3f68c-114">For more information about tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span>  
  
### <a name="configure-tracking-in-code"></a><span data-ttu-id="3f68c-115">Configurer le suivi dans le code</span><span class="sxs-lookup"><span data-stu-id="3f68c-115">Configure Tracking in Code</span></span>  
  
1. <span data-ttu-id="3f68c-116">Ajoutez le <xref:System.Activities.Tracking.EtwTrackingParticipant> à l'aide du comportement <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> dans le code, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="3f68c-116">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> behavior in code, as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     <span data-ttu-id="3f68c-117">L'exemple de code précédent ajoute un objet <xref:System.Activities.Tracking.EtwTrackingParticipant> et spécifie un nom de modèle de suivi.</span><span class="sxs-lookup"><span data-stu-id="3f68c-117">The preceding code sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="3f68c-118">Les profils de suivi sont créés dans`trackingProfile`un élément < > au`tracking`sein d’un élément < > comme indiqué dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="3f68c-118">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element as shown in the previous section.</span></span>  
  
     <span data-ttu-id="3f68c-119">Pour plus d’informations sur les profils de suivi, consultez [suivi des profils](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="3f68c-119">For more information about tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="3f68c-120">Pour plus d’informations sur le suivi en général, consultez [suivi et traçage de workflow](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="3f68c-120">For more information about tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span> <span data-ttu-id="3f68c-121">Pour obtenir un exemple de configuration du suivi par programme, consultez [configuration du suivi d’un workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="3f68c-121">For an example of configuring tracking programmatically see [Configuring Tracking for a Workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f68c-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f68c-122">See also</span></span>

- [<span data-ttu-id="3f68c-123">Configuration simplifiée pour les services WCF</span><span class="sxs-lookup"><span data-stu-id="3f68c-123">Simplified Configuration for WCF Services</span></span>](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)
- [<span data-ttu-id="3f68c-124">Services de workflow</span><span class="sxs-lookup"><span data-stu-id="3f68c-124">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="3f68c-125">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="3f68c-125">Tracking Profiles</span></span>](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)

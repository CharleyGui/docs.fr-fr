---
title: 'Procédure : configurer le comportement d’exception non prise en charge du workflow avec WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: 93eb2f4493b70f54336a5d47957c6913239088e5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96264853"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a><span data-ttu-id="89b3c-102">Procédure : configurer le comportement d’exception non prise en charge du workflow avec WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="89b3c-102">How to: Configure Workflow Unhandled Exception Behavior with WorkflowServiceHost</span></span>

<span data-ttu-id="89b3c-103"><xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> est un comportement qui vous permet de spécifier l'action à entreprendre en cas d'exception non gérée dans un workflow hébergé par <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="89b3c-103">The <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is a behavior that enables you to specify the action to take if an unhandled exception occurs within a workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="89b3c-104">Cette rubrique indique comment configurer ce comportement dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="89b3c-104">This topic shows how to configure this behavior in a configuration file.</span></span>  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a><span data-ttu-id="89b3c-105">Pour configurer WorkflowUnhandledExceptionBehavior</span><span class="sxs-lookup"><span data-stu-id="89b3c-105">To configure WorkflowUnhandledExceptionBehavior</span></span>  
  
1. <span data-ttu-id="89b3c-106">Ajoutez un `workflowUnhandledException` élément <> dans un `behavior` élément <> dans un élément <> `serviceBehaviors` , en utilisant `action` l’attribut pour spécifier l’action à entreprendre lorsqu’une exception non gérée se produit, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="89b3c-106">Add a <`workflowUnhandledException`> element in a <`behavior`> element within a <`serviceBehaviors`> element, using the `action` attribute to specify the action to take when an unhandled exception occurs as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowUnhandledException action="abandonAndSuspend"/>
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="89b3c-107">L'exemple de configuration précédent utilise la configuration simplifiée.</span><span class="sxs-lookup"><span data-stu-id="89b3c-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="89b3c-108">Pour plus d’informations, consultez [configuration simplifiée](../simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="89b3c-108">For more information, see [Simplified Configuration](../simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="89b3c-109">Ce comportement peut être configuré dans le code, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="89b3c-109">This behavior can be configured in code as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     <span data-ttu-id="89b3c-110">L' `action` attribut de l' `workflowUnhandledException` élément <> peut être défini sur l’une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="89b3c-110">The `action` attribute of the <`workflowUnhandledException`> element can be set to one of the following values:</span></span>  
  
     <span data-ttu-id="89b3c-111">**consistant**</span><span class="sxs-lookup"><span data-stu-id="89b3c-111">**abandon**</span></span>  
     <span data-ttu-id="89b3c-112">Abandonne l'instance en mémoire sans modifier l'état de l'instance persistante (autrement dit, restaure le dernier point persistant).</span><span class="sxs-lookup"><span data-stu-id="89b3c-112">Aborts the instance in memory without touching the persisted instance state (that is, roll back to the last persist point).</span></span>  
  
     <span data-ttu-id="89b3c-113">**abandonAndSuspend**</span><span class="sxs-lookup"><span data-stu-id="89b3c-113">**abandonAndSuspend**</span></span>  
     <span data-ttu-id="89b3c-114">Abandonne l'instance en mémoire et met à jour l'instance persistante à interrompre.</span><span class="sxs-lookup"><span data-stu-id="89b3c-114">Aborts the instance in memory and updates the persisted instance to be suspended.</span></span>  
  
     <span data-ttu-id="89b3c-115">**cancel**</span><span class="sxs-lookup"><span data-stu-id="89b3c-115">**cancel**</span></span>  
     <span data-ttu-id="89b3c-116">Appelle des gestionnaires d'annulation pour l'instance, puis termine l'instance dans la mémoire, ce qui peut également la supprimer du magasin d'instances</span><span class="sxs-lookup"><span data-stu-id="89b3c-116">Calls cancellation handlers for the instance and then completes the instance in memory, which may also remove it from the instance store</span></span>  
  
     <span data-ttu-id="89b3c-117">**pire**</span><span class="sxs-lookup"><span data-stu-id="89b3c-117">**terminate**</span></span>  
     <span data-ttu-id="89b3c-118">Termine l'instance en mémoire et la supprime du magasin d'instances.</span><span class="sxs-lookup"><span data-stu-id="89b3c-118">Completes the instance in memory and removes it from the instance store.</span></span>  
  
     <span data-ttu-id="89b3c-119">Pour plus d’informations sur, consultez la page extensibilité de l' <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> [hôte du service de workflow](workflow-service-host-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="89b3c-119">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, see [Workflow Service Host Extensibility](workflow-service-host-extensibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89b3c-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89b3c-120">See also</span></span>

- [<span data-ttu-id="89b3c-121">Extensibilité de l'hôte du service de workflow</span><span class="sxs-lookup"><span data-stu-id="89b3c-121">Workflow Service Host Extensibility</span></span>](workflow-service-host-extensibility.md)
- [<span data-ttu-id="89b3c-122">Services de workflow</span><span class="sxs-lookup"><span data-stu-id="89b3c-122">Workflow Services</span></span>](workflow-services.md)

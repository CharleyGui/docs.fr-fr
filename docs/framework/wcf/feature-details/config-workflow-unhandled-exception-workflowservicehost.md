---
title: 'Procédure : configurer le comportement des exceptions non gérées du workflow avec WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: 69c6b1ce11d735181390a0c67df2f8dbea4f906c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185309"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a>Procédure : configurer le comportement des exceptions non gérées du workflow avec WorkflowServiceHost
<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> est un comportement qui vous permet de spécifier l'action à entreprendre en cas d'exception non gérée dans un workflow hébergé par <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Cette rubrique indique comment configurer ce comportement dans un fichier de configuration.  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a>Pour configurer WorkflowUnhandledExceptionBehavior  
  
1. Ajoutez un élément `workflowUnhandledException` <> dans un élément `behavior`> <dans un élément `serviceBehaviors` <>, en utilisant `action` l’attribut pour spécifier l’action à prendre lorsqu’une exception non gérée se produit comme indiqué dans l’exemple suivant.  
  
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
    > L'exemple de configuration précédent utilise la configuration simplifiée. Pour plus d’informations, voir [Configuration simplifiée](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     Ce comportement peut être configuré dans le code, comme indiqué dans l'exemple suivant.  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     L’attribut `action` de l’élément `workflowUnhandledException` <> peut être défini à l’une des valeurs suivantes :  
  
     **Abandonner**  
     Abandonne l'instance en mémoire sans modifier l'état de l'instance persistante (autrement dit, restaure le dernier point persistant).  
  
     **abandonAndSuspend**  
     Abandonne l'instance en mémoire et met à jour l'instance persistante à interrompre.  
  
     **Annuler**  
     Appelle des gestionnaires d'annulation pour l'instance, puis termine l'instance dans la mémoire, ce qui peut également la supprimer du magasin d'instances  
  
     **Mettre fin**  
     Termine l'instance en mémoire et la supprime du magasin d'instances.  
  
     Pour plus <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>d’informations sur , voir [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="see-also"></a>Voir aussi

- [Extensibilité de l'hôte du service de workflow](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [Services de flux de travail](../../../../docs/framework/wcf/feature-details/workflow-services.md)

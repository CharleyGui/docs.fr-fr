---
title: 'Procédure : configurer le comportement des exceptions non gérées du workflow avec WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: 3881d1af21dcc0c211c6738162360e522648d949
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593592"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a>Procédure : configurer le comportement des exceptions non gérées du workflow avec WorkflowServiceHost
<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> est un comportement qui vous permet de spécifier l'action à entreprendre en cas d'exception non gérée dans un workflow hébergé par <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Cette rubrique indique comment configurer ce comportement dans un fichier de configuration.  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a>Pour configurer WorkflowUnhandledExceptionBehavior  
  
1. Ajoutez un `workflowUnhandledException` élément <> dans un `behavior` élément <> dans un élément <> `serviceBehaviors` , en utilisant `action` l’attribut pour spécifier l’action à entreprendre lorsqu’une exception non gérée se produit, comme indiqué dans l’exemple suivant.  
  
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
    > L'exemple de configuration précédent utilise la configuration simplifiée. Pour plus d’informations, consultez [configuration simplifiée](../simplified-configuration.md).  
  
     Ce comportement peut être configuré dans le code, comme indiqué dans l'exemple suivant.  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     L' `action` attribut de l' `workflowUnhandledException` élément <> peut être défini sur l’une des valeurs suivantes :  
  
     **consistant**  
     Abandonne l'instance en mémoire sans modifier l'état de l'instance persistante (autrement dit, restaure le dernier point persistant).  
  
     **abandonAndSuspend**  
     Abandonne l'instance en mémoire et met à jour l'instance persistante à interrompre.  
  
     **cancel**  
     Appelle des gestionnaires d'annulation pour l'instance, puis termine l'instance dans la mémoire, ce qui peut également la supprimer du magasin d'instances  
  
     **pire**  
     Termine l'instance en mémoire et la supprime du magasin d'instances.  
  
     Pour plus d’informations sur, consultez la page extensibilité de l' <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> [hôte du service de workflow](workflow-service-host-extensibility.md).  
  
## <a name="see-also"></a>Voir aussi

- [Extensibilité de l'hôte du service de workflow](workflow-service-host-extensibility.md)
- [Services de workflow](workflow-services.md)

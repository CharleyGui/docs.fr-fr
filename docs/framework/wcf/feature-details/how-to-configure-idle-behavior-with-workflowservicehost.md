---
title: 'Procédure : configurer le comportement inactif avec WorkflowServiceHost'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
ms.openlocfilehash: 67be47f97e57792e2f1e14505d3cd121729db33b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185084"
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a>Procédure : configurer le comportement inactif avec WorkflowServiceHost
Les workflows deviennent inactifs lorsqu'ils rencontrent un signet qui doit être repris au moyen d'une impulsion externe, par exemple, l'instance de workflow attend qu'un message soit remis à l'aide d'une activité <xref:System.ServiceModel.Activities.Receive> . <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> est un comportement qui vous permet de spécifier le délai entre le moment où une instance du service devient inactive et celui où elle est persistante ou déchargée. Il contient deux propriétés qui permettent de définir ces intervalles. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> spécifie l'intervalle de temps entre le moment où une instance du service de workflow devient inactive et celui où elle est persistante. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> spécifie l'intervalle entre le moment où une instance du service de workflow devient inactive et celui où elle est déchargée, c'est-à-dire rendue persistante dans le magasin d'instances et supprimée de la mémoire. Cette rubrique explique comment configurer le comportement <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> dans un fichier de configuration.  
  
### <a name="to-configure-workflowidlebehavior"></a>Pour configurer WorkflowIdleBehavior  
  
1. Ajoutez un élément `workflowIdle` <> à l’élément `behavior`> <dans l’élément `serviceBehaviors`> <tel que indiqué dans l’exemple suivant.  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     L'attribut `timeToUnload` spécifie le délai entre le moment où une instance du service de workflow devient inactive et celui où le service de workflow est déchargé. L'attribut `timeToPersist` spécifie le délai entre le moment où une instance du service de workflow devient inactive et celui où elle est persistante. La valeur par défaut de `timeToUnload` est égale à 1 minute. La valeur par défaut pour `timeToPersist` est <xref:System.TimeSpan.MaxValue>. Si vous souhaitez conserver les instances inactives en mémoire mais les rendre persistantes pour plus de fiabilité, définissez les valeurs ainsi : `timeToPersist` < `timeToUnload`. Si vous souhaitez empêcher que les instances inactives soient déchargées, définissez `timeToUnload` sur <xref:System.TimeSpan.MaxValue>. Pour plus <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>d’informations sur , voir [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
  
    > [!NOTE]
    > L'exemple de configuration précédent utilise la configuration simplifiée. Pour plus d’informations, voir [Configuration simplifiée](../../../../docs/framework/wcf/simplified-configuration.md).  
  
### <a name="to-change-idle-behavior-in-code"></a>Pour modifier le comportement de l'inactivité en code  
  
- L’exemple suivant modifie la temporisation avant la persistance et le déchargement par programmation.  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Extensibilité de l'hôte du service de workflow](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [Configuration simplifiée](../../../../docs/framework/wcf/simplified-configuration.md)
- [Services de flux de travail](../../../../docs/framework/wcf/feature-details/workflow-services.md)

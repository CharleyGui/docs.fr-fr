---
title: 'Procédure : configurer le comportement inactif avec WorkflowServiceHost'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
ms.openlocfilehash: 8b9fa36408d5f2bc5445ebeccba61f71417935e7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599124"
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a>Procédure : configurer le comportement inactif avec WorkflowServiceHost
Les workflows deviennent inactifs lorsqu'ils rencontrent un signet qui doit être repris au moyen d'une impulsion externe, par exemple, l'instance de workflow attend qu'un message soit remis à l'aide d'une activité <xref:System.ServiceModel.Activities.Receive> . <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> est un comportement qui vous permet de spécifier le délai entre le moment où une instance du service devient inactive et celui où elle est persistante ou déchargée. Il contient deux propriétés qui permettent de définir ces intervalles. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> spécifie l'intervalle de temps entre le moment où une instance du service de workflow devient inactive et celui où elle est persistante. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> spécifie l'intervalle entre le moment où une instance du service de workflow devient inactive et celui où elle est déchargée, c'est-à-dire rendue persistante dans le magasin d'instances et supprimée de la mémoire. Cette rubrique explique comment configurer le comportement <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> dans un fichier de configuration.  
  
### <a name="to-configure-workflowidlebehavior"></a>Pour configurer WorkflowIdleBehavior  
  
1. Ajoutez un `workflowIdle` élément <> à l' `behavior` élément <> au sein de l’élément <> `serviceBehaviors` comme indiqué dans l’exemple suivant.  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     L'attribut `timeToUnload` spécifie le délai entre le moment où une instance du service de workflow devient inactive et celui où le service de workflow est déchargé. L'attribut `timeToPersist` spécifie le délai entre le moment où une instance du service de workflow devient inactive et celui où elle est persistante. La valeur par défaut de `timeToUnload` est égale à 1 minute. La valeur par défaut pour `timeToPersist` est <xref:System.TimeSpan.MaxValue>. Si vous souhaitez conserver les instances inactives en mémoire mais les rendre persistantes pour plus de fiabilité, définissez les valeurs ainsi : `timeToPersist` < `timeToUnload`. Si vous souhaitez empêcher que les instances inactives soient déchargées, définissez `timeToUnload` sur <xref:System.TimeSpan.MaxValue>. Pour plus d’informations sur <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> , voir extensibilité de l' [hôte du service de workflow](workflow-service-host-extensibility.md) .  
  
    > [!NOTE]
    > L'exemple de configuration précédent utilise la configuration simplifiée. Pour plus d’informations, consultez [configuration simplifiée](../simplified-configuration.md).  
  
### <a name="to-change-idle-behavior-in-code"></a>Pour modifier le comportement de l'inactivité en code  
  
- L’exemple suivant modifie la temporisation avant la persistance et le déchargement par programmation.  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Extensibilité de l'hôte du service de workflow](workflow-service-host-extensibility.md)
- [Configuration simplifiée](../simplified-configuration.md)
- [Services de workflow](workflow-services.md)

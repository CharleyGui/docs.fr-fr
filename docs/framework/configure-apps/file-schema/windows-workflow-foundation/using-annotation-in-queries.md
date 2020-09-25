---
title: Utilisation de l'annotation dans les requêtes
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 50855b30-d5fe-49a9-89d3-3f1bfd670958
ms.openlocfilehash: 3dd5d19cc303314386ae62ba67f7eec978f6d80b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185364"
---
# <a name="using-annotation-in-queries"></a>Utilisation de l'annotation dans les requêtes

Grâce aux annotations, vous pouvez baliser arbitrairement des enregistrements de suivi avec une valeur configurable après la génération. Par exemple, vous pouvez avoir besoin de plusieurs enregistrements de suivi sur plusieurs flux de travail à baliser avec « serveur de messagerie » = = « messagerie Serveur1 ». Lors de l’interrogation ultérieure d’enregistrements de suivi, cela facilite la recherche de tous les enregistrements ayant cette étiquette.  
  
## <a name="adding-annotations"></a>Ajout d'annotations  

 Une annotation peut être ajoutée à une requête de suivi tel qu'indiqué dans l'exemple suivant.  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <annotations>  
    <annotation name="MailServer" value="Mail Server1"/>  
  </annotations>  
</activityStateQuery>  
```  
  
> [!NOTE]
> Ces éléments de requête de suivi peuvent être utilisés pour créer un modèle de suivi. Un modèle de suivi peut être créé dans la configuration ou à l'aide du code.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [\<participants>](participants.md)
- [Suivi et traçage de workflow](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Modèles de suivi](../../../windows-workflow-foundation/tracking-profiles.md)

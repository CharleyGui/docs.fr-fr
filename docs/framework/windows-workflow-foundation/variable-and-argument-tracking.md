---
title: Suivi de variables et arguments
ms.date: 03/30/2017
ms.assetid: 8f3d9d30-d899-49aa-b7ce-a8d0d32c4ff0
ms.openlocfilehash: 85cecbfaf1db224152d4582325326f1f80e08266
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242901"
---
# <a name="variable-and-argument-tracking"></a>Suivi de variables et arguments

Lors du suivi de l'exécution d'un workflow, il est souvent utile d'extraire des données. Vous obtenez ainsi un contexte supplémentaire lors de l'accès à une post-exécution d'enregistrement de suivi. Dans [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], vous pouvez extraire toute variable ou argument visible dans l’étendue de toute activité d’un flux de travail utilisant le suivi. Les profils de suivi facilitent l'extraction de données.  
  
## <a name="variables-and-arguments"></a>Variables et arguments  

 Les variables et arguments sont extraits lorsqu'une activité émet un objet ActivityStateRecord.  Une variable est disponible pour l'extraction, seulement si elle se trouve dans l'étendue de l'activité. Une variable à extraire dans une activité est spécifiée comme suit :  
  
- Si une variable est spécifiée par son nom, le suivi recherche la variable dans l'activité en cours de suivi et dans les activités parentes. Elle est recherchée dans l'étendue de l'activité en cours et dans l'étendue parente.  
  
- Si les variables à extraire sont spécifiées à l’aide de Name = " \* ", toutes les variables dans l’activité en cours de suivi sont extraites. Dans ce cas, les variables qui sont dans l'étendue, mais définies dans les activités parentes ne sont pas extraites.  
  
 Lors de l’extraction d’arguments, les arguments extraits dépendent de l’état de l’activité. Lorsque l'état d'une activité est Exécution, seuls les `InArguments` sont disponibles pour l'extraction. Pour tout autre état d’activité (Closed, Faulted, Canceled), tous les arguments, InArguments et OutArguments, sont disponibles pour l’extraction.  
  
 L’exemple suivant illustre une requête d’état d’activité qui extrait des variables et arguments lorsque l’enregistrement de suivi `Closed` de l’activité est émis. Les variables et arguments peuvent être extraits uniquement avec un objet <xref:System.Activities.Tracking.ActivityStateRecord> et l’abonnement à ces derniers se fait donc à partir d’un modèle de suivi à l’aide de l’objet <xref:System.Activities.Tracking.ActivityStateQuery>.  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="protecting-information-stored-within-variables-and-arguments"></a>Protection des informations stockées dans les variables et arguments  

 Par défaut, une variable ou un argument suivi est rendu visible par le runtime WF. Un développeur de workflow peut les protéger contre tout accès en procédant comme suit :  
  
1. Chiffrez la valeur d'une variable.  
  
2. Contrôlez la création d’un modèle de suivi pour éviter l’extraction de variable ou d’argument.  
  
3. Pour les participants au suivi personnalisé, vérifiez que le code WF ne divulgue pas les informations sensibles stockées dans les variables ou les arguments.  
  
## <a name="see-also"></a>Voir aussi

- [Analyse Windows Server App Fabric](/previous-versions/appfabric/ee677251(v=azure.10))
- [Surveillance des applications avec application Fabric](/previous-versions/appfabric/ee677276(v=azure.10))

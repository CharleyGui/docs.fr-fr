---
title: <state>de WCF,<workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
ms.openlocfilehash: 80f7532f3c51680a2e34713b526dc43822db61b9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854953"
---
# <a name="state-of-wcf-workflowinstancequery"></a>\<> d’état de WCF \<, workflowInstanceQuery >
Représente une collection d’états faisant l’objet d’un abonnement dans l’instance de flux de travail suivie lors de la création des enregistrements de suivi.  
  
 Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<suivi des >** ](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<profils >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de flux de travail**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQueries >** ](workflowinstancequeries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQuery >** ](workflowinstancequery-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<États >** ](states-of-wcf-workflowinstancequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> d’État**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <workflowInstanceQueries>
          <workflowInstanceQuery>
            <states>
              <state name="Name" />
            </states>
          </workflowInstanceQuery>
        </workflowInstanceQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.
  
### <a name="attributes"></a>Attributs

|Attribut|Description|  
|---------------|-----------------|  
|`name`|Chaîne qui spécifie un état faisant l'objet d'un abonnement dans l'instance de flux de travail suivie lors de la création de l'enregistrement de suivi.|  
  
### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|  
|-------------|-----------------|  
|[\<states>](states-of-wcf-workflowinstancequery.md)|Collection d'états faisant l'objet d'un abonnement dans l'instance de flux de travail suivie lors de la création des enregistrements de suivi.|  
  
## <a name="remarks"></a>Notes  

Les enregistrements retournés sont filtrés par états dans cette collection.  
  
Les valeurs d’État possibles sont décrites dans le tableau suivant :
  
|État|Description|  
|-----------|-----------------|  
|Abandonné|L'instance de flux de travail est abandonnée.|  
|Terminé|L'instance de flux de travail est terminée.|  
|Supprimé|L'instance de flux de travail est supprimée.|  
|Inactif|L'instance de workflow est inactive.|  
|Persistant|L'instance de flux de travail est persistante.|  
|Repris|L'instance de flux de travail est reprise.|  
|Démarré|L'instance de flux de travail est démarrée.|  
|UnhandledException|L'instance de flux de travail a rencontré une exception non gérée.|  
|Non chargé|L'instance de flux de travail est déchargée.|  
|Canceled|L'instance de flux de travail est annulée.|  
|Interrompu|L'instance de workflow est interrompue.|  
|Arrêté|L'instance de flux de travail est arrêtée.|  
|Unsuspended|L'instance de flux de travail est non interrompue.|  
  
## <a name="example"></a>Exemple

La configuration suivante permet de s'abonner aux enregistrements de suivi au niveau de l'instance de flux de travail pour l'état de l'instance `Started` à l'aide de cette requête.  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [Suivi et traçage de workflow](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Profils de suivi](../../../windows-workflow-foundation/tracking-profiles.md)

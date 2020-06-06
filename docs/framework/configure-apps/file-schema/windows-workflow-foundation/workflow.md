---
title: <workflow>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560aa9b6-9cf3-460e-b798-f87d14b1d2de
ms.openlocfilehash: e2df5d83375b2daa2e39ba1ee990c47a6a04f6fb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79151856"
---
# \<workflow>
Élément de configuration qui contient toutes les requêtes d'un flux de travail spécifique identifié par la propriété <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType>.  
  
 Pour plus d’informations sur le suivi de workflow et sa configuration, consultez [suivi et traçage de workflow](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) et [profils](../../../windows-workflow-foundation/tracking-profiles.md)de suivi.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflow>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <participants>
        <add name="String"
             profileName="String"
             type="String" />
      </participants>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String"
                                    childActivityName="String"/>
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String" />
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String"  />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQueries>
          <bookmarkResumptionQueries>
            <bookmarkResumptionQuery name="String" />
          </bookmarkResumptionQueries>
          <cancelRequestQueries>
            <cancelRequestQuery activityName="String"
                                childActivityName="String"/>
          </cancelRequestQueries>
          <customTrackingQueries>
            <customTrackingQuery activityName="String"
                                 name="String"/>
          </customTrackingQueries>
          <faultPropagationQueries>
            <faultPropagationQuery activityName="String"
                                   faultHandlerActivityName="String" />
          </faultPropagationQueries>
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="String" />
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|activityDefinitionId|Chaîne qui spécifie l'ID de définition de l'activité du flux de travail faisant l'objet d'un suivi.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<activityScheduledQueries>](activityscheduledqueries.md)|Représente une collection de requêtes qui permettent d'effectuer le suivi d'une activité dont l'exécution par une activité parent est planifiée. La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements d'une activité planifiée.|  
|[\<activityStateQueries>](activitystatequeries.md)|Représente une collection de requêtes qui permettent d’effectuer le suivi des changements dans le cycle de vie des activités qui composent une instance de workflow. Par exemple, vous pouvez effectuer le suivi de chaque fois que l’activité « Envoyer un message électronique » se termine dans une instance de Workflow. Cette requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement d'état d'activité. Les états disponibles auxquels s'abonner sont spécifiés dans ActivityStates.|  
|[\<bookmarkResumptionQueries>](bookmarkresumptionqueries.md)|Représente une collection de requêtes qui permettent d’effectuer le suivi de la reprise d’un signet dans une instance de flux de travail. La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de reprise de signet.|  
|[\<cancelRequestedQueries>](cancelrequestedqueries.md)|Représente une collection de requêtes qui permettent d’effectuer le suivi des demandes d’annulation d’une activité enfant par l’activité parent. La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.|  
|[\<customTrackingQueries>](customtrackingqueries.md)|Représente une collection de requêtes permettant d'effectuer le suivi des événements que vous définissez dans vos activités de code. La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de suivi personnalisés.|  
|[\<faultPropagationQueries>](faultpropagationqueries.md)|Représente une collection de requêtes qui permettent d’effectuer le suivi de la gestion des erreurs qui se produisent dans une activité.  Cet événement se produit chaque fois qu'un FaultHandler traite une erreur. Vous devez utiliser cette requête pour effectuer le suivi de la gestion des erreurs qui se produisent dans une activité. La requête est nécessaire pour qu'un participant au suivi puisse s'abonner aux enregistrements de propagation d'erreur.|  
|[\<workflowInstanceQueries>](workflowinstancequeries.md)|Représente une collection d'éléments de configuration qui effectuent le suivi des changements dans le cycle de vie d'une instance de flux de travail, tels que le début ou la fin d'un événement.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<trackingProfile>](trackingprofile.md)|Représente une section de configuration pour la création d'un abonnement à des enregistrements de suivi de flux de travail dans un participant au suivi. Un modèle de suivi contient des requêtes de suivi qui permettent à un participant au suivi de s'abonner à des événements de flux de travail émis lorsque l'état d'une instance de flux de travail change au moment de l'exécution. Les requêtes définies dans la section de modèle de suivi déterminent les types d'événements retournés par l'abonnement.|  
  
## <a name="remarks"></a>Remarques  
 Les modèles de suivi contiennent des requêtes de suivi qui permettent à un participant au suivi de s'abonner à des événements de flux de travail émis lorsque l'état d'une instance de flux de travail particulière change au moment de l'exécution. L'instance de flux de travail faisant l'objet d'un suivi est identifiée par cet élément de configuration.  
  
 Selon vos exigences d’analyse, vous pouvez écrire un profil très général, qui s’abonne à un petit jeu de modifications d’état de haut niveau d’un workflow. Inversement, vous pouvez créer un profil très spécifique dont les événements résultants sont suffisamment riches pour reconstruire ultérieurement un flux d'exécution détaillé.  
  
 Les modèles de suivi sont structurés comme des abonnements déclaratifs aux enregistrements de suivi qui vous permettent d'interroger le runtime de flux de travail pour rechercher des enregistrements de suivi particuliers. Quelques types de requêtes vous permettent de vous abonner à différentes classes d'enregistrements de suivi. Pour obtenir la liste complète des requêtes, consultez la liste des éléments enfants de cette rubrique et des [profils de suivi](../../../windows-workflow-foundation/tracking-profiles.md).  
  
 L’exemple suivant montre un modèle de suivi dans un fichier de configuration qui permet à un participant de suivi de s’abonner aux `Started` `Completed` événements de flux de travail et.  
  
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
   </profiles>  
  </tracking>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [Suivi et traçage de workflow](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Profils de suivi](../../../windows-workflow-foundation/tracking-profiles.md)

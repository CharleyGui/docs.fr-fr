---
title: <behavior> de <serviceBehaviors>
ms.date: 03/30/2017
ms.assetid: 78fc0a08-55de-416a-ac12-a5e6ffc9a987
ms.openlocfilehash: a17fac5c519f41588ef90383f024e645b809b49b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400605"
---
# <a name="behavior-of-servicebehaviors"></a>\<> de comportement \<de la > serviceBehaviors
L'élément `behavior` contient une collection de paramètres concernant le comportement d'un service. Chaque comportement est indexé en fonction de son `name`. Les services peuvent être liés à chaque comportement via ce nom `behaviorConfiguration` à l’aide de l’attribut de l' [ \<élément de point de terminaison >](endpoint-element.md) . Ceci permet aux points de terminaison de partager des configurations de comportement communes sans redéfinir les paramètres. Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d’avoir un nom. Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).  
  
> [!NOTE]
> Les éléments de comportement spécifiques aux activités de flux de travail Windows, tels que l' [ \<élément sendMessageChannelCache >](../windows-workflow-foundation/sendmessagechannelcache.md) , sont documentés dans le [ \<> de comportement de la page de \<> serviceBehaviors](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) .  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de comportement**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <serviceBehaviors>
       <behavior name="String" />
    </serviceBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|name|Chaîne unique qui contient le nom de configuration du comportement. Cette valeur est une chaîne définie par l'utilisateur qui doit être unique, puisqu'elle sert de chaîne d'identification pour l'élément. Depuis [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], les liaisons et les comportements ne sont pas obligés d’avoir un nom. Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-element.md)|Contient les données de configuration pour DataContractSerializer.|  
|[\<persistenceProvider>](persistenceprovider.md)|Indique le type d'implémentation de fournisseur de persistance à utiliser, ainsi que le délai d'expiration à utiliser pour les opérations de persistance.|  
|[\<routing>](routing-of-servicebehavior.md)|Fournit un accès au service de routage au moment de l'exécution afin d'autoriser une modification dynamique de la configuration de routage.|  
|[\<serviceAuthenticationManager>](serviceauthenticationmanager.md)|Fournit un élément de configuration de flux de travail qui établit au niveau du service la validité d'une transmission, d'un message ou d'un expéditeur.|  
|[\<serviceAuthorization>](serviceauthorization-element.md)|Spécifie les paramètres qui autorisent l'accès aux opérations de service.|  
|[\<serviceCredentials>](servicecredentials.md)|Spécifie l'information d'identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation des informations d'identification du client.|  
|[\<serviceDebug>](servicedebug.md)|Spécifie les fonctionnalités de débogage et d’informations d’aide pour un service Windows Communication Foundation (WCF).|  
|[\<serviceDiscovery>](servicediscovery.md)|Spécifie la fonctionnalité de découverte des points de terminaison de service.|  
|[\<serviceMetadata>](servicemetadata.md)|Spécifie la publication de métadonnées de service et des informations associées.|  
|[\<serviceSecurityAudit>](servicesecurityaudit.md)|Spécifie des paramètres qui activent l'audit d'événements de sécurité pendant des opérations de service.|  
|[\<serviceThrottling>](servicethrottling.md)|Spécifie le mécanisme de limitation d’un service WCF.|  
|[\<serviceTimeouts>](servicetimeouts.md)|Spécifie le délai d'attente pour un service.|  
|[\<workflowRuntime>](workflowruntime.md)|Spécifie les paramètres d’une instance de WorkflowRuntime pour l’hébergement des services WCF basés sur le Workflow.|  
|[\<useRequestHeadersForMetadataAddress>](userequestheadersformetadataaddress.md)|Active la récupération des informations d'adresse des métadonnées à partir des en-têtes de message de demande.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors.md)|Collection d’éléments de comportement de service.|

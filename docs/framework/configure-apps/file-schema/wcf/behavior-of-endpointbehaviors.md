---
title: <behavior> de <endpointBehaviors>
ms.date: 03/30/2017
ms.assetid: b90ca3bc-3c22-4174-b903-e3a39898bd27
ms.openlocfilehash: d191b968e1c3fd1db0837ba7e03f210a1b00062d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201497"
---
# <a name="behavior-of-endpointbehaviors"></a>\<behavior> de \<endpointBehaviors>

L’élément `behavior` contient une collection de paramètres concernant le comportement d’un point de terminaison. Chaque comportement est indexé en fonction de son `name`. Les points de terminaison peuvent être liés à chaque comportement à travers ce nom. À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom. Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior name="String" />
    </endpointBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|name|Chaîne unique qui contient le nom de configuration du comportement. Cette valeur est une chaîne définie par l'utilisateur qui doit être unique, puisqu'elle sert de chaîne d'identification pour l'élément. À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom. Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|Indique les informations d'identification utilisées pour authentifier le client auprès d'un service.|  
|[\<callbackDebug>](callbackdebug.md)|Spécifie le débogage de service pour un objet de rappel Windows Communication Foundation (WCF).|  
|[\<callbackTimeouts>](callbacktimeouts.md)|Spécifie le délai d'attente pour le rappel du client.|  
|[\<clientVia>](clientvia.md)|Spécifie l'itinéraire qu'un message doit suivre.|  
|[\<dataContractSerializer>](datacontractserializer.md)|Contient les données de configuration pour DataContractSerializer.|  
|[\<dispatcherSynchronization>](dispatchersynchronization.md)|Spécifie un comportement de point de terminaison qui permet à un service d'envoyer des réponses de manière asynchrone.|  
|[\<enableWebScript>](enablewebscript.md)|Active le comportement de point de terminaison qui permet de consommer le service à partir de pages Web ASP.NET AJAX. Le comportement doit être utilisé uniquement avec la \<webHttpBinding> liaison standard ou l' \<webMessageEncoding> élément de liaison.|  
|[\<endpointDiscovery>](endpointdiscovery.md)|Spécifie les différents paramètres de découverte d’un point de terminaison, tels que la fonctionnalité de découverte, les portées et toutes les extensions personnalisées de ses métadonnées.|  
|[\<soapProcessing>](soapprocessing.md)|Définit le comportement de point de terminaison client utilisé pour marshaler des messages entre les versions de message et les types de liaison différents.|  
|[\<synchronousReceive>](synchronousreceive-element.md)|Spécifie le comportement au moment de l'exécution pour la réception de messages dans une application de service ou cliente. Il n'a aucun attribut ou élément enfant.|  
|[\<transactedBatching>](transactedbatching.md)|Spécifie si le traitement par lots de la transaction est pris en charge pour les opérations de réception.|  
|[\<webHttp>](webhttp.md)|Spécifie le WebHttpBehavior d'un point de terminaison via la configuration. Ce comportement, lorsqu’il est utilisé conjointement avec la \<webHttpBinding> liaison standard, active le modèle de programmation Web pour un service WCF.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<endpointBehaviors>](endpointbehaviors.md)|Collection d’éléments de comportement de point de terminaison.|

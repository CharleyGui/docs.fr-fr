---
title: <discoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
ms.openlocfilehash: 32b14f8fb3235040a51455f2099a403c8312c699
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855397"
---
# \<discoveryEndpoint>

Cet élément de configuration définit un point de terminaison standard avec un contrat de découverte fixe. Lorsqu'il est ajouté à la configuration du service, il spécifie où écouter les messages de découverte. Lorsqu'il est ajouté à la configuration client, il spécifie où envoyer les requêtes de découverte.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryEndpoint>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <discoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed"
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxResponseDelay="Timespan"
                        name="String" />
    </discoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs

| Attribut        | Description |  
| ---------------- | ----------- |  
| discoveryMode    | Chaîne qui spécifie le mode de protocole de découverte. Les valeurs valides sont « adhoc » et « Managed ». En mode managé, le protocole repose sur un proxy de découverte, qui fait office de référentiel des services détectables. Le mode ad hoc nécessite que le protocole utilise le mécanisme de multidiffusion UDP pour rechercher les services disponibles. Pour plus d’informations sur la propriété, consultez <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A> . |  
| discoveryVersion | Chaîne qui spécifie l'une des deux versions du protocole WS-Discovery. Les valeurs valides sont WSDiscovery11 et WSDiscoveryApril2005. Cette valeur est de type <xref:System.ServiceModel.Discovery.DiscoveryVersion>. |  
| maxResponseDelay | Valeur Timespan qui indique la valeur maximale du délai d'attente du protocole de découverte avant l'envoi de certains messages, tels que ceux de type Probe Match ou Resolve Match.<br /><br /> Si tous les messages ProbeMatches sont envoyés en même temps, une tempête de réseau peut en résulter. Pour empêcher cet effet, les messages ProbeMatches sont envoyés avec un délai aléatoire entre chaque message ProbeMatch. Le délai aléatoire est compris entre 0 et la valeur définie par cet attribut. Si l'attribut a la valeur 0, les messages ProbeMatches sont envoyés dans une boucle serrée sans délai. Sinon, les messages ProbeMatches sont envoyés avec un délai aléatoire de sorte que la durée totale nécessaire à l'envoi de tous les messages ProbeMatches ne dépasse pas le maxResponseDelay. Cette valeur est uniquement pertinente pour les services, elle n'est pas utilisée par les clients. |  
| `name`           | Chaîne qui spécifie le nom de la configuration du point de terminaison standard. Le nom est utilisé dans l'attribut `endpointConfiguration` du point de terminaison de service pour lier un point de terminaison standard à sa configuration. |  
  
### <a name="child-elements"></a>Éléments enfants

Aucun.  
  
### <a name="parent-elements"></a>Éléments parents

| Élément | Description |  
| ------- | ----------- |  
| [\<standardEndpoints>](standardendpoints.md) | Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés (adresse, liaison, contrat) sont fixes. |  
  
## <a name="example"></a>Exemple

L'exemple suivant montre un service qui écoute des messages de découverte sur un transport de multidiffusion Peernet. L'exemple spécifie de manière explicite la version WS-Discovery Avril 2005.  
  
La configuration du point de terminaison standard est définie par service et ne peut pas être partagée entre les services. Si un autre service souhaite avoir le même point de terminaison de découverte, la même configuration doit être ajoutée à la section de ce service.  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService" />
    <endpoint name="peerNetDiscovery"
              binding="peerTcpBinding"
              address="net.p2p://discoveryMesh/multicast"
              kind="discoveryEndpoint"
              endpointConfiguration="peerTcpDiscoveryEndpointConfiguration"
              bindingConfiguration="discoveryPeerTcpBindingConfig" />
  </service>
</services>
<standardEndpoints>
  <discoveryEndpoint>
    <standardEndpoint name="peerTcpDiscoveryEndpointConfiguration"
                      version="WSDiscoveryApril2005" />
  </discoveryEndpoint>
</standardEndpoints>
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>

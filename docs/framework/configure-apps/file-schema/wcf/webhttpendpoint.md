---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 8d4f55fd5b51ea77839b7fdbb930e937f5700417
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854799"
---
# <a name="webhttpendpoint"></a>\<webHttpEndpoint>
Cet élément de configuration définit un point de terminaison standard avec une liaison [ \<WebHttpBinding >](webhttpbinding.md) fixe qui ajoute automatiquement le comportement de [ \<> Webhttp](webhttp.md) . Utilisez ce point de terminaison lors de l'écriture d'un service REST.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<webHttpEndpoint >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint automaticFormatSelectionEnabled="String"
                        defaultOutgoingResponseFormat="Xml/Json"
                        helpEnabled="Boolean"
                        webEndpointType="String" />
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|automaticFormatSelectionEnabled|Valeur booléenne qui indique si la sélection automatique du format est activée.<br /><br /> Lorsque la sélection automatique du format est activée, l'infrastructure analyse l'en-tête `Accept` du message de demande et détermine le format de réponse le plus approprié. Si l'en-tête `Accept` ne spécifie pas de format de réponse approprié, l'infrastructure utilise le `Content-Type` du message de demande ou le format de réponse par défaut de l'opération.|  
|defaultOutgoingResponseFormat|Attribut qui spécifie le format de réponse sortant par défaut. Cet attribut est de type <xref:System.ServiceModel.Web.WebMessageFormat>.|  
|helpEnabled|Valeur booléenne qui indique si la page d'aide HTTP est activée pour le point de terminaison.|  
|webEndpointType|Chaîne qui spécifie le type du point de terminaison.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés (adresse, liaison, contrat) sont fixes.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>

---
title: <add> de <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: df69b5f8a79489b722c1074f118b9c6f6e8e363d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926668"
---
# <a name="add-of-protocolmapping"></a>\<Ajouter > de \<la > protocolMapping
Représente un mappage de protocole par défaut entre un schéma de protocole de transport (par exemple, http, net. TCP, net. pipe, etc.) et une liaison Windows Communication Foundation (WCF). Lors de la création de points de terminaison par défaut au moment de l’exécution, WCF examine les mappages configurés et décide de la liaison à utiliser pour une adresse de base particulière.  
  
 \<system.serviceModel>  
\<protocolMapping>  
\<add>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Élément|Description|  
|-------------|-----------------|  
|liaison|Chaîne qui spécifie le type de liaison à utiliser pour un point de terminaison pendant la création de points de terminaison par défaut.|  
|bindingConfiguration|Chaîne qui spécifie le nom de la section de configuration de liaison à référencer.|  
|scheme|Schéma de protocole de transport à utiliser pour le point de terminaison par défaut.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<protocolMapping>](protocolmapping.md)|Représente une section de configuration pour la définition de mappages de protocole par défaut entre des schémas de protocole de transport (par exemple, http, net. TCP, net. pipe, etc.) et des liaisons Windows Communication Foundation (WCF).|  
  
## <a name="example"></a>Exemple  
 L'exemple de configuration suivant montre le mappage de protocole par défaut dans le fichier machine.config. Vous pouvez remplacer ce mappage par défaut au niveau de l'ordinateur en modifiant le fichier machine.config. Ou, si vous souhaitez uniquement le remplacer dans la portée d'une application, vous pouvez remplacer cette section dans le fichier de configuration de votre application et modifier le mappage pour les schémas de protocole individuels.  
  
```xml  
<protocolMapping>
  <add scheme="http"
       binding="basicHttpBinding" />
  <add scheme="net.tcp"
       binding="netTcpBinding" />
  <add scheme="net.pipe"
       binding="netNamedPipeBinding" />
  <add scheme="net.msmq"
       binding="netMsmqBinding" />
</protocolMapping>
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>

---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: e2fec2c2e5979b08ed0d832f636b3d0847b9a5dc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915660"
---
# <a name="textmessageencoding"></a>\<textMessageEncoding>
Spécifie l'encodage de caractères et le suivi des versions de message utilisés pour les messages XML textuels.  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<textMessageEncoding>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|maxReadPoolSize|Entier qui spécifie combien de messages peuvent être lus de manière simultanée sans allouer de nouveaux lecteurs. Des pools plus volumineux permettent au système d'être plus tolérant aux pics d'activité au prix d'une plage de travail plus volumineuse. La valeur par défaut est 64.|  
|maxWritePoolSize|Entier qui spécifie combien de messages peuvent être envoyés simultanément sans allouer de nouveaux enregistreurs. Des pools plus volumineux permettent au système d'être plus tolérant aux pics d'activité au prix d'une plage de travail plus volumineuse. La valeur par défaut est 16.|  
|messageVersion|Spécifie la version SOAP des messages envoyés à l'aide de la liaison. Les valeurs valides sont les suivantes :<br /><br /> - Soap11Addressing10<br />- Soap12Addressing10<br />- Soap11<br />-Soap12<br /><br />La valeur par défaut est Soap12Addressing10. Cet attribut est de type <xref:System.ServiceModel.Channels.MessageVersion>.|  
|writeEncoding|Spécifie l'encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison. Les valeurs valides sont les suivantes :<br /><br /> UnicodeFffeTextEncoding Encodage BigEndian Unicode<br />Utf16TextEncoding Encodage Unicode<br />Utf8TextEncoding encodage 8 bits<br /><br /> La valeur par défaut est Utf8TextEncoding. Cet attribut est de type <xref:System.Text.Encoding>.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison. Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<binding>](../../../misc/binding.md)|Définit toutes les fonctions de liaison d’une liaison personnalisée.|  
  
## <a name="remarks"></a>Notes  
 L'encodage est le processus de transformation d'un message en une séquence d'octets. Le décodage est le processus inverse. Windows Communication Foundation (WCF) comprend trois types d’encodage pour les messages SOAP: Texte, binaire et MTOM (Message Transmission Optimization Mechanism).  
  
 L'encodage de texte représenté par l'élément `textMessageEncoding` est l'encodeur le plus interopérable, mais le moins efficace pour les messages XML.  L'encodeur de texte crée des messages textuels sur le câble. Les messages produits par cet encodeur sont adaptés à l'interopérabilité basée sur WS-*. Les services Web ou les clients de ces services comprennent généralement le XML textuel. Toutefois, la transmission de grands blocs de données binaires sous forme de texte est la méthode d'encodage de messages XML la moins efficace.  
  
## <a name="example"></a>Exemples  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [Sélection d’un encodeur de message](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [Encodage de message](message-encoding.md)
- [Liaisons](../../../wcf/bindings.md)
- [Extension de liaisons](../../../wcf/extending/extending-bindings.md)
- [Liaisons personnalisées](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)

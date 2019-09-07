---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: a73085320eaf248887422316e1b7787b8654d71d
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400488"
---
# <a name="compositeduplex"></a>\<compositeDuplex>
Définit l'élément de liaison utilisé lorsque le client doit exposer un point de terminaison pour permettre au service de renvoyer des messages au client.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<compositeDuplex >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|clientBaseAddress|URI qui définit l'adresse du canal arrière en mode duplex. Le service utilise cette adresse pour entrer en contact et établir une connexion avec le client.<br /><br /> Si cet attribut n’est pas défini, une adresse par`full qualified name+default port\TemporaryIndigoAddress\guid`défaut "" est générée. Par défaut, il s’agit de `null`.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<binding>](../../../misc/binding.md)|Définit toutes les fonctions de liaison d’une liaison personnalisée.|  
  
## <a name="remarks"></a>Notes  
 Cet élément de configuration est utilisé avec les transports qui n'autorisent pas de communications duplex en mode natif, par exemple, HTTP. En revanche, TCP autorise nativement les communications duplex et ne requiert pas l'utilisation de cet élément de liaison pour permettre au service de renvoyer des messages à un client.  
  
 Le client doit exposer une adresse pour que le service puisse entrer en contact avec lui et établir une connexion. Cette adresse cliente est fournie par l'attribut `clientBaseAddress`. Notez que Windows Communication Foundation (WCF) génère automatiquement un attribut ClientBaseAddress si aucun n'est explicitement défini par l'utilisateur.  
  
## <a name="example"></a>Exemples  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Liaisons](../../../wcf/bindings.md)
- [Extension de liaisons](../../../wcf/extending/extending-bindings.md)
- [Liaisons personnalisées](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)

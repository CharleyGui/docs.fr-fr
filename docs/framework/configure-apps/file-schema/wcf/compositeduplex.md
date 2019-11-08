---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: c3bae4dfee36e9de62c27bbccecd9a31a5b7d459
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736780"
---
# <a name="compositeduplex"></a>\<compositeDuplex >
Définit l'élément de liaison utilisé lorsque le client doit exposer un point de terminaison pour permettre au service de renvoyer des messages au client.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**customBinding >** ](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\< **\**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**compositeDuplex >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|clientBaseAddress|URI qui définit l'adresse du canal arrière en mode duplex. Le service utilise cette adresse pour entrer en contact et établir une connexion avec le client.<br /><br /> Si cet attribut n’est pas défini, une adresse par défaut «`full qualified name+default port\TemporaryIndigoAddress\guid`» est générée. La valeur par défaut est `null`,|  
  
### <a name="child-elements"></a>Éléments enfants  
 aucune.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[liaison de \<](bindings.md)|Définit toutes les fonctions de liaison d’une liaison personnalisée.|  
  
## <a name="remarks"></a>Notes  
 Cet élément de configuration est utilisé avec les transports qui n'autorisent pas de communications duplex en mode natif, par exemple, HTTP. En revanche, TCP autorise nativement les communications duplex et ne requiert pas l'utilisation de cet élément de liaison pour permettre au service de renvoyer des messages à un client.  
  
 Le client doit exposer une adresse pour que le service puisse entrer en contact avec lui et établir une connexion. Cette adresse cliente est fournie par l'attribut `clientBaseAddress`. Notez que Windows Communication Foundation (WCF) génère automatiquement un attribut ClientBaseAddress si aucun n'est explicitement défini par l'utilisateur.  
  
## <a name="example"></a>Exemple  
  
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
- [\<customBinding >](custombinding.md)

---
title: <endpoint> de <client>
ms.date: 03/30/2017
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
ms.openlocfilehash: f1ffbc1e8efac70523d7f631c8cf9ba9a1622bfc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855316"
---
# <a name="endpoint-of-client"></a>\<endpoint> de \<client>
Spécifie les propriétés du contrat, de la liaison et de l’adresse du point de terminaison du canal employées par les clients pour se connecter aux points de terminaison de service sur le serveur.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpoint>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<endpoint address="String"
          behaviorConfiguration="String"
          binding="String"
          bindingConfiguration="String"
          contract="String"
          endpointConfiguration="String"
          kind="String"
          name="String">
</endpoint>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|address|Attribut de chaîne requis.<br /><br /> Spécifie l'adresse du point de terminaison. La valeur par défaut est une chaîne vide. L'adresse doit être un URI absolu.|  
|behaviorConfiguration|Chaîne qui contient le nom de comportement du comportement à utiliser pour instancier le point de terminaison. Le nom du comportement doit être dans la portée, au niveau où le service est défini. La valeur par défaut est une chaîne vide.|  
|binding|Attribut de chaîne requis.<br /><br /> Chaîne qui indique le type de liaison à utiliser. Ce type doit posséder une section de configuration inscrite pour pouvoir être référencé. Il est inscrit en fonction du nom de la section et non en fonction du nom du type de la liaison.|  
|bindingConfiguration|facultatif. Chaîne qui contient le nom de la configuration de liaison à utiliser lorsque le point de terminaison est instancié. La configuration de la liaison doit être dans la portée, au niveau où le point de terminaison est défini. La valeur par défaut est une chaîne vide.<br /><br /> Cet attribut est utilisé conjointement à `binding` pour référencer une configuration de liaison spécifique dans le fichier de configuration. Définissez cet attribut si vous essayez d’utiliser une liaison personnalisée. Sinon, une exception peut être levée.|  
|contract|Attribut de chaîne requis.<br /><br /> Chaîne qui indique le contrat exposé par ce point de terminaison. L'assembly doit implémenter le type de contrat.|  
|endpointConfiguration|Chaîne qui spécifie le nom du point de terminaison standard défini par l'attribut `kind`, qui fait référence aux informations de configuration supplémentaires de ce point de terminaison standard. Le même nom doit être défini dans la section `<standardEndpoints>`.|  
|kind|Chaîne qui spécifie le type de point de terminaison standard appliqué. Le type doit être inscrit dans la `<extensions>` section ou dans machine. config. Si rien n’est spécifié, un point de terminaison de canal commun est créé.|  
|name|Attribut de chaîne facultatif. Cet attribut identifie uniquement un point de terminaison pour un contrat donné. Vous pouvez définir plusieurs clients pour un type de contrat donné. Chaque définition doit être différenciée par un nom de configuration unique. Si cet attribut est omis, le point de terminaison correspondant est utilisé comme point de terminaison par défaut associé au type de contrat spécifié. La valeur par défaut est une chaîne vide.<br /><br /> L'attribut `name` d'une liaison est utilisé pour l'exportation de définition à travers WSDL.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<headers>](headers.md)|Collection d'en-têtes d'adresses.|  
|[\<identity>](identity.md)|Identité qui permet l'authentification d'un point de terminaison par les autres points de terminaison qui échangent des messages avec lui.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<client>](client.md)|Section de configuration qui définit une liste des points de terminaison auxquels un client peut se connecter.|  
  
## <a name="example"></a>Exemple  
 Il s'agit d'un exemple de configuration de point de terminaison de canal.  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          name="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
</endpoint>
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>
- <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- [Configuration client WCF](../../../wcf/feature-details/client-configuration.md)
- [Clients](../../../wcf/feature-details/clients.md)

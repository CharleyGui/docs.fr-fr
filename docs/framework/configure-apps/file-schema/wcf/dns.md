---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: e49a564c9793b371425b2b787586bb9d3cbed58b
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452225"
---
# <a name="dns"></a>> DNS \<
Spécifie l'identité attendue du serveur. Cette identité est valide pour le mode d'authentification du certificat X509 si le certificat du serveur contient un DNS avec la même valeur. Elle est également valide pour le mode d'authentification Windows si le SPN a la même valeur.  
  
Pour plus d’informations sur la définition de la valeur de l’élément, consultez [identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md).  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<> [**client**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **&nbsp;&nbsp;\<** ](endpoint-of-client.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<> d' [**identité**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**DNS** >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|valeur|Système DNS du certificat. Le système DNS est un protocole standard utilisé pour localiser des ordinateurs sur un réseau IP. Les utilisateurs peuvent mémoriser les noms d’affichage, tels que `https://go.microsoft.com/fwlink/?prd=10929` ou `https://go.microsoft.com/fwlink/?LinkID=96165`, plus faciles que les adresses basées sur les nombres, par exemple composées.|  
  
### <a name="child-elements"></a>Éléments enfants  
 None.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<d’identité >](identity.md)|Spécifie l'identité du service à authentifier par le client.|  
  
## <a name="example"></a>Exemple  
 Le code de configuration suivant spécifie le système DNS d'un certificat X.509 utilisé pour authentifier un serveur.  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [Identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<d’identité >](identity.md)

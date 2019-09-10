---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: c68cabd03eca71b41a0d0acce26897fa2653f4d3
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855373"
---
# <a name="dns"></a>\<dns>
Spécifie l'identité attendue du serveur. Cette identité est valide pour le mode d'authentification du certificat X509 si le certificat du serveur contient un DNS avec la même valeur. Elle est également valide pour le mode d'authentification Windows si le SPN a la même valeur.  
  
Pour plus d’informations sur la définition de la valeur de l’élément, consultez [identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md).  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> client**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<point de terminaison >** ](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> d’identité**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> DNS**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|value|Système DNS du certificat. Le système DNS est un protocole standard utilisé pour localiser des ordinateurs sur un réseau IP. Les utilisateurs peuvent mémoriser les noms d' <https://go.microsoft.com/fwlink/?prd=10929> affichage [https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165), tels que ou, plus faciles que les adresses basées sur les nombres, par exemple composées.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<identity>](identity.md)|Spécifie l'identité du service à authentifier par le client.|  
  
## <a name="example"></a>Exemples  
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
- [\<identity>](identity.md)

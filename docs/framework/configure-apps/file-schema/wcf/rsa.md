---
title: <rsa>
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: 0e1651f563bdb2b2b24eacacf7bfe387e33a82c7
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855048"
---
# <a name="rsa"></a>\<rsa>
Un client WCF sécurisé qui se connecte à un point de terminaison avec cette identité vérifie que les revendications présentées par le serveur contiennent une revendication intégrant la clé publique RSA utilisée pour construire cette identité.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> client**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<point de terminaison >** ](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> d’identité**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> RSA**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|value|Chaîne facultative. Valeur de clé publique RSA à comparer sur le client.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<identity>](identity.md)|Spécifie l'identité du service à authentifier par le client.|  
  
## <a name="remarks"></a>Notes  
 Un contrôle RSA vous permet de limiter l'authentification à un seul certificat basé sur sa clé RSA ou de générer votre propre valeur de clé RSA. Cette opération active une authentification plus stricte d'une clé RSA spécifique aux dépens du service, qui n'utilise plus les clients existants lorsque la valeur de clé RSA est modifiée.  
  
 Pour plus d’informations sur l’utilisation de l’identité pour valider un service auprès d’un client, consultez [identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="example"></a>Exemple  
 Le code de configuration suivant spécifie la valeur de clé publique d'un certificat X.509 utilisé pour authentifier un serveur.  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [Identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)

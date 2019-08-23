---
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 423a3249a9298675517f0cff08566c3735fa35f1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940516"
---
# <a name="userprincipalname"></a>\<userPrincipalName>
Indique le nom d'utilisateur principal (UPN) d'un service à authentifier par le client.  
  
 Pour plus d’informations sur la définition de l’UPN, consultez [identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md).  
  
\<identity>  
\<userPrincipalName>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|value|Nom de compte d'utilisateur (parfois connu sous le nom de connexion d'utilisateur) et nom de domaine identifiant le domaine dans lequel se trouve le compte d'utilisateur. Il s'agit de la méthode de connexion standard à un domaine Windows. Le format est le someone@example.com suivant: (comme pour une adresse de messagerie).|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<identity>](identity.md)|Spécifie l'identité du service à authentifier par le client.|  
  
## <a name="remarks"></a>Notes  
 Un client Windows Communication Foundation sécurisé (WCF) qui se connecte à un point de terminaison avec cette identité utilise l’UPN lors de l’exécution de l’authentification SSPI avec le point de terminaison.  
  
## <a name="example"></a>Exemple  
 Le code de configuration suivant indique le nom UPN du service devant être authentifié par le client.  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [Identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)

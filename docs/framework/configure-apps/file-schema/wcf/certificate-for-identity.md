---
title: <certificate> pour <identity>
ms.date: 03/30/2017
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
ms.openlocfilehash: 52d1fa31cebd949c91809464976739ef1334af29
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919613"
---
# <a name="certificate-for-identity"></a>\<> de certificat \<pour l’identité >
Spécifie un certificat X.509 utilisé pour valider un serveur auprès d'un client.  
  
 Pour plus d’informations sur la définition de la valeur de l’élément, consultez [identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md).  
  
 \<identity>  
\<certificate>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<certificate encodedValue = "String" />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|encodedValue|Encodage Base64 du certificat.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<identity>](identity.md)|Spécifie l'identité du service à authentifier par le client.|  
  
## <a name="example"></a>Exemple  
 Le code suivant spécifie la représentation encodée d'un certificat qui est utilisée pour valider un serveur auprès d'un client.  
  
```xml  
<identity>
  <certificate encodedValue="MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />
</identity>
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.EndpointIdentity>
- [Identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)

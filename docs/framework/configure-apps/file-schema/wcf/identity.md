---
title: <identity>
ms.date: 03/30/2017
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
ms.openlocfilehash: 262ac9be6d5ce6466cf9aff33c0c2791c0e149dd
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988382"
---
# <a name="identity"></a>\<identity>
L'élément d'identité autorise un développeur client à spécifier au moment de la conception l'identité attendue du service. Dans le processus d’établissement de liaison entre le client et le service, l’infrastructure Windows Communication Foundation (WCF) garantit que l’identité du service attendu correspond aux valeurs de cet élément et peut donc être authentifiée. Pour plus d’informations, consultez [identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md).  
  
 \<system.ServiceModel>  
\<client>  
\<endpoint>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<identity>
  <certificate encodedValue="String" />
  <certificateReference findValue="String"
                        isChainIncluded="Boolean"
                        storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                        storeLocation="LocalMachine/CurrentUser"
                        X509FindType="Enumeration" />
  <dns value="String" />
  <rsa value="String" />
  <servicePrincipalName value="String" />
  <userPrincipalName value="String" />
</identity>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|certificate|Spécifie les paramètres d'un certificat X.509. Cet élément est de type <xref:System.ServiceModel.Configuration.CertificateElement>. Il contient un `encodedValue` d'attribut qui est une chaîne indiquant la valeur encodée par ce certificat.|  
|certificateReference|Spécifie les paramètres de validation du certificat X.509. Cet élément est de type <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.|  
|dns|Spécifie le système DNS d'un certificat X.509 utilisé pour authentifier un service. Cet élément contient un attribut `value` qui est une chaîne et qui contient l'identité réelle.|  
|rsa|Indique la valeur du champ RSA d'un certificat X.509 utilisée pour authentifier un service au niveau d'un client. Cet élément contient un attribut `value` qui est une chaîne et qui contient l'identité réelle.|  
|servicePrincipalName|Indique le nom SPN correspondant au nom principal utilisé par un client pour identifier de manière unique l'instance d'un service. Cet élément contient un `value` d'attribut qui est une chaîne contenant le nom principal réel. Cet élément est de type <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.|  
|userPrincipalName|Spécifie une identité UPN correspondant au type de nom de connexion d'un utilisateur sur un réseau. Le nom d’utilisateur principal est constitué du nom d’objet utilisateur utilisé dans Active Directory, suivi du symbole arobase (\@), puis, généralement, du domaine parent du système de noms de domaine. Par exemple, Jeff dans l’arborescence de domaine Fabrikam.com peut avoir le nom [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com)d’utilisateur principal.  Cet élément contient un `value` d'attribut qui est une chaîne contenant le nom principal réel. Cet élément est de type <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<custom>](custom.md)|Indique le programme de résolution d'homologue personnalisé pour un netPeerTcpBinding.|  
|[\<endpoint>](endpoint-element.md)|Configure les points de terminaison de service.|  
|[\<> de point \<de terminaison du > client](endpoint-of-client.md)|Configure les points de terminaison de canal.|  
|[\<issuer>](issuer.md)|Spécifie le service STS pour le service fédéré.|  
|[\<issuerMetadata>](issuermetadata.md)|Spécifie le point de terminaison de métadonnées pour le service STS d'un service fédéré.|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|Définit des paramètres correspondant à un jeton émis dans une liaison personnalisée.|  
|[\<localIssuer>](localissuer.md)|Spécifie un service STS local.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- [Identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md)
- [Terminaison Adresses, liaisons et contrats](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)

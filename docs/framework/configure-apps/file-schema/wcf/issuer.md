---
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 08fda249b526961ff711f439cf729a18e15b412b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929371"
---
# <a name="issuer"></a>\<émetteur >
Spécifie le service d'émission de jeton de sécurité (STS) qui émet des jetons de sécurité.  
  
 \<system.serviceModel>  
\<bindings>  
\<wsFederationHttpBinding>  
\<binding>  
\<> de sécurité  
\<message>  
\<émetteur >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<issuer address="Uri">
  <headers>
    <add name="String"
         namespace="String" />
  </headers>
  <identity>
    <certificate encodedValue="String" />
    <certificateReference findValue="String"
                          isChainIncluded="Boolean"
                          storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                          storeLocation="LocalMachine/CurrentUser"
                          x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
    <dns value="String" />
    <rsa value="String" />
    <servicePrincipalName value="String" />
    <usePrincipalName value="String" />
  </identity>
</issuer>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|adresse|Chaîne requise. URL du service STS.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|Collection d'en-têtes d'adresse de points de terminaison pouvant être créée par le générateur.|  
|[\<identity>](identity.md)|Lors de l'utilisation d'un jeton émis, spécifie des paramètres qui permettent au client d'authentifier le serveur.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|Définit les paramètres pour la sécurité au niveau du message pour l' [ \<élément WSFederationHttpBinding >](wsfederationhttpbinding.md) .|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [Identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md)
- [Fédération et jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [Identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md)
- [Fédération et jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [Fonctionnalités de sécurité avec des liaisons personnalisées](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [Fédération et jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md)

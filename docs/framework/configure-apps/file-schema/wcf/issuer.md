---
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 74f5f2fc1a0fa1ffbbb510e4e700c33a13d02ab3
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397918"
---
# <a name="issuer"></a>\<émetteur >
Spécifie le service d'émission de jeton de sécurité (STS) qui émet des jetons de sécurité.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de sécurité**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de messages**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<émetteur >**  
  
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

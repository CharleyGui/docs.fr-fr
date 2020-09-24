---
title: <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: c90024a0629f39d160967ca00434e48f682d8933
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157315"
---
# \<issuedTokenParameters>

Indique les paramètres d'un jeton de sécurité émis dans un scénario de sécurité fédéré.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenParameters>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<issuedTokenParameters defaultMessageSecurityVersion="System.ServiceModel.MessageSecurityVersion"
                       inclusionMode="AlwaysToInitiator/AlwaysToRecipient/Never/Once"
                       keySize="Integer"
                       keyType="AsymmetricKey/BearerKey/SymmetricKey"
                       tokenType="String">
  <additionalRequestParameters />
  <claimTypeRequirements>
    <add claimType="URI"
         isOptional="Boolean" />
  </claimTypeRequirements>
  <issuer address="String"
          binding="" />
  <issuerMetadata address="String" />
</issuedTokenParameters>
```  
  
## <a name="type"></a>Type  

 `Type`  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|defaultMessageSecurityVersion|Spécifie les versions des caractéristiques de sécurité (WS-Security, WS-Trust, WS-Secure Conversation et WS-Security Policy) devant être prises en charge par la liaison. Cette valeur est de type <xref:System.ServiceModel.MessageSecurityVersion>.|  
|inclusionMode|Indique les spécifications d'inclusion de jeton. Cet attribut est de type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.|  
|keySize|Entier qui spécifie la taille de clé de jeton. La valeur par défaut est 256.|  
|keyType|Valeur correcte de <xref:System.IdentityModel.Tokens.SecurityKeyType> indiquant le type de clé. Par défaut, il s’agit de `SymmetricKey`.|  
|tokenType|Chaîne indiquant le type de jeton. La valeur par défaut est « http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML »|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<additionalRequestParameters>](additionalrequestparameters-element.md)|Collection d'éléments de configuration indiquant des paramètres de demande supplémentaires.|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|Spécifie une collection de types de revendications requis.<br /><br /> Dans un scénario fédéré, les services déclarent les spécifications relatives aux informations d'identification entrantes. Par exemple, ces informations d'identification doivent posséder un jeu de types de revendications défini. Chaque élément de la collection indique les types de revendications requis et facultatifs censés apparaître dans les informations d'identification fédérées.|  
|[\<issuer>](issuer-of-issuedtokenparameters.md)|Élément de configuration qui spécifie le point de terminaison émettant le jeton actuel.|  
|[\<issuerMetadata>](issuermetadata-of-issuedtokenparameters.md)|Élément de configuration qui spécifie l'adresse de point de terminaison correspondant aux métadonnées de l'émetteur de jeton.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|Spécifie les valeurs par défaut utilisées pour initialiser un service de conversation sécurisé.|  
|[\<security>](security-of-custombinding.md)|Spécifie les options de sécurité d’une liaison personnalisée.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Liaisons](../../../wcf/bindings.md)
- [Extension de liaisons](../../../wcf/extending/extending-bindings.md)
- [Liaisons personnalisées](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [Procédure : créer une liaison personnalisée à l’aide de SecurityBindingElement](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Custom Binding Security](../../../wcf/samples/custom-binding-security.md)
- [Identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md)
- [Fédération et jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [Fonctionnalités de sécurité avec des liaisons personnalisées](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [Fédération et jetons émis](../../../wcf/feature-details/federation-and-issued-tokens.md)

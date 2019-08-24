---
title: <federationConfiguration>
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: c4dbb31bb7961f0d33df9d1faee8fe36ecb520a3
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988335"
---
# <a name="federationconfiguration"></a>\<federationConfiguration>
Configure le <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) et le <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam) lors de l’utilisation de l’authentification fédérée via le protocole WS-Federation. Configure <xref:System.Security.Claims.ClaimsAuthorizationManager> lors de l’utilisation de <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> la <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> classe ou pour fournir un contrôle d’accès basé sur les revendications.  
  
 \<system.identityModel.services>  
\<federationConfiguration>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|name|Nom de cet élément de configuration de Fédération. Cet attribut fournit principalement un point d’extensibilité pour les futurs protocoles. facultatif.|  
|identityConfigurationName|Nom de la section de configuration de l’identité telle qu’elle est spécifiée dans un [ \<élément identityConfiguration >](identityconfiguration.md) à utiliser. Si cet attribut n’est pas spécifié, la section de configuration d’identité par défaut est utilisée. facultatif.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|Configure le gestionnaire de cookies utilisé par le SAM. facultatif.|  
|[\<serviceCertificate>](servicecertificate.md)|Configure le certificat utilisé pour chiffrer et déchiffrer les jetons. facultatif.|  
|[\<wsFederation>](wsfederation.md)|Configure le module d’authentification WS-Federation (WSFAM). facultatif.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<system.identityModel.services>](system-identitymodel-services.md)|Section de configuration pour l’authentification à l’aide du protocole WS-Federation.|  
  
## <a name="remarks"></a>Notes  
 L' \<élément federationConfiguration > fournit des paramètres dans deux scénarios différents:  
  
- Lors de l’utilisation de WS-Federation dans une application Web passive, l’élément contient <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> les paramètres qui configurent le (WSFAM) et le <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam). Elle fait également référence à la configuration d’identité à utiliser pour configurer des certificats et des gestionnaires de jetons de sécurité, ainsi qu’à des composants tels que le gestionnaire d’autorisations des revendications et le gestionnaire d’authentification des revendications.  
  
- Lors de l' <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> utilisation de <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> la classe ou pour fournir un contrôle d’accès basé sur les revendications dans votre code, l’élément fait référence à la configuration d’identité qui configure le gestionnaire d’autorisation des revendications et la stratégie utilisée pour effectuer l’autorisation. ses. Cela est vrai, même dans les scénarios qui ne sont pas des scénarios Web passifs; par exemple, les applications Windows Communication Foundation (WCF) ou une application qui n’est pas basée sur le Web. Si l’application n’est pas une application Web passive, l' `<federationConfiguration>` [ \<élément claimsAuthorizationManager >](claimsauthorizationmanager.md) (et ses éléments de stratégie enfants, le cas échéant) de la configuration d’identité référencée par l’élément sont les seuls paramètres exercé. Tous les autres sont ignorés.  
  
 Quel que soit le scénario, le runtime charge la configuration de Fédération par défaut. Le comportement est défini comme suit:  
  
1. Si aucun `<federationConfiguration>` élément n’est présent, le runtime crée une configuration de Fédération et la remplit avec les valeurs par défaut. Cette configuration de Fédération par défaut fait référence à la configuration d’identité par défaut.  
  
2. Si un seul `<federationConfiguration>` élément est présent, il s’agit de la configuration de Fédération par défaut, qu’il soit nommé ou sans nom. Si son `identityConfiguration` attribut est spécifié, la configuration d’identité nommée est référencée; sinon, la configuration d’identité par défaut est référencée.  
  
3. Si un `<federationConfiguration>` élément sans nom est présent, il s’agit de la configuration de Fédération par défaut. Si son `identityConfiguration` attribut est spécifié, la configuration d’identité nommée est référencée; sinon, la configuration d’identité par défaut est référencée.  
  
4. Si plusieurs éléments `<federationConfiguration>` nommés sont présents et qu’aucun `<federationConfiguration>` élément sans nom n’est présent, une exception est levée.  
  
 En règle générale, une `<federationConfiguration>` seule section est définie. Cette section est la configuration de Fédération par défaut. Vous pouvez spécifier plusieurs éléments portant un nom `<federationConfiguration>` unique; Toutefois, dans ce cas, si vous souhaitez charger une configuration de Fédération autre que la configuration sans nom, vous devez fournir un gestionnaire pour le. <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated>et définissez la <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> propriété à l’intérieur du gestionnaire sur <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> un objet initialisé avec les valeurs de l' `<federationConfiguration>` élément approprié dans le fichier de configuration.  
  
 L' `<federationConfiguration>` élément est représenté par la <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> classe. L’objet de configuration lui-même est <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> représenté par la classe. Une seule <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> instance est définie sur la <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> propriété et fournit une configuration fédérée pour l’application.  
  
## <a name="example"></a>Exemple  
 Le code XML suivant montre `<federationConfiguration>` un élément qui spécifie des paramètres pour le WSFAM et spécifie que le gestionnaire de cookies par <xref:System.IdentityModel.Services.ChunkedCookieHandler> défaut (une instance de la classe) doit être utilisé par le Sam.  
  
> [!WARNING]
> Dans cet exemple, ni le gestionnaire de cookies ni WSFAM ne sont requis pour utiliser le protocole HTTPs. Cela est dû au `requireHttps` fait que l' `<wsFederation>` attribut sur l' `requireSsl` élément et l' `<cookieHandlerElement>` attribut `false`sur le sont. Ces paramètres ne sont pas recommandés pour la plupart des environnements de production, car ils peuvent présenter un risque pour la sécurité.  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <wsFederation passiveRedirectEnabled="true"   
      issuer="http://localhost:15839/wsFederationSTS/Issue"   
      realm="http://localhost:50969/" reply="http://localhost:50969/"   
      requireHttps="false"   
      signOutReply="http://localhost:50969/SignedOutPage.html"   
      signOutQueryString="Param1=value2&Param2=value2"   
      persistentCookiesOnPassiveRedirects="true" />  
    <cookieHandler requireSsl="false" />  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
- [\<identityConfiguration>](identityconfiguration.md)

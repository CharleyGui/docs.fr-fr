---
title: <federationConfiguration>
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: 39e96a161a2e75d5f00b73f6b08b1e4a0c109aee
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201354"
---
# \<federationConfiguration>

Configure le <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) et le <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam) lors de l’utilisation de l’authentification fédérée via le protocole WS-Federation. Configure lors de l’utilisation de la <xref:System.Security.Claims.ClaimsAuthorizationManager> <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> classe ou pour fournir un contrôle d’accès basé sur les revendications.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<federationConfiguration>**  
  
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
|name|Nom cet élément de configuration de fédération. Cet attribut fournit principalement un point d’extensibilité pour les futurs protocoles. Optionnel.|  
|identityConfigurationName|Nom de la section de configuration de l’identité telle qu’elle est spécifiée dans un [\<identityConfiguration>](identityconfiguration.md) élément à utiliser. Si cet attribut n’est pas spécifié, la section de configuration d’identité par défaut est utilisée. Optionnel.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|Configure le gestionnaire de cookies utilisé par le SAM. Optionnel.|  
|[\<serviceCertificate>](servicecertificate.md)|Configure le certificat utilisé pour chiffrer et déchiffrer les jetons. Optionnel.|  
|[\<wsFederation>](wsfederation.md)|Configure le module d’authentification WS-Federation (WSFAM). Optionnel.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<system.identityModel.services>](system-identitymodel-services.md)|Section de configuration pour l’authentification à l’aide du protocole WS-Federation.|  
  
## <a name="remarks"></a>Notes  

 L' \<federationConfiguration> élément fournit des paramètres dans deux scénarios différents :  
  
- Lors de l’utilisation de WS-Federation dans une application Web passive, l’élément contient les paramètres qui configurent le <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) et le <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam). Elle fait également référence à la configuration d’identité à utiliser pour configurer des certificats et des gestionnaires de jetons de sécurité, ainsi qu’à des composants tels que le gestionnaire d’autorisations des revendications et le gestionnaire d’authentification des revendications.  
  
- Lors de l’utilisation de la <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> classe ou pour fournir un contrôle d’accès basé sur les revendications dans votre code, l’élément fait référence à la configuration d’identité qui configure le gestionnaire d’autorisation des revendications et la stratégie utilisée pour prendre des décisions d’autorisation. Cela est vrai, même dans les scénarios qui ne sont pas des scénarios Web passifs ; par exemple, les applications Windows Communication Foundation (WCF) ou une application qui n’est pas basée sur le Web. Si l’application n’est pas une application Web passive, l' [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) élément (et ses éléments de stratégie enfants, le cas échéant) de la configuration d’identité référencée par l' `<federationConfiguration>` élément sont les seuls paramètres appliqués. Tous les autres sont ignorés.  
  
 Quel que soit le scénario, le runtime charge la configuration de Fédération par défaut. Le comportement est défini comme suit :  
  
1. Si aucun élément n’est `<federationConfiguration>` présent, le runtime crée une configuration de Fédération et la remplit avec les valeurs par défaut. Cette configuration de Fédération par défaut fait référence à la configuration d’identité par défaut.  
  
2. Si un seul `<federationConfiguration>` élément est présent, il s’agit de la configuration de Fédération par défaut, qu’il soit nommé ou sans nom. Si son `identityConfiguration` attribut est spécifié, la configuration d’identité nommée est référencée ; sinon, la configuration d’identité par défaut est référencée.  
  
3. Si un élément sans nom `<federationConfiguration>` est présent, il s’agit de la configuration de Fédération par défaut. Si son `identityConfiguration` attribut est spécifié, la configuration d’identité nommée est référencée ; sinon, la configuration d’identité par défaut est référencée.  
  
4. Si plusieurs `<federationConfiguration>` éléments nommés sont présents et qu’aucun élément sans nom `<federationConfiguration>` n’est présent, une exception est levée.  
  
 En règle générale, une seule `<federationConfiguration>` section est définie. Cette section est la configuration de Fédération par défaut. Vous pouvez spécifier plusieurs éléments portant un nom unique `<federationConfiguration>` ; Toutefois, dans ce cas, si vous souhaitez charger une configuration de Fédération autre que la configuration sans nom, vous devez fournir un gestionnaire pour le. <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated> et définissez la propriété à l' <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> intérieur du gestionnaire sur un <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> objet initialisé avec les valeurs de l' `<federationConfiguration>` élément approprié dans le fichier de configuration.  
  
 L' `<federationConfiguration>` élément est représenté par la <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> classe. L’objet de configuration lui-même est représenté par la <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> classe. Une seule <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> instance est définie sur la <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> propriété et fournit une configuration fédérée pour l’application.  
  
## <a name="example"></a>Exemple  

 Le code XML suivant montre un `<federationConfiguration>` élément qui spécifie des paramètres pour le WSFAM et spécifie que le gestionnaire de cookies par défaut (une instance de la <xref:System.IdentityModel.Services.ChunkedCookieHandler> classe) doit être utilisé par le Sam.  
  
> [!WARNING]
> Dans cet exemple, ni le gestionnaire de cookies ni WSFAM ne sont requis pour utiliser le protocole HTTPs. Cela est dû au fait que l' `requireHttps` attribut sur l' `<wsFederation>` élément et l' `requireSsl` attribut sur le `<cookieHandlerElement>` sont `false` . Ces paramètres ne sont pas recommandés pour la plupart des environnements de production, car ils peuvent présenter un risque pour la sécurité.  
  
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

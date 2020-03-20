---
title: <federationConfiguration>
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: bcd8e00b770517e3faff011b4acee08ebdc5a0df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152734"
---
# <a name="federationconfiguration"></a>\<federationConfiguration>
Configure le <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) <xref:System.IdentityModel.Services.SessionAuthenticationModule> et le (SAM) lors de l’utilisation de l’authentification fédérée par le protocole WS-Federation. Configure le <xref:System.Security.Claims.ClaimsAuthorizationManager> lors <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> de <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> l’utilisation ou de la classe pour fournir un contrôle d’accès fondé sur les revendications.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<fédérationConfiguration>**  
  
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
|name|Nom cet élément de configuration de fédération. Cet attribut fournit principalement un point d’extabilité pour les protocoles futurs. facultatif.|  
|identitéConfigurationName|Le nom de la section de configuration d’identité tel que spécifié dans une [ \<identitéConfiguration>](identityconfiguration.md) élément à utiliser. Si cet attribut n’est pas spécifié, la section de configuration d’identité par défaut est utilisée. facultatif.|  
  
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
 La \<fédérationConfiguration> élément fournit des paramètres dans deux scénarios différents:  
  
- Lors de l’utilisation de WS-Federation dans une <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> application Web passive, <xref:System.IdentityModel.Services.SessionAuthenticationModule> l’élément contient des paramètres qui configurent le (WSFAM) et le (SAM). Il fait également référence à la configuration d’identité à utiliser pour configurer les gestionnaires et certificats de jetons de sécurité, ainsi que des composants comme le gestionnaire de l’autorisation des réclamations et le gestionnaire de l’authentification des réclamations.  
  
- Lorsque vous <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> utilisez <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> le ou le groupe pour fournir un contrôle d’accès fondé sur les revendications dans votre code, l’élément fait référence à la configuration d’identité qui configure le gestionnaire d’autorisation des sinistres et la stratégie qui est utilisée pour prendre des décisions d’autorisation. C’est vrai, même dans des scénarios qui ne sont pas des scénarios Web passifs; par exemple, les applications de la Windows Communication Foundation (WCF) ou une application qui n’est pas basée sur le Web. Si l’application n’est pas une application Web passive, les `<federationConfiguration>` [ \<revendicationsAuthorizationManager>](claimsauthorizationmanager.md) élément (et ses éléments de politique de l’enfant, s’il est présent) de la configuration d’identité référencée par l’élément sont les seuls paramètres appliqués. Tous les autres sont ignorés.  
  
 Quel que soit le scénario, le temps d’exécution charge la configuration de la fédération par défaut. Le comportement est défini comme suit :  
  
1. S’il `<federationConfiguration>` n’y a pas d’élément présent, le temps d’exécution crée une configuration de fédération et le remplit de valeurs par défaut. Cette configuration de fédération par défaut fera référence à la configuration d’identité par défaut.  
  
2. Si un `<federationConfiguration>` seul élément est présent, c’est la configuration de la fédération par défaut, qu’elle soit nommée ou sans nom. Si `identityConfiguration` son attribut est spécifié, la configuration d’identité nommée est référencée; autrement, la configuration d’identité par défaut est référencée.  
  
3. Si un `<federationConfiguration>` élément anonyme est présent, c’est la configuration de la fédération par défaut. Si `identityConfiguration` son attribut est spécifié, la configuration d’identité nommée est référencée; autrement, la configuration d’identité par défaut est référencée.  
  
4. Si plusieurs `<federationConfiguration>` éléments nommés sont `<federationConfiguration>` présents et qu’aucun élément anonyme n’est présent, une exception est lancée.  
  
 En règle générale, seule une seule `<federationConfiguration>` section est définie. Cette section est la configuration de fédération par défaut. Vous pouvez spécifier `<federationConfiguration>` plusieurs éléments de nom unique; cependant, dans ce cas, si vous voulez charger une configuration de fédération autre que celle sans nom, vous devez fournir un gestionnaire pour le. <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated>l’événement <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> et réglez <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> la propriété à l’intérieur du gestionnaire à un objet initialisé avec des valeurs de l’élément approprié `<federationConfiguration>` dans le fichier de configuration.  
  
 L’élément `<federationConfiguration>` est représenté <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> par la classe. L’objet de configuration lui-même est représenté par la <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> classe. Une <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> seule instance est <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> réglée sur la propriété et fournit une configuration fédérée pour l’application.  
  
## <a name="example"></a> Exemple  
 Le XML suivant `<federationConfiguration>` montre un élément qui spécifie les paramètres pour le WSFAM et spécifie que le gestionnaire de cookies par défaut (une instance de la <xref:System.IdentityModel.Services.ChunkedCookieHandler> classe) soit utilisé par le SAM.  
  
> [!WARNING]
> Dans cet exemple, ni le gestionnaire de biscuits ni WSFAM ne sont tenus d’utiliser HTTPS. C’est `requireHttps` parce que `<wsFederation>` l’attribut sur `<cookieHandlerElement>` `false`l’élément et l’attribut `requireSsl` sur le sont . Ces paramètres ne sont pas recommandés pour la plupart des environnements de production car ils peuvent présenter un risque pour la sécurité.  
  
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
- [\<identitéConfiguration>](identityconfiguration.md)

---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: 57757aaec39bc5c552e7ba12c9779cb3a92a9025
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152502"
---
# <a name="systemidentitymodelservices"></a>\<system.identityModel.services>
Section de configuration pour l’authentification à l’aide du protocole WS-Federation.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.identityModel.services>**  
  
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
 None  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<fédérationConfiguration>](federationconfiguration.md)|Contient les paramètres <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> qui configurent les <xref:System.IdentityModel.Services.SessionAuthenticationModule> modules HTTP (WSFAM) et (SAM).|  
  
### <a name="parent-elements"></a>Éléments parents  
 None  
  
## <a name="remarks"></a>Notes   
 Ajoutez `<system.identityModel.services>` une section au fichier de configuration de votre application pour fournir les paramètres du SAM et du WSFAM.  
  
> [!IMPORTANT]
> Lorsque vous <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> utilisez <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> le ou le groupe pour fournir un contrôle<xref:System.Security.Claims.ClaimsAuthorizationManager>d’accès fondé sur les réclamations dans `<identityConfiguration>` votre code, le gestionnaire de `<federationConfiguration>` l’autorisation des réclamations () et la stratégie utilisée pour prendre des décisions d’autorisation sont configurés à travers un élément qui est implicitement ou explicitement référencé à partir d’un élément de cette section. Pour plus d’informations, voir **les remarques** sous la [ \<fédérationConfiguration>](federationconfiguration.md) élément.  
  
 La `<system.identityModel.services>` section est représentée <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> par la classe. La collection `<federationConfiguration>` d’éléments pour enfants configuré <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> dans la section est représentée par la classe.  
  
## <a name="example"></a> Exemple  
 Le XML suivant montre `<system.identityModel.services>` comment ajouter une section à un fichier de configuration. Vous devez d’abord ajouter `<system.identityModel.services>` des déclarations de section pour la section et les `<system.identityModel>` sections. (Lorsque vous `<system.identityModel.services>` ajoutez une section, vous devez `<system.identityModel>` également ajouter une `<identityConfiguration>` déclaration pour la section afin de vous assurer qu’une section par défaut peut être créée par l’heure d’exécution si nécessaire.) Une fois les déclarations de section ajoutées, vous pouvez `<system.identityModel.services>` configurer les paramètres d’authentification fédéraux sous l’élément.  
  
```xml  
<configuration>  
  <configSections>  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
  </configSections>  
  
  <!-- Additional elements (not shown) -->  
  
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
  
</configuration>  
```

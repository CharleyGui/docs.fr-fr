---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: bef061c5c982fb0e740f889336a3b334bc19225e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943658"
---
# <a name="systemidentitymodelservices"></a>\<system.identityModel.services>
Section de configuration pour l’authentification à l’aide du protocole WS-Federation.  
  
 \<system.identityModel.services>  
  
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
 Aucun  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|Contient les paramètres qui configurent les <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> modules http (WSFAM) <xref:System.IdentityModel.Services.SessionAuthenticationModule> et (Sam).|  
  
### <a name="parent-elements"></a>Éléments parents  
 Aucun  
  
## <a name="remarks"></a>Notes  
 Ajoutez une `<system.identityModel.services>` section au fichier de configuration de votre application pour fournir des paramètres pour le Sam et WSFAM.  
  
> [!IMPORTANT]
> Lors de l' <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> utilisation de <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> la classe ou pour fournir un contrôle d’accès basé sur les revendications dans votre code,<xref:System.Security.Claims.ClaimsAuthorizationManager>le gestionnaire d’autorisations des revendications () et la stratégie utilisés pour prendre `<identityConfiguration>` des décisions d’autorisation sont configurés via un élément qui est référencé implicitement ou explicitement à partir d' `<federationConfiguration>` un élément de cette section. Pour plus d’informations, consultez les **Notes** sous l' [ \<élément federationConfiguration >](federationconfiguration.md) .  
  
 La `<system.identityModel.services>` section est représentée par la <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> classe. La collection d’éléments `<federationConfiguration>` enfants configurés dans la section est représentée par <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> la classe.  
  
## <a name="example"></a>Exemple  
 Le code XML suivant montre comment ajouter une `<system.identityModel.services>` section à un fichier de configuration. Vous devez d’abord ajouter des déclarations de section `<system.identityModel.services>` pour la section `<system.identityModel>` et les sections. (Lorsque vous ajoutez une `<system.identityModel.services>` section, vous devez également ajouter une déclaration pour la `<system.identityModel>` section pour vous assurer qu’une `<identityConfiguration>` section par défaut peut être créée par le runtime, si nécessaire.) Une fois les déclarations de section ajoutées, vous pouvez configurer les paramètres d’authentification fédérée `<system.identityModel.services>` sous l’élément.  
  
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

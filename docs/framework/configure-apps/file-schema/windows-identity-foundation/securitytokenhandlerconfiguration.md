---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: e3e65820fa4dc341371d4f67689a288cd3f63951
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152565"
---
# <a name="securitytokenhandlerconfiguration"></a>\<sécuritéTokenHandlerConfiguration>
Fournit la configuration pour la collection de maîtres-livres.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identitéConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<sécuritéTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sécuritéTokenHandlerConfiguration>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration saveBootstrapContext=xs:boolean  
          maximumClockSkew=TimeSpan>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|saveBootstrapContext|Précise si les jetons de bootstrap doivent être inclus dans le jeton de session. La valeur peut également être définie sur une `saveBootstrapContext` collection de gestionnaires de jetons en définissant l’attribut sur [ \<l’élément>d’identitéconfiguration.](identityconfiguration.md) Une valeur définie sur la collection de gestionnaires de jetons l’emporte sur la valeur fixée sur le service.|  
|maximumClockSkew|A <xref:System.TimeSpan> qui spécifie le biais maximal autorisé de l’horloge. Contrôle l’inclinaison maximale de l’horloge autorisée lors de l’exécution d’opérations sensibles au temps, telles que la validation de l’heure d’expiration d’une session de connexion. La valeur par défaut est de 5 minutes, "00:05:00". Pour plus d’informations <xref:System.TimeSpan> sur la façon de spécifier les valeurs, voir [Valeurs Timespan](../windows-workflow-foundation/index.md). Le biais d’horloge maximum peut également être `maximumClockSkew` réglé au niveau du service en définissant l’attribut sur [ \<l’élément>d’identitéconfiguration.](identityconfiguration.md) Une valeur définie sur la collection de gestionnaires de jetons l’emporte sur la valeur fixée sur le service.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<audienceUris>](audienceuris.md)|Spécifie l’ensemble d’ITI qui sont des identifiants acceptables de cette partie de compte. facultatif.|  
|[\<caches>](caches.md)|Enregistre les caches utilisées pour les jetons de session et la détection des relecteurs symboliques. Peut être spécifié au niveau du service ou sur une collection de gestionnaires de jetons de sécurité. facultatif.|  
|[\<certificateValidation>](certificatevalidation.md)|Contrôle les paramètres utilisés par les gestionnaires de jetons pour valider les certificats. Peut être spécifié au niveau du service ou sur une collection de gestionnaires de jetons de sécurité. Ces paramètres sont remplacés si un gestionnaire spécifique est configuré avec son propre validateur. facultatif.|  
|[\<issuerNameRegistry>](issuernameregistry.md)|Configure le registre des noms d’émetteur qui est utilisé par les gestionnaires dans la collection de gestionnaires de jetons. facultatif.|  
|[\<émetteurTokenResolver>](issuertokenresolver.md)|Enregistre le résa résolveur de jetons de l’émetteur qui est utilisé par les gestionnaires dans la collection de gestionnaires de jetons. Le résolveur de jetons de l’émetteur est utilisé pour résoudre le jeton de signature sur les jetons entrants et les messages. facultatif.|  
|[\<serviceTokenResolver>](servicetokenresolver.md)|Enregistre le résammateur de jetons de service qui est utilisé par les gestionnaires dans la collection de manutention de jetons. Le résolveur de jetons de service est utilisé pour résoudre le jeton de chiffrement sur les jetons et les messages entrants. facultatif.|  
|[\<tokenReplayDetection>](tokenreplaydetection.md)|Permet la détection de relecture de jetons et spécifie le temps d’expiration des jetons. Peut être spécifié au niveau du service ou sur une collection de gestionnaires de jetons de sécurité. facultatif.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<sécuritéTokenHandlers>](securitytokenhandlers.md)|Spécifie une collection de gestionnaires de jetons de sécurité qui sont enregistrés avec le point de terminaison.|  
  
## <a name="remarks"></a>Notes   
 Cette section fournit des <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> valeurs de propriété pour un objet. Les paramètres configurés dans cette section remplacent ceux configurés sur le service. Certains de ces paramètres peuvent, à leur tour, être remplacés par des paramètres qui sont spécifiés lorsqu’un gestionnaire est ajouté à la collection de gestionnaires de jetons de sécurité.  
  
## <a name="example"></a> Exemple  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>
      <securityTokenHandlerConfiguration>  
  
        <audienceUris>  
          <clear/>  
          <add value="http://www.example.com/myapp/" />  
        </audienceUris>  
  
        <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel">  
          <trustedIssuers>  
            <add thumbprint="97249e1a … 4c9158de" name="contoso.com" />  
          </trustedIssuers>  
        </issuerNameRegistry>  
  
        <issuerTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
        <serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```

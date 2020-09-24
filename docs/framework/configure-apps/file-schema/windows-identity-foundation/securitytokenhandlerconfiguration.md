---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: 4c6affbc24a58424158e466fb732e9a3b3d6f1ed
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157016"
---
# \<securityTokenHandlerConfiguration>

Fournit la configuration pour la collection de gestionnaires de jetons.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlerConfiguration>**  
  
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
|saveBootstrapContext|Spécifie si les jetons de démarrage doivent être inclus dans le jeton de session. La valeur peut également être définie sur une collection de gestionnaires de jetons en définissant l' `saveBootstrapContext` attribut sur l' [\<identityConfiguration>](identityconfiguration.md) élément. Une valeur définie sur la collection de gestionnaires de jetons remplace la valeur définie sur le service.|  
|maximumClockSkew|<xref:System.TimeSpan>Qui spécifie la variation d’horloge maximale autorisée. Contrôle la variation d’horloge maximale autorisée lors de l’exécution d’opérations sensibles au temps, telles que la validation du délai d’expiration d’une session de connexion. La valeur par défaut est 5 minutes, « 00:05:00 ». Pour plus d’informations sur la spécification des <xref:System.TimeSpan> valeurs, consultez [TimeSpan values](../windows-workflow-foundation/index.md). Le décalage d’horloge maximal peut également être défini au niveau du service en définissant l' `maximumClockSkew` attribut sur l' [\<identityConfiguration>](identityconfiguration.md) élément. Une valeur définie sur la collection de gestionnaires de jetons remplace la valeur définie sur le service.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<audienceUris>](audienceuris.md)|Spécifie l’ensemble d’URI qui sont des identificateurs acceptables de cette partie de confiance. Optionnel.|  
|[\<caches>](caches.md)|Inscrit les caches utilisés pour les jetons de session et la détection de relecture de jetons. Peut être spécifié au niveau du service ou sur une collection de gestionnaires de jetons de sécurité. Optionnel.|  
|[\<certificateValidation>](certificatevalidation.md)|Contrôle les paramètres que les gestionnaires de jetons utilisent pour valider les certificats. Peut être spécifié au niveau du service ou sur une collection de gestionnaires de jetons de sécurité. Ces paramètres sont substitués si un gestionnaire spécifique est configuré avec son propre validateur. Optionnel.|  
|[\<issuerNameRegistry>](issuernameregistry.md)|Configure le registre des noms d’émetteurs qui est utilisé par les gestionnaires dans la collection de gestionnaires de jetons. Optionnel.|  
|[\<issuerTokenResolver>](issuertokenresolver.md)|Inscrit le programme de résolution de jetons d’émetteur utilisé par les gestionnaires dans la collection de gestionnaires de jetons. Le programme de résolution de jetons d’émetteur est utilisé pour résoudre le jeton de signature sur les jetons et les messages entrants. Optionnel.|  
|[\<serviceTokenResolver>](servicetokenresolver.md)|Inscrit le programme de résolution de jetons de service qui est utilisé par les gestionnaires dans la collection de gestionnaires de jetons. Le programme de résolution de jetons de service est utilisé pour résoudre le jeton de chiffrement sur les jetons et les messages entrants. Optionnel.|  
|[\<tokenReplayDetection>](tokenreplaydetection.md)|Active la détection de relecture de jetons et spécifie l’heure d’expiration des jetons. Peut être spécifié au niveau du service ou sur une collection de gestionnaires de jetons de sécurité. Optionnel.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|Spécifie une collection de gestionnaires de jetons de sécurité inscrits auprès du point de terminaison.|  
  
## <a name="remarks"></a>Notes  

 Cette section fournit des valeurs de propriété pour un <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> objet. Les paramètres configurés dans cette section remplacent ceux configurés sur le service. Certains de ces paramètres peuvent, à leur tour, être remplacés par les paramètres spécifiés lors de l’ajout d’un gestionnaire à la collection de gestionnaires de jetons de sécurité.  
  
## <a name="example"></a>Exemple  
  
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

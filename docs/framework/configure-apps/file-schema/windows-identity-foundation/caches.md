---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: 5ad75ae18772d6e7c724f2cbf40c1e3083d5c345
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941966"
---
# <a name="caches"></a>\<caches>
Inscrit les caches utilisés pour les jetons de session et la détection de relecture de jetons.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<caches>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<sessionSecurityTokenCache>](sessionsecuritytokencache.md)|Inscrit un cache pour les jetons de session avec un service ou une collection de gestionnaires de jetons de sécurité.|  
|[\<tokenReplayCache>](tokenreplaycache.md)|Inscrit un cache de relecture de jetons avec un service ou une collection de gestionnaires de jetons de sécurité.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|Spécifie les paramètres d’identité au niveau du service.|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.|  
  
## <a name="remarks"></a>Notes  
 Un `<caches>` élément peut être spécifié au niveau du service sous l' `<identityConfiguration>` élément ou au niveau de la collection du gestionnaire de jetons `<securityTokenHandlerConfiguration>` de sécurité sous l’élément. Les paramètres d’une collection de gestionnaires de jetons remplacent ceux spécifiés sur le service.  
  
 L' `<caches>` élément est représenté par la <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> classe. Les caches configurés sont représentés par <xref:System.IdentityModel.Configuration.IdentityModelCaches> la classe.  
  
## <a name="example"></a>Exemple  
 Le code XML suivant montre la configuration d’un cache personnalisé pour la conservation des jetons de<xref:System.IdentityModel.Tokens.SessionSecurityToken>sécurité de session (). La configuration est extraite de `ClaimsAwareWebFarm` l’exemple.  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```

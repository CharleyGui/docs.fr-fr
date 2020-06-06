---
title: <defaultFtpCachePolicy>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
ms.openlocfilehash: 9261a430642cb4d5ac4507835bd0fd3561bd8c02
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088425"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a>\<defaultFtpCachePolicy>, élément (paramètres réseau)
Indique si la mise en cache FTP est active et décrit la stratégie de mise en cache par défaut.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultFtpCachePolicy>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`policyLevel`|Spécifie la stratégie de mise en cache FTP. La valeur par défaut est `Default`.|  
  
## <a name="policylevel-attribute"></a>policyLevel (attribut)  
  
|Valeur|Description|  
|-----------|-----------------|  
|`Default`|Retourne la ressource mise en cache si la ressource est actualisée, si la longueur du contenu est exacte et si les attributs d’expiration, de modification et de longueur du contenu sont présents.|  
|`BypassCache`|Retourne la ressource à partir du serveur.|  
|`CacheOnly`|Retourne la ressource mise en cache si la longueur du contenu est présente et correspond à la taille de l’entrée.|  
|`CacheIfAvailable`|Retourne la ressource mise en cache si la longueur du contenu est fournie et correspond à la taille de l’entrée ; dans le cas contraire, la ressource est téléchargée à partir du serveur et est retournée à l’appelant.|  
|`Revalidate`|Retourne la ressource mise en cache si l’horodateur de la ressource mise en cache est le même que celui de la ressource sur le serveur ; dans le cas contraire, la ressource est téléchargée à partir du serveur, stockée dans le cache et retournée à l’appelant.|  
|`Reload`|Télécharge la ressource à partir du serveur, la stocke dans le cache et retourne la ressource à l’appelant.|  
|`NoCacheNoStore`|Si une ressource mise en cache existe, elle est supprimée. La ressource est téléchargée à partir du serveur et est retournée à l’appelant.|  
|`Revalidate`|Satisfait une demande en utilisant la copie mise en cache de la ressource si l'horodatage est le même que celui de la ressource sur le serveur ; sinon, la ressource est téléchargée à partir du serveur, présentée à l'appelant et stockée dans le cache.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[requestCaching](requestcaching-element-network-settings.md)|Contrôle le mécanisme de mise en cache pour les demandes réseau.|  
  
## <a name="remarks"></a>Remarques  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment spécifier une stratégie de mise en cache FTP de `NoCacheNoStore` .  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultFtpCachePolicy  
        policyLevel="NoCacheNoStore">  
      </defaultFtpCachePolicy>  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [Schéma des paramètres réseau](index.md)

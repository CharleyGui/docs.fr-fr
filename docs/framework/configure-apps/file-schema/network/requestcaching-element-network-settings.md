---
title: <requestCaching>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
ms.openlocfilehash: 3eb32b7ae643efdb19892410b669c1e7ff80e0ad
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174158"
---
# <a name="requestcaching-element-network-settings"></a>\<requestCaching>, élément (paramètres réseau)

Contrôle le mécanisme de mise en cache pour les demandes réseau.  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<requestCaching>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<requestCaching  
  isPrivateCache ="true|false"  
  disableAllCaching="true|false"  
  defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
  unspecifiedMaximumAge= "d.hh:mm:ss">  
    <defaultHttpCachePolicy>...</defaultHttpCachePolicy>  
    <defaultFtpCachePolicy>...</defaultFtpCachePolicy>  
</requestCaching>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`isPrivateCache`|Spécifie si le cache assure l’isolement entre les informations des différents utilisateurs. La valeur par défaut est `true`. Cette valeur doit être `false` pour les applications de niveau intermédiaire.|  
|`disableAllCaching`|Spécifie que la mise en cache est désactivée pour toutes les réponses Web et ne peut pas être substituée par programmation.|  
|`defaultPolicyLevel`|Une des valeurs dans l'énumération <xref:System.Net.Cache.RequestCacheLevel>. La valeur par défaut est `BypassCache`.|  
|`unspecifiedMaximumAge`|Spécifie l’heure par défaut après laquelle le contenu est marqué comme ayant expiré.|  
  
## <a name="policylevel-attribute"></a>policyLevel (attribut)  
  
|Valeur|Description|  
|-----------|-----------------|  
|`Default`|Retourne la ressource mise en cache si la ressource est actualisée, si la longueur du contenu est exacte et si les attributs d’expiration, de modification et de longueur du contenu sont présents.|  
|`BypassCache`|Retourne la ressource à partir du serveur.|  
|`CacheOnly`|Retourne la ressource mise en cache si la longueur du contenu est présente et correspond à la taille de l’entrée.|  
|`CacheIfAvailable`|Retourne la ressource mise en cache si la longueur du contenu est fournie et correspond à la taille de l’entrée ; dans le cas contraire, la ressource est téléchargée à partir du serveur et est retournée à l’appelant.|  
|`Revalidate`|Retourne la ressource mise en cache si l’horodateur de la ressource mise en cache est le même que celui de la ressource sur le serveur ; dans le cas contraire, la ressource est téléchargée à partir du serveur, stockée dans le cache, et est retournée à l’appelant.|  
|`Reload`|Télécharge la ressource à partir du serveur, la stocke dans le cache et retourne la ressource à l’appelant.|  
|`NoCacheNoStore`|Si une ressource mise en cache existe, elle est supprimée. La ressource est téléchargée à partir du serveur et est retournée à l’appelant.|  
|`Revalidate`|Satisfait une demande en utilisant la copie mise en cache de la ressource si l’horodatage est le même que celui de la ressource sur le serveur ; dans le cas contraire, la ressource est téléchargée à partir du serveur, présentée à l’appelant et stockée dans le cache.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[defaultHttpCachePolicy](defaulthttpcachepolicy-element-network-settings.md)|Élément facultatif.<br /><br /> Indique si la mise en cache HTTP est active et décrit la stratégie de mise en cache par défaut.|  
|[\<defaultFtpCachePolicy> , Élément (paramètres réseau)](defaultftpcachepolicy-element-network-settings.md)|Élément facultatif.<br /><br /> Indique si la mise en cache FTP est active et décrit la stratégie de mise en cache par défaut.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[system.net](system-net-element-network-settings.md)|Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.|  
  
## <a name="example"></a>Exemple  

 L’exemple suivant montre comment désactiver toute la mise en cache.  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Net.Cache?displayProperty=nameWithType>
- [Schéma des paramètres réseau](index.md)

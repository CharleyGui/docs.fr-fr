---
title: Stratégie de cache
description: En savoir plus sur la stratégie de cache, les règles qui déterminent si une requête peut être satisfaite à l’aide d’une copie mise en cache de la ressource demandée.
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- location-based cache policies
- cache [.NET Framework], policies
- request cache policies
- freshness of cached resources
- content cache policies
- expired content
ms.assetid: 1a7e04ec-7872-41c2-96c6-52566dcb412b
ms.openlocfilehash: 5492fd9f7b27f7546b951710e4b3e099a1d6664d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250591"
---
# <a name="cache-policy"></a>Stratégie de cache

Une stratégie de cache définit les règles utilisées pour déterminer si une requête peut être satisfaite à l’aide d’une copie mise en cache de la ressource demandée. Les applications spécifient les exigences d’actualisation du cache du client, mais la stratégie de cache effective est déterminée par les exigences de cache du client, les exigences d’expiration du contenu du serveur, et les exigences de revalidation du serveur. L’interaction entre la stratégie de cache du client et les exigences du serveur ont toujours comme résultat la stratégie de cache la plus restrictive, afin d’aider à garantir que le contenu le plus récent est renvoyé à l’application cliente.  
  
 Les stratégies de cache sont basées sur l’emplacement ou sur la durée. Une stratégie de cache basée sur l’emplacement définit l’actualisation des entrées en cache en fonction de l’emplacement d’où la ressource demandée peut être récupérée. Une stratégie de cache basée sur la durée définit l’actualisation des entrées en cache en fonction de l’heure de récupération de la ressource, des en-têtes retournés avec la ressource et de l’heure actuelle. La plupart des applications peuvent utiliser la stratégie de cache basée sur la durée par défaut, qui implémente la stratégie de mise en cache spécifiée dans le document RFC 2616, disponible sur le site web [Internet Engineering Task Force (IETF)](https://www.ietf.org/).  
  
 Les classes décrites dans le tableau suivant permettent de spécifier des stratégies de cache.  
  
|Nom de classe|Description|  
|----------------|-----------------|  
|<xref:System.Net.Cache.HttpRequestCachePolicy>|Représente des stratégies de cache basées sur l’emplacement et sur la durée pour les ressources demandées à l’aide d’objets <xref:System.Net.HttpWebRequest>.|  
|<xref:System.Net.Cache.RequestCachePolicy>|Représente des stratégies de cache basées sur l’emplacement ou la stratégie de cache basée sur la durée <xref:System.Net.Cache.RequestCacheLevel.Default> pour les ressources demandées à l’aide d’objets <xref:System.Net.WebRequest>.|  
|<xref:System.Net.Cache.HttpCacheAgeControl>|Spécifie les valeurs utilisées pour créer des objets <xref:System.Net.Cache.HttpRequestCachePolicy> basés sur la durée.|  
|<xref:System.Net.Cache.HttpRequestCacheLevel>|Spécifie les valeurs utilisées pour créer des objets <xref:System.Net.Cache.HttpRequestCachePolicy> basés sur la durée et sur l’emplacement.|  
|<xref:System.Net.Cache.RequestCacheLevel>|Spécifie les valeurs utilisées pour créer des objets basés sur l’emplacement ou les objets <xref:System.Net.Cache.RequestCachePolicy> basés sur la durée <xref:System.Net.Cache.RequestCacheLevel.Default>.|  
  
 Vous pouvez définir une stratégie de cache pour toutes les requêtes effectuées par votre application ou pour des requêtes individuelles. Quand vous spécifiez à la fois une stratégie de cache au niveau de l’application et une stratégie de cache au niveau de la requête, c’est la stratégie au niveau de la requête qui est utilisée. Vous pouvez spécifier une stratégie de cache au niveau de l’application par programmation ou à l’aide de fichiers de configuration d’application ou d’ordinateur. Pour plus d’informations, consultez [ \<requestCaching> élément (paramètres réseau)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md).  
  
 Pour créer une stratégie de cache, vous devez créer un objet de stratégie en créant une instance de la classe <xref:System.Net.Cache.RequestCachePolicy> ou <xref:System.Net.Cache.HttpRequestCachePolicy>. Pour spécifier la stratégie sur une requête, affectez l’objet de stratégie comme valeur de la propriété <xref:System.Net.WebRequest.CachePolicy%2A> de la requête. Quand vous définissez une stratégie au niveau de l’application par programmation, affectez l’objet de stratégie comme valeur de la propriété <xref:System.Net.HttpWebRequest.DefaultCachePolicy%2A>.  
  
 Pour obtenir des exemples de code qui montrent comment créer et utiliser des stratégies de cache, consultez [Configuration de la mise en cache dans les applications réseau](configuring-caching-in-network-applications.md).  
  
## <a name="see-also"></a>Voir aussi

- [Gestion du cache pour les applications réseau](cache-management-for-network-applications.md)
- [stratégies de cache basées sur l’emplacement](location-based-cache-policies.md)
- [stratégies de cache basées sur la durée](time-based-cache-policies.md)
- [Configuration de la mise en cache dans les applications réseau](configuring-caching-in-network-applications.md)

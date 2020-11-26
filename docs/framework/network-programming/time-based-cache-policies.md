---
title: stratégies de cache basées sur la durée
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- cache synchronization date policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- time, cached resources
- maximum age policy
- synchronization, cache
- staleness of cached resources
- default time-based cache policy
- maximum staleness policy
- content cache policies
- expired content
- minimum freshness policy
- age of cached resources
ms.assetid: 74f0bcaf-5c95-40c1-9967-f3bbf1d2360a
ms.openlocfilehash: 372621ce55891cb87594e6d059c7bbeeb99f6468
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239417"
---
# <a name="time-based-cache-policies"></a>stratégies de cache basées sur la durée

Une stratégie de cache basée sur la durée définit l’actualisation des entrées en cache en fonction de l’heure de récupération de la ressource, des en-têtes retournés avec la ressource et de l’heure actuelle. Quand vous définissez une stratégie de cache basée sur la durée, vous pouvez utiliser la stratégie basée sur la durée <xref:System.Net.Cache.HttpRequestCacheLevel.Default> ou créer une stratégie basée sur la durée personnalisée. Si vous utilisez la stratégie basée sur la durée par défaut pour les ressources obtenues à l’aide du protocole HTTP (Hypertext Transfer Protocol), le comportement du cache est précisé par les en-têtes inclus dans la réponse en cache et par les comportements spécifiés dans les sections 13 et 14 de la norme RFC 2616, disponible sur le site web [Internet Engineering Task Force (IETF)](https://www.ietf.org/). Pour obtenir un exemple de code qui montre comment définir la stratégie basée sur la durée par défaut pour les ressources HTTP, consultez [Guide pratique pour définir la stratégie de cache basée sur la durée par défaut pour une application](how-to-set-the-default-time-based-cache-policy-for-an-application.md). Pour obtenir des exemples de code qui montrent comment créer et utiliser des stratégies de cache, consultez [Configuration de la mise en cache dans les applications réseau](configuring-caching-in-network-applications.md).  
  
## <a name="criteria-to-determine-freshness-of-cached-entries"></a>Critères déterminant l’actualisation des entrées en cache  

 Pour personnaliser une stratégie de cache basée sur la durée, vous pouvez spécifier un ou plusieurs des critères suivants qui déterminent l’actualisation des entrées en cache :  
  
- Ancienneté maximale  
  
- Obsolescence maximale  
  
- Actualisation minimale  
  
- Date de synchronisation du cache  
  
> [!NOTE]
> Utiliser la stratégie de cache basée sur la durée par défaut n’équivaut pas à définir une stratégie de cache par défaut pour votre application. La stratégie basée sur la durée par défaut est une stratégie spécifique qui peut être utilisée au niveau de la requête ou de l’application. La stratégie de cache par défaut pour votre application est une stratégie (basée sur l’emplacement ou sur la durée) qui est appliquée quand aucune stratégie n’est définie au niveau d’une requête. Pour plus d’informations sur la définition d’une stratégie de cache par défaut pour votre application, consultez <xref:System.Net.WebRequest.DefaultCachePolicy%2A>.  
  
### <a name="maximum-age"></a>Maximum Age  

 Le critère de stratégie d’ancienneté maximale spécifie la durée pendant laquelle une copie en cache d’une ressource peut être utilisée. Si la copie en cache de la ressource est plus ancienne que la durée spécifiée, la ressource doit être revalidée en la vérifiant par rapport au contenu sur le serveur. Si l’ancienneté maximale permet l’utilisation de la ressource après son expiration, ce critère n’est pas appliqué, sauf si une valeur d’obsolescence maximale est également spécifiée.  
  
### <a name="maximum-staleness"></a>Obsolescence maximale  

 Le critère de stratégie d’obsolescence maximale spécifie la durée pendant laquelle la copie en cache de la ressource peut continuer à être utilisée après l’expiration du contenu. C’est le seul critère de stratégie de cache qui autorise l’utilisation d’une ressource après son expiration.  
  
### <a name="minimum-freshness"></a>Actualisation minimale  

 Le critère de stratégie d’actualisation minimale spécifie la durée pendant laquelle la copie en cache de la ressource peut être utilisée avant l’expiration du contenu. Avec cette stratégie, une entrée en cache devient obsolète avant même sa date d’expiration. Les paramètres d’actualisation minimale et d’obsolescence maximale s’excluent donc mutuellement.  
  
## <a name="cache-synchronization-date"></a>Date de synchronisation du cache  

 Le critère de stratégie de date de synchronisation du cache détermine à quel moment une copie en cache d’une ressource doit être revalidée en la vérifiant par rapport au contenu sur le serveur. Si le contenu a été modifié depuis la mise en cache de l’élément, le nouveau contenu est récupéré du serveur, stocké dans le cache et retourné à l’application. Si le contenu n’a pas été modifié, son timestamp est mis à jour et l’application récupère le contenu en cache.  
  
 La date de synchronisation du cache vous permet de spécifier une date fixe à laquelle le contenu en cache doit être revalidé. Si une entrée en cache actualisée a été revalidée avant la date de synchronisation du cache, une nouvelle revalidation auprès du serveur est effectuée. Si l’entrée en cache a été revalidée après la date de synchronisation du cache et qu’aucune autre exigence d’actualisation ou de revalidation auprès du serveur n’invalide l’entrée en cache, l’entrée en cache actuelle est utilisée. Si la date de synchronisation du cache est définie à une date ultérieure, l’entrée est revalidée à chaque nouvelle requête jusqu’à ce que la date de synchronisation du cache soit atteinte.  
  
 Les rubriques suivantes fournissent des informations sur les effets de la combinaison de plusieurs critères d’une stratégie de cache basée sur la durée :  
  
- [Interaction de la stratégie de cache : ancienneté maximale et péremption maximale](cache-policy-interaction-maximum-age-and-maximum-staleness.md)  
  
- [Interaction de la stratégie de cache : ancienneté maximale et actualisation minimale](cache-policy-interaction-maximum-age-and-minimum-freshness.md)  
  
## <a name="see-also"></a>Voir aussi

- [Gestion du cache pour les applications réseau](cache-management-for-network-applications.md)
- [Stratégie de cache](cache-policy.md)
- [stratégies de cache basées sur l’emplacement](location-based-cache-policies.md)
- [Configuration de la mise en cache dans les applications réseau](configuring-caching-in-network-applications.md)
- [\<requestCaching> , Élément (paramètres réseau)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)

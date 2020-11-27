---
title: 'Interaction de la stratégie de cache : ancienneté maximale et péremption maximale'
ms.date: 03/30/2017
helpviewer_keywords:
- maximum staleness
- freshness of cached resources
- time, cached resources
- maximum age policy
- staleness of cached resources
- age of cached resources
ms.assetid: 7f775925-89a1-4956-ba90-c869c1749a94
ms.openlocfilehash: bdfa608b5169755b2b4daaaa26e562308ae2be01
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250604"
---
# <a name="cache-policy-interactionmaximum-age-and-maximum-staleness"></a>Interaction de la stratégie de cache : ancienneté maximale et péremption maximale

Pour vous assurer que le contenu le plus récent est renvoyé à l’application cliente, l’interaction entre la stratégie de cache du client et les exigences de revalidation du serveur ont toujours comme résultat la stratégie de cache la plus restrictive. Tous les exemples de cette rubrique illustrent la stratégie de cache pour une ressource mise en cache le 1er janvier et expirant le 4 janvier.  
  
 Dans les exemples suivants, la valeur de péremption maximale (`maxStale`) est utilisée conjointement avec une ancienneté maximale (`maxAge`) :  
  
- Si la stratégie de cache définit `maxAge` = 5 jours et ne spécifie pas de valeur `maxStale`, d’après la valeur `maxAge`, le contenu est utilisable jusqu’au 6 janvier. Toutefois, conformément aux besoins de revalidation du serveur, le contenu expire le 4 janvier. La date d’expiration du contenu étant plus restrictive (plus tôt), elle est prioritaire par rapport à la stratégie `maxAge`. Par conséquent, le contenu expire le 4 janvier et doit être revalidé même si son ancienneté maximale n’a pas été atteinte.  
  
- Si la stratégie de cache définit `maxAge` = 5 jours et `maxStale` = 3 jours, d’après la valeur `maxAge`, le contenu est utilisable jusqu’au 6 janvier. D’après la valeur `maxStale`, le contenu est utilisable jusqu’au 7 janvier. Par conséquent, le contenu est revalidé le 6 janvier.  
  
- Si la stratégie de cache définit `maxAge` = 5 jours et `maxStale` = 1 jour, d’après la valeur `maxAge`, le contenu est utilisable jusqu’au 6 janvier. D’après la valeur `maxStale`, le contenu est utilisable jusqu’au 5 janvier. Par conséquent, le contenu est revalidé le 5 janvier.  
  
 Quand l’ancienneté maximale est inférieure à la date d’expiration du contenu, le comportement de mise en cache le plus restrictif prévaut toujours et la valeur de péremption maximale n’a aucun effet. Les exemples suivants illustrent l’effet de la définition d’une valeur de péremption maximale (`maxStale`) quand l’ancienneté maximale (`maxAge`) est atteinte avant l’expiration du contenu :  
  
- Si la stratégie de cache définit `maxAge` = 1 jour et ne spécifie pas de valeur pour `maxStale`, le contenu est revalidé le 2 janvier même s’il n’a pas expiré.  
  
- Si la stratégie de cache définit `maxAge` = 1 jour et `maxStale` = 3 jours, le contenu est revalidé le 2 janvier pour appliquer le paramètre de stratégie le plus restrictif.  
  
- Si la stratégie de cache définit `maxAge` = 1 jour et `maxStale` = 1 jour, le contenu est revalidé le 2 janvier.  
  
## <a name="see-also"></a>Voir aussi

- [Gestion du cache pour les applications réseau](cache-management-for-network-applications.md)
- [Stratégie de cache](cache-policy.md)
- [stratégies de cache basées sur l’emplacement](location-based-cache-policies.md)
- [stratégies de cache basées sur la durée](time-based-cache-policies.md)
- [Configuration de la mise en cache dans les applications réseau](configuring-caching-in-network-applications.md)
- [Interaction de la stratégie de cache : ancienneté maximale et actualisation minimale](cache-policy-interaction-maximum-age-and-minimum-freshness.md)

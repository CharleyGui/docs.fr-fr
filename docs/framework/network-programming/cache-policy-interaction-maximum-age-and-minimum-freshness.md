---
title: 'Interaction de la stratégie de cache : ancienneté maximale et actualisation minimale'
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- Revalidate policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- maximum age policy
- minimum freshness policy
- age of cached resources
ms.assetid: 6567d451-ecec-496c-95a3-a415b99ba52a
ms.openlocfilehash: d4182268341f4a4334a627fc8c9e24fa235f003f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96287551"
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a>Interaction de la stratégie de cache : ancienneté maximale et actualisation minimale

Pour vous assurer que le contenu le plus récent est renvoyé à l’application cliente, l’interaction entre la stratégie de cache du client et les exigences de revalidation du serveur ont toujours comme résultat la stratégie de cache la plus restrictive. Tous les exemples de cette rubrique illustrent la stratégie de cache pour une ressource mise en cache le 1er janvier et expirant le 4 janvier.  
  
 Les exemples suivants illustrent la stratégie de cache qui résulte de l’interaction entre les valeurs d’ancienneté maximale (`maxAge`) et d’actualisation minimale (`minFresh`).  
  
- Si la stratégie de cache définit `maxAge` = 2 jours et `minFresh` n’est pas spécifié, le contenu est revalidé le 3 janvier.  
  
- Si la stratégie de cache définit `maxAge` = 2 jours et `minFresh` = 1 jour, d’après `maxAge`, le contenu est utilisable jusqu’au 3 janvier. D’après `minFresh`, le contenu est utilisable jusqu’au 3 janvier. Par conséquent, le contenu doit être revalidé le 3 janvier.  
  
- Si la stratégie de cache définit `maxAge` = 2 jours et `minFresh` = 2 jours, d’après `maxAge`, le contenu est utilisable jusqu’au 3 janvier. D’après `minFresh`, le contenu est utilisable jusqu’au 2 janvier. Par conséquent, le contenu doit être revalidé le 2 janvier.  
  
## <a name="see-also"></a>Voir aussi

- [Gestion du cache pour les applications réseau](cache-management-for-network-applications.md)
- [Stratégie de cache](cache-policy.md)
- [stratégies de cache basées sur l’emplacement](location-based-cache-policies.md)
- [stratégies de cache basées sur la durée](time-based-cache-policies.md)
- [Configuration de la mise en cache dans les applications réseau](configuring-caching-in-network-applications.md)
- [Interaction de la stratégie de cache : ancienneté maximale et péremption maximale](cache-policy-interaction-maximum-age-and-maximum-staleness.md)

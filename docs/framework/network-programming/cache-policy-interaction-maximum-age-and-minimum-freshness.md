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
ms.openlocfilehash: 8d4071a7f8dbb1cca1440fa69ae40df17330b060
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624656"
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a>Interaction de la stratégie de cache : ancienneté maximale et actualisation minimale
Pour vous assurer que le contenu le plus récent est renvoyé à l’application cliente, l’interaction entre la stratégie de cache du client et les exigences de revalidation du serveur ont toujours comme résultat la stratégie de cache la plus restrictive. Tous les exemples de cette rubrique illustrent la stratégie de cache pour une ressource mise en cache le 1er janvier et expirant le 4 janvier.  
  
 Les exemples suivants illustrent la stratégie de cache qui résulte de l’interaction entre les valeurs d’ancienneté maximale (`maxAge`) et d’actualisation minimale (`minFresh`).  
  
- Si la stratégie de cache définit `maxAge` = 2 jours et `minFresh` n’est pas spécifié, le contenu est revalidé le 3 janvier.  
  
- Si la stratégie de cache définit `maxAge` = 2 jours et `minFresh` = 1 jour, d’après `maxAge`, le contenu est utilisable jusqu’au 3 janvier. D’après `minFresh`, le contenu est utilisable jusqu’au 3 janvier. Par conséquent, le contenu doit être revalidé le 3 janvier.  
  
- Si la stratégie de cache définit `maxAge` = 2 jours et `minFresh` = 2 jours, d’après `maxAge`, le contenu est utilisable jusqu’au 3 janvier. D’après `minFresh`, le contenu est utilisable jusqu’au 2 janvier. Par conséquent, le contenu doit être revalidé le 2 janvier.  
  
## <a name="see-also"></a>Voir aussi

- [Gestion du cache pour les applications réseau](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [Stratégie de cache](../../../docs/framework/network-programming/cache-policy.md)
- [Stratégies de cache basées sur l’emplacement](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [Stratégies de cache basées sur la durée](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [Configuration de la mise en cache dans les applications réseau](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)
- [Interaction de la stratégie de cache : ancienneté maximale et péremption maximale](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)

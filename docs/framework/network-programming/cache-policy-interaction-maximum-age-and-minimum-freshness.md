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
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a><span data-ttu-id="faf23-102">Interaction de la stratégie de cache : ancienneté maximale et actualisation minimale</span><span class="sxs-lookup"><span data-stu-id="faf23-102">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>
<span data-ttu-id="faf23-103">Pour vous assurer que le contenu le plus récent est renvoyé à l’application cliente, l’interaction entre la stratégie de cache du client et les exigences de revalidation du serveur ont toujours comme résultat la stratégie de cache la plus restrictive.</span><span class="sxs-lookup"><span data-stu-id="faf23-103">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="faf23-104">Tous les exemples de cette rubrique illustrent la stratégie de cache pour une ressource mise en cache le 1er janvier et expirant le 4 janvier.</span><span class="sxs-lookup"><span data-stu-id="faf23-104">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="faf23-105">Les exemples suivants illustrent la stratégie de cache qui résulte de l’interaction entre les valeurs d’ancienneté maximale (`maxAge`) et d’actualisation minimale (`minFresh`).</span><span class="sxs-lookup"><span data-stu-id="faf23-105">The following examples illustrate the cache policy that results from the interaction of the maximum age (`maxAge`) and minimum freshness (`minFresh`) values.</span></span>  
  
- <span data-ttu-id="faf23-106">Si la stratégie de cache définit `maxAge` = 2 jours et `minFresh` n’est pas spécifié, le contenu est revalidé le 3 janvier.</span><span class="sxs-lookup"><span data-stu-id="faf23-106">If the cache policy sets `maxAge` = 2 days and `minFresh` is not specified, the content is revalidated on January 3.</span></span>  
  
- <span data-ttu-id="faf23-107">Si la stratégie de cache définit `maxAge` = 2 jours et `minFresh` = 1 jour, d’après `maxAge`, le contenu est utilisable jusqu’au 3 janvier.</span><span class="sxs-lookup"><span data-stu-id="faf23-107">If the cache policy sets `maxAge` = 2 days and `minFresh` = 1 day, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="faf23-108">D’après `minFresh`, le contenu est utilisable jusqu’au 3 janvier.</span><span class="sxs-lookup"><span data-stu-id="faf23-108">According to `minFresh`, the content is fresh until January 3.</span></span> <span data-ttu-id="faf23-109">Par conséquent, le contenu doit être revalidé le 3 janvier.</span><span class="sxs-lookup"><span data-stu-id="faf23-109">Therefore, the content must be revalidated on January 3.</span></span>  
  
- <span data-ttu-id="faf23-110">Si la stratégie de cache définit `maxAge` = 2 jours et `minFresh` = 2 jours, d’après `maxAge`, le contenu est utilisable jusqu’au 3 janvier.</span><span class="sxs-lookup"><span data-stu-id="faf23-110">If the cache policy sets `maxAge` = 2 days and `minFresh` = 2 days, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="faf23-111">D’après `minFresh`, le contenu est utilisable jusqu’au 2 janvier.</span><span class="sxs-lookup"><span data-stu-id="faf23-111">According to `minFresh` the content is fresh until January 2.</span></span> <span data-ttu-id="faf23-112">Par conséquent, le contenu doit être revalidé le 2 janvier.</span><span class="sxs-lookup"><span data-stu-id="faf23-112">Therefore, the content must be revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faf23-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="faf23-113">See also</span></span>

- [<span data-ttu-id="faf23-114">Gestion du cache pour les applications réseau</span><span class="sxs-lookup"><span data-stu-id="faf23-114">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [<span data-ttu-id="faf23-115">Stratégie de cache</span><span class="sxs-lookup"><span data-stu-id="faf23-115">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)
- [<span data-ttu-id="faf23-116">Stratégies de cache basées sur l’emplacement</span><span class="sxs-lookup"><span data-stu-id="faf23-116">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [<span data-ttu-id="faf23-117">Stratégies de cache basées sur la durée</span><span class="sxs-lookup"><span data-stu-id="faf23-117">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [<span data-ttu-id="faf23-118">Configuration de la mise en cache dans les applications réseau</span><span class="sxs-lookup"><span data-stu-id="faf23-118">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)
- [<span data-ttu-id="faf23-119">Interaction de la stratégie de cache : ancienneté maximale et péremption maximale</span><span class="sxs-lookup"><span data-stu-id="faf23-119">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>](../../../docs/framework/network-programming/cache-policy-interaction-maximum-age-and-maximum-staleness.md)

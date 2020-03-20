---
title: Gestion du cache pour les applications réseau
ms.date: 03/30/2017
helpviewer_keywords:
- cache [.NET Framework], network applications
- network resources, caching
- Internet, caching
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
ms.openlocfilehash: 7e131963999db3e3d5e0e6f3fa110da36e6452a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048876"
---
# <a name="cache-management-for-network-applications"></a><span data-ttu-id="aa22f-102">Gestion du cache pour les applications réseau</span><span class="sxs-lookup"><span data-stu-id="aa22f-102">Cache Management for Network Applications</span></span>
<span data-ttu-id="aa22f-103">Cette rubrique et ses sous-rubriques associées décrivent la mise en cache pour les ressources obtenues à l’aide des classes <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest> et <xref:System.Net.FtpWebRequest>.</span><span class="sxs-lookup"><span data-stu-id="aa22f-103">This topic and its related subtopics describe caching for resources obtained using the <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>  
  
 <span data-ttu-id="aa22f-104">Un cache procure un stockage temporaire des ressources qui ont été demandées par une application.</span><span class="sxs-lookup"><span data-stu-id="aa22f-104">A cache provides temporary storage of resources that have been requested by an application.</span></span> <span data-ttu-id="aa22f-105">Si une application demande la même ressource plusieurs fois, celle-ci peut être retournée à partir du cache, ce qui évite de devoir la redemander au serveur.</span><span class="sxs-lookup"><span data-stu-id="aa22f-105">If an application requests the same resource more than once, the resource can be returned from the cache, avoiding the overhead of re-requesting it from the server.</span></span> <span data-ttu-id="aa22f-106">La mise en cache peut améliorer les performances de l’application en réduisant la durée nécessaire pour obtenir une ressource demandée.</span><span class="sxs-lookup"><span data-stu-id="aa22f-106">Caching can improve application performance by reducing the time required to get a requested resource.</span></span> <span data-ttu-id="aa22f-107">Elle peut également réduire le trafic réseau en réduisant le nombre d’allers-retours au serveur.</span><span class="sxs-lookup"><span data-stu-id="aa22f-107">Caching can also decrease network traffic by reducing the number of trips to the server.</span></span> <span data-ttu-id="aa22f-108">Bien que la mise en cache améliore les performances, elle augmente le risque que la ressource retournée à l’application soit périmée, c’est-à-dire qu’elle ne soit pas identique à la ressource qui aurait été envoyée par le serveur si la mise en cache n’était pas utilisée.</span><span class="sxs-lookup"><span data-stu-id="aa22f-108">While caching improves performance, it increases the risk that the resource returned to the application is stale, meaning that it is not identical to the resource that would have been sent by the server if caching were not in use.</span></span>  
  
 <span data-ttu-id="aa22f-109">La mise en cache peut permettre à des utilisateurs ou des processus non autorisés de lire des données sensibles.</span><span class="sxs-lookup"><span data-stu-id="aa22f-109">Caching may allow unauthorized users or processes to read sensitive data.</span></span> <span data-ttu-id="aa22f-110">Une réponse authentifiée mise en cache peut-être récupérée à partir du cache sans autorisation supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="aa22f-110">An authenticated response that is cached may be retrieved from the cache without an additional authorization.</span></span> <span data-ttu-id="aa22f-111">Si la mise en cache est activée, définissez <xref:System.Net.WebRequest.CachePolicy%2A> sur <xref:System.Net.Cache.RequestCacheLevel.BypassCache> ou <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> pour désactiver la mise en cache pour cette demande.</span><span class="sxs-lookup"><span data-stu-id="aa22f-111">If caching is enabled, change to <xref:System.Net.WebRequest.CachePolicy%2A> to <xref:System.Net.Cache.RequestCacheLevel.BypassCache> or <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> to disable caching for this request.</span></span>  
  
 <span data-ttu-id="aa22f-112">Pour des raisons de sécurité, la mise en cache n’est **pas** recommandée pour les scénarios de couche intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="aa22f-112">Due to security concerns, caching is **not** recommended for middle tier scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aa22f-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="aa22f-113">In This Section</span></span>  
 [<span data-ttu-id="aa22f-114">Stratégie de cache</span><span class="sxs-lookup"><span data-stu-id="aa22f-114">Cache Policy</span></span>](cache-policy.md)  
 <span data-ttu-id="aa22f-115">Explique ce qu’est une stratégie de cache et comment en définir une.</span><span class="sxs-lookup"><span data-stu-id="aa22f-115">Explains what a cache policy is and how to define one.</span></span>  
  
 [<span data-ttu-id="aa22f-116">Stratégies de cache basées sur l’emplacement</span><span class="sxs-lookup"><span data-stu-id="aa22f-116">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)  
 <span data-ttu-id="aa22f-117">Définit chaque type de stratégie de cache basée sur l’emplacement disponible pour les ressources Hypertext Transfer Protocol (http et https).</span><span class="sxs-lookup"><span data-stu-id="aa22f-117">Defines each type of location-based cache policy available for Hypertext Transfer Protocol (http and https) resources.</span></span>  
  
 [<span data-ttu-id="aa22f-118">Stratégies de cache basées sur la durée</span><span class="sxs-lookup"><span data-stu-id="aa22f-118">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)  
 <span data-ttu-id="aa22f-119">Décrit les critères qui peuvent être utilisés pour personnaliser une stratégie de cache basée sur la durée.</span><span class="sxs-lookup"><span data-stu-id="aa22f-119">Describes the criteria that can be used to customize a time-based cache policy.</span></span>  
  
 [<span data-ttu-id="aa22f-120">Configuration de la mise en cache dans les applications réseau</span><span class="sxs-lookup"><span data-stu-id="aa22f-120">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)  
 <span data-ttu-id="aa22f-121">Décrit comment créer par programmation des stratégies de cache et des demandes qui utilisent la mise en cache.</span><span class="sxs-lookup"><span data-stu-id="aa22f-121">Describes how to programmatically create cache policies and requests that use caching.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="aa22f-122">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="aa22f-122">Reference</span></span>  
 <xref:System.Net.Cache>  
 <span data-ttu-id="aa22f-123">Définit les types et les énumérations utilisés pour définir des stratégies de cache applicables aux ressources obtenues à l’aide des classes <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest> et <xref:System.Net.FtpWebRequest>.</span><span class="sxs-lookup"><span data-stu-id="aa22f-123">Defines the types and enumerations used to define cache policies for resources obtained using the <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>

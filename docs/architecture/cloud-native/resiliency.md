---
title: Résilience cloud native
description: Architecture des applications .NET natives Cloud pour Azure | Résilience native du Cloud
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: f3aa89e3ae21b13a31f65013b59636b3f931553c
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613770"
---
# <a name="cloud-native-resiliency"></a><span data-ttu-id="622da-103">Résilience cloud native</span><span class="sxs-lookup"><span data-stu-id="622da-103">Cloud-native resiliency</span></span>

<span data-ttu-id="622da-104">La résilience est la capacité de votre système à réagir à une défaillance tout en restant fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="622da-104">Resiliency is the ability of your system to react to failure and still remain functional.</span></span> <span data-ttu-id="622da-105">Il ne s’agit pas d’éviter les défaillances, mais d’accepter les défaillances et de créer vos services Cloud natifs pour y répondre.</span><span class="sxs-lookup"><span data-stu-id="622da-105">It's not about avoiding failure, but accepting failure and constructing your cloud-native services to respond to it.</span></span> <span data-ttu-id="622da-106">Vous souhaitez revenir à un état de fonctionnement complet le plus rapidement possible.</span><span class="sxs-lookup"><span data-stu-id="622da-106">You want to return to a fully functioning state quickly as possible.</span></span>

<span data-ttu-id="622da-107">Contrairement aux applications monolithiques traditionnelles, où tout fonctionne ensemble dans un processus unique, les systèmes Cloud natifs adoptent une architecture distribuée, comme illustré dans la figure 6-1 :</span><span class="sxs-lookup"><span data-stu-id="622da-107">Unlike traditional monolithic applications, where everything runs together in a single process, cloud-native systems embrace a distributed architecture as shown in Figure 6-1:</span></span>

![Cloud distribué-environnement natif](./media/distributed-cloud-native-environment.png)

<span data-ttu-id="622da-109">**Figure 6-1.**</span><span class="sxs-lookup"><span data-stu-id="622da-109">**Figure 6-1.**</span></span> <span data-ttu-id="622da-110">Cloud distribué-environnement natif</span><span class="sxs-lookup"><span data-stu-id="622da-110">Distributed cloud-native environment</span></span>

<span data-ttu-id="622da-111">Dans la figure précédente, chaque microservice et [service de sauvegarde](https://12factor.net/backing-services) basé sur le Cloud s’exécutent dans un processus distinct, sur l’infrastructure de serveur, communiquant via des appels basés sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="622da-111">In the previous figure, each microservice and cloud-based [backing service](https://12factor.net/backing-services) execute in a separate process, across server infrastructure, communicating via network-based calls.</span></span>

<span data-ttu-id="622da-112">Dans cet environnement, un service doit être sensible à de nombreux défis :</span><span class="sxs-lookup"><span data-stu-id="622da-112">Operating in this environment, a service must be sensitive to many different challenges:</span></span>

- <span data-ttu-id="622da-113">Latence réseau inattendue : durée d’une demande de service pour le déplacement vers le récepteur et l’inverse.</span><span class="sxs-lookup"><span data-stu-id="622da-113">Unexpected network latency - the time for a service request to travel to the receiver and back.</span></span>

- <span data-ttu-id="622da-114">Erreurs [temporaires](https://docs.microsoft.com/azure/architecture/best-practices/transient-faults) -erreurs de connectivité réseau à courte durée de vie.</span><span class="sxs-lookup"><span data-stu-id="622da-114">[Transient faults](https://docs.microsoft.com/azure/architecture/best-practices/transient-faults) - short-lived network connectivity errors.</span></span>

- <span data-ttu-id="622da-115">Blocage par une opération synchrone de longue durée.</span><span class="sxs-lookup"><span data-stu-id="622da-115">Blockage by a long-running synchronous operation.</span></span>

- <span data-ttu-id="622da-116">Processus hôte qui s’est bloqué et qui est en cours de redémarrage ou de déplacement.</span><span class="sxs-lookup"><span data-stu-id="622da-116">A host process that has crashed and is being restarted or moved.</span></span>

- <span data-ttu-id="622da-117">Microservice surchargé qui ne peut pas répondre pendant une brève période.</span><span class="sxs-lookup"><span data-stu-id="622da-117">An overloaded microservice that can't respond for a short time.</span></span>

- <span data-ttu-id="622da-118">Une opération Orchestrator in-Flight, telle qu’une mise à niveau propagée ou le déplacement d’un service d’un nœud à un autre.</span><span class="sxs-lookup"><span data-stu-id="622da-118">An in-flight orchestrator operation such as a rolling upgrade or moving a service from one node to another.</span></span>

- <span data-ttu-id="622da-119">Défaillances matérielles.</span><span class="sxs-lookup"><span data-stu-id="622da-119">Hardware failures.</span></span>

<span data-ttu-id="622da-120">Les plateformes Cloud peuvent détecter et atténuer un grand nombre de ces problèmes d’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="622da-120">Cloud platforms can detect and mitigate many of these infrastructure issues.</span></span> <span data-ttu-id="622da-121">Il peut redémarrer, monter en charge et même redistribuer votre service vers un autre nœud.</span><span class="sxs-lookup"><span data-stu-id="622da-121">It may restart, scale out, and even redistribute your service to a different node.</span></span>  <span data-ttu-id="622da-122">Toutefois, pour tirer pleinement parti de cette protection intégrée, vous devez concevoir vos services pour y réagir et prospérer dans cet environnement dynamique.</span><span class="sxs-lookup"><span data-stu-id="622da-122">However, to take full advantage of this built-in protection, you must design your services to react to it and thrive in this dynamic environment.</span></span>

<span data-ttu-id="622da-123">Dans les sections suivantes, nous allons explorer les techniques défensives que votre service et vos ressources cloud gérées peuvent exploiter pour réduire les temps d’arrêt et les interruptions.</span><span class="sxs-lookup"><span data-stu-id="622da-123">In the following sections, we'll explore defensive techniques that your service and managed cloud resources can leverage to minimize downtime and disruption.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="622da-124">[Précédent](elastic-search-in-azure.md) 
> [Suivant](application-resiliency-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="622da-124">[Previous](elastic-search-in-azure.md)
[Next](application-resiliency-patterns.md)</span></span>

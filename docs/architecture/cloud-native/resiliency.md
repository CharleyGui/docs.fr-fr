---
title: Résilience cloud native
description: Architecture des applications .NET natives Cloud pour Azure | Résilience native du Cloud
ms.date: 06/30/2019
ms.openlocfilehash: 427405d95534c4467ab519c2188fe88e2f18e2b2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781084"
---
# <a name="cloud-native-resiliency"></a><span data-ttu-id="22d94-103">Résilience cloud native</span><span class="sxs-lookup"><span data-stu-id="22d94-103">Cloud-native resiliency</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="22d94-104">La résilience est la capacité de votre système à réagir à une défaillance tout en restant fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="22d94-104">Resiliency is the ability of your system to react to failure and still remain functional.</span></span> <span data-ttu-id="22d94-105">Il ne s’agit pas d’éviter les défaillances.</span><span class="sxs-lookup"><span data-stu-id="22d94-105">It isn't about avoiding failure.</span></span> <span data-ttu-id="22d94-106">Mais il s’agit d’accepter que l’échec soit inévitable dans les systèmes Cloud et de créer votre application pour y répondre.</span><span class="sxs-lookup"><span data-stu-id="22d94-106">But it's about accepting that failure is inevitable in cloud-based systems and building your application to respond to it.</span></span> <span data-ttu-id="22d94-107">L’objectif final de la résilience est de ramener l’application à un état de fonctionnement complet après une défaillance.</span><span class="sxs-lookup"><span data-stu-id="22d94-107">The end-goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="22d94-108">Contrairement aux applications monolithiques traditionnelles, où tout s’exécute dans un processus unique, les systèmes natifs du Cloud intègrent l’architecture distribuée, comme illustré dans la figure 6-1 :</span><span class="sxs-lookup"><span data-stu-id="22d94-108">Unlike traditional monolithic applications, where everything runs together in a single process, cloud-native systems embrace distributed architecture as shown in Figure 6-1:</span></span>

![Cloud distribué-environnement natif](./media/distributed-cloud-native-environment.png)

<span data-ttu-id="22d94-110">**Figure 6-1.**</span><span class="sxs-lookup"><span data-stu-id="22d94-110">**Figure 6-1.**</span></span> <span data-ttu-id="22d94-111">Cloud distribué-environnement natif</span><span class="sxs-lookup"><span data-stu-id="22d94-111">Distributed cloud-native environment</span></span>

<span data-ttu-id="22d94-112">Dans la figure précédente, notez la manière dont chaque client, microservice et service de [sauvegarde](https://12factor.net/backing-services) Cloud s’exécute en tant que processus distinct, exécuté sur différents serveurs, communiquant toutes les communications via des appels basés sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="22d94-112">In the previous figure, note how each client, microservice, and cloud-based [backing service](https://12factor.net/backing-services) executes as a separate process, running across different servers, all communicating via network-based calls.</span></span>

<span data-ttu-id="22d94-113">Alors, que se passe-t-il ?</span><span class="sxs-lookup"><span data-stu-id="22d94-113">So, what could go wrong?</span></span>

- <span data-ttu-id="22d94-114">[Latence réseau](https://www.techopedia.com/definition/8553/network-latency)inattendue.</span><span class="sxs-lookup"><span data-stu-id="22d94-114">Unexpected [network latency](https://www.techopedia.com/definition/8553/network-latency).</span></span>
- <span data-ttu-id="22d94-115">[Erreurs temporaires (erreurs](https://docs.microsoft.com/azure/architecture/best-practices/transient-faults) de connectivité réseau temporaires).</span><span class="sxs-lookup"><span data-stu-id="22d94-115">[Transient faults](https://docs.microsoft.com/azure/architecture/best-practices/transient-faults) (temporary network connectivity errors).</span></span>
- <span data-ttu-id="22d94-116">Blocage par une opération synchrone de longue durée.</span><span class="sxs-lookup"><span data-stu-id="22d94-116">Blocking by a long-running synchronous operation.</span></span>
- <span data-ttu-id="22d94-117">Processus hôte qui s’est bloqué et qui est en cours de redémarrage ou de déplacement.</span><span class="sxs-lookup"><span data-stu-id="22d94-117">A host process that has crashed and is being restarted or moved.</span></span>
- <span data-ttu-id="22d94-118">Microservice surchargé qui ne peut pas répondre pendant une brève période.</span><span class="sxs-lookup"><span data-stu-id="22d94-118">An overloaded microservice that can't respond for a short time.</span></span>
- <span data-ttu-id="22d94-119">Opération DevOps en cours, telle qu’une opération de mise à jour ou de mise à l’échelle.</span><span class="sxs-lookup"><span data-stu-id="22d94-119">An in-flight DevOps operation such as an update or scaling operation.</span></span>
- <span data-ttu-id="22d94-120">Une opération Orchestrator, telle que le déplacement d’un service d’un nœud à un autre.</span><span class="sxs-lookup"><span data-stu-id="22d94-120">An Orchestrator operation such as moving a service from one node to another.</span></span>
- <span data-ttu-id="22d94-121">Défaillances matérielles du matériel de la marchandise.</span><span class="sxs-lookup"><span data-stu-id="22d94-121">Hardware failures from commodity hardware.</span></span>

<span data-ttu-id="22d94-122">Lors du déploiement de services distribués dans une infrastructure basée sur le Cloud, les facteurs de la liste précédente deviennent très réels et vous devez concevoir et développer de manière défensive pour les gérer.</span><span class="sxs-lookup"><span data-stu-id="22d94-122">When deploying distributed services into cloud-based infrastructure, the factors from the previous list become very real and you must architect and develop defensively to deal with them.</span></span>

<span data-ttu-id="22d94-123">Dans un système distribué à petite échelle, les défaillances sont moins fréquentes, mais quand un système est mis à l’échelle, vous pouvez vous attendre à rencontrer ces problèmes à un point où une défaillance partielle devient une opération normale.</span><span class="sxs-lookup"><span data-stu-id="22d94-123">In a small-scale distributed system, failure will be less frequent, but as a system scales up and out, you can expect to experience more of these issues to a point where partial failure becomes normal operation.</span></span>

<span data-ttu-id="22d94-124">Par conséquent, votre application et votre infrastructure doivent être résilientes.</span><span class="sxs-lookup"><span data-stu-id="22d94-124">Therefore, your application and infrastructure must be resilient.</span></span> <span data-ttu-id="22d94-125">Dans les sections suivantes, nous allons explorer les techniques défensives que vous pouvez ajouter à votre application et les fonctionnalités de Cloud intégrées que vous pouvez exploiter pour aider à vérifier l’expérience de vos utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="22d94-125">In the following sections, we'll explore defensive techniques that you can add to your application and built-in cloud features that you can leverage to help bullet-proof your user's experience.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="22d94-126">[Précédent](elastic-search-in-azure.md)
>[Suivant](application-resiliency-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="22d94-126">[Previous](elastic-search-in-azure.md)
[Next](application-resiliency-patterns.md)</span></span>

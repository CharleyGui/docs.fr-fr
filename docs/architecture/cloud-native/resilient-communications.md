---
title: Communication résiliente
description: Architecture des applications .NET natives Cloud pour Azure | Communication résiliente
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 33e4c03c1f3d8c01f72c588326fbb0bdfa512cdd
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613744"
---
# <a name="resilient-communications"></a><span data-ttu-id="965d4-103">Communications résilientes</span><span class="sxs-lookup"><span data-stu-id="965d4-103">Resilient communications</span></span>

<span data-ttu-id="965d4-104">Tout au long de ce document, nous avons adopté une approche architecturale basée sur des microservices.</span><span class="sxs-lookup"><span data-stu-id="965d4-104">Throughout this book, we've embraced a microservice-based architectural approach.</span></span> <span data-ttu-id="965d4-105">Bien qu’une telle architecture offre des avantages importants, elle présente de nombreux défis :</span><span class="sxs-lookup"><span data-stu-id="965d4-105">While such an architecture provides important benefits, it presents many challenges:</span></span>

- <span data-ttu-id="965d4-106">*Communication réseau hors processus.*</span><span class="sxs-lookup"><span data-stu-id="965d4-106">*Out-of-process network communication.*</span></span> <span data-ttu-id="965d4-107">Chaque microservice communique via un protocole réseau qui introduit une congestion du réseau, une latence et des erreurs temporaires.</span><span class="sxs-lookup"><span data-stu-id="965d4-107">Each microservice communicates over a network protocol that introduces network congestion, latency, and transient faults.</span></span>

- <span data-ttu-id="965d4-108">*Détection du service.*</span><span class="sxs-lookup"><span data-stu-id="965d4-108">*Service discovery.*</span></span> <span data-ttu-id="965d4-109">Comment les microservices découvrent et communiquent les uns avec les autres lorsqu’ils s’exécutent sur un cluster de machines avec leurs propres ports et adresses IP ?</span><span class="sxs-lookup"><span data-stu-id="965d4-109">How do microservices discover and communicate with each other when running across a cluster of machines with their own IP addresses and ports?</span></span>

- <span data-ttu-id="965d4-110">*Résilience.*</span><span class="sxs-lookup"><span data-stu-id="965d4-110">*Resiliency.*</span></span> <span data-ttu-id="965d4-111">Comment gérer les défaillances de courte durée de vie et assurer la stabilité du système ?</span><span class="sxs-lookup"><span data-stu-id="965d4-111">How do you manage short-lived failures and keep the system stable?</span></span>

- <span data-ttu-id="965d4-112">*Équilibrage de charge.*</span><span class="sxs-lookup"><span data-stu-id="965d4-112">*Load balancing.*</span></span> <span data-ttu-id="965d4-113">Comment le trafic entrant est-il distribué entre plusieurs instances d’un microservice ?</span><span class="sxs-lookup"><span data-stu-id="965d4-113">How does inbound traffic get distributed across multiple instances of a microservice?</span></span>

- <span data-ttu-id="965d4-114">*Sécurité.*</span><span class="sxs-lookup"><span data-stu-id="965d4-114">*Security.*</span></span> <span data-ttu-id="965d4-115">Comment les problèmes de sécurité tels que le chiffrement au niveau du transport et la gestion des certificats sont-ils appliqués ?</span><span class="sxs-lookup"><span data-stu-id="965d4-115">How are security concerns such as transport-level encryption and certificate management enforced?</span></span>

- <span data-ttu-id="965d4-116">*Analyse distribuée.*</span><span class="sxs-lookup"><span data-stu-id="965d4-116">*Distributed Monitoring.*</span></span> <span data-ttu-id="965d4-117">-Comment mettre en corrélation et capturer la traçabilité et la surveillance d’une seule requête sur plusieurs microservices consommés ?</span><span class="sxs-lookup"><span data-stu-id="965d4-117">- How do you correlate and capture traceability and monitoring for a single request across multiple consuming microservices?</span></span>

<span data-ttu-id="965d4-118">Vous pouvez résoudre ces problèmes avec des bibliothèques et des infrastructures différentes, mais l’implémentation peut être coûteuse, complexe et fastidieuse.</span><span class="sxs-lookup"><span data-stu-id="965d4-118">You can address these concerns with different libraries and frameworks, but the implementation can be expensive, complex, and time-consuming.</span></span> <span data-ttu-id="965d4-119">Vous obtenez également des problèmes d’infrastructure associés à la logique métier.</span><span class="sxs-lookup"><span data-stu-id="965d4-119">You also end up with infrastructure concerns coupled to business logic.</span></span>

## <a name="service-mesh"></a><span data-ttu-id="965d4-120">Maille de service</span><span class="sxs-lookup"><span data-stu-id="965d4-120">Service mesh</span></span>

<span data-ttu-id="965d4-121">Une meilleure approche est une technologie en constante évolution intitulée *Mesh service*.</span><span class="sxs-lookup"><span data-stu-id="965d4-121">A better approach is an evolving technology entitled *Service Mesh*.</span></span> <span data-ttu-id="965d4-122">Une [maille de service](https://www.nginx.com/blog/what-is-a-service-mesh/) est une couche d’infrastructure configurable avec des fonctionnalités intégrées pour gérer la communication de service et les autres difficultés mentionnées ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="965d4-122">A [service mesh](https://www.nginx.com/blog/what-is-a-service-mesh/) is a configurable infrastructure layer with built-in capabilities to handle service communication and the other challenges mentioned above.</span></span> <span data-ttu-id="965d4-123">Il dissocie ces préoccupations en les déplaçant dans un proxy de service.</span><span class="sxs-lookup"><span data-stu-id="965d4-123">It decouples these concerns by moving them into a service proxy.</span></span> <span data-ttu-id="965d4-124">Le proxy est déployé dans un processus séparé (appelé [side-car](https://docs.microsoft.com/azure/architecture/patterns/sidecar)) pour assurer l’isolation à partir du code d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="965d4-124">The proxy is deployed into a separate process (called a [sidecar](https://docs.microsoft.com/azure/architecture/patterns/sidecar)) to provide isolation from business code.</span></span> <span data-ttu-id="965d4-125">Toutefois, le side-car est lié au service, il est créé avec lui et partage son cycle de vie.</span><span class="sxs-lookup"><span data-stu-id="965d4-125">However, the sidecar is linked to the service - it's created with it and shares its lifecycle.</span></span> <span data-ttu-id="965d4-126">La figure 6-7 illustre ce scénario.</span><span class="sxs-lookup"><span data-stu-id="965d4-126">Figure 6-7 shows this scenario.</span></span>

![Maille de service avec une voiture latérale](./media/service-mesh-with-side-car.png)

<span data-ttu-id="965d4-128">**Figure 6-7.**</span><span class="sxs-lookup"><span data-stu-id="965d4-128">**Figure 6-7**.</span></span> <span data-ttu-id="965d4-129">Maille de service avec une voiture latérale</span><span class="sxs-lookup"><span data-stu-id="965d4-129">Service mesh with a side car</span></span>

<span data-ttu-id="965d4-130">Dans la figure précédente, Notez comment le proxy intercepte et gère la communication entre les microservices et le cluster.</span><span class="sxs-lookup"><span data-stu-id="965d4-130">In the previous figure, note how the proxy intercepts and manages communication among the microservices and the cluster.</span></span>

<span data-ttu-id="965d4-131">Un maillage de service est logiquement divisé en deux composants disparates : un [plan de données](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc) et un [plan de contrôle](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc).</span><span class="sxs-lookup"><span data-stu-id="965d4-131">A service mesh is logically split into two disparate components: A [data plane](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc) and [control plane](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc).</span></span> <span data-ttu-id="965d4-132">La figure 6-8 montre ces composants et leurs responsabilités.</span><span class="sxs-lookup"><span data-stu-id="965d4-132">Figure 6-8 shows these components and their responsibilities.</span></span>

![Contrôle de maillage de service et plan de données](./media/istio-control-and-data-plane.png)

<span data-ttu-id="965d4-134">**Figure 6-8.**</span><span class="sxs-lookup"><span data-stu-id="965d4-134">**Figure 6-8.**</span></span> <span data-ttu-id="965d4-135">Contrôle de maillage de service et plan de données</span><span class="sxs-lookup"><span data-stu-id="965d4-135">Service mesh control and data plane</span></span>

<span data-ttu-id="965d4-136">Une fois configuré, un maillage de service est très fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="965d4-136">Once configured, a service mesh is highly functional.</span></span> <span data-ttu-id="965d4-137">Il peut récupérer un pool d’instances correspondant à partir d’un point de terminaison de découverte de service.</span><span class="sxs-lookup"><span data-stu-id="965d4-137">It can retrieve a corresponding pool of instances from a service discovery endpoint.</span></span> <span data-ttu-id="965d4-138">La maille peut ensuite envoyer une demande à une instance spécifique, en enregistrant la latence et le type de réponse du résultat.</span><span class="sxs-lookup"><span data-stu-id="965d4-138">The mesh can then send a request to a specific instance, recording the latency and response type of the result.</span></span> <span data-ttu-id="965d4-139">Une maille peut choisir l’instance la plus susceptible de retourner une réponse rapide en fonction de nombreux facteurs, y compris la latence observée pour les demandes récentes.</span><span class="sxs-lookup"><span data-stu-id="965d4-139">A mesh can choose the instance most likely to return a fast response based on many factors, including its observed latency for recent requests.</span></span>

<span data-ttu-id="965d4-140">Si une instance ne répond pas ou échoue, le maillage réessaie la demande sur une autre instance.</span><span class="sxs-lookup"><span data-stu-id="965d4-140">If an instance is unresponsive or fails, the mesh will retry the request on another instance.</span></span> <span data-ttu-id="965d4-141">Si elle retourne des erreurs, une maille supprime l’instance du pool d’équilibrage de charge et la renomme après sa réparation.</span><span class="sxs-lookup"><span data-stu-id="965d4-141">If it returns errors, a mesh will evict the instance from the load-balancing pool and restate it after it heals.</span></span> <span data-ttu-id="965d4-142">Si une demande expire, une maille peut échouer, puis retenter la demande.</span><span class="sxs-lookup"><span data-stu-id="965d4-142">If a request times out, a mesh can fail and then retry the request.</span></span> <span data-ttu-id="965d4-143">Une maille capture et émet des métriques et le traçage distribué vers un système de mesures centralisé.</span><span class="sxs-lookup"><span data-stu-id="965d4-143">A mesh captures and emits metrics and distributed tracing to a centralized metrics system.</span></span>

## <a name="istio-and-envoy"></a><span data-ttu-id="965d4-144">Istio et Envoy</span><span class="sxs-lookup"><span data-stu-id="965d4-144">Istio and Envoy</span></span>

<span data-ttu-id="965d4-145">Bien qu’il existe actuellement quelques options de maillage de service, [Istio](https://istio.io/docs/concepts/what-is-istio/) est le plus populaire au moment de la rédaction de cet article.</span><span class="sxs-lookup"><span data-stu-id="965d4-145">While a few service mesh options currently exist, [Istio](https://istio.io/docs/concepts/what-is-istio/) is the most popular at the time of this writing.</span></span> <span data-ttu-id="965d4-146">Istio est une entreprise conjointe d’IBM, Google et LYFT.</span><span class="sxs-lookup"><span data-stu-id="965d4-146">Istio is a joint venture from IBM, Google, and Lyft.</span></span> <span data-ttu-id="965d4-147">Il s’agit d’une offre Open source qui peut être intégrée dans une application distribuée nouvelle ou existante.</span><span class="sxs-lookup"><span data-stu-id="965d4-147">It's an open-source offering that can be integrated into a new or existing distributed application.</span></span> <span data-ttu-id="965d4-148">La technologie offre une solution cohérente et complète pour sécuriser, connecter et surveiller les microservices.</span><span class="sxs-lookup"><span data-stu-id="965d4-148">The technology provides a consistent and complete solution to secure, connect, and monitor microservices.</span></span> <span data-ttu-id="965d4-149">Ses fonctionnalités sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="965d4-149">Its features include:</span></span>

- <span data-ttu-id="965d4-150">Sécuriser les communications de service à service dans un cluster avec une authentification et une autorisation puissantes basées sur l’identité.</span><span class="sxs-lookup"><span data-stu-id="965d4-150">Secure service-to-service communication in a cluster with strong identity-based authentication and authorization.</span></span>
- <span data-ttu-id="965d4-151">Équilibrage de charge automatique pour le trafic HTTP, [gRPC](https://grpc.io/), WebSocket et TCP.</span><span class="sxs-lookup"><span data-stu-id="965d4-151">Automatic load balancing for HTTP, [gRPC](https://grpc.io/), WebSocket, and TCP traffic.</span></span>
- <span data-ttu-id="965d4-152">Contrôle affiné du comportement du trafic avec des règles de routage riches, des nouvelles tentatives, des basculements et une injection d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="965d4-152">Fine-grained control of traffic behavior with rich routing rules, retries, failovers, and fault injection.</span></span>
- <span data-ttu-id="965d4-153">Une couche de stratégie enfichable et une API de configuration prennent en charge les contrôles d’accès, les limites de taux et les quotas.</span><span class="sxs-lookup"><span data-stu-id="965d4-153">A pluggable policy layer and configuration API supporting access controls, rate limits, and quotas.</span></span>
- <span data-ttu-id="965d4-154">Mesures automatiques, journaux et traces pour tout le trafic au sein d’un cluster, y compris l’entrée et la sortie du cluster.</span><span class="sxs-lookup"><span data-stu-id="965d4-154">Automatic metrics, logs, and traces for all traffic within a cluster, including cluster ingress and egress.</span></span>

<span data-ttu-id="965d4-155">Un composant clé pour une implémentation de Istio est un service proxy ayant le [proxy Envoy](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy).</span><span class="sxs-lookup"><span data-stu-id="965d4-155">A key component for an Istio implementation is a proxy service entitled the [Envoy proxy](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy).</span></span> <span data-ttu-id="965d4-156">Il s’exécute à côté de chaque service et fournit une base de plateforme agnostique pour les fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="965d4-156">It runs alongside each service and provides a platform-agnostic foundation for the following features:</span></span>

- <span data-ttu-id="965d4-157">Découverte de service dynamique.</span><span class="sxs-lookup"><span data-stu-id="965d4-157">Dynamic service discovery.</span></span>
- <span data-ttu-id="965d4-158">Équilibrage de charge :</span><span class="sxs-lookup"><span data-stu-id="965d4-158">Load balancing.</span></span>
- <span data-ttu-id="965d4-159">Arrêt TLS.</span><span class="sxs-lookup"><span data-stu-id="965d4-159">TLS termination.</span></span>
- <span data-ttu-id="965d4-160">Proxys HTTP et gRPC.</span><span class="sxs-lookup"><span data-stu-id="965d4-160">HTTP and gRPC proxies.</span></span>
- <span data-ttu-id="965d4-161">Résilience de disjoncteur.</span><span class="sxs-lookup"><span data-stu-id="965d4-161">Circuit breaker resiliency.</span></span>
- <span data-ttu-id="965d4-162">Contrôles d’intégrité.</span><span class="sxs-lookup"><span data-stu-id="965d4-162">Health checks.</span></span>
- <span data-ttu-id="965d4-163">Mises à jour propagées avec des déploiements de [Canaries](https://martinfowler.com/bliki/CanaryRelease.html) .</span><span class="sxs-lookup"><span data-stu-id="965d4-163">Rolling updates with [canary](https://martinfowler.com/bliki/CanaryRelease.html) deployments.</span></span>

<span data-ttu-id="965d4-164">Comme indiqué précédemment, Envoy est déployé en tant que side-car pour chaque microservice du cluster.</span><span class="sxs-lookup"><span data-stu-id="965d4-164">As previously discussed, Envoy is deployed as a sidecar to each microservice in the cluster.</span></span>

## <a name="integration-with-azure-kubernetes-services"></a><span data-ttu-id="965d4-165">Intégration avec les services Azure Kubernetes</span><span class="sxs-lookup"><span data-stu-id="965d4-165">Integration with Azure Kubernetes Services</span></span>

<span data-ttu-id="965d4-166">Le Cloud Azure prend en charge Istio et fournit un support direct pour celui-ci dans les services Azure Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="965d4-166">The Azure cloud embraces Istio and provides direct support for it within Azure Kubernetes Services.</span></span> <span data-ttu-id="965d4-167">Les liens suivants peuvent vous aider à vous lancer :</span><span class="sxs-lookup"><span data-stu-id="965d4-167">The following links can help you get started:</span></span>

- [<span data-ttu-id="965d4-168">Installation de Istio dans AKS</span><span class="sxs-lookup"><span data-stu-id="965d4-168">Installing Istio in AKS</span></span>](https://docs.microsoft.com/azure/aks/istio-install)
- [<span data-ttu-id="965d4-169">Utilisation de AKS et Istio</span><span class="sxs-lookup"><span data-stu-id="965d4-169">Using AKS and Istio</span></span>](https://docs.microsoft.com/azure/aks/istio-scenario-routing)

### <a name="references"></a><span data-ttu-id="965d4-170">References</span><span class="sxs-lookup"><span data-stu-id="965d4-170">References</span></span>

- [<span data-ttu-id="965d4-171">Polly</span><span class="sxs-lookup"><span data-stu-id="965d4-171">Polly</span></span>](http://www.thepollyproject.org/)

- [<span data-ttu-id="965d4-172">Modèle Nouvelle tentative</span><span class="sxs-lookup"><span data-stu-id="965d4-172">Retry pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/retry)

- [<span data-ttu-id="965d4-173">Modèle disjoncteur</span><span class="sxs-lookup"><span data-stu-id="965d4-173">Circuit Breaker pattern</span></span>](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)

- [<span data-ttu-id="965d4-174">Livre blanc sur la résilience dans Azure</span><span class="sxs-lookup"><span data-stu-id="965d4-174">Resilience in Azure whitepaper</span></span>](https://azure.microsoft.com/mediahandler/files/resourcefiles/resilience-in-azure-whitepaper/Resilience%20in%20Azure.pdf)

- [<span data-ttu-id="965d4-175">latence du réseau</span><span class="sxs-lookup"><span data-stu-id="965d4-175">network latency</span></span>](https://www.techopedia.com/definition/8553/network-latency)

- [<span data-ttu-id="965d4-176">Redondance</span><span class="sxs-lookup"><span data-stu-id="965d4-176">Redundancy</span></span>](https://docs.microsoft.com/azure/architecture/guide/design-principles/redundancy)

- [<span data-ttu-id="965d4-177">géo-réplication</span><span class="sxs-lookup"><span data-stu-id="965d4-177">geo-replication</span></span>](https://docs.microsoft.com/azure/sql-database/sql-database-active-geo-replication)

- [<span data-ttu-id="965d4-178">Azure Traffic Manager</span><span class="sxs-lookup"><span data-stu-id="965d4-178">Azure Traffic Manager</span></span>](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)

- [<span data-ttu-id="965d4-179">Recommandations en matière de mise à l’échelle automatique</span><span class="sxs-lookup"><span data-stu-id="965d4-179">Autoscaling guidance</span></span>](https://docs.microsoft.com/azure/architecture/best-practices/auto-scaling)

- [<span data-ttu-id="965d4-180">Istio</span><span class="sxs-lookup"><span data-stu-id="965d4-180">Istio</span></span>](https://istio.io/docs/concepts/what-is-istio/)

- [<span data-ttu-id="965d4-181">Proxy d’envoi</span><span class="sxs-lookup"><span data-stu-id="965d4-181">Envoy proxy</span></span>](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy)

>[!div class="step-by-step"]
><span data-ttu-id="965d4-182">[Précédent](infrastructure-resiliency-azure.md) 
> [Suivant](monitoring-health.md)</span><span class="sxs-lookup"><span data-stu-id="965d4-182">[Previous](infrastructure-resiliency-azure.md)
[Next](monitoring-health.md)</span></span>

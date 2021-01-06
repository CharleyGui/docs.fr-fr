---
title: Équilibrage de charge gRPC-gRPC pour les développeurs WCF
description: Choix d’un équilibreur de charge pour fonctionner avec les services gRPC.
ms.date: 12/15/2020
ms.openlocfilehash: 55f61608dce1f159b11d7265a47938ba49e9e188
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938583"
---
# <a name="load-balancing-grpc"></a><span data-ttu-id="d9ffd-103">Équilibrage de charge gRPC</span><span class="sxs-lookup"><span data-stu-id="d9ffd-103">Load balancing gRPC</span></span>

<span data-ttu-id="d9ffd-104">Un déploiement classique d’une application gRPC comprend un certain nombre d’instances identiques du service, offrant ainsi une résilience et une évolutivité horizontale.</span><span class="sxs-lookup"><span data-stu-id="d9ffd-104">A typical deployment of a gRPC application includes a number of identical instances of the service, providing resilience and horizontal scalability.</span></span> <span data-ttu-id="d9ffd-105">L’équilibrage de charge distribue les demandes entrantes sur ces instances pour fournir une utilisation complète de toutes les ressources disponibles.</span><span class="sxs-lookup"><span data-stu-id="d9ffd-105">Load balancing distributes incoming requests across these instances to provide full usage of all available resources.</span></span> <span data-ttu-id="d9ffd-106">Pour rendre cet équilibrage de charge invisible au client, il est courant d’utiliser un serveur d’équilibrage de charge de proxy pour gérer les demandes des clients et les acheminer vers les instances de serveur principal.</span><span class="sxs-lookup"><span data-stu-id="d9ffd-106">To make this load balancing invisible to the client, it's common to use a proxy load balancer server to handle requests from clients and route them to back-end instances.</span></span>

<span data-ttu-id="d9ffd-107">Les équilibrages de charge sont classés en fonction de la *couche* sur laquelle ils opèrent.</span><span class="sxs-lookup"><span data-stu-id="d9ffd-107">Load balancers are classified according to the *layer* they operate on.</span></span> <span data-ttu-id="d9ffd-108">Les équilibreurs de charge de couche 4 fonctionnent au niveau du *transport* , par exemple avec les sockets, les connexions et les paquets TCP.</span><span class="sxs-lookup"><span data-stu-id="d9ffd-108">Layer 4 load balancers work on the *transport* level, for example, with TCP sockets, connections, and packets.</span></span> <span data-ttu-id="d9ffd-109">Les équilibreurs de charge de couche 7 fonctionnent au niveau de l' *application* , en gérant spécifiquement les demandes http/2 pour les applications gRPC.</span><span class="sxs-lookup"><span data-stu-id="d9ffd-109">Layer 7 load balancers work at the *application* level, specifically handling HTTP/2 requests for gRPC applications.</span></span>

## <a name="l4-load-balancers"></a><span data-ttu-id="d9ffd-110">Équilibreurs de charge L4</span><span class="sxs-lookup"><span data-stu-id="d9ffd-110">L4 load balancers</span></span>

<span data-ttu-id="d9ffd-111">Un équilibreur de charge L4 accepte une demande de connexion TCP à partir d’un client, ouvre une autre connexion à l’une des instances de serveur principal, et copie les données entre les deux connexions sans traitement réel.</span><span class="sxs-lookup"><span data-stu-id="d9ffd-111">An L4 load balancer accepts a TCP connection request from a client, opens another connection to one of the back-end instances, and copies data between the two connections with no real processing.</span></span> <span data-ttu-id="d9ffd-112">L4 offre d’excellentes performances et une faible latence, mais avec peu de contrôle ou d’intelligence.</span><span class="sxs-lookup"><span data-stu-id="d9ffd-112">L4 offers excellent performance and low latency, but with little control or intelligence.</span></span> <span data-ttu-id="d9ffd-113">Tant que le client maintient la connexion ouverte, toutes les demandes sont dirigées vers la même instance de serveur principal.</span><span class="sxs-lookup"><span data-stu-id="d9ffd-113">As long as the client keeps the connection open, all requests will be directed to the same back-end instance.</span></span>

 <span data-ttu-id="d9ffd-114">[Azure load balancer](https://azure.microsoft.com/services/load-balancer/) est un exemple d’équilibrage de charge n4.</span><span class="sxs-lookup"><span data-stu-id="d9ffd-114">[Azure Load Balancer](https://azure.microsoft.com/services/load-balancer/) is an example of an L4 load balancer.</span></span>

## <a name="l7-load-balancers"></a><span data-ttu-id="d9ffd-115">Équilibreurs de charge L7</span><span class="sxs-lookup"><span data-stu-id="d9ffd-115">L7 load balancers</span></span>

<span data-ttu-id="d9ffd-116">Un équilibreur de charge L7 analyse les demandes HTTP/2 entrantes et les transmet aux instances du serveur principal à la demande, quelle que soit la durée pendant laquelle la connexion est maintenue par le client.</span><span class="sxs-lookup"><span data-stu-id="d9ffd-116">An L7 load balancer parses incoming HTTP/2 requests and passes them on to back-end instances on a request-by-request basis, no matter how long the connection is held by the client.</span></span>

<span data-ttu-id="d9ffd-117">Exemples d’équilibreurs de charge L7 :</span><span class="sxs-lookup"><span data-stu-id="d9ffd-117">Examples of L7 load balancers:</span></span>

- [<span data-ttu-id="d9ffd-118">NGINX</span><span class="sxs-lookup"><span data-stu-id="d9ffd-118">NGINX</span></span>](https://www.nginx.com/)
- [<span data-ttu-id="d9ffd-119">HAProxy</span><span class="sxs-lookup"><span data-stu-id="d9ffd-119">HAProxy</span></span>](https://www.haproxy.com/)
- [<span data-ttu-id="d9ffd-120">Traefik</span><span class="sxs-lookup"><span data-stu-id="d9ffd-120">Traefik</span></span>](https://traefik.io/)

<span data-ttu-id="d9ffd-121">En règle générale, les équilibreurs de charge L7 sont le meilleur choix pour gRPC et d’autres applications HTTP/2 (et, en fait, pour les applications HTTP).</span><span class="sxs-lookup"><span data-stu-id="d9ffd-121">As a rule of thumb, L7 load balancers are the best choice for gRPC and other HTTP/2 applications (and for HTTP applications generally, in fact).</span></span> <span data-ttu-id="d9ffd-122">Les équilibreurs de charge L4 *fonctionnent* avec les applications gRPC, mais ils sont principalement utiles lorsque la faible latence et la faible surcharge sont importantes.</span><span class="sxs-lookup"><span data-stu-id="d9ffd-122">L4 load balancers will *work* with gRPC applications, but they're primarily useful when low latency and low overhead are important.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d9ffd-123">Au moment de la rédaction de cet article, certains équilibrages de charge L7 ne prennent pas en charge toutes les parties de la spécification HTTP/2 requises par les services gRPC, tels que les en-têtes de fin.</span><span class="sxs-lookup"><span data-stu-id="d9ffd-123">At the time of this writing, some L7 load balancers don't support all the parts of the HTTP/2 specification that are required by gRPC services, such as trailing headers.</span></span>

<span data-ttu-id="d9ffd-124">Si vous utilisez le chiffrement TLS, les équilibrages de charge peuvent mettre fin à la connexion TLS et transmettre des demandes non chiffrées à l’application principale, ou elles peuvent transmettre la requête chiffrée.</span><span class="sxs-lookup"><span data-stu-id="d9ffd-124">If you're using TLS encryption, load balancers can terminate the TLS connection and pass unencrypted requests to the back-end application, or they can pass the encrypted request along.</span></span> <span data-ttu-id="d9ffd-125">Dans les deux cas, l’équilibreur de charge doit être configuré avec la clé publique et la clé privée du serveur afin de pouvoir déchiffrer les demandes de traitement.</span><span class="sxs-lookup"><span data-stu-id="d9ffd-125">Either way, the load balancer will need to be configured with the server's public and private key so it can decrypt requests for processing.</span></span>

<span data-ttu-id="d9ffd-126">Consultez la documentation de votre équilibreur de charge préféré pour savoir comment le configurer pour gérer les demandes HTTP/2 avec vos services principaux.</span><span class="sxs-lookup"><span data-stu-id="d9ffd-126">See to the documentation for your preferred load balancer to find out how to configure it to handle HTTP/2 requests with your back-end services.</span></span>

## <a name="load-balancing-within-kubernetes"></a><span data-ttu-id="d9ffd-127">Équilibrage de charge dans Kubernetes</span><span class="sxs-lookup"><span data-stu-id="d9ffd-127">Load balancing within Kubernetes</span></span>

<span data-ttu-id="d9ffd-128">Consultez [la section sur les maillages de service](service-mesh.md) pour une discussion sur l’équilibrage de charge entre les services internes sur Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="d9ffd-128">See [the section on service meshes](service-mesh.md) for a discussion of load balancing across internal services on Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d9ffd-129">[Précédent](service-mesh.md) 
> [Suivant](application-performance-management.md)</span><span class="sxs-lookup"><span data-stu-id="d9ffd-129">[Previous](service-mesh.md)
[Next](application-performance-management.md)</span></span>

---
title: Protocoles réseau-gRPC pour les développeurs WCF
description: Vue d’ensemble des protocoles réseau gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: a176d3e84f5f454f746273c9cc7e7afe7c7f9d8a
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184287"
---
# <a name="network-protocols"></a><span data-ttu-id="ee0f2-103">Protocoles réseau</span><span class="sxs-lookup"><span data-stu-id="ee0f2-103">Network protocols</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="ee0f2-104">Contrairement à WCF, gRPC utilise HTTP/2 comme base pour sa mise en réseau.</span><span class="sxs-lookup"><span data-stu-id="ee0f2-104">Unlike WCF, gRPC uses HTTP/2 as a base for its networking.</span></span> <span data-ttu-id="ee0f2-105">Cela offre des avantages significatifs par rapport à WCF et SOAP, qui fonctionnent uniquement sur HTTP/1.1.</span><span class="sxs-lookup"><span data-stu-id="ee0f2-105">This offers significant advantages over WCF and SOAP, which only operate on HTTP/1.1.</span></span> <span data-ttu-id="ee0f2-106">Pour les développeurs souhaitant utiliser gRPC, étant donné qu’il n’y a pas d’alternative à HTTP/2, il semblerait être le moment idéal pour explorer HTTP/2 plus en détail et pour identifier les avantages supplémentaires de l’utilisation de gRPC.</span><span class="sxs-lookup"><span data-stu-id="ee0f2-106">For developers wanting to use gRPC, given that there's no alternative to HTTP/2, it would seem to be the ideal moment to explore HTTP/2 in more detail and identify additional benefits to using gRPC.</span></span>

<span data-ttu-id="ee0f2-107">HTTP/2, publié par l’IETF (Internet Engineering Task Force) dans 2015, était dérivé du protocole expérimental SPDY, qui était déjà utilisé par Google.</span><span class="sxs-lookup"><span data-stu-id="ee0f2-107">HTTP/2, released by Internet Engineering Task Force in 2015, was derived from the experimental SPDY protocol, which was already being used by Google.</span></span> <span data-ttu-id="ee0f2-108">Il a été spécialement conçu pour être plus efficace, plus rapide et plus sûr que HTTP/1.1.</span><span class="sxs-lookup"><span data-stu-id="ee0f2-108">It was specifically designed to be more efficient, faster, and more secure than HTTP/1.1.</span></span>

## <a name="key-features-of-http2"></a><span data-ttu-id="ee0f2-109">Fonctionnalités clés du protocole HTTP/2</span><span class="sxs-lookup"><span data-stu-id="ee0f2-109">Key features of HTTP/2</span></span>

<span data-ttu-id="ee0f2-110">La liste suivante présente quelques-unes des fonctionnalités clés et des avantages du protocole HTTP/2 :</span><span class="sxs-lookup"><span data-stu-id="ee0f2-110">The following list shows some of the key features and advantages of HTTP/2:</span></span>

### <a name="binary-protocol"></a><span data-ttu-id="ee0f2-111">Protocole binaire</span><span class="sxs-lookup"><span data-stu-id="ee0f2-111">Binary protocol</span></span>

<span data-ttu-id="ee0f2-112">Les cycles de demande/réponse n’ont plus besoin de commandes de texte.</span><span class="sxs-lookup"><span data-stu-id="ee0f2-112">Request/response cycles no longer need text commands.</span></span> <span data-ttu-id="ee0f2-113">Cela simplifie et accélère l’implémentation des commandes.</span><span class="sxs-lookup"><span data-stu-id="ee0f2-113">This simplifies and speeds up implementation of commands.</span></span> <span data-ttu-id="ee0f2-114">Plus précisément, l’analyse des données est plus rapide et utilise moins de mémoire, la latence du réseau est réduite avec des améliorations significatives en termes de vitesse et une meilleure utilisation globale des ressources réseau.</span><span class="sxs-lookup"><span data-stu-id="ee0f2-114">Specifically, parsing data is faster and uses less memory, network latency is reduced with obvious related improvements to speed, and there's an overall better use of network resources.</span></span>

### <a name="streams"></a><span data-ttu-id="ee0f2-115">Flux</span><span class="sxs-lookup"><span data-stu-id="ee0f2-115">Streams</span></span>

<span data-ttu-id="ee0f2-116">Les flux permettent de créer des connexions à long terme entre l’expéditeur et le récepteur, sur lesquels plusieurs messages ou frames peuvent être envoyés de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="ee0f2-116">Streams allow for the creation of long-lived connections between sender and receiver, over which multiple messages or frames can be sent asynchronously.</span></span> <span data-ttu-id="ee0f2-117">Plusieurs flux peuvent fonctionner indépendamment sur une seule connexion HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="ee0f2-117">Multiple streams can operate independently over a single HTTP/2 connection.</span></span>

### <a name="request-multiplexing-over-a-single-tcp-connection"></a><span data-ttu-id="ee0f2-118">Demander le multiplexage sur une seule connexion TCP</span><span class="sxs-lookup"><span data-stu-id="ee0f2-118">Request multiplexing over a single TCP connection</span></span>

<span data-ttu-id="ee0f2-119">Cette fonctionnalité est l’une des innovations les plus importantes de HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="ee0f2-119">This feature is one of the most important innovations of HTTP/2.</span></span> <span data-ttu-id="ee0f2-120">En autorisant plusieurs demandes parallèles de données, il est désormais possible de télécharger des fichiers Web simultanément à partir d’un seul serveur.</span><span class="sxs-lookup"><span data-stu-id="ee0f2-120">By allowing multiple parallel requests for data, it's now possible to download web files concurrently from a single server.</span></span> <span data-ttu-id="ee0f2-121">Les sites Web se chargent plus rapidement et le besoin d’optimisation est réduit.</span><span class="sxs-lookup"><span data-stu-id="ee0f2-121">Websites load faster and the need for optimization is reduced.</span></span> <span data-ttu-id="ee0f2-122">Blocage de la tête de ligne (HOL), où les réponses qui sont prêtes doivent attendre d’être envoyées jusqu’à ce qu’une requête antérieure soit terminée, est également atténuée (bien que le blocage de HOL puisse encore se produire au niveau du transport TCP).</span><span class="sxs-lookup"><span data-stu-id="ee0f2-122">Head-of-line (HOL) blocking, where responses that are ready must wait to be sent until an earlier request is completed, is also mitigated (although HOL blocking can still occur at the TCP transport level).</span></span>

### <a name="nettcp-like-performance-cross-platform"></a><span data-ttu-id="ee0f2-123">Performances NetTCP, multiplateforme</span><span class="sxs-lookup"><span data-stu-id="ee0f2-123">NetTCP-like performance, cross-platform</span></span>

<span data-ttu-id="ee0f2-124">Fondamentalement, la combinaison de gRPC et HTTP/2 offre aux développeurs au moins la vitesse et l’efficacité équivalentes des liaisons NetTCP pour WCF, et dans certains cas encore plus rapides et plus efficaces.</span><span class="sxs-lookup"><span data-stu-id="ee0f2-124">Fundamentally, the combination of gRPC and HTTP/2 offer developers at least the equivalent speed and efficiency of NetTCP bindings for WCF, and in some cases even greater speed and efficiency.</span></span> <span data-ttu-id="ee0f2-125">Toutefois, contrairement à NetTCP, gRPC sur HTTP/2 n’est pas restreinte aux applications .NET.</span><span class="sxs-lookup"><span data-stu-id="ee0f2-125">However, unlike NetTCP, gRPC over HTTP/2 isn't constrained to .NET applications.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ee0f2-126">[Précédent](interface-definition-language.md)
>[Suivant](why-grpc.md)</span><span class="sxs-lookup"><span data-stu-id="ee0f2-126">[Previous](interface-definition-language.md)
[Next](why-grpc.md)</span></span>

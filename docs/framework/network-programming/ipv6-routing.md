---
title: Routage IPv6
ms.date: 03/30/2017
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
ms.openlocfilehash: 93300107710164d755d578633b7fa6651f984987
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047785"
---
# <a name="ipv6-routing"></a><span data-ttu-id="3cd7b-102">Routage IPv6</span><span class="sxs-lookup"><span data-stu-id="3cd7b-102">IPv6 Routing</span></span>
<span data-ttu-id="3cd7b-103">Le protocole IPv6 comprend un mécanisme de routage souple.</span><span class="sxs-lookup"><span data-stu-id="3cd7b-103">A flexible routing mechanism is a benefit of IPv6.</span></span> <span data-ttu-id="3cd7b-104">En raison de la façon dont les ID réseau IPv4 sont alloués, les tables de routage volumineuses doivent être gérées par les routeurs Internet principaux.</span><span class="sxs-lookup"><span data-stu-id="3cd7b-104">Due to the way in which IPv4 network IDs were and are allocated, large routing tables need to be maintained by the routers that are on the Internet backbones.</span></span> <span data-ttu-id="3cd7b-105">Ces routeurs doivent connaître tous les itinéraires afin de transmettre les paquets qui sont susceptibles d’être dirigés vers des nœuds Internet.</span><span class="sxs-lookup"><span data-stu-id="3cd7b-105">These routers must know all the routes in order to forward packets that are potentially directed to any node on the Internet.</span></span> <span data-ttu-id="3cd7b-106">Grâce à sa capacité de regrouper des adresses, IPv6 permet un adressage souple et réduit considérablement la taille des tables de routage.</span><span class="sxs-lookup"><span data-stu-id="3cd7b-106">With its ability to aggregate addresses, IPv6 allows flexible addressing and drastically reduces the size of routing tables.</span></span> <span data-ttu-id="3cd7b-107">Dans cette nouvelle architecture d’adressage, les routeurs intermédiaires doivent uniquement effectuer le suivi de la partie locale de leur réseau afin de transmettre les messages de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="3cd7b-107">In this new addressing architecture, intermediate routers must keep track only of the local portion of their network in order to forward the messages appropriately.</span></span>  
  
## <a name="neighbor-discovery"></a><span data-ttu-id="3cd7b-108">Découverte de voisin</span><span class="sxs-lookup"><span data-stu-id="3cd7b-108">Neighbor Discovery</span></span>  
 <span data-ttu-id="3cd7b-109">Voici certaines des fonctionnalités fournies par la découverte de voisin :</span><span class="sxs-lookup"><span data-stu-id="3cd7b-109">Some of the features provided by Neighbor Discovery are:</span></span>  
  
- <span data-ttu-id="3cd7b-110">La découverte de routeurs.</span><span class="sxs-lookup"><span data-stu-id="3cd7b-110">Router discovery.</span></span> <span data-ttu-id="3cd7b-111">Elle permet aux hôtes d’identifier les routeurs locaux.</span><span class="sxs-lookup"><span data-stu-id="3cd7b-111">This allows hosts to identify local routers.</span></span>  
  
- <span data-ttu-id="3cd7b-112">La résolution d’adresse.</span><span class="sxs-lookup"><span data-stu-id="3cd7b-112">Address resolution.</span></span> <span data-ttu-id="3cd7b-113">Elle permet aux nœuds de résoudre une adresse link-layer pour l’adresse correspondante du tronçon suivant (en remplacement du protocole ARP).</span><span class="sxs-lookup"><span data-stu-id="3cd7b-113">This allows nodes to resolve a link-layer address for a corresponding next-hop address (a replacement for Address Resolution Protocol [ARP]).</span></span>  
  
- <span data-ttu-id="3cd7b-114">La configuration automatique des adresses.</span><span class="sxs-lookup"><span data-stu-id="3cd7b-114">Address auto-configuration.</span></span> <span data-ttu-id="3cd7b-115">Elle permet aux hôtes de configurer automatiquement les adresses locales et globales.</span><span class="sxs-lookup"><span data-stu-id="3cd7b-115">This allows hosts to automatically configure site-local and global addresses.</span></span>  
  
 <span data-ttu-id="3cd7b-116">La découverte de voisin utilise le protocole IPv6 (ICMPv6) pour les types de messages suivants :</span><span class="sxs-lookup"><span data-stu-id="3cd7b-116">Neighbor Discovery uses Internet Control Message Protocol for IPv6 (ICMPv6) messages that include:</span></span>  
  
- <span data-ttu-id="3cd7b-117">Annonces de routeur.</span><span class="sxs-lookup"><span data-stu-id="3cd7b-117">Router advertisement.</span></span> <span data-ttu-id="3cd7b-118">Envoyées par un routeur à intervalles réguliers ou en réponse à une sollicitation de routeur.</span><span class="sxs-lookup"><span data-stu-id="3cd7b-118">Sent by a router on a pseudo-periodic basis or in response to a router solicitation.</span></span> <span data-ttu-id="3cd7b-119">Les routeurs IPv6 utilisent des annonces de routeur pour annoncer leur disponibilité, leurs préfixes d’adresse et autres paramètres.</span><span class="sxs-lookup"><span data-stu-id="3cd7b-119">IPv6 routers use router advertisements to advertise their availability, address prefixes, and other parameters.</span></span>  
  
- <span data-ttu-id="3cd7b-120">Sollicitations de routeur.</span><span class="sxs-lookup"><span data-stu-id="3cd7b-120">Router solicitation.</span></span> <span data-ttu-id="3cd7b-121">Envoyées par un hôte pour demander que les routeurs présents sur la liaison envoient immédiatement une annonce de routeur.</span><span class="sxs-lookup"><span data-stu-id="3cd7b-121">Sent by a host to request that routers on the link send a router advertisement immediately.</span></span>  
  
- <span data-ttu-id="3cd7b-122">Sollicitations de voisin.</span><span class="sxs-lookup"><span data-stu-id="3cd7b-122">Neighbor solicitation.</span></span> <span data-ttu-id="3cd7b-123">Envoyées par les nœuds pour la résolution d’adresse, la détection d’adresses en double et la vérification de disponibilité d’un voisin.</span><span class="sxs-lookup"><span data-stu-id="3cd7b-123">Sent by nodes for address resolution, duplicate address detection, or to verify that a neighbor is still reachable.</span></span>  
  
- <span data-ttu-id="3cd7b-124">Annonces de voisin.</span><span class="sxs-lookup"><span data-stu-id="3cd7b-124">Neighbor advertisement.</span></span> <span data-ttu-id="3cd7b-125">Envoyées par les nœuds pour répondre à une sollicitation de voisin ou pour avertir les voisins d’un changement d’adresse link-layer.</span><span class="sxs-lookup"><span data-stu-id="3cd7b-125">Sent by nodes to respond to a neighbor solicitation or to notify neighbors of a change in link-layer address.</span></span>  
  
- <span data-ttu-id="3cd7b-126">Redirections.</span><span class="sxs-lookup"><span data-stu-id="3cd7b-126">Redirect.</span></span> <span data-ttu-id="3cd7b-127">Envoyées par les routeurs pour indiquer une meilleure adresse de tronçon suivant à une destination particulière pour un nœud expéditeur.</span><span class="sxs-lookup"><span data-stu-id="3cd7b-127">Sent by routers to indicate a better next-hop address to a particular destination for a sending node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cd7b-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3cd7b-128">See also</span></span>

- [<span data-ttu-id="3cd7b-129">Version 6 du protocole Internet</span><span class="sxs-lookup"><span data-stu-id="3cd7b-129">Internet Protocol Version 6</span></span>](internet-protocol-version-6.md)
- [<span data-ttu-id="3cd7b-130">Sockets</span><span class="sxs-lookup"><span data-stu-id="3cd7b-130">Sockets</span></span>](sockets.md)

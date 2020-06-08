---
title: Protocole PNRP (Peer Name Resolution Protocol)
description: En savoir plus sur le protocole PNRP (Peer Name Resolution Protocol), un protocole de résolution de noms et d’inscription de noms sécurisé, évolutif et dynamique.
ms.date: 03/30/2017
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
ms.openlocfilehash: 72eb63c2c90f398c515d77cd2b2d693237e533a5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502221"
---
# <a name="peer-name-resolution-protocol"></a><span data-ttu-id="caaa8-103">Protocole PNRP (Peer Name Resolution Protocol)</span><span class="sxs-lookup"><span data-stu-id="caaa8-103">Peer Name Resolution Protocol</span></span>
<span data-ttu-id="caaa8-104">Dans les environnements pair à pair, les pairs utilisent des systèmes de résolution de noms spécifiques pour résoudre les emplacements réseau les uns des autres (adresses, protocoles et ports) à partir de noms et d’autres types d’identificateurs.</span><span class="sxs-lookup"><span data-stu-id="caaa8-104">In peer-to-peer environments, peers use specific name resolution systems to resolve each other's network locations (addresses, protocols, and ports) from names or other types of identifiers.</span></span> <span data-ttu-id="caaa8-105">Dans le passé, la résolution des noms de pairs était compliquée en raison de la nature transitoire de la connectivité, et d’autres défauts du système DNS.</span><span class="sxs-lookup"><span data-stu-id="caaa8-105">In the past, peer name resolution has been complicated by the inherently transient connectivity as well as other shortcomings within the Domain Name System (DNS).</span></span>  
  
 <span data-ttu-id="caaa8-106">La plateforme de réseau pair à pair de Microsoft® Windows® a résolu ce problème grâce au protocole PNRP, à une inscription de noms sécurisée, évolutive et dynamique, ainsi qu’au protocole de résolution de noms développé à l’origine pour Windows XP, puis amélioré pour Windows Vista™.</span><span class="sxs-lookup"><span data-stu-id="caaa8-106">The Microsoft® Windows® Peer-to-Peer Networking platform solves this problem with the Peer Name Resolution Protocol (PNRP), a secure, scalable, and dynamic name registration and name resolution protocol first developed for Windows XP and then upgraded in Windows Vista™.</span></span> <span data-ttu-id="caaa8-107">Le protocole PNRP fonctionne très différemment des systèmes traditionnels de résolution de noms, et offre de nouvelles possibilités aux développeurs d’applications.</span><span class="sxs-lookup"><span data-stu-id="caaa8-107">PNRP works very differently from traditional name resolution systems, opening up exciting new possibilities for application developers.</span></span>  
  
 <span data-ttu-id="caaa8-108">Avec le protocole PNRP, les noms de pairs peuvent être appliqués à l’ordinateur, ou à certaines applications ou certains services de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="caaa8-108">With PNRP, peer names can be applied to the machine, or individual applications or services on the machine.</span></span> <span data-ttu-id="caaa8-109">Une résolution de noms de pairs comprend une adresse, un port et éventuellement une charge utile étendue.</span><span class="sxs-lookup"><span data-stu-id="caaa8-109">A peer name resolution includes an address, port, and possibly an extended payload.</span></span> <span data-ttu-id="caaa8-110">Les avantages de ce système sont la tolérance de panne, l’absence de goulots d’étranglement et le fait que les résolutions de noms ne retournent jamais d’adresses périmées. Ce protocole constitue donc une excellente solution pour la localisation des utilisateurs mobiles.</span><span class="sxs-lookup"><span data-stu-id="caaa8-110">Benefits of this system include fault tolerance, no bottlenecks, and name resolutions that will never return stale addresses; making the protocol an excellent solution for locating mobile users.</span></span>  
  
 <span data-ttu-id="caaa8-111">En ce qui concerne la sécurité, les noms de pairs peuvent être publiés comme des noms sécurisés (protégés) ou non sécurisés (non protégés).</span><span class="sxs-lookup"><span data-stu-id="caaa8-111">In terms of security, peer names can be published as secured (protected) or unsecured (unprotected).</span></span> <span data-ttu-id="caaa8-112">Le protocole PNRP utilise le chiffrement à clé publique pour protéger les noms de pairs sécurisés contre l’usurpation d’identité. Les ordinateurs et les services peuvent être nommés à l’aide du protocole PNRP.</span><span class="sxs-lookup"><span data-stu-id="caaa8-112">PNRP uses public key cryptography to protect secure peer names against spoofing; both computers and services can be named with PNRP.</span></span>  
  
<span data-ttu-id="caaa8-113">Les particularités du protocole PNRP sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="caaa8-113">The Peer Name Resolution Protocol demonstrates the following properties:</span></span>  
  
- <span data-ttu-id="caaa8-114">Il est distribué et presque entièrement sans serveur.</span><span class="sxs-lookup"><span data-stu-id="caaa8-114">Distributed and almost entirely serverless.</span></span> <span data-ttu-id="caaa8-115">Les serveurs sont uniquement nécessaires pour le processus d’amorçage.</span><span class="sxs-lookup"><span data-stu-id="caaa8-115">Servers are only required for the bootstrapping process.</span></span>  
  
- <span data-ttu-id="caaa8-116">La publication des noms est sécurisée (elle n’implique pas de tierces parties).</span><span class="sxs-lookup"><span data-stu-id="caaa8-116">Secure name publication without the involvement of third parties.</span></span> <span data-ttu-id="caaa8-117">Contrairement à la publication de noms DNS, la publication de noms PNRP est instantanée et sans coûts financiers.</span><span class="sxs-lookup"><span data-stu-id="caaa8-117">Unlike DNS name publication, PNRP name publication is instantaneous and without financial cost.</span></span>  
  
- <span data-ttu-id="caaa8-118">Le protocole PNRP est mis à jour en temps réel, ce qui évite la résolution d’adresses périmées.</span><span class="sxs-lookup"><span data-stu-id="caaa8-118">PNRP updates in real-time, which prevents the resolution of stale addresses.</span></span>  
  
- <span data-ttu-id="caaa8-119">La résolution de noms via le protocole PNRP s’étend au-delà des ordinateurs, puisqu’elle permet également de résoudre des noms de services.</span><span class="sxs-lookup"><span data-stu-id="caaa8-119">The resolution of names via PNRP extends beyond computers by also allowing name resolution for services.</span></span>  
  
## <a name="the-systemnetpeertopeer-namespace"></a><span data-ttu-id="caaa8-120">Espace de noms System.Net.PeerToPeer</span><span class="sxs-lookup"><span data-stu-id="caaa8-120">The System.Net.PeerToPeer namespace</span></span>  
  
- <span data-ttu-id="caaa8-121">La fonctionnalité PNRP est définie par l’espace de noms <xref:System.Net.PeerToPeer> dans le .NET Framework version 3.5.</span><span class="sxs-lookup"><span data-stu-id="caaa8-121">PNRP functionality is defined by the <xref:System.Net.PeerToPeer> namespace within the .NET Framework version 3.5.</span></span> <span data-ttu-id="caaa8-122">Elle fournit un ensemble de types qui peuvent être utilisés pour inscrire et résoudre des noms de pairs avec un service PNRP disponible.</span><span class="sxs-lookup"><span data-stu-id="caaa8-122">It provides a set of types that can be used to register and resolve peer names with an available PNRP service.</span></span>  
  
- <span data-ttu-id="caaa8-123">Les programmes de résolution de pairs personnalisés et les programmes de résolution PNRP peuvent être créés et instanciés à l’aide des types fournis dans l’espace de noms <xref:System.ServiceModel.PeerResolvers>.</span><span class="sxs-lookup"><span data-stu-id="caaa8-123">(PNRP and custom peer resolvers can be created and instantiated using the types provided in the <xref:System.ServiceModel.PeerResolvers> namespace.)</span></span>  
  
- <span data-ttu-id="caaa8-124">Les types de base utilisés pour inscrire et résoudre des noms avec un service PNRP disponible sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="caaa8-124">The basic types used to register and resolve names with an available PNRP service are as follows:</span></span>  
  
- <span data-ttu-id="caaa8-125"><xref:System.Net.PeerToPeer.Cloud> : définit les informations qui décrivent un cloud PNRP disponible, y compris son étendue.</span><span class="sxs-lookup"><span data-stu-id="caaa8-125"><xref:System.Net.PeerToPeer.Cloud>: Defines the information describing an available PNRP cloud, including its scope.</span></span>  
  
- <span data-ttu-id="caaa8-126"><xref:System.Net.PeerToPeer.PeerName> : définit un nom de pair qui peut être utilisé pour inscrire puis résoudre un pair au sein d’un cloud.</span><span class="sxs-lookup"><span data-stu-id="caaa8-126"><xref:System.Net.PeerToPeer.PeerName>: Defines a peer name that can be used to register and subsequently resolve a peer within a cloud.</span></span>  
  
- <span data-ttu-id="caaa8-127"><xref:System.Net.PeerToPeer.PeerNameRecord> : définit l’enregistrement du cloud PNRP qui contient les informations d’inscription d’un pair, notamment les points de terminaison réseau auxquels le pair peut être contacté.</span><span class="sxs-lookup"><span data-stu-id="caaa8-127"><xref:System.Net.PeerToPeer.PeerNameRecord>: Defines the record in PNRP cloud that contains the registration information for a peer, which includes the network endpoints at which the peer can be contacted.</span></span>  
  
- <span data-ttu-id="caaa8-128"><xref:System.Net.PeerToPeer.PeerNameRegistration> : définit le processus d’inscription d’un nom de pair, y compris les méthodes pour démarrer et arrêter l’inscription des noms de pairs.</span><span class="sxs-lookup"><span data-stu-id="caaa8-128"><xref:System.Net.PeerToPeer.PeerNameRegistration>: Defines the registration process for a peer name, including methods to start and stop peer name registration.</span></span>  
  
- <span data-ttu-id="caaa8-129"><xref:System.Net.PeerToPeer.PeerNameResolver> : définit la procédure de résolution d’un nom de pair en son point de terminaison réseau, y compris les méthodes synchrones et asynchrones de résolution.</span><span class="sxs-lookup"><span data-stu-id="caaa8-129"><xref:System.Net.PeerToPeer.PeerNameResolver>: Defines the process for resolving a peer name to its network endpoint(s), including both synchronous and asynchronous methods for resolution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caaa8-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="caaa8-130">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers>
- <xref:System.Net.PeerToPeer>
- [<span data-ttu-id="caaa8-131">Exemples de programmation réseau</span><span class="sxs-lookup"><span data-stu-id="caaa8-131">Network Programming Samples</span></span>](network-programming-samples.md)

<!-- to-do: review sample links
- [PeerToPeer Technology Sample](https://go.microsoft.com/fwlink/?LinkID=179571)
-->

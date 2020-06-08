---
title: Protocole Internet version 6
description: Découvrez le protocole IPv6 et sa différence par rapport à IPv4. Les applications .NET Framework prennent en charge IPv6, mais peuvent nécessiter une configuration.
ms.date: 03/30/2017
helpviewer_keywords:
- IPv6, improvements
- IPv4
- IPv6
- Internet Protocol version 6, improvements
- Internet Protocol version 6
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
ms.openlocfilehash: dd8b0b26e449fba7479d2678aff25ed49e721a90
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502390"
---
# <a name="internet-protocol-version-6"></a><span data-ttu-id="ba4ad-104">Protocole Internet version 6</span><span class="sxs-lookup"><span data-stu-id="ba4ad-104">Internet Protocol Version 6</span></span>
<span data-ttu-id="ba4ad-105">Le protocole IPv6 (protocole Internet version 6) est une nouvelle suite de protocoles standard conçus pour la couche réseau d’Internet.</span><span class="sxs-lookup"><span data-stu-id="ba4ad-105">The Internet Protocol version 6 (IPv6) is a new suite of standard protocols for the network layer of the Internet.</span></span> <span data-ttu-id="ba4ad-106">IPv6 est destiné à résoudre bon nombre des problèmes de l’actuelle version de la suite de protocoles (appelée IPv4), notamment ceux liés à l’épuisement des adresses, la sécurité, la configuration automatique, l’extensibilité, etc.</span><span class="sxs-lookup"><span data-stu-id="ba4ad-106">IPv6 is designed to solve many of the problems of the current version of the Internet Protocol suite (known as IPv4) with regard to address depletion, security, auto-configuration, extensibility, and so on.</span></span> <span data-ttu-id="ba4ad-107">IPv6 étend les capacités d’Internet à de nouveaux types d’applications, comme les applications pair à pair (P2P) et les applications mobiles.</span><span class="sxs-lookup"><span data-stu-id="ba4ad-107">IPv6 expands the capabilities of the Internet to enable new kinds of applications, including peer-to-peer and mobile applications.</span></span> <span data-ttu-id="ba4ad-108">Voici les principaux problèmes du protocole IPv4 actuel :</span><span class="sxs-lookup"><span data-stu-id="ba4ad-108">The following are the main issues of the current IPv4 protocol:</span></span>  
  
- <span data-ttu-id="ba4ad-109">Épuisement rapide de l’espace d’adressage.</span><span class="sxs-lookup"><span data-stu-id="ba4ad-109">Rapid depletion of the address space.</span></span>  
  
     <span data-ttu-id="ba4ad-110">Cela a conduit à l’utilisation de NAT (Network Address Translator) pour mapper plusieurs adresses privées à une seule adresse IP publique.</span><span class="sxs-lookup"><span data-stu-id="ba4ad-110">This has led to the use of Network Address Translators (NATs) that map multiple private addresses to a single public IP address.</span></span> <span data-ttu-id="ba4ad-111">Les principaux problèmes de ce mécanisme sont la surcharge de traitement et l’absence de connectivité de bout en bout.</span><span class="sxs-lookup"><span data-stu-id="ba4ad-111">The main problems created by this mechanism are processing overhead and lack of end-to-end connectivity.</span></span>  
  
- <span data-ttu-id="ba4ad-112">Prise en charge hiérarchique insuffisante.</span><span class="sxs-lookup"><span data-stu-id="ba4ad-112">Lack of hierarchy support.</span></span>  
  
     <span data-ttu-id="ba4ad-113">En raison de son organisation inhérente en classes prédéfinies, IPv4 n’offre pas de véritable prise en charge hiérarchique.</span><span class="sxs-lookup"><span data-stu-id="ba4ad-113">Because of its inherent predefined class organization, IPv4 lacks true hierarchical support.</span></span> <span data-ttu-id="ba4ad-114">Il est impossible d’organiser les adresses IP en les mappant parfaitement à la topologie du réseau.</span><span class="sxs-lookup"><span data-stu-id="ba4ad-114">It is impossible to structure the IP addresses in a way that truly maps the network topology.</span></span> <span data-ttu-id="ba4ad-115">Ce défaut de conception majeur impose l’utilisation de tables de routage de grande taille pour la remise des paquets IPv4 sur Internet.</span><span class="sxs-lookup"><span data-stu-id="ba4ad-115">This crucial design flaw creates the need for large routing tables to deliver IPv4 packets to any location on the Internet.</span></span>  
  
- <span data-ttu-id="ba4ad-116">Configuration complexe du réseau.</span><span class="sxs-lookup"><span data-stu-id="ba4ad-116">Complex network configuration.</span></span>  
  
     <span data-ttu-id="ba4ad-117">Avec IPv4, les adresses doivent être assignées de façon statique ou à l’aide d’un protocole de configuration tel que DHCP.</span><span class="sxs-lookup"><span data-stu-id="ba4ad-117">With IPv4, addresses must be assigned statically or using a configuration protocol such as DHCP.</span></span> <span data-ttu-id="ba4ad-118">Dans l’idéal, les ordinateurs hôtes ne devraient pas avoir à s’appuyer sur l’administration d’une infrastructure DHCP.</span><span class="sxs-lookup"><span data-stu-id="ba4ad-118">In an ideal situation, hosts would not have to rely on the administration of a DHCP infrastructure.</span></span> <span data-ttu-id="ba4ad-119">Ils devraient pouvoir effectuer la configuration eux-mêmes en fonction du segment réseau où ils se trouvent.</span><span class="sxs-lookup"><span data-stu-id="ba4ad-119">Instead, they would be able to configure themselves based on the network segment in which they are located.</span></span>  
  
- <span data-ttu-id="ba4ad-120">Absence de mécanismes d’authentification et de confidentialité intégrés.</span><span class="sxs-lookup"><span data-stu-id="ba4ad-120">Lack of built-in authentication and confidentiality.</span></span>  
  
     <span data-ttu-id="ba4ad-121">IPv4 ne nécessite pas la prise en charge d’un mécanisme qui fournit l’authentification ou le chiffrement des données échangées.</span><span class="sxs-lookup"><span data-stu-id="ba4ad-121">IPv4 does not require the support for any mechanism that provides authentication or encryption of the exchanged data.</span></span> <span data-ttu-id="ba4ad-122">Cela n’est plus le cas avec IPv6.</span><span class="sxs-lookup"><span data-stu-id="ba4ad-122">This changes with IPv6.</span></span> <span data-ttu-id="ba4ad-123">La sécurité du protocole Internet (IPsec) est une exigence de prise en charge d’IPv6.</span><span class="sxs-lookup"><span data-stu-id="ba4ad-123">Internet Protocol security (IPSec) is an IPv6 support requirement.</span></span>  
  
 <span data-ttu-id="ba4ad-124">Une nouvelle suite de protocoles doit répondre aux exigences de base suivantes :</span><span class="sxs-lookup"><span data-stu-id="ba4ad-124">A new protocol suite must satisfy the following basic requirements:</span></span>  
  
- <span data-ttu-id="ba4ad-125">Routage et adressage à grande échelle, avec une faible surcharge.</span><span class="sxs-lookup"><span data-stu-id="ba4ad-125">Large-scale routing and addressing with low overhead.</span></span>  
  
- <span data-ttu-id="ba4ad-126">Configuration automatique pour diverses situations de connexion.</span><span class="sxs-lookup"><span data-stu-id="ba4ad-126">Auto-configuration for various connecting situations.</span></span>  
  
- <span data-ttu-id="ba4ad-127">Authentification et confidentialité intégrées.</span><span class="sxs-lookup"><span data-stu-id="ba4ad-127">Built-in authentication and confidentiality.</span></span>  
  
 <span data-ttu-id="ba4ad-128">Pour plus d’informations, consultez [Adressage IPv6](ipv6-addressing.md), [Routage IPv6](ipv6-routing.md), [Configuration automatique IPv6](ipv6-auto-configuration.md), [Activation et désactivation d’IPv6](enabling-and-disabling-ipv6.md) et [Guide pratique pour modifier le fichier de configuration de l’ordinateur en vue de la prise en charge d’IPv6](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span><span class="sxs-lookup"><span data-stu-id="ba4ad-128">For more information, see [IPv6 Addressing](ipv6-addressing.md), [IPv6 Routing](ipv6-routing.md), [IPv6 Auto-Configuration](ipv6-auto-configuration.md), [Enabling and Disabling IPv6](enabling-and-disabling-ipv6.md), and [How to: Modify the Computer Configuration File to Enable IPv6 Support](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="ba4ad-129">References</span><span class="sxs-lookup"><span data-stu-id="ba4ad-129">References</span></span>  
 <span data-ttu-id="ba4ad-130">Voici une sélection de normes RFC que vous pouvez consulter sur le site web [Internet Engineering Task Force (IETF)](https://www.ietf.org/) :</span><span class="sxs-lookup"><span data-stu-id="ba4ad-130">The following are selected RFC documents that you can find at the [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website:</span></span>  
  
- <span data-ttu-id="ba4ad-131">RFC 1287 : Towards the Future Internet Architecture.</span><span class="sxs-lookup"><span data-stu-id="ba4ad-131">RFC 1287, Towards the Future Internet Architecture.</span></span>  
  
- <span data-ttu-id="ba4ad-132">RFC 1454 : Comparison of Proposals for Next Version of IP.</span><span class="sxs-lookup"><span data-stu-id="ba4ad-132">RFC 1454, Comparison of Proposals for Next Version of IP.</span></span>  
  
- <span data-ttu-id="ba4ad-133">RFC 2373 : IP Version 6 Addressing Architecture.</span><span class="sxs-lookup"><span data-stu-id="ba4ad-133">RFC 2373, IP Version 6 Addressing Architecture.</span></span>  
  
- <span data-ttu-id="ba4ad-134">RFC 2374 : An IPv6 Aggregatable Global Unicast Address Format.</span><span class="sxs-lookup"><span data-stu-id="ba4ad-134">RFC 2374, An IPv6 Aggregatable Global Unicast Address Format.</span></span>  
  
 <span data-ttu-id="ba4ad-135">Vous pouvez également trouver des informations concernant IPv6 dans la section [IP Version 6 (IPv6)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498%28v=ws.10%29).</span><span class="sxs-lookup"><span data-stu-id="ba4ad-135">You can also find IPv6-related information on the [IP Version 6 (IPv6)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498%28v=ws.10%29).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba4ad-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba4ad-136">See also</span></span>

- [<span data-ttu-id="ba4ad-137">Exemple de sockets IPv6</span><span class="sxs-lookup"><span data-stu-id="ba4ad-137">IPv6 Sockets Sample</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms180981%28v=vs.85%29)
- [<span data-ttu-id="ba4ad-138">Exemples de programmation réseau</span><span class="sxs-lookup"><span data-stu-id="ba4ad-138">Network Programming Samples</span></span>](network-programming-samples.md)
- [<span data-ttu-id="ba4ad-139">Sockets</span><span class="sxs-lookup"><span data-stu-id="ba4ad-139">Sockets</span></span>](sockets.md)

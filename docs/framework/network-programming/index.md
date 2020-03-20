---
title: Programmation réseau dans le .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- Networking
- Internet
- Internet, .NET Framework Internet services
- Network Resources
ms.assetid: 8d455610-67a0-4fa8-a62f-7747064a9256
ms.openlocfilehash: 1e7f0123ab07fd4e83eea957b72bf79eeeecef2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74204696"
---
# <a name="network-programming-in-the-net-framework"></a><span data-ttu-id="e9bba-102">Programmation réseau dans le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e9bba-102">Network Programming in the .NET Framework</span></span>
<span data-ttu-id="e9bba-103">Microsoft .NET Framework fournit une implémentation en couche, extensible et managée des services Internet que vous pouvez intégrer rapidement et facilement à vos applications.</span><span class="sxs-lookup"><span data-stu-id="e9bba-103">The Microsoft .NET Framework provides a layered, extensible, and managed implementation of Internet services that can be quickly and easily integrated into your applications.</span></span> <span data-ttu-id="e9bba-104">Les applications réseau peuvent générer des protocoles enfichables pour tirer parti automatiquement de nouveaux protocoles Internet, ou elles peuvent utiliser une implémentation managée de l'interface Windows Socket pour fonctionner au niveau du socket.</span><span class="sxs-lookup"><span data-stu-id="e9bba-104">Your network applications can build on pluggable protocols to automatically take advantage of new Internet protocols, or they can use a managed implementation of the Windows socket interface to work with the network on the socket level.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e9bba-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="e9bba-105">In This Section</span></span>  

 [<span data-ttu-id="e9bba-106">Introduction aux protocoles enfichables</span><span class="sxs-lookup"><span data-stu-id="e9bba-106">Introducing Pluggable Protocols</span></span>](introducing-pluggable-protocols.md)  
 <span data-ttu-id="e9bba-107">Décrit comment accéder à une ressource réseau sans tenir compte du protocole d'accès dont elle a besoin.</span><span class="sxs-lookup"><span data-stu-id="e9bba-107">Describes how to access an Internet resource without regard to the access protocol that it requires.</span></span>  
  
 [<span data-ttu-id="e9bba-108">Demande de données</span><span class="sxs-lookup"><span data-stu-id="e9bba-108">Requesting Data</span></span>](requesting-data.md)  
 <span data-ttu-id="e9bba-109">Explique comment utiliser des protocoles enfichables pour charger et télécharger les données à partir des ressources Internet.</span><span class="sxs-lookup"><span data-stu-id="e9bba-109">Explains how to use pluggable protocols to upload and download data from Internet resources.</span></span>  
  
 [<span data-ttu-id="e9bba-110">programmation de protocoles enfichables</span><span class="sxs-lookup"><span data-stu-id="e9bba-110">Programming Pluggable Protocols</span></span>](programming-pluggable-protocols.md)  
 <span data-ttu-id="e9bba-111">Explique comment dériver les classes spécifiques au protocole pour implémenter des protocoles enfichables.</span><span class="sxs-lookup"><span data-stu-id="e9bba-111">Explains how to derive protocol-specific classes to implement pluggable protocols.</span></span>  
  
 [<span data-ttu-id="e9bba-112">Utilisation de protocoles d’application</span><span class="sxs-lookup"><span data-stu-id="e9bba-112">Using Application Protocols</span></span>](using-application-protocols.md)  
 <span data-ttu-id="e9bba-113">Décrit les applications de programmation qui tirent parti des protocoles réseau comme TCP, UDP, et HTTP.</span><span class="sxs-lookup"><span data-stu-id="e9bba-113">Describes programming applications that take advantage of network protocols such as TCP, UDP, and HTTP.</span></span>  
  
 [<span data-ttu-id="e9bba-114">Version 6 du protocole Internet</span><span class="sxs-lookup"><span data-stu-id="e9bba-114">Internet Protocol Version 6</span></span>](internet-protocol-version-6.md)  
 <span data-ttu-id="e9bba-115">Décrit les avantages du protocole IPv6 (Internet Protocol version 6) par rapport à la version actuelle de la suite des protocoles Internet (IPv4), décrit l’adressage IPv6, le routage et la configuration automatique, et comment activer et désactiver IPv6.</span><span class="sxs-lookup"><span data-stu-id="e9bba-115">Describes the advantages of Internet Protocol version 6 (IPv6) over the current version of the Internet Protocol suite (IPv4), describes IPv6 addressing, routing and auto-configuration, and how to enable and disable IPv6.</span></span>  
  
 [<span data-ttu-id="e9bba-116">Configuration des applications Internet</span><span class="sxs-lookup"><span data-stu-id="e9bba-116">Configuring Internet Applications</span></span>](configuring-internet-applications.md)  
 <span data-ttu-id="e9bba-117">Explique comment utiliser les fichiers de configuration .NET Framework pour configurer les applications Web.</span><span class="sxs-lookup"><span data-stu-id="e9bba-117">Explains how to use the .NET Framework configuration files to configure Internet applications.</span></span>  
  
 [<span data-ttu-id="e9bba-118">Traçage réseau dans .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e9bba-118">Network Tracing in the .NET Framework</span></span>](network-tracing.md)  
 <span data-ttu-id="e9bba-119">Explique comment utiliser le traçage réseau pour obtenir des informations sur les appels de méthode et le trafic réseau généré par une application managée.</span><span class="sxs-lookup"><span data-stu-id="e9bba-119">Explains how to use network tracing to get information about method invocations and network traffic generated by a managed application.</span></span>  
  
 [<span data-ttu-id="e9bba-120">Gestion du cache pour les applications réseau</span><span class="sxs-lookup"><span data-stu-id="e9bba-120">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)  
 <span data-ttu-id="e9bba-121">Décrit comment utiliser la mise en cache pour les applications qui utilisent les classes <xref:System.Net.WebClient?displayProperty=nameWithType>, <xref:System.Net.WebRequest?displayProperty=nameWithType>et <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e9bba-121">Describes how to use caching for applications that use the <xref:System.Net.WebClient?displayProperty=nameWithType>, <xref:System.Net.WebRequest?displayProperty=nameWithType>, and <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> classes.</span></span>  
  
 [<span data-ttu-id="e9bba-122">Sécurité dans la programmation réseau</span><span class="sxs-lookup"><span data-stu-id="e9bba-122">Security in Network Programming</span></span>](security-in-network-programming.md)  
 <span data-ttu-id="e9bba-123">Explique comment utiliser des techniques standard de sécurité Internet et d'authentification.</span><span class="sxs-lookup"><span data-stu-id="e9bba-123">Describes how to use standard Internet security and authentication techniques.</span></span>  
  
 [<span data-ttu-id="e9bba-124">Pratiques recommandées pour les classes System.Net</span><span class="sxs-lookup"><span data-stu-id="e9bba-124">Best Practices for System.Net Classes</span></span>](best-practices-for-system-net-classes.md)  
 <span data-ttu-id="e9bba-125">Fournit des conseils et des astuces pour profiter au mieux de vos applications Web.</span><span class="sxs-lookup"><span data-stu-id="e9bba-125">Provides tips and tricks for getting the most out of your Internet applications.</span></span>  
  
 [<span data-ttu-id="e9bba-126">Accès à Internet par le biais d’un proxy</span><span class="sxs-lookup"><span data-stu-id="e9bba-126">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)  
 <span data-ttu-id="e9bba-127">Décrit comment configurer des proxies.</span><span class="sxs-lookup"><span data-stu-id="e9bba-127">Describes how to configure proxies.</span></span>  
  
 [<span data-ttu-id="e9bba-128">NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="e9bba-128">NetworkInformation</span></span>](networkinformation.md)  
 <span data-ttu-id="e9bba-129">Explique comment collecter des informations sur les événements, les modifications, les statistiques et les propriétés réseau et explique également comment déterminer si un hôte distant est accessible ou non à l'aide de la classe <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e9bba-129">Describes how to gather information about network events, changes, statistics, and properties and also explains how to determine whether a remote host is reachable by using the <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> class.</span></span>  
  
 [<span data-ttu-id="e9bba-130">Modifications apportées à l’espace nom System.Uri dans la version 2.0</span><span class="sxs-lookup"><span data-stu-id="e9bba-130">Changes to the System.Uri namespace in Version 2.0</span></span>](changes-to-the-system-uri-namespace-in-version-2-0.md)  
 <span data-ttu-id="e9bba-131">Décrit plusieurs modifications apportées à la classe <xref:System.Uri?displayProperty=nameWithType> dans la version 2.0 pour corriger les comportements incorrects, améliorer la convivialité et la sécurité.</span><span class="sxs-lookup"><span data-stu-id="e9bba-131">Describes several changes made to the <xref:System.Uri?displayProperty=nameWithType> class in Version 2.0 to fixed incorrect behavior, enhance usability, and enhance security.</span></span>  
  
 [<span data-ttu-id="e9bba-132">Prise en charge de l’identifiant de ressource internationalisée dans System.Uri</span><span class="sxs-lookup"><span data-stu-id="e9bba-132">International Resource Identifier Support in System.Uri</span></span>](international-resource-identifier-support-in-system-uri.md)  
 <span data-ttu-id="e9bba-133">Décrit les améliorations apportées à la classe <xref:System.Uri?displayProperty=nameWithType> dans la version 3.5, 3.0 SP1, et 2.0 SP1 pour la prise en charge de l'identifiant de ressource internationalisée et du nom de domaine internationalisé.</span><span class="sxs-lookup"><span data-stu-id="e9bba-133">Describes enhancements to the <xref:System.Uri?displayProperty=nameWithType> class in Version 3.5, 3.0 SP1, and 2.0 SP1 for International Resource Identifier (IRI) and Internationalized Domain Name (IDN) support.</span></span>  
  
 [<span data-ttu-id="e9bba-134">Améliorations des performances de socket dans la version 3.5</span><span class="sxs-lookup"><span data-stu-id="e9bba-134">Socket Performance Enhancements in Version 3.5</span></span>](socket-performance-enhancements-in-version-3-5.md)  
 <span data-ttu-id="e9bba-135">Décrit un ensemble d'améliorations apportées à la classe <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> dans la version 3.5, 3.0 SP1 et 2.0 SP1 qui fournit un autre modèle asynchrone pouvant être utilisé par les applications de socket spécialisées très performantes.</span><span class="sxs-lookup"><span data-stu-id="e9bba-135">Describes a set of enhancements to the <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> class in Version 3.5, 3.0 SP1, and 2.0 SP1 that provide an alternative asynchronous pattern that can be used by specialized high-performance socket applications.</span></span>  
  
 [<span data-ttu-id="e9bba-136">protocole PNRP</span><span class="sxs-lookup"><span data-stu-id="e9bba-136">Peer Name Resolution Protocol</span></span>](peer-name-resolution-protocol.md)  
 <span data-ttu-id="e9bba-137">Décrit l’ajout de la prise en charge à la version 3.5 pour prendre en charge le protocole PNRP (Peer Name Resolution Protocol), une inscription de noms dynamiques et sans serveur et un protocole de résolution de noms.</span><span class="sxs-lookup"><span data-stu-id="e9bba-137">Describes support added in Version 3.5 to support the Peer Name Resolution Protocol (PNRP), a serverless and dynamic name registration and name resolution protocol.</span></span> <span data-ttu-id="e9bba-138">Ces nouvelles fonctionnalités sont prises en charge par l'espace de noms <xref:System.Net.PeerToPeer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e9bba-138">These new features are supported by the <xref:System.Net.PeerToPeer?displayProperty=nameWithType> namespace.</span></span>  
  
 [<span data-ttu-id="e9bba-139">Collaboration pair à pair</span><span class="sxs-lookup"><span data-stu-id="e9bba-139">Peer-to-Peer Collaboration</span></span>](peer-to-peer-collaboration.md)  
 <span data-ttu-id="e9bba-140">Décrit l'ajout de la prise en charge à la version 3.5 pour prendre en charge la collaboration pair à pair qui s'appuie sur PNRP.</span><span class="sxs-lookup"><span data-stu-id="e9bba-140">Describes support added in Version 3.5 to support the Peer-to-Peer Collaboration that builds on PNRP.</span></span> <span data-ttu-id="e9bba-141">Ces nouvelles fonctionnalités sont prises en charge par l'espace de noms <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e9bba-141">These new features are supported by the <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType> namespace.</span></span>  
  
 [<span data-ttu-id="e9bba-142">Changements apportés à l’authentification NTLM pour HttpWebRequest dans la version 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="e9bba-142">Changes to NTLM authentication for HttpWebRequest in Version 3.5 SP1</span></span>](changes-to-ntlm-authentication-for-httpwebrequest-in-version-3-5-sp1.md)  
 <span data-ttu-id="e9bba-143">Décrit les changements de sécurité apportés à la version 3.5 SP1 qui affectent la manière dont l'intégration de l'authentification Windows est gérée par <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>, <xref:System.Net.HttpListener?displayProperty=nameWithType>, <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>, et les classes associées dans l'espace de noms System.Net.</span><span class="sxs-lookup"><span data-stu-id="e9bba-143">Describes security changes made in Version 3.5 SP1 that affect how integrated Windows authentication is handled by the <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>, <xref:System.Net.HttpListener?displayProperty=nameWithType>, <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>, and related classes in the System.Net namespace.</span></span>  
  
 [<span data-ttu-id="e9bba-144">Integrated Windows Authentication with Extended Protection</span><span class="sxs-lookup"><span data-stu-id="e9bba-144">Integrated Windows Authentication with Extended Protection</span></span>](integrated-windows-authentication-with-extended-protection.md)  
 <span data-ttu-id="e9bba-145">Décrit les améliorations de la protection étendue qui affectent la manière dont l'authentification Windows intégrée est gérée par <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>, <xref:System.Net.HttpListener?displayProperty=nameWithType>, <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>, <xref:System.Net.Security.SslStream?displayProperty=nameWithType>, <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>, et les classes associées dans <xref:System.Net?displayProperty=nameWithType> et les espaces de noms associés.</span><span class="sxs-lookup"><span data-stu-id="e9bba-145">Describes enhancements for extended protection that affect how integrated Windows authentication is handled by the <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>, <xref:System.Net.HttpListener?displayProperty=nameWithType>, <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>, <xref:System.Net.Security.SslStream?displayProperty=nameWithType>, <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>, and related classes in the <xref:System.Net?displayProperty=nameWithType> and related namespaces.</span></span>  
  
 [<span data-ttu-id="e9bba-146">Parcours NAT avec IPv6 et Teredo</span><span class="sxs-lookup"><span data-stu-id="e9bba-146">NAT Traversal using IPv6 and Teredo</span></span>](nat-traversal-using-ipv6-and-teredo.md)  
 <span data-ttu-id="e9bba-147">Décrit les améliorations apportées aux espaces de noms <xref:System.Net?displayProperty=nameWithType>, <xref:System.Net.NetworkInformation?displayProperty=nameWithType>, et <xref:System.Net.Sockets?displayProperty=nameWithType> pour prendre en charge le parcours NAT avec IPv6 et Teredo.</span><span class="sxs-lookup"><span data-stu-id="e9bba-147">Describes enhancements added to the <xref:System.Net?displayProperty=nameWithType>, <xref:System.Net.NetworkInformation?displayProperty=nameWithType>, and <xref:System.Net.Sockets?displayProperty=nameWithType> namespaces to support NAT traversal using IPv6 and Teredo.</span></span>  
  
 [<span data-ttu-id="e9bba-148">Isolement réseau pour les applications du Windows Store</span><span class="sxs-lookup"><span data-stu-id="e9bba-148">Network Isolation for Windows Store Apps</span></span>](network-isolation-for-windows-store-apps.md)  
 <span data-ttu-id="e9bba-149">Décrit l’impact de l’isolement <xref:System.Net> <xref:System.Net.Http>du <xref:System.Net.Http.Headers> réseau lorsque les classes dans le , , et les espaces nominaux sont utilisés dans Windows 8.x Store applications.</span><span class="sxs-lookup"><span data-stu-id="e9bba-149">Describes the impact of network isolation when classes in the <xref:System.Net>, <xref:System.Net.Http>, and <xref:System.Net.Http.Headers> namespaces are used in Windows 8.x Store apps.</span></span>  
  
 [<span data-ttu-id="e9bba-150">Exemples de programmation réseau</span><span class="sxs-lookup"><span data-stu-id="e9bba-150">Network Programming Samples</span></span>](network-programming-samples.md)  
 <span data-ttu-id="e9bba-151">Liens vers des exemples téléchargeables de programmation qui utilisent des classes dans les espaces de noms <xref:System.Net>, <xref:System.Net.Cache>, <xref:System.Net.Configuration>, <xref:System.Net.Mail>, <xref:System.Net.Mime>, <xref:System.Net.NetworkInformation>, <xref:System.Net.PeerToPeer>, <xref:System.Net.Security>, <xref:System.Net.Sockets> .</span><span class="sxs-lookup"><span data-stu-id="e9bba-151">Links to downloadable network programming samples that use classes in the <xref:System.Net>, <xref:System.Net.Cache>, <xref:System.Net.Configuration>, <xref:System.Net.Mail>, <xref:System.Net.Mime>, <xref:System.Net.NetworkInformation>, <xref:System.Net.PeerToPeer>, <xref:System.Net.Security>, <xref:System.Net.Sockets> namespaces.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e9bba-152">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="e9bba-152">Reference</span></span>  
 <xref:System.Net?displayProperty=nameWithType>  
 <span data-ttu-id="e9bba-153">Constitue une interface de programmation simple pour un grand nombre des protocoles réseau employés aujourd'hui.</span><span class="sxs-lookup"><span data-stu-id="e9bba-153">Provides a simple programming interface for many of the protocols used on networks today.</span></span> <span data-ttu-id="e9bba-154">Les classes <xref:System.Net.WebRequest?displayProperty=nameWithType> et <xref:System.Net.WebResponse?displayProperty=nameWithType> de cet espace de noms servent de base aux protocoles enfichables.</span><span class="sxs-lookup"><span data-stu-id="e9bba-154">The <xref:System.Net.WebRequest?displayProperty=nameWithType> and <xref:System.Net.WebResponse?displayProperty=nameWithType> classes in this namespace are the basis for pluggable protocols.</span></span>  
  
 <xref:System.Net.Cache?displayProperty=nameWithType>  
 <span data-ttu-id="e9bba-155">Définit les types et les énumérations utilisés pour définir des stratégies de cache applicables aux ressources et obtenus via l'utilisation des classes <xref:System.Net.WebRequest?displayProperty=nameWithType> et <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e9bba-155">Defines the types and enumerations used to define cache policies for resources obtained using the <xref:System.Net.WebRequest?displayProperty=nameWithType> and <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> classes.</span></span>  
  
 <xref:System.Net.Configuration?displayProperty=nameWithType>  
 <span data-ttu-id="e9bba-156">Classes utilisées par les applications pour accéder et mettre à jour par programmation des paramètres de configuration pour les espaces de noms System.Net.</span><span class="sxs-lookup"><span data-stu-id="e9bba-156">Classes that applications use to programmatically access and update configuration settings for the System.Net namespaces.</span></span>  
  
 <xref:System.Net.Http?displayProperty=nameWithType>  
 <span data-ttu-id="e9bba-157">Classes qui fournissent une interface de programmation pour les applications HTTP modernes.</span><span class="sxs-lookup"><span data-stu-id="e9bba-157">Classes that provides a programming interface for modern HTTP applications.</span></span>  
  
 <xref:System.Net.Http.Headers?displayProperty=nameWithType>  
 <span data-ttu-id="e9bba-158">Prend en charge les collections d'en-têtes HTTP utilisés par l'espace de noms <xref:System.Net.Http?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e9bba-158">Provides support for collections of HTTP headers used by the <xref:System.Net.Http?displayProperty=nameWithType> namespace</span></span>  
  
 <xref:System.Net.Mail?displayProperty=nameWithType>  
 <span data-ttu-id="e9bba-159">Classes pour composer et envoyer des messages à l'aide du protocole SMTP.</span><span class="sxs-lookup"><span data-stu-id="e9bba-159">Classes to compose and send mail using the SMTP protocol.</span></span>  
  
 <xref:System.Net.Mime?displayProperty=nameWithType>  
 <span data-ttu-id="e9bba-160">Définit les types utilisés pour représenter les en-têtes MIME (Multipurpose Internet Mail Exchange) utilisés par les classes de l'espace de noms <xref:System.Net.Mail?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e9bba-160">Defines types that are used to represent Multipurpose Internet Mail Exchange (MIME) headers used by classes in the <xref:System.Net.Mail?displayProperty=nameWithType> namespace.</span></span>  
  
 <xref:System.Net.NetworkInformation?displayProperty=nameWithType>  
 <span data-ttu-id="e9bba-161">Classes permettant de recueillir des informations par programmation sur les événements, les modifications, des statistiques et les propriétés réseau.</span><span class="sxs-lookup"><span data-stu-id="e9bba-161">Classes to programmatically gather information about network events, changes, statistics, and properties.</span></span>  
  
 <xref:System.Net.PeerToPeer?displayProperty=nameWithType>  
 <span data-ttu-id="e9bba-162">Fournit une implémentation managée du protocole PNRP (Peer Name Resolution Protocol) pour les développeurs.</span><span class="sxs-lookup"><span data-stu-id="e9bba-162">Provides a managed implementation of the Peer Name Resolution Protocol (PNRP) for developers.</span></span>  
  
 <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType>  
 <span data-ttu-id="e9bba-163">Fournit une implémentation managée de l'interface de collaboration pair à pair aux développeurs.</span><span class="sxs-lookup"><span data-stu-id="e9bba-163">Provides a managed implementation of the Peer-to-Peer Collaboration interface for developers.</span></span>  
  
 <xref:System.Net.Security?displayProperty=nameWithType>  
 <span data-ttu-id="e9bba-164">Classes pour fournir des flux de réseau pour des communications sécurisées entre les hôtes.</span><span class="sxs-lookup"><span data-stu-id="e9bba-164">Classes to provide network streams for secure communications between hosts.</span></span>  
  
 <xref:System.Net.Sockets?displayProperty=nameWithType>  
 <span data-ttu-id="e9bba-165">Fournit une implémentation managée de l'interface Windows Sockets (Winsock) pour les développeurs qui doivent aider à contrôler étroitement l'accès au réseau.</span><span class="sxs-lookup"><span data-stu-id="e9bba-165">Provides a managed implementation of the Windows Sockets (Winsock) interface for developers who need to help control access to the network.</span></span>  
  
 <xref:System.Net.WebSockets?displayProperty=nameWithType>  
 <span data-ttu-id="e9bba-166">Fournit une implémentation managée de l'interface WebSocket pour les développeurs.</span><span class="sxs-lookup"><span data-stu-id="e9bba-166">Provides a managed implementation of the WebSocket interface for developers.</span></span>  
  
 <xref:System.Uri?displayProperty=nameWithType>  
 <span data-ttu-id="e9bba-167">Fournit une représentation d'objet d'un URI (Uniform Resource Identifier) et un accès aisé aux parties de l'URI.</span><span class="sxs-lookup"><span data-stu-id="e9bba-167">Provides an object representation of a uniform resource identifier (URI) and easy access to the parts of the URI.</span></span>  
  
 <xref:System.Security.Authentication.ExtendedProtection?displayProperty=nameWithType>  
 <span data-ttu-id="e9bba-168">Fournit un support pour l'authentification à l'aide de la protection étendue pour les applications.</span><span class="sxs-lookup"><span data-stu-id="e9bba-168">Provides support for authentication using extended protection for applications.</span></span>  
  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration?displayProperty=nameWithType>  
 <span data-ttu-id="e9bba-169">Fournit un support pour la configuration de l'authentification à l'aide de la protection étendue pour les applications.</span><span class="sxs-lookup"><span data-stu-id="e9bba-169">Provides support for configuration of authentication using extended protection for applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9bba-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9bba-170">See also</span></span>

- [<span data-ttu-id="e9bba-171">Bonnes pratiques du protocole TLS (Transport Layer Security) avec le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e9bba-171">Transport Layer Security (TLS) best practices with .NET Framework</span></span>](tls.md)
- [<span data-ttu-id="e9bba-172">Rubriques de guide pratique sur la programmation réseau</span><span class="sxs-lookup"><span data-stu-id="e9bba-172">Network Programming How-to Topics</span></span>](network-programming-how-to-topics.md)
- [<span data-ttu-id="e9bba-173">Exemples de programmation réseau</span><span class="sxs-lookup"><span data-stu-id="e9bba-173">Network Programming Samples</span></span>](network-programming-samples.md)
- [<span data-ttu-id="e9bba-174">Exemple HttpClient</span><span class="sxs-lookup"><span data-stu-id="e9bba-174">HttpClient Sample</span></span>](https://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664)

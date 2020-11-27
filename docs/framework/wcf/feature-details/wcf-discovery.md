---
title: Discovery WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], discovery
- Windows Communication Foundation [WCF], discovery
- discovery [WCF]
ms.assetid: 462c4913-f388-45a9-9042-28ae96a4e735
ms.openlocfilehash: 176e9760d98f9640bd9d1c7b059287dc29c0d666
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289358"
---
# <a name="wcf-discovery"></a><span data-ttu-id="0a7a0-102">Discovery WCF</span><span class="sxs-lookup"><span data-stu-id="0a7a0-102">WCF Discovery</span></span>

<span data-ttu-id="0a7a0-103">Windows Communication Foundation (WCF) fournit la prise en charge pour permettre aux services d’être détectables au moment de l’exécution d’une manière interopérable à l’aide du protocole WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-103">Windows Communication Foundation (WCF) provides support to enable services to be discoverable at runtime in an interoperable way using the WS-Discovery protocol.</span></span> <span data-ttu-id="0a7a0-104">Les services WCF peuvent annoncer leur disponibilité au réseau à l’aide d’un message de multidiffusion ou d’un serveur proxy de découverte.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-104">WCF services can announce their availability to the network using a multicast message or to a discovery proxy server.</span></span> <span data-ttu-id="0a7a0-105">Les applications clientes peuvent rechercher sur le réseau ou dans un serveur proxy de découverte des services qui répondent à un jeu de critères.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-105">Client applications can search the network or a discovery proxy server to find services that meet a set of criteria.</span></span> <span data-ttu-id="0a7a0-106">Les rubriques de cette section donnent une vue d’ensemble et décrivent en détail le modèle de programmation pour cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-106">The topics in this section provide an overview and describe the programming model for this feature in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0a7a0-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="0a7a0-107">In This Section</span></span>  

 [<span data-ttu-id="0a7a0-108">Vue d'ensemble de la découverte WCF</span><span class="sxs-lookup"><span data-stu-id="0a7a0-108">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)  
 <span data-ttu-id="0a7a0-109">Fournit une vue d’ensemble de la prise en charge de WS-Discovery fournie par WCF.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-109">Provides an overview of WS-Discovery support provided by WCF.</span></span>  
  
 [<span data-ttu-id="0a7a0-110">Modèle objet de découverte WCF</span><span class="sxs-lookup"><span data-stu-id="0a7a0-110">WCF Discovery Object Model</span></span>](wcf-discovery-object-model.md)  
 <span data-ttu-id="0a7a0-111">Décrit les classes du modèle objet et l'extensibilité de la prise en charge de WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-111">Describes the classes in the object model and extensibility of WS-Discovery support.</span></span>  
  
 [<span data-ttu-id="0a7a0-112">Procédure : ajouter par programmation la détectabilité à un service et un client WCF</span><span class="sxs-lookup"><span data-stu-id="0a7a0-112">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)  
 <span data-ttu-id="0a7a0-113">Montre comment rendre un service Windows Communication Foundation (WCF) détectable.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-113">Shows how to make a Windows Communication Foundation (WCF) service discoverable.</span></span>  
  
 [<span data-ttu-id="0a7a0-114">Implémentation d'un proxy de découverte</span><span class="sxs-lookup"><span data-stu-id="0a7a0-114">Implementing a Discovery Proxy</span></span>](implementing-a-discovery-proxy.md)  
 <span data-ttu-id="0a7a0-115">Décrit les étapes nécessaires pour implémenter un proxy de découverte, un service détectable qui s'enregistre avec le proxy de découverte et un client qui utilise le proxy de découverte pour rechercher le service détectable.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-115">Describes the steps required to implement a discovery proxy, a discoverable service that registers with the discovery proxy, and a client that uses the discovery proxy to find the discoverable service.</span></span>  
  
 [<span data-ttu-id="0a7a0-116">Contrôle des versions de découverte</span><span class="sxs-lookup"><span data-stu-id="0a7a0-116">Discovery Versioning</span></span>](discovery-versioning.md)  
 <span data-ttu-id="0a7a0-117">Donne une vue d'ensemble d'une implémentation prototype de nouvelles fonctionnalités de découverte.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-117">Provides a brief overview of a prototype implementation of some new discovery features.</span></span> <span data-ttu-id="0a7a0-118">Elle donne également une vue d'ensemble de la manière de sélectionner la version de découverte à utiliser.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-118">It also gives an overview on how to select the discovery version to use.</span></span>  
  
 [<span data-ttu-id="0a7a0-119">Configuration de la découverte dans un fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="0a7a0-119">Configuring Discovery in a Configuration File</span></span>](configuring-discovery-in-a-configuration-file.md)  
 <span data-ttu-id="0a7a0-120">Indique comment configurer la découverte dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-120">Shows how to configure Discovery in configuration.</span></span>  
  
 [<span data-ttu-id="0a7a0-121">Utilisation du canal client de découverte</span><span class="sxs-lookup"><span data-stu-id="0a7a0-121">Using the Discovery Client Channel</span></span>](using-the-discovery-client-channel.md)  
 <span data-ttu-id="0a7a0-122">Montre comment utiliser un canal client de découverte lors de l’écriture d’une application cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-122">Shows how to use a Discovery Client Channel when writing a WCF client application.</span></span>

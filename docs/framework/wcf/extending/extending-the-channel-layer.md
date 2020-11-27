---
title: Extension de la couche du canal
ms.date: 03/30/2017
helpviewer_keywords:
- extending channels [WCF]
ms.assetid: 4238db74-2fb6-4dc8-a326-f58527230810
ms.openlocfilehash: 8d051ff84ea0562b3d7c810b2c884f4d8b787952
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273020"
---
# <a name="extending-the-channel-layer"></a><span data-ttu-id="d5e87-102">Extension de la couche du canal</span><span class="sxs-lookup"><span data-stu-id="d5e87-102">Extending the Channel Layer</span></span>

<span data-ttu-id="d5e87-103">La couche du canal est responsable de l'échange de messages entre clients et services.</span><span class="sxs-lookup"><span data-stu-id="d5e87-103">The channel layer is responsible for the exchange of messages between clients and services.</span></span> <span data-ttu-id="d5e87-104">Les extensions de canal peuvent implémenter de nouvelles fonctionnalités d'un protocole, telles que la sécurité, ou des fonctionnalités de transport, telles que l'implémentation d'un nouveau transport réseau pour les messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="d5e87-104">Channel extensions can implement new protocol functionality, such as security, or transport functionality, such as implementing a new network transport to carry SOAP messages.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d5e87-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="d5e87-105">In This Section</span></span>  

 [<span data-ttu-id="d5e87-106">Vue d'ensemble du modèle de canal</span><span class="sxs-lookup"><span data-stu-id="d5e87-106">Channel Model Overview</span></span>](channel-model-overview.md)  
 <span data-ttu-id="d5e87-107">Fournit une vue d'ensemble générale de ce que sont les canaux, des fonctionnalités qu'ils fournissent et de la manière dont ils fonctionnent dans un service et dans une application cliente.</span><span class="sxs-lookup"><span data-stu-id="d5e87-107">Provides a high-level overview of what channels are, the features that they provide and how they work both in a service and a client application.</span></span>  
  
 [<span data-ttu-id="d5e87-108">Développement de canaux</span><span class="sxs-lookup"><span data-stu-id="d5e87-108">Developing Channels</span></span>](developing-channels.md)  
 <span data-ttu-id="d5e87-109">Décrit en détail les rôles que jouent les divers types d'infrastructures de canal, comment le moteur d'état et le cycle de vie de l'état fonctionnent, comment gérer des exceptions et des erreurs, comment implémenter la prise en charge des métadonnées, et comment les canaux fonctionnent avec les encodeurs de message.</span><span class="sxs-lookup"><span data-stu-id="d5e87-109">Describes in depth the roles that the various channel infrastructure types play, how the state engine and state lifecycle works, how to handle exceptions and faults, how to implement metadata support, and how channels work with message encoders.</span></span>  
  
 [<span data-ttu-id="d5e87-110">Encodeurs personnalisés</span><span class="sxs-lookup"><span data-stu-id="d5e87-110">Custom Encoders</span></span>](custom-encoders.md)  
 <span data-ttu-id="d5e87-111">Décrit le rôle que les encodeurs de message jouent dans les canaux et comment en générer un.</span><span class="sxs-lookup"><span data-stu-id="d5e87-111">Describes the role that message encoders play in channels and how to build one.</span></span>  
  
 [<span data-ttu-id="d5e87-112">Mises à niveau de flux personnalisées</span><span class="sxs-lookup"><span data-stu-id="d5e87-112">Custom Stream Upgrades</span></span>](custom-stream-upgrades.md)  
 <span data-ttu-id="d5e87-113">Décrit le processus de la mise à niveau des flux fournis par les transports orientés flux.</span><span class="sxs-lookup"><span data-stu-id="d5e87-113">Describes the process of upgrading the streams provided by stream-oriented transports.</span></span>

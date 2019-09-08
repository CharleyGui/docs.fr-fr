---
title: Traçage analytique avec ETW
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: dd745730ca186b9489c547f790c546e95bf96372
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798093"
---
# <a name="analytic-tracing-with-etw"></a><span data-ttu-id="bcd45-102">Traçage analytique avec ETW</span><span class="sxs-lookup"><span data-stu-id="bcd45-102">Analytic Tracing with ETW</span></span>
<span data-ttu-id="bcd45-103">Le suivi analytique Windows Communication Foundation (WCF) offre un moyen de capturer des informations de diagnostic pendant l’exécution d’un service WCF.</span><span class="sxs-lookup"><span data-stu-id="bcd45-103">Windows Communication Foundation (WCF) analytic tracing offers a way to capture diagnostic information during the execution of a WCF service.</span></span> <span data-ttu-id="bcd45-104">Les événements de traçage analytique WCF sont émis à des points clés dans la pile WCF pour permettre la résolution des problèmes des services WCF dans un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="bcd45-104">WCF analytic tracing events are emitted at key points in the WCF stack to allow troubleshooting of WCF services in a production environment.</span></span> <span data-ttu-id="bcd45-105">Le suivi analytique pour les services WCF a un impact minimal sur les performances d’un serveur [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] de produit qui héberge les services WCF, car ces événements sont émis très efficacement dans une session suivi d’v nements pour Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="bcd45-105">Analytic tracing for WCF services has minimal impact on the performance of a product server that hosts [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] WCF services as these events are very efficiently emitted to an Event Tracing for Windows (ETW) session.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bcd45-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="bcd45-106">In This Section</span></span>  
 [<span data-ttu-id="bcd45-107">Vue d’ensemble du suivi analytique</span><span class="sxs-lookup"><span data-stu-id="bcd45-107">Analytic Tracing Overview</span></span>](analytic-tracing-overview.md)  
 <span data-ttu-id="bcd45-108">Décrit le fonctionnement du traçage analytique WCF dans [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bcd45-108">Discusses how WCF analytic tracing works in [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="bcd45-109">Activation dynamique du suivi analytique</span><span class="sxs-lookup"><span data-stu-id="bcd45-109">Dynamically Enabling Analytic Tracing</span></span>](dynamically-enabling-analytic-tracing.md)  
 <span data-ttu-id="bcd45-110">Explique comment activer ou désactiver le traçage de manière dynamique à l'aide d'ETW.</span><span class="sxs-lookup"><span data-stu-id="bcd45-110">Discusses how to enable or disable tracing dynamically using ETW.</span></span>  
  
 [<span data-ttu-id="bcd45-111">Configuration du suivi de flux de messages</span><span class="sxs-lookup"><span data-stu-id="bcd45-111">Configuring Message Flow Tracing</span></span>](configuring-message-flow-tracing.md)  
 <span data-ttu-id="bcd45-112">Décrit comment configurer le traçage du flux des messages.</span><span class="sxs-lookup"><span data-stu-id="bcd45-112">Describes how to configure message flow tracing.</span></span>  
  
 [<span data-ttu-id="bcd45-113">Informations de référence sur les événements de suivi analytique</span><span class="sxs-lookup"><span data-stu-id="bcd45-113">Analytic Trace Event Reference</span></span>](analytic-trace-event-reference.md)  
 <span data-ttu-id="bcd45-114">Affiche une table d'ID d'événements avec leurs niveaux d'événements, leurs messages d'événements et leurs mots clés.</span><span class="sxs-lookup"><span data-stu-id="bcd45-114">Shows a table of event IDs with their event levels, event messages and keywords.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcd45-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bcd45-115">See also</span></span>

- [<span data-ttu-id="bcd45-116">Services WCF et suivi des événements pour Windows</span><span class="sxs-lookup"><span data-stu-id="bcd45-116">WCF Services and Event Tracing for Windows</span></span>](../../samples/wcf-services-and-event-tracing-for-windows.md)
- [<span data-ttu-id="bcd45-117">Événements de suivi dans Event Tracing for Windows</span><span class="sxs-lookup"><span data-stu-id="bcd45-117">Tracking Events into Event Tracing in Windows</span></span>](../../../windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)

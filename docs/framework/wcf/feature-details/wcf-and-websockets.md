---
title: WCF et WebSockets
ms.date: 03/30/2017
ms.assetid: 1e53b49e-022c-49c7-8984-4b21b53c05b3
ms.openlocfilehash: 2ee27eef015ee8c2fbee8360b444343a1c757097
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281584"
---
# <a name="wcf-and-websockets"></a><span data-ttu-id="da500-102">WCF et WebSockets</span><span class="sxs-lookup"><span data-stu-id="da500-102">WCF and WebSockets</span></span>

<span data-ttu-id="da500-103">.NET Framework 4.5 introduit la prise en charge de WebSockets dans Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="da500-103">The .NET Framework 4.5 introduces support for WebSockets in Windows Communication Foundation.</span></span>  <span data-ttu-id="da500-104">WebSockets est une technologie efficace basée sur des normes qui permet la communication bidirectionnelle sur les ports HTTP standard 80 et 443.</span><span class="sxs-lookup"><span data-stu-id="da500-104">WebSockets is an efficient, standards-based technology that enables bidirectional communication over the standard HTTP ports 80 and 443.</span></span> <span data-ttu-id="da500-105">L'utilisation des ports HTTP standard permet à WebSockets de communiquer sur le Web via des intermédiaires.</span><span class="sxs-lookup"><span data-stu-id="da500-105">The use of the standard HTTP ports allow WebSockets to communicate across the web through intermediaries.</span></span>  <span data-ttu-id="da500-106">Deux nouvelles liaisons standard ont été ajoutées pour prendre en charge les communications via un transport WebSocket.</span><span class="sxs-lookup"><span data-stu-id="da500-106">Two new standard bindings have been added to support communication over a WebSocket transport.</span></span> <span data-ttu-id="da500-107">Voir <xref:System.ServiceModel.NetHttpBinding> et <xref:System.ServiceModel.NetHttpsBinding>.</span><span class="sxs-lookup"><span data-stu-id="da500-107"><xref:System.ServiceModel.NetHttpBinding> and <xref:System.ServiceModel.NetHttpsBinding>.</span></span> <span data-ttu-id="da500-108">Les paramètres spécifiques à WebSocket peuvent être configurés sur le <xref:System.ServiceModel.Channels.HttpTransportBindingElement> en accédant à la <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="da500-108">WebSockets-specific settings can be configured on the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> by accessing the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> property.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="da500-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="da500-109">In This Section</span></span>  

 [<span data-ttu-id="da500-110">Utilisation de NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="da500-110">Using the NetHttpBinding</span></span>](using-the-nethttpbinding.md)  
 <span data-ttu-id="da500-111">Décrit <xref:System.ServiceModel.NetHttpBinding> et la façon de le configurer.</span><span class="sxs-lookup"><span data-stu-id="da500-111">Discusses the <xref:System.ServiceModel.NetHttpBinding> and how to configure it.</span></span>  
  
 [<span data-ttu-id="da500-112">Procédure : créer un service WCF qui communique sur WebSockets</span><span class="sxs-lookup"><span data-stu-id="da500-112">How to: Create a WCF Service that Communicates over WebSockets</span></span>](how-to-create-a-wcf-service-that-communicates-over-websockets.md)  
 <span data-ttu-id="da500-113">Décrit comment créer un service WCF qui communique sur WebSockets</span><span class="sxs-lookup"><span data-stu-id="da500-113">Describes how to create a WCF service that communicates over Websockets.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="da500-114">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="da500-114">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="da500-115">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="da500-115">Related Sections</span></span>

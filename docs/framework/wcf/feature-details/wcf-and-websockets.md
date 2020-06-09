---
title: WCF et WebSockets
ms.date: 03/30/2017
ms.assetid: 1e53b49e-022c-49c7-8984-4b21b53c05b3
ms.openlocfilehash: df4a251eb5a570c9fedf19d385a027e23481afed
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594944"
---
# <a name="wcf-and-websockets"></a><span data-ttu-id="3c3d7-102">WCF et WebSockets</span><span class="sxs-lookup"><span data-stu-id="3c3d7-102">WCF and WebSockets</span></span>
<span data-ttu-id="3c3d7-103">.NET Framework 4.5 introduit la prise en charge de WebSockets dans Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="3c3d7-103">The .NET Framework 4.5 introduces support for WebSockets in Windows Communication Foundation.</span></span>  <span data-ttu-id="3c3d7-104">WebSockets est une technologie efficace basée sur des normes qui permet la communication bidirectionnelle sur les ports HTTP standard 80 et 443.</span><span class="sxs-lookup"><span data-stu-id="3c3d7-104">WebSockets is an efficient, standards-based technology that enables bidirectional communication over the standard HTTP ports 80 and 443.</span></span> <span data-ttu-id="3c3d7-105">L'utilisation des ports HTTP standard permet à WebSockets de communiquer sur le Web via des intermédiaires.</span><span class="sxs-lookup"><span data-stu-id="3c3d7-105">The use of the standard HTTP ports allow WebSockets to communicate across the web through intermediaries.</span></span>  <span data-ttu-id="3c3d7-106">Deux nouvelles liaisons standard ont été ajoutées pour prendre en charge les communications via un transport WebSocket.</span><span class="sxs-lookup"><span data-stu-id="3c3d7-106">Two new standard bindings have been added to support communication over a WebSocket transport.</span></span> <span data-ttu-id="3c3d7-107"><xref:System.ServiceModel.NetHttpBinding> et <xref:System.ServiceModel.NetHttpsBinding>.</span><span class="sxs-lookup"><span data-stu-id="3c3d7-107"><xref:System.ServiceModel.NetHttpBinding> and <xref:System.ServiceModel.NetHttpsBinding>.</span></span> <span data-ttu-id="3c3d7-108">Les paramètres spécifiques à WebSocket peuvent être configurés sur le <xref:System.ServiceModel.Channels.HttpTransportBindingElement> en accédant à la <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="3c3d7-108">WebSockets-specific settings can be configured on the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> by accessing the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> property.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="3c3d7-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="3c3d7-109">In This Section</span></span>  
 [<span data-ttu-id="3c3d7-110">Utilisation de NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="3c3d7-110">Using the NetHttpBinding</span></span>](using-the-nethttpbinding.md)  
 <span data-ttu-id="3c3d7-111">Décrit <xref:System.ServiceModel.NetHttpBinding> et la façon de le configurer.</span><span class="sxs-lookup"><span data-stu-id="3c3d7-111">Discusses the <xref:System.ServiceModel.NetHttpBinding> and how to configure it.</span></span>  
  
 [<span data-ttu-id="3c3d7-112">Procédure pour créer un service WCF qui communique sur WebSockets</span><span class="sxs-lookup"><span data-stu-id="3c3d7-112">How to: Create a WCF Service that Communicates over WebSockets</span></span>](how-to-create-a-wcf-service-that-communicates-over-websockets.md)  
 <span data-ttu-id="3c3d7-113">Décrit comment créer un service WCF qui communique sur WebSockets</span><span class="sxs-lookup"><span data-stu-id="3c3d7-113">Describes how to create a WCF service that communicates over Websockets.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3c3d7-114">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="3c3d7-114">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3c3d7-115">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="3c3d7-115">Related Sections</span></span>

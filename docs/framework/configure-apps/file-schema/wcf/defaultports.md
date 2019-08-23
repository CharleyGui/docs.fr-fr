---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 462a06e5a773310b6364838ae2ebc14da0a2ee1b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925885"
---
# <a name="defaultports"></a><span data-ttu-id="0fa08-101">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="0fa08-101">\<defaultPorts></span></span>
<span data-ttu-id="0fa08-102">Collection des ports par défaut répertoriant les points de terminaison de communication par défaut écoutés par l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="0fa08-102">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="0fa08-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0fa08-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="0fa08-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="0fa08-104">\<behaviors></span></span>  
<span data-ttu-id="0fa08-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="0fa08-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="0fa08-106">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="0fa08-106">\<behavior></span></span>  
<span data-ttu-id="0fa08-107">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="0fa08-107">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="0fa08-108">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="0fa08-108">\<defaultPorts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fa08-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0fa08-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0fa08-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0fa08-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0fa08-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0fa08-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0fa08-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="0fa08-112">Attributes</span></span>  
 <span data-ttu-id="0fa08-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0fa08-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0fa08-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0fa08-114">Child Elements</span></span>  
  
|<span data-ttu-id="0fa08-115">Élément</span><span class="sxs-lookup"><span data-stu-id="0fa08-115">Element</span></span>|<span data-ttu-id="0fa08-116">Description</span><span class="sxs-lookup"><span data-stu-id="0fa08-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0fa08-117">\<Ajouter > de \<la > defaultPorts</span><span class="sxs-lookup"><span data-stu-id="0fa08-117">\<add> of \<defaultPorts></span></span>](add-of-defaultports.md)|<span data-ttu-id="0fa08-118">Point de terminaison de communication par défaut écouté par l'application cliente.</span><span class="sxs-lookup"><span data-stu-id="0fa08-118">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0fa08-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0fa08-119">Parent Elements</span></span>  
  
|<span data-ttu-id="0fa08-120">Élément</span><span class="sxs-lookup"><span data-stu-id="0fa08-120">Element</span></span>|<span data-ttu-id="0fa08-121">Description</span><span class="sxs-lookup"><span data-stu-id="0fa08-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0fa08-122">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="0fa08-122">\<useRequestHeadersForMetadataAddress></span></span>](userequestheadersformetadataaddress.md)|<span data-ttu-id="0fa08-123">Liste de ports par défaut.</span><span class="sxs-lookup"><span data-stu-id="0fa08-123">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0fa08-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0fa08-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>

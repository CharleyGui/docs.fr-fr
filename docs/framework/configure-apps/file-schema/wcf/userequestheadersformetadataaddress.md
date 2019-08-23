---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: 84310d4ae5e04e76e4484f4fc606c9896239c776
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940548"
---
# <a name="userequestheadersformetadataaddress"></a><span data-ttu-id="f808f-101">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="f808f-101">\<useRequestHeadersForMetadataAddress></span></span>
<span data-ttu-id="f808f-102">Active la récupération des informations d'adresse des métadonnées à partir des en-têtes de message de demande.</span><span class="sxs-lookup"><span data-stu-id="f808f-102">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="f808f-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f808f-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="f808f-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="f808f-104">\<behaviors></span></span>  
<span data-ttu-id="f808f-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="f808f-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="f808f-106">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="f808f-106">\<behavior></span></span>  
<span data-ttu-id="f808f-107">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="f808f-107">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f808f-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f808f-108">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f808f-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f808f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f808f-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f808f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f808f-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="f808f-111">Attributes</span></span>  
 <span data-ttu-id="f808f-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f808f-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f808f-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f808f-113">Child Elements</span></span>  
  
|<span data-ttu-id="f808f-114">Élément</span><span class="sxs-lookup"><span data-stu-id="f808f-114">Element</span></span>|<span data-ttu-id="f808f-115">Description</span><span class="sxs-lookup"><span data-stu-id="f808f-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f808f-116">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="f808f-116">\<defaultPorts></span></span>](defaultports.md)|<span data-ttu-id="f808f-117">Collection des ports par défaut répertoriant les points de terminaison de communication par défaut écoutés par l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="f808f-117">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f808f-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f808f-118">Parent Elements</span></span>  
  
|<span data-ttu-id="f808f-119">Élément</span><span class="sxs-lookup"><span data-stu-id="f808f-119">Element</span></span>|<span data-ttu-id="f808f-120">Description</span><span class="sxs-lookup"><span data-stu-id="f808f-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f808f-121">\<behavior></span><span class="sxs-lookup"><span data-stu-id="f808f-121">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="f808f-122">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="f808f-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f808f-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f808f-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>

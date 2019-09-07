---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: e0b46953924a3825420b719085e1210981da643a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399201"
---
# <a name="userequestheadersformetadataaddress"></a><span data-ttu-id="38b0e-101">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="38b0e-101">\<useRequestHeadersForMetadataAddress></span></span>
<span data-ttu-id="38b0e-102">Active la récupération des informations d'adresse des métadonnées à partir des en-têtes de message de demande.</span><span class="sxs-lookup"><span data-stu-id="38b0e-102">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="38b0e-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="38b0e-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="38b0e-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="38b0e-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="38b0e-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="38b0e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="38b0e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="38b0e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="38b0e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="38b0e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="38b0e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<useRequestHeadersForMetadataAddress >**</span><span class="sxs-lookup"><span data-stu-id="38b0e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useRequestHeadersForMetadataAddress>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38b0e-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38b0e-109">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38b0e-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="38b0e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="38b0e-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="38b0e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38b0e-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="38b0e-112">Attributes</span></span>  
 <span data-ttu-id="38b0e-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="38b0e-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="38b0e-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="38b0e-114">Child Elements</span></span>  
  
|<span data-ttu-id="38b0e-115">Élément</span><span class="sxs-lookup"><span data-stu-id="38b0e-115">Element</span></span>|<span data-ttu-id="38b0e-116">Description</span><span class="sxs-lookup"><span data-stu-id="38b0e-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="38b0e-117">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="38b0e-117">\<defaultPorts></span></span>](defaultports.md)|<span data-ttu-id="38b0e-118">Collection des ports par défaut répertoriant les points de terminaison de communication par défaut écoutés par l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="38b0e-118">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="38b0e-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="38b0e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="38b0e-120">Élément</span><span class="sxs-lookup"><span data-stu-id="38b0e-120">Element</span></span>|<span data-ttu-id="38b0e-121">Description</span><span class="sxs-lookup"><span data-stu-id="38b0e-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="38b0e-122">\<behavior></span><span class="sxs-lookup"><span data-stu-id="38b0e-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="38b0e-123">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="38b0e-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="38b0e-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38b0e-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>

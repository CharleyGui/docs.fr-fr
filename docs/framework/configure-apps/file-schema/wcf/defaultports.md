---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 89ebad118c1c9210357d8fd281c9216b7f64b450
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398075"
---
# <a name="defaultports"></a><span data-ttu-id="08143-101">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="08143-101">\<defaultPorts></span></span>
<span data-ttu-id="08143-102">Collection des ports par défaut répertoriant les points de terminaison de communication par défaut écoutés par l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="08143-102">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
<span data-ttu-id="08143-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="08143-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="08143-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="08143-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="08143-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="08143-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="08143-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="08143-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="08143-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="08143-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="08143-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<useRequestHeadersForMetadataAddress >** ](userequestheadersformetadataaddress.md)</span><span class="sxs-lookup"><span data-stu-id="08143-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)</span></span>\
<span data-ttu-id="08143-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<defaultPorts >**</span><span class="sxs-lookup"><span data-stu-id="08143-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultPorts>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08143-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08143-110">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08143-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="08143-111">Attributes and Elements</span></span>  
 <span data-ttu-id="08143-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="08143-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08143-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="08143-113">Attributes</span></span>  
 <span data-ttu-id="08143-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="08143-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="08143-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="08143-115">Child Elements</span></span>  
  
|<span data-ttu-id="08143-116">Élément</span><span class="sxs-lookup"><span data-stu-id="08143-116">Element</span></span>|<span data-ttu-id="08143-117">Description</span><span class="sxs-lookup"><span data-stu-id="08143-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="08143-118">\<Ajouter > de \<la > defaultPorts</span><span class="sxs-lookup"><span data-stu-id="08143-118">\<add> of \<defaultPorts></span></span>](add-of-defaultports.md)|<span data-ttu-id="08143-119">Point de terminaison de communication par défaut écouté par l'application cliente.</span><span class="sxs-lookup"><span data-stu-id="08143-119">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="08143-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="08143-120">Parent Elements</span></span>  
  
|<span data-ttu-id="08143-121">Élément</span><span class="sxs-lookup"><span data-stu-id="08143-121">Element</span></span>|<span data-ttu-id="08143-122">Description</span><span class="sxs-lookup"><span data-stu-id="08143-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="08143-123">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="08143-123">\<useRequestHeadersForMetadataAddress></span></span>](userequestheadersformetadataaddress.md)|<span data-ttu-id="08143-124">Liste de ports par défaut.</span><span class="sxs-lookup"><span data-stu-id="08143-124">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="08143-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08143-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>

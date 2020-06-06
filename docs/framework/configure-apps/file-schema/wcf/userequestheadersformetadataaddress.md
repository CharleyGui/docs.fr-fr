---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: e0b46953924a3825420b719085e1210981da643a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399201"
---
# \<useRequestHeadersForMetadataAddress>
<span data-ttu-id="7b1c7-101">Active la récupération des informations d'adresse des métadonnées à partir des en-têtes de message de demande.</span><span class="sxs-lookup"><span data-stu-id="7b1c7-101">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useRequestHeadersForMetadataAddress>**  
  
## <a name="syntax"></a><span data-ttu-id="7b1c7-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b1c7-102">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b1c7-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7b1c7-103">Attributes and Elements</span></span>  
 <span data-ttu-id="7b1c7-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7b1c7-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b1c7-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="7b1c7-105">Attributes</span></span>  
 <span data-ttu-id="7b1c7-106">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7b1c7-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7b1c7-107">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7b1c7-107">Child Elements</span></span>  
  
|<span data-ttu-id="7b1c7-108">Élément</span><span class="sxs-lookup"><span data-stu-id="7b1c7-108">Element</span></span>|<span data-ttu-id="7b1c7-109">Description</span><span class="sxs-lookup"><span data-stu-id="7b1c7-109">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultPorts>](defaultports.md)|<span data-ttu-id="7b1c7-110">Collection des ports par défaut répertoriant les points de terminaison de communication par défaut écoutés par l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="7b1c7-110">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7b1c7-111">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7b1c7-111">Parent Elements</span></span>  
  
|<span data-ttu-id="7b1c7-112">Élément</span><span class="sxs-lookup"><span data-stu-id="7b1c7-112">Element</span></span>|<span data-ttu-id="7b1c7-113">Description</span><span class="sxs-lookup"><span data-stu-id="7b1c7-113">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="7b1c7-114">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="7b1c7-114">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7b1c7-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7b1c7-115">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>

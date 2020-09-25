---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: a323e6da0eb173e303d70cc3b7309b898a805573
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172812"
---
# \<useRequestHeadersForMetadataAddress>

<span data-ttu-id="9a10c-101">Active la récupération des informations d'adresse des métadonnées à partir des en-têtes de message de demande.</span><span class="sxs-lookup"><span data-stu-id="9a10c-101">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useRequestHeadersForMetadataAddress>**  
  
## <a name="syntax"></a><span data-ttu-id="9a10c-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a10c-102">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9a10c-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9a10c-103">Attributes and Elements</span></span>  

 <span data-ttu-id="9a10c-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9a10c-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9a10c-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="9a10c-105">Attributes</span></span>  

 <span data-ttu-id="9a10c-106">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9a10c-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9a10c-107">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9a10c-107">Child Elements</span></span>  
  
|<span data-ttu-id="9a10c-108">Élément</span><span class="sxs-lookup"><span data-stu-id="9a10c-108">Element</span></span>|<span data-ttu-id="9a10c-109">Description</span><span class="sxs-lookup"><span data-stu-id="9a10c-109">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultPorts>](defaultports.md)|<span data-ttu-id="9a10c-110">Collection des ports par défaut répertoriant les points de terminaison de communication par défaut écoutés par l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="9a10c-110">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9a10c-111">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9a10c-111">Parent Elements</span></span>  
  
|<span data-ttu-id="9a10c-112">Élément</span><span class="sxs-lookup"><span data-stu-id="9a10c-112">Element</span></span>|<span data-ttu-id="9a10c-113">Description</span><span class="sxs-lookup"><span data-stu-id="9a10c-113">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="9a10c-114">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="9a10c-114">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9a10c-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a10c-115">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>

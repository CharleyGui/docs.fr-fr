---
title: <defaultPorts>
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 08ca8a2bfcf5b905152f7e64a45cbae4992a7b78
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192371"
---
# \<defaultPorts>

<span data-ttu-id="e792b-101">Collection des ports par défaut répertoriant les points de terminaison de communication par défaut écoutés par l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="e792b-101">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultPorts>**  
  
## <a name="syntax"></a><span data-ttu-id="e792b-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e792b-102">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e792b-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e792b-103">Attributes and Elements</span></span>  

 <span data-ttu-id="e792b-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e792b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e792b-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="e792b-105">Attributes</span></span>  

 <span data-ttu-id="e792b-106">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e792b-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e792b-107">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e792b-107">Child Elements</span></span>  
  
|<span data-ttu-id="e792b-108">Élément</span><span class="sxs-lookup"><span data-stu-id="e792b-108">Element</span></span>|<span data-ttu-id="e792b-109">Description</span><span class="sxs-lookup"><span data-stu-id="e792b-109">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e792b-110">\<add> of \<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="e792b-110">\<add> of \<defaultPorts></span></span>](add-of-defaultports.md)|<span data-ttu-id="e792b-111">Point de terminaison de communication par défaut écouté par l'application cliente.</span><span class="sxs-lookup"><span data-stu-id="e792b-111">A default communications endpoint that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e792b-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e792b-112">Parent Elements</span></span>  
  
|<span data-ttu-id="e792b-113">Élément</span><span class="sxs-lookup"><span data-stu-id="e792b-113">Element</span></span>|<span data-ttu-id="e792b-114">Description</span><span class="sxs-lookup"><span data-stu-id="e792b-114">Description</span></span>|  
|-------------|-----------------|  
|[\<useRequestHeadersForMetadataAddress>](userequestheadersformetadataaddress.md)|<span data-ttu-id="e792b-115">Liste de ports par défaut.</span><span class="sxs-lookup"><span data-stu-id="e792b-115">A list of default ports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e792b-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e792b-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>

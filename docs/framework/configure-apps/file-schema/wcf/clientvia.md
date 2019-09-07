---
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: a1c2ee68fb039e24e1462148cb52daf1bb57f8ed
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398108"
---
# <a name="clientvia"></a><span data-ttu-id="f983f-101">\<clientVia></span><span class="sxs-lookup"><span data-stu-id="f983f-101">\<clientVia></span></span>
<span data-ttu-id="f983f-102">Spécifie l'URI pour lequel le canal de transport doit être créé.</span><span class="sxs-lookup"><span data-stu-id="f983f-102">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="f983f-103">Pour plus d'informations, consultez <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="f983f-103">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
<span data-ttu-id="f983f-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f983f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f983f-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f983f-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f983f-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f983f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="f983f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f983f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="f983f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f983f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="f983f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<clientVia >**</span><span class="sxs-lookup"><span data-stu-id="f983f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientVia>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f983f-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f983f-110">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f983f-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f983f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f983f-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f983f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f983f-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="f983f-113">Attributes</span></span>  
  
|<span data-ttu-id="f983f-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="f983f-114">Attribute</span></span>|<span data-ttu-id="f983f-115">Description</span><span class="sxs-lookup"><span data-stu-id="f983f-115">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="f983f-116">Chaîne qui spécifie un URI indiquant l'itinéraire d'un message.</span><span class="sxs-lookup"><span data-stu-id="f983f-116">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f983f-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f983f-117">Child Elements</span></span>  
 <span data-ttu-id="f983f-118">Aucun</span><span class="sxs-lookup"><span data-stu-id="f983f-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f983f-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f983f-119">Parent Elements</span></span>  
  
|<span data-ttu-id="f983f-120">Élément</span><span class="sxs-lookup"><span data-stu-id="f983f-120">Element</span></span>|<span data-ttu-id="f983f-121">Description</span><span class="sxs-lookup"><span data-stu-id="f983f-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f983f-122">\<behavior></span><span class="sxs-lookup"><span data-stu-id="f983f-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="f983f-123">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="f983f-123">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f983f-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f983f-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>

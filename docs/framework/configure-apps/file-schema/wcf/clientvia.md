---
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: a1c2ee68fb039e24e1462148cb52daf1bb57f8ed
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398108"
---
# \<clientVia>
<span data-ttu-id="ffad2-101">Spécifie l'URI pour lequel le canal de transport doit être créé.</span><span class="sxs-lookup"><span data-stu-id="ffad2-101">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="ffad2-102">Pour plus d’informations, consultez <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="ffad2-102">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientVia>**  
  
## <a name="syntax"></a><span data-ttu-id="ffad2-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ffad2-103">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ffad2-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ffad2-104">Attributes and Elements</span></span>  
 <span data-ttu-id="ffad2-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ffad2-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ffad2-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="ffad2-106">Attributes</span></span>  
  
|<span data-ttu-id="ffad2-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="ffad2-107">Attribute</span></span>|<span data-ttu-id="ffad2-108">Description</span><span class="sxs-lookup"><span data-stu-id="ffad2-108">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="ffad2-109">Chaîne qui spécifie un URI indiquant l'itinéraire d'un message.</span><span class="sxs-lookup"><span data-stu-id="ffad2-109">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ffad2-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ffad2-110">Child Elements</span></span>  
 <span data-ttu-id="ffad2-111">Aucune</span><span class="sxs-lookup"><span data-stu-id="ffad2-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ffad2-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ffad2-112">Parent Elements</span></span>  
  
|<span data-ttu-id="ffad2-113">Élément</span><span class="sxs-lookup"><span data-stu-id="ffad2-113">Element</span></span>|<span data-ttu-id="ffad2-114">Description</span><span class="sxs-lookup"><span data-stu-id="ffad2-114">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="ffad2-115">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="ffad2-115">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ffad2-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ffad2-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>

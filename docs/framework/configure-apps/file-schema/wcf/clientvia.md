---
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: 5e62201a38dc4dc251996531a4af5f294dd2395f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151101"
---
# \<clientVia>

<span data-ttu-id="1cf8d-101">Spécifie l'URI pour lequel le canal de transport doit être créé.</span><span class="sxs-lookup"><span data-stu-id="1cf8d-101">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="1cf8d-102">Pour plus d'informations, consultez <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="1cf8d-102">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientVia>**  
  
## <a name="syntax"></a><span data-ttu-id="1cf8d-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1cf8d-103">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1cf8d-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1cf8d-104">Attributes and Elements</span></span>  

 <span data-ttu-id="1cf8d-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1cf8d-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1cf8d-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="1cf8d-106">Attributes</span></span>  
  
|<span data-ttu-id="1cf8d-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="1cf8d-107">Attribute</span></span>|<span data-ttu-id="1cf8d-108">Description</span><span class="sxs-lookup"><span data-stu-id="1cf8d-108">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="1cf8d-109">Chaîne qui spécifie un URI indiquant l'itinéraire d'un message.</span><span class="sxs-lookup"><span data-stu-id="1cf8d-109">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1cf8d-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1cf8d-110">Child Elements</span></span>  

 <span data-ttu-id="1cf8d-111">None</span><span class="sxs-lookup"><span data-stu-id="1cf8d-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1cf8d-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1cf8d-112">Parent Elements</span></span>  
  
|<span data-ttu-id="1cf8d-113">Élément</span><span class="sxs-lookup"><span data-stu-id="1cf8d-113">Element</span></span>|<span data-ttu-id="1cf8d-114">Description</span><span class="sxs-lookup"><span data-stu-id="1cf8d-114">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="1cf8d-115">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="1cf8d-115">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1cf8d-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1cf8d-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>

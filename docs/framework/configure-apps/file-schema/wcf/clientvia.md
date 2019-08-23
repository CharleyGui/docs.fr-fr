---
title: <clientVia>
ms.date: 03/30/2017
ms.assetid: c27ee94e-babd-459b-9574-2a6d67d11314
ms.openlocfilehash: b12a882d942555a24c145b243d2cea764ba106b1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919502"
---
# <a name="clientvia"></a><span data-ttu-id="87c5f-101">\<clientVia></span><span class="sxs-lookup"><span data-stu-id="87c5f-101">\<clientVia></span></span>
<span data-ttu-id="87c5f-102">Spécifie l'URI pour lequel le canal de transport doit être créé.</span><span class="sxs-lookup"><span data-stu-id="87c5f-102">Specifies the URI for which the transport channel should be created.</span></span> <span data-ttu-id="87c5f-103">Pour plus d'informations, consultez <xref:System.ServiceModel.Description.ClientViaBehavior>.</span><span class="sxs-lookup"><span data-stu-id="87c5f-103">For more information, see <xref:System.ServiceModel.Description.ClientViaBehavior>.</span></span>  
  
 <span data-ttu-id="87c5f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="87c5f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="87c5f-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="87c5f-105">\<behaviors></span></span>  
<span data-ttu-id="87c5f-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="87c5f-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="87c5f-107">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="87c5f-107">\<behavior></span></span>  
<span data-ttu-id="87c5f-108">\<clientVia></span><span class="sxs-lookup"><span data-stu-id="87c5f-108">\<clientVia></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87c5f-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87c5f-109">Syntax</span></span>  
  
```xml  
<clientVia viaUri="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87c5f-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="87c5f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="87c5f-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="87c5f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87c5f-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="87c5f-112">Attributes</span></span>  
  
|<span data-ttu-id="87c5f-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="87c5f-113">Attribute</span></span>|<span data-ttu-id="87c5f-114">Description</span><span class="sxs-lookup"><span data-stu-id="87c5f-114">Description</span></span>|  
|---------------|-----------------|  
|`viaUri`|<span data-ttu-id="87c5f-115">Chaîne qui spécifie un URI indiquant l'itinéraire d'un message.</span><span class="sxs-lookup"><span data-stu-id="87c5f-115">A string that specifies a URI that indicates the route a message should take.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87c5f-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="87c5f-116">Child Elements</span></span>  
 <span data-ttu-id="87c5f-117">Aucun</span><span class="sxs-lookup"><span data-stu-id="87c5f-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="87c5f-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="87c5f-118">Parent Elements</span></span>  
  
|<span data-ttu-id="87c5f-119">Élément</span><span class="sxs-lookup"><span data-stu-id="87c5f-119">Element</span></span>|<span data-ttu-id="87c5f-120">Description</span><span class="sxs-lookup"><span data-stu-id="87c5f-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87c5f-121">\<behavior></span><span class="sxs-lookup"><span data-stu-id="87c5f-121">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="87c5f-122">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="87c5f-122">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="87c5f-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87c5f-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientViaElement>
- <xref:System.ServiceModel.Description.ClientViaBehavior>

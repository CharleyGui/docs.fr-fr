---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 123f58ee3d77bf605db21fa0d9537b3196d56468
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919115"
---
# <a name="enablewebscript"></a><span data-ttu-id="a742b-101">\<enableWebScript></span><span class="sxs-lookup"><span data-stu-id="a742b-101">\<enableWebScript></span></span>
<span data-ttu-id="a742b-102">Cet élément active le comportement de point de terminaison qui permet de consommer le service à partir de pages web ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="a742b-102">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
 <span data-ttu-id="a742b-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a742b-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="a742b-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="a742b-104">\<behaviors></span></span>  
<span data-ttu-id="a742b-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="a742b-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="a742b-106">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="a742b-106">\<behavior></span></span>  
<span data-ttu-id="a742b-107">\<enableWebScript></span><span class="sxs-lookup"><span data-stu-id="a742b-107">\<enableWebScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a742b-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a742b-108">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a742b-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a742b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a742b-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a742b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a742b-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="a742b-111">Attributes</span></span>  
 <span data-ttu-id="a742b-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a742b-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a742b-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a742b-113">Child Elements</span></span>  
 <span data-ttu-id="a742b-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a742b-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a742b-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a742b-115">Parent Elements</span></span>  
  
|<span data-ttu-id="a742b-116">Élément</span><span class="sxs-lookup"><span data-stu-id="a742b-116">Element</span></span>|<span data-ttu-id="a742b-117">Description</span><span class="sxs-lookup"><span data-stu-id="a742b-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a742b-118">\<behavior></span><span class="sxs-lookup"><span data-stu-id="a742b-118">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="a742b-119">Spécifie le jeu de comportements du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="a742b-119">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a742b-120">Notes</span><span class="sxs-lookup"><span data-stu-id="a742b-120">Remarks</span></span>  
 <span data-ttu-id="a742b-121">Ce comportement doit être utilisé uniquement avec la [ \<liaison WebHttpBinding >](webhttpbinding.md) standard ou l' [ \<](webmessageencoding.md) élément de liaison webMessageEncoding >.</span><span class="sxs-lookup"><span data-stu-id="a742b-121">This behavior should only be used in conjunction with either the [\<webHttpBinding>](webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="a742b-122">Pour plus d'informations sur ce comportement, consultez <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span><span class="sxs-lookup"><span data-stu-id="a742b-122">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a742b-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a742b-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="a742b-124">Intégration d’AJAX et prise en charge de JSON</span><span class="sxs-lookup"><span data-stu-id="a742b-124">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="a742b-125">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="a742b-125">\<webHttp></span></span>](webhttp.md)

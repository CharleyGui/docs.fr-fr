---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 20c0057c80b668df97379d0168bb7c005d9927ce
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400383"
---
# <a name="enablewebscript"></a><span data-ttu-id="d3e6f-101">\<enableWebScript></span><span class="sxs-lookup"><span data-stu-id="d3e6f-101">\<enableWebScript></span></span>
<span data-ttu-id="d3e6f-102">Cet élément active le comportement de point de terminaison qui permet de consommer le service à partir de pages web ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="d3e6f-102">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
<span data-ttu-id="d3e6f-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d3e6f-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d3e6f-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="d3e6f-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d3e6f-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="d3e6f-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="d3e6f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="d3e6f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="d3e6f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="d3e6f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="d3e6f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<enableWebScript >**</span><span class="sxs-lookup"><span data-stu-id="d3e6f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<enableWebScript>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3e6f-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3e6f-109">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3e6f-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d3e6f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d3e6f-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d3e6f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3e6f-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="d3e6f-112">Attributes</span></span>  
 <span data-ttu-id="d3e6f-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d3e6f-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d3e6f-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d3e6f-114">Child Elements</span></span>  
 <span data-ttu-id="d3e6f-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d3e6f-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d3e6f-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d3e6f-116">Parent Elements</span></span>  
  
|<span data-ttu-id="d3e6f-117">Élément</span><span class="sxs-lookup"><span data-stu-id="d3e6f-117">Element</span></span>|<span data-ttu-id="d3e6f-118">Description</span><span class="sxs-lookup"><span data-stu-id="d3e6f-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3e6f-119">\<behavior></span><span class="sxs-lookup"><span data-stu-id="d3e6f-119">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="d3e6f-120">Spécifie le jeu de comportements du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="d3e6f-120">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3e6f-121">Notes</span><span class="sxs-lookup"><span data-stu-id="d3e6f-121">Remarks</span></span>  
 <span data-ttu-id="d3e6f-122">Ce comportement doit être utilisé uniquement avec la [ \<liaison WebHttpBinding >](webhttpbinding.md) standard ou l' [ \<](webmessageencoding.md) élément de liaison webMessageEncoding >.</span><span class="sxs-lookup"><span data-stu-id="d3e6f-122">This behavior should only be used in conjunction with either the [\<webHttpBinding>](webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="d3e6f-123">Pour plus d'informations sur ce comportement, consultez <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span><span class="sxs-lookup"><span data-stu-id="d3e6f-123">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3e6f-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3e6f-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="d3e6f-125">Intégration d’AJAX et prise en charge de JSON</span><span class="sxs-lookup"><span data-stu-id="d3e6f-125">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="d3e6f-126">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="d3e6f-126">\<webHttp></span></span>](webhttp.md)

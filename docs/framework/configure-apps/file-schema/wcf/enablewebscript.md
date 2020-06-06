---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 20c0057c80b668df97379d0168bb7c005d9927ce
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400383"
---
# \<enableWebScript>
<span data-ttu-id="ebead-101">Cet élément active le comportement de point de terminaison qui permet de consommer le service à partir de pages web ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="ebead-101">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<enableWebScript>**  
  
## <a name="syntax"></a><span data-ttu-id="ebead-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ebead-102">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ebead-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ebead-103">Attributes and Elements</span></span>  
 <span data-ttu-id="ebead-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ebead-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ebead-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="ebead-105">Attributes</span></span>  
 <span data-ttu-id="ebead-106">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ebead-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ebead-107">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ebead-107">Child Elements</span></span>  
 <span data-ttu-id="ebead-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ebead-108">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ebead-109">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ebead-109">Parent Elements</span></span>  
  
|<span data-ttu-id="ebead-110">Élément</span><span class="sxs-lookup"><span data-stu-id="ebead-110">Element</span></span>|<span data-ttu-id="ebead-111">Description</span><span class="sxs-lookup"><span data-stu-id="ebead-111">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="ebead-112">Spécifie le jeu de comportements du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="ebead-112">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebead-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="ebead-113">Remarks</span></span>  
 <span data-ttu-id="ebead-114">Ce comportement doit être utilisé uniquement avec la [\<webHttpBinding>](webhttpbinding.md) liaison standard ou l' [\<webMessageEncoding>](webmessageencoding.md) élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="ebead-114">This behavior should only be used in conjunction with either the [\<webHttpBinding>](webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="ebead-115">Pour plus d'informations sur ce comportement, consultez <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span><span class="sxs-lookup"><span data-stu-id="ebead-115">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebead-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ebead-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="ebead-117">Intégration d'AJAX et prise en charge de JSON</span><span class="sxs-lookup"><span data-stu-id="ebead-117">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttp>](webhttp.md)

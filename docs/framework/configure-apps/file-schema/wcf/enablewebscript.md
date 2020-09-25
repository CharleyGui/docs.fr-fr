---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 11378e6cc8cbe8e631fd77ab74c91a616099df52
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190083"
---
# \<enableWebScript>

<span data-ttu-id="e2cff-101">Cet élément active le comportement de point de terminaison qui permet de consommer le service à partir de pages web ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="e2cff-101">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<enableWebScript>**  
  
## <a name="syntax"></a><span data-ttu-id="e2cff-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2cff-102">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2cff-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e2cff-103">Attributes and Elements</span></span>  

 <span data-ttu-id="e2cff-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e2cff-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2cff-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="e2cff-105">Attributes</span></span>  

 <span data-ttu-id="e2cff-106">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e2cff-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e2cff-107">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e2cff-107">Child Elements</span></span>  

 <span data-ttu-id="e2cff-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e2cff-108">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e2cff-109">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e2cff-109">Parent Elements</span></span>  
  
|<span data-ttu-id="e2cff-110">Élément</span><span class="sxs-lookup"><span data-stu-id="e2cff-110">Element</span></span>|<span data-ttu-id="e2cff-111">Description</span><span class="sxs-lookup"><span data-stu-id="e2cff-111">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="e2cff-112">Spécifie le jeu de comportements du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="e2cff-112">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2cff-113">Notes</span><span class="sxs-lookup"><span data-stu-id="e2cff-113">Remarks</span></span>  

 <span data-ttu-id="e2cff-114">Ce comportement doit être utilisé uniquement avec la [\<webHttpBinding>](webhttpbinding.md) liaison standard ou l' [\<webMessageEncoding>](webmessageencoding.md) élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="e2cff-114">This behavior should only be used in conjunction with either the [\<webHttpBinding>](webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="e2cff-115">Pour plus d'informations sur ce comportement, consultez <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span><span class="sxs-lookup"><span data-stu-id="e2cff-115">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2cff-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2cff-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="e2cff-117">Intégration d'AJAX et prise en charge de JSON</span><span class="sxs-lookup"><span data-stu-id="e2cff-117">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttp>](webhttp.md)

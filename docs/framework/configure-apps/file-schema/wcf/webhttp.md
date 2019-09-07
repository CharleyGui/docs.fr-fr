---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 00644d248e6fb85d7cf712620e6ac74405e6b0c3
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399163"
---
# <a name="webhttp"></a><span data-ttu-id="63aed-101">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="63aed-101">\<webHttp></span></span>
<span data-ttu-id="63aed-102">Cet élément spécifie le <xref:System.ServiceModel.Description.WebHttpBehavior> d'un point de terminaison via la configuration.</span><span class="sxs-lookup"><span data-stu-id="63aed-102">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="63aed-103">Ce comportement, lorsqu’il est utilisé conjointement avec [ \<WebHttpBinding >](webhttpbinding.md) la liaison standard, active le modèle de programmation Web pour un service Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="63aed-103">This behavior, when used in conjunction with the [\<webHttpBinding>](webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
<span data-ttu-id="63aed-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="63aed-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="63aed-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="63aed-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="63aed-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="63aed-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="63aed-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="63aed-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="63aed-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="63aed-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="63aed-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Webhttp**</span><span class="sxs-lookup"><span data-stu-id="63aed-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttp>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63aed-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63aed-110">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="63aed-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="63aed-111">Attributes and Elements</span></span>  
 <span data-ttu-id="63aed-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="63aed-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="63aed-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="63aed-113">Attributes</span></span>  
  
|<span data-ttu-id="63aed-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="63aed-114">Attribute</span></span>|<span data-ttu-id="63aed-115">Description</span><span class="sxs-lookup"><span data-stu-id="63aed-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="63aed-116">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="63aed-116">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="63aed-117">Lorsque cette propriété a la valeur `true`, l'infrastructure WCF détermine le meilleur format à utiliser.</span><span class="sxs-lookup"><span data-stu-id="63aed-117">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="63aed-118">La sélection automatique du format est désactivée par défaut à des fins de compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="63aed-118">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="63aed-119">La sélection automatique du format peut être activée par programme ou par configuration.</span><span class="sxs-lookup"><span data-stu-id="63aed-119">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="63aed-120">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="63aed-120">defaultBodyStyle</span></span>|<span data-ttu-id="63aed-121">Spécifie le style du corps par défaut des messages retournés.</span><span class="sxs-lookup"><span data-stu-id="63aed-121">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="63aed-122">Pour plus d’informations, <xref:System.ServiceModel.Web.WebMessageBodyStyle> consultez et [mise en forme http Web WCF](../../../wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="63aed-122">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="63aed-123">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="63aed-123">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="63aed-124">Spécifie le format de réponse sortante par défaut des messages.</span><span class="sxs-lookup"><span data-stu-id="63aed-124">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="63aed-125">Pour plus d’informations, consultez [mise en forme http Web WCF](../../../wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="63aed-125">For more information, see [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="63aed-126">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="63aed-126">faultExceptionEnabled</span></span>|<span data-ttu-id="63aed-127">Obtient ou définit l’indicateur qui spécifie si FaultException est généré quand une erreur de serveur interne (code d’état HTTP : 500) se produit.</span><span class="sxs-lookup"><span data-stu-id="63aed-127">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="63aed-128">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="63aed-128">helpEnabled</span></span>|<span data-ttu-id="63aed-129">Obtient ou définit une valeur qui détermine si la page d'aide est activée.</span><span class="sxs-lookup"><span data-stu-id="63aed-129">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="63aed-130">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="63aed-130">Child Elements</span></span>  
 <span data-ttu-id="63aed-131">Aucun.</span><span class="sxs-lookup"><span data-stu-id="63aed-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="63aed-132">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="63aed-132">Parent Elements</span></span>  
  
|<span data-ttu-id="63aed-133">Élément</span><span class="sxs-lookup"><span data-stu-id="63aed-133">Element</span></span>|<span data-ttu-id="63aed-134">Description</span><span class="sxs-lookup"><span data-stu-id="63aed-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63aed-135">\<behavior></span><span class="sxs-lookup"><span data-stu-id="63aed-135">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="63aed-136">Spécifie le jeu de comportements du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="63aed-136">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="63aed-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63aed-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="63aed-138">Intégration d’AJAX et prise en charge de JSON</span><span class="sxs-lookup"><span data-stu-id="63aed-138">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="63aed-139">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="63aed-139">\<webHttpBinding></span></span>](webhttpbinding.md)

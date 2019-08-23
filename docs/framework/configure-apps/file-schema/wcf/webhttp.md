---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 366def5d0f4cc82b0ff0a5127701b0b5a6adb6a0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940502"
---
# <a name="webhttp"></a><span data-ttu-id="00a12-101">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="00a12-101">\<webHttp></span></span>
<span data-ttu-id="00a12-102">Cet élément spécifie le <xref:System.ServiceModel.Description.WebHttpBehavior> d'un point de terminaison via la configuration.</span><span class="sxs-lookup"><span data-stu-id="00a12-102">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="00a12-103">Ce comportement, lorsqu’il est utilisé conjointement avec [ \<WebHttpBinding >](webhttpbinding.md) la liaison standard, active le modèle de programmation Web pour un service Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="00a12-103">This behavior, when used in conjunction with the [\<webHttpBinding>](webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="00a12-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="00a12-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="00a12-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="00a12-105">\<behaviors></span></span>  
<span data-ttu-id="00a12-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="00a12-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="00a12-107">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="00a12-107">\<behavior></span></span>  
<span data-ttu-id="00a12-108">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="00a12-108">\<webHttp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00a12-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00a12-109">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00a12-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="00a12-110">Attributes and Elements</span></span>  
 <span data-ttu-id="00a12-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="00a12-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00a12-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="00a12-112">Attributes</span></span>  
  
|<span data-ttu-id="00a12-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="00a12-113">Attribute</span></span>|<span data-ttu-id="00a12-114">Description</span><span class="sxs-lookup"><span data-stu-id="00a12-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="00a12-115">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="00a12-115">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="00a12-116">Lorsque cette propriété a la valeur `true`, l'infrastructure WCF détermine le meilleur format à utiliser.</span><span class="sxs-lookup"><span data-stu-id="00a12-116">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="00a12-117">La sélection automatique du format est désactivée par défaut à des fins de compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="00a12-117">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="00a12-118">La sélection automatique du format peut être activée par programme ou par configuration.</span><span class="sxs-lookup"><span data-stu-id="00a12-118">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="00a12-119">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="00a12-119">defaultBodyStyle</span></span>|<span data-ttu-id="00a12-120">Spécifie le style du corps par défaut des messages retournés.</span><span class="sxs-lookup"><span data-stu-id="00a12-120">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="00a12-121">Pour plus d’informations, <xref:System.ServiceModel.Web.WebMessageBodyStyle> consultez et [mise en forme http Web WCF](../../../wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="00a12-121">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="00a12-122">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="00a12-122">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="00a12-123">Spécifie le format de réponse sortante par défaut des messages.</span><span class="sxs-lookup"><span data-stu-id="00a12-123">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="00a12-124">Pour plus d’informations, consultez [mise en forme http Web WCF](../../../wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="00a12-124">For more information, see [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="00a12-125">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="00a12-125">faultExceptionEnabled</span></span>|<span data-ttu-id="00a12-126">Obtient ou définit l’indicateur qui spécifie si FaultException est généré quand une erreur de serveur interne (code d’état HTTP : 500) se produit.</span><span class="sxs-lookup"><span data-stu-id="00a12-126">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="00a12-127">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="00a12-127">helpEnabled</span></span>|<span data-ttu-id="00a12-128">Obtient ou définit une valeur qui détermine si la page d'aide est activée.</span><span class="sxs-lookup"><span data-stu-id="00a12-128">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="00a12-129">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="00a12-129">Child Elements</span></span>  
 <span data-ttu-id="00a12-130">Aucun.</span><span class="sxs-lookup"><span data-stu-id="00a12-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="00a12-131">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="00a12-131">Parent Elements</span></span>  
  
|<span data-ttu-id="00a12-132">Élément</span><span class="sxs-lookup"><span data-stu-id="00a12-132">Element</span></span>|<span data-ttu-id="00a12-133">Description</span><span class="sxs-lookup"><span data-stu-id="00a12-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="00a12-134">\<behavior></span><span class="sxs-lookup"><span data-stu-id="00a12-134">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="00a12-135">Spécifie le jeu de comportements du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="00a12-135">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="00a12-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00a12-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="00a12-137">Intégration d’AJAX et prise en charge de JSON</span><span class="sxs-lookup"><span data-stu-id="00a12-137">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="00a12-138">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="00a12-138">\<webHttpBinding></span></span>](webhttpbinding.md)

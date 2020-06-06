---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 00644d248e6fb85d7cf712620e6ac74405e6b0c3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399163"
---
# \<webHttp>
<span data-ttu-id="3c267-101">Cet élément spécifie le <xref:System.ServiceModel.Description.WebHttpBehavior> d'un point de terminaison via la configuration.</span><span class="sxs-lookup"><span data-stu-id="3c267-101">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="3c267-102">Ce comportement, lorsqu’il est utilisé conjointement avec la [\<webHttpBinding>](webhttpbinding.md) liaison standard, active le modèle de programmation Web pour un service Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3c267-102">This behavior, when used in conjunction with the [\<webHttpBinding>](webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttp>**  
  
## <a name="syntax"></a><span data-ttu-id="3c267-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c267-103">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3c267-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3c267-104">Attributes and Elements</span></span>  
 <span data-ttu-id="3c267-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3c267-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3c267-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="3c267-106">Attributes</span></span>  
  
|<span data-ttu-id="3c267-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="3c267-107">Attribute</span></span>|<span data-ttu-id="3c267-108">Description</span><span class="sxs-lookup"><span data-stu-id="3c267-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3c267-109">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="3c267-109">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="3c267-110">Lorsque cette propriété a la valeur `true`, l'infrastructure WCF détermine le meilleur format à utiliser.</span><span class="sxs-lookup"><span data-stu-id="3c267-110">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="3c267-111">La sélection automatique du format est désactivée par défaut à des fins de compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="3c267-111">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="3c267-112">La sélection automatique du format peut être activée par programme ou par configuration.</span><span class="sxs-lookup"><span data-stu-id="3c267-112">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="3c267-113">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="3c267-113">defaultBodyStyle</span></span>|<span data-ttu-id="3c267-114">Spécifie le style du corps par défaut des messages retournés.</span><span class="sxs-lookup"><span data-stu-id="3c267-114">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="3c267-115">Pour plus d’informations, consultez <xref:System.ServiceModel.Web.WebMessageBodyStyle> et [mise en forme http Web WCF](../../../wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="3c267-115">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="3c267-116">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="3c267-116">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="3c267-117">Spécifie le format de réponse sortante par défaut des messages.</span><span class="sxs-lookup"><span data-stu-id="3c267-117">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="3c267-118">Pour plus d’informations, consultez [mise en forme http Web WCF](../../../wcf/feature-details/wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="3c267-118">For more information, see [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="3c267-119">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="3c267-119">faultExceptionEnabled</span></span>|<span data-ttu-id="3c267-120">Obtient ou définit l'indicateur qui spécifie si FaultException est généré lorsqu'une erreur de serveur interne (code d'état HTTP: 500) se produit.</span><span class="sxs-lookup"><span data-stu-id="3c267-120">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="3c267-121">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="3c267-121">helpEnabled</span></span>|<span data-ttu-id="3c267-122">Obtient ou définit une valeur qui détermine si la page d'aide est activée.</span><span class="sxs-lookup"><span data-stu-id="3c267-122">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3c267-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3c267-123">Child Elements</span></span>  
 <span data-ttu-id="3c267-124">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3c267-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3c267-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3c267-125">Parent Elements</span></span>  
  
|<span data-ttu-id="3c267-126">Élément</span><span class="sxs-lookup"><span data-stu-id="3c267-126">Element</span></span>|<span data-ttu-id="3c267-127">Description</span><span class="sxs-lookup"><span data-stu-id="3c267-127">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="3c267-128">Spécifie le jeu de comportements du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="3c267-128">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3c267-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c267-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="3c267-130">Intégration d'AJAX et prise en charge de JSON</span><span class="sxs-lookup"><span data-stu-id="3c267-130">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttpBinding>](webhttpbinding.md)

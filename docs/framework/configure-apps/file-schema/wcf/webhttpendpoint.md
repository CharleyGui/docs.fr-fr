---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 8d4f55fd5b51ea77839b7fdbb930e937f5700417
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854799"
---
# <a name="webhttpendpoint"></a><span data-ttu-id="c5c00-101">\<webHttpEndpoint></span><span class="sxs-lookup"><span data-stu-id="c5c00-101">\<webHttpEndpoint></span></span>
<span data-ttu-id="c5c00-102">Cet élément de configuration définit un point de terminaison standard avec une liaison [ \<WebHttpBinding >](webhttpbinding.md) fixe qui ajoute automatiquement le comportement de [ \<> Webhttp](webhttp.md) .</span><span class="sxs-lookup"><span data-stu-id="c5c00-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<webHttp>](webhttp.md) behavior.</span></span> <span data-ttu-id="c5c00-103">Utilisez ce point de terminaison lors de l'écriture d'un service REST.</span><span class="sxs-lookup"><span data-stu-id="c5c00-103">Use this endpoint when writing a REST service.</span></span>  
  
<span data-ttu-id="c5c00-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c5c00-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c5c00-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c5c00-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c5c00-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="c5c00-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="c5c00-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<webHttpEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="c5c00-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttpEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5c00-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5c00-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint automaticFormatSelectionEnabled="String"
                        defaultOutgoingResponseFormat="Xml/Json"
                        helpEnabled="Boolean"
                        webEndpointType="String" />
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5c00-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c5c00-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c5c00-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c5c00-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5c00-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="c5c00-111">Attributes</span></span>  
  
|<span data-ttu-id="c5c00-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="c5c00-112">Attribute</span></span>|<span data-ttu-id="c5c00-113">Description</span><span class="sxs-lookup"><span data-stu-id="c5c00-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c5c00-114">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="c5c00-114">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="c5c00-115">Valeur booléenne qui indique si la sélection automatique du format est activée.</span><span class="sxs-lookup"><span data-stu-id="c5c00-115">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="c5c00-116">Lorsque la sélection automatique du format est activée, l'infrastructure analyse l'en-tête `Accept` du message de demande et détermine le format de réponse le plus approprié.</span><span class="sxs-lookup"><span data-stu-id="c5c00-116">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="c5c00-117">Si l'en-tête `Accept` ne spécifie pas de format de réponse approprié, l'infrastructure utilise le `Content-Type` du message de demande ou le format de réponse par défaut de l'opération.</span><span class="sxs-lookup"><span data-stu-id="c5c00-117">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="c5c00-118">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="c5c00-118">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="c5c00-119">Attribut qui spécifie le format de réponse sortant par défaut.</span><span class="sxs-lookup"><span data-stu-id="c5c00-119">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="c5c00-120">Cet attribut est de type <xref:System.ServiceModel.Web.WebMessageFormat>.</span><span class="sxs-lookup"><span data-stu-id="c5c00-120">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="c5c00-121">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="c5c00-121">helpEnabled</span></span>|<span data-ttu-id="c5c00-122">Valeur booléenne qui indique si la page d'aide HTTP est activée pour le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="c5c00-122">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="c5c00-123">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="c5c00-123">webEndpointType</span></span>|<span data-ttu-id="c5c00-124">Chaîne qui spécifie le type du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="c5c00-124">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5c00-125">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c5c00-125">Child Elements</span></span>  
 <span data-ttu-id="c5c00-126">Aucun.</span><span class="sxs-lookup"><span data-stu-id="c5c00-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c5c00-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c5c00-127">Parent Elements</span></span>  
  
|<span data-ttu-id="c5c00-128">Élément</span><span class="sxs-lookup"><span data-stu-id="c5c00-128">Element</span></span>|<span data-ttu-id="c5c00-129">Description</span><span class="sxs-lookup"><span data-stu-id="c5c00-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5c00-130">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="c5c00-130">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="c5c00-131">Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés (adresse, liaison, contrat) sont fixes.</span><span class="sxs-lookup"><span data-stu-id="c5c00-131">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c5c00-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5c00-132">See also</span></span>

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>

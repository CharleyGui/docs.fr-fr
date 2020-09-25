---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 3282871bf8dbd25726ada7003d3066b9a42e2366
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177980"
---
# \<webHttpEndpoint>

<span data-ttu-id="1256b-101">Cet élément de configuration définit un point de terminaison standard avec une [\<webHttpBinding>](webhttpbinding.md) liaison fixe qui ajoute automatiquement le [\<webHttp>](webhttp.md) comportement.</span><span class="sxs-lookup"><span data-stu-id="1256b-101">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<webHttp>](webhttp.md) behavior.</span></span> <span data-ttu-id="1256b-102">Utilisez ce point de terminaison lors de l'écriture d'un service REST.</span><span class="sxs-lookup"><span data-stu-id="1256b-102">Use this endpoint when writing a REST service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttpEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="1256b-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1256b-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1256b-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1256b-104">Attributes and Elements</span></span>  

 <span data-ttu-id="1256b-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1256b-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1256b-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="1256b-106">Attributes</span></span>  
  
|<span data-ttu-id="1256b-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="1256b-107">Attribute</span></span>|<span data-ttu-id="1256b-108">Description</span><span class="sxs-lookup"><span data-stu-id="1256b-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1256b-109">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="1256b-109">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="1256b-110">Valeur booléenne qui indique si la sélection automatique du format est activée.</span><span class="sxs-lookup"><span data-stu-id="1256b-110">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="1256b-111">Lorsque la sélection automatique du format est activée, l'infrastructure analyse l'en-tête `Accept` du message de demande et détermine le format de réponse le plus approprié.</span><span class="sxs-lookup"><span data-stu-id="1256b-111">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="1256b-112">Si l'en-tête `Accept` ne spécifie pas de format de réponse approprié, l'infrastructure utilise le `Content-Type` du message de demande ou le format de réponse par défaut de l'opération.</span><span class="sxs-lookup"><span data-stu-id="1256b-112">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="1256b-113">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="1256b-113">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="1256b-114">Attribut qui spécifie le format de réponse sortant par défaut.</span><span class="sxs-lookup"><span data-stu-id="1256b-114">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="1256b-115">Cet attribut est de type <xref:System.ServiceModel.Web.WebMessageFormat>.</span><span class="sxs-lookup"><span data-stu-id="1256b-115">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="1256b-116">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="1256b-116">helpEnabled</span></span>|<span data-ttu-id="1256b-117">Valeur booléenne qui indique si la page d'aide HTTP est activée pour le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="1256b-117">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="1256b-118">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="1256b-118">webEndpointType</span></span>|<span data-ttu-id="1256b-119">Chaîne qui spécifie le type du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="1256b-119">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1256b-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1256b-120">Child Elements</span></span>  

 <span data-ttu-id="1256b-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="1256b-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1256b-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1256b-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1256b-123">Élément</span><span class="sxs-lookup"><span data-stu-id="1256b-123">Element</span></span>|<span data-ttu-id="1256b-124">Description</span><span class="sxs-lookup"><span data-stu-id="1256b-124">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="1256b-125">Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés (adresse, liaison, contrat) sont fixes.</span><span class="sxs-lookup"><span data-stu-id="1256b-125">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1256b-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1256b-126">See also</span></span>

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>

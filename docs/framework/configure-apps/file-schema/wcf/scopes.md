---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 57e9e19025db5e1fa588f073fdf30de09837a25d
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399937"
---
# <a name="scopes"></a><span data-ttu-id="e8ed7-101">\<scopes></span><span class="sxs-lookup"><span data-stu-id="e8ed7-101">\<scopes></span></span>
<span data-ttu-id="e8ed7-102">Contient une collection d’éléments de configuration qui spécifient des URI de portée personnalisés à utiliser pour filtrer des points de terminaison de service pendant la requête.</span><span class="sxs-lookup"><span data-stu-id="e8ed7-102">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="e8ed7-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e8ed7-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e8ed7-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e8ed7-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e8ed7-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e8ed7-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="e8ed7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e8ed7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="e8ed7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e8ed7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="e8ed7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointDiscovery >** ](endpointdiscovery.md)</span><span class="sxs-lookup"><span data-stu-id="e8ed7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)</span></span>\
<span data-ttu-id="e8ed7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<étendues >**</span><span class="sxs-lookup"><span data-stu-id="e8ed7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<scopes>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8ed7-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8ed7-110">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI" />
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8ed7-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e8ed7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e8ed7-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e8ed7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8ed7-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="e8ed7-113">Attributes</span></span>  
 <span data-ttu-id="e8ed7-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e8ed7-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e8ed7-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e8ed7-115">Child Elements</span></span>  
  
|<span data-ttu-id="e8ed7-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="e8ed7-116">Attribute</span></span>|<span data-ttu-id="e8ed7-117">Description</span><span class="sxs-lookup"><span data-stu-id="e8ed7-117">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="e8ed7-118">\<add></span><span class="sxs-lookup"><span data-stu-id="e8ed7-118">\<add></span></span>](add-of-scopes.md)|<span data-ttu-id="e8ed7-119">Ajoute les informations de portée du point de terminaison à utiliser lors de la mise en correspondance des critères de recherche des services.</span><span class="sxs-lookup"><span data-stu-id="e8ed7-119">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e8ed7-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e8ed7-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e8ed7-121">Élément</span><span class="sxs-lookup"><span data-stu-id="e8ed7-121">Element</span></span>|<span data-ttu-id="e8ed7-122">Description</span><span class="sxs-lookup"><span data-stu-id="e8ed7-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e8ed7-123">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="e8ed7-123">\<endpointDiscovery></span></span>](endpointdiscovery.md)|<span data-ttu-id="e8ed7-124">Spécifie les différents paramètres de découverte d’un point de terminaison, tels que la fonctionnalité de découverte, les portées et toutes les extensions personnalisées de ses métadonnées.</span><span class="sxs-lookup"><span data-stu-id="e8ed7-124">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e8ed7-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8ed7-125">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>

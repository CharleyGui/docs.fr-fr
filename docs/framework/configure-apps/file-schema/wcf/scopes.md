---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: dd6513930798e9e1ab263f75c9350511c2dcdcd5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935181"
---
# <a name="scopes"></a><span data-ttu-id="cf125-101">\<scopes></span><span class="sxs-lookup"><span data-stu-id="cf125-101">\<scopes></span></span>
<span data-ttu-id="cf125-102">Contient une collection d’éléments de configuration qui spécifient des URI de portée personnalisés à utiliser pour filtrer des points de terminaison de service pendant la requête.</span><span class="sxs-lookup"><span data-stu-id="cf125-102">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="cf125-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cf125-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="cf125-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="cf125-104">\<behaviors></span></span>  
<span data-ttu-id="cf125-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="cf125-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="cf125-106">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="cf125-106">\<behavior></span></span>  
<span data-ttu-id="cf125-107">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="cf125-107">\<endpointDiscovery></span></span>  
<span data-ttu-id="cf125-108">\<scopes></span><span class="sxs-lookup"><span data-stu-id="cf125-108">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf125-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf125-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf125-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="cf125-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cf125-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="cf125-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf125-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="cf125-112">Attributes</span></span>  
 <span data-ttu-id="cf125-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="cf125-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cf125-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cf125-114">Child Elements</span></span>  
  
|<span data-ttu-id="cf125-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="cf125-115">Attribute</span></span>|<span data-ttu-id="cf125-116">Description</span><span class="sxs-lookup"><span data-stu-id="cf125-116">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="cf125-117">\<add></span><span class="sxs-lookup"><span data-stu-id="cf125-117">\<add></span></span>](add-of-scopes.md)|<span data-ttu-id="cf125-118">Ajoute les informations de portée du point de terminaison à utiliser lors de la mise en correspondance des critères de recherche des services.</span><span class="sxs-lookup"><span data-stu-id="cf125-118">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cf125-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cf125-119">Parent Elements</span></span>  
  
|<span data-ttu-id="cf125-120">Élément</span><span class="sxs-lookup"><span data-stu-id="cf125-120">Element</span></span>|<span data-ttu-id="cf125-121">Description</span><span class="sxs-lookup"><span data-stu-id="cf125-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cf125-122">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="cf125-122">\<endpointDiscovery></span></span>](endpointdiscovery.md)|<span data-ttu-id="cf125-123">Spécifie les différents paramètres de découverte d’un point de terminaison, tels que la fonctionnalité de découverte, les portées et toutes les extensions personnalisées de ses métadonnées.</span><span class="sxs-lookup"><span data-stu-id="cf125-123">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cf125-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf125-124">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>

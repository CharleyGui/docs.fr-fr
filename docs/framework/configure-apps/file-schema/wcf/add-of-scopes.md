---
title: <add> de <scopes>
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: bcde6b18c34dccf1716c809dddeb45b1b4da90f0
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398308"
---
# <a name="add-of-scopes"></a><span data-ttu-id="f63cb-102">\<Ajouter > d' \<étendues ></span><span class="sxs-lookup"><span data-stu-id="f63cb-102">\<add> of \<scopes></span></span>
<span data-ttu-id="f63cb-103">Ajoute un URI de portée personnalisé qui permet de filtrer les points de terminaison de service pendant la requête.</span><span class="sxs-lookup"><span data-stu-id="f63cb-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="f63cb-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f63cb-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f63cb-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f63cb-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f63cb-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f63cb-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="f63cb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f63cb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="f63cb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f63cb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="f63cb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointDiscovery >** ](endpointdiscovery.md)</span><span class="sxs-lookup"><span data-stu-id="f63cb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)</span></span>\
<span data-ttu-id="f63cb-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<étendues >** ](scopes.md)</span><span class="sxs-lookup"><span data-stu-id="f63cb-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<scopes>**](scopes.md)</span></span>\
<span data-ttu-id="f63cb-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Ajouter >**</span><span class="sxs-lookup"><span data-stu-id="f63cb-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f63cb-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f63cb-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f63cb-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f63cb-113">Attributes and Elements</span></span>  
 <span data-ttu-id="f63cb-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f63cb-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f63cb-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="f63cb-115">Attributes</span></span>  
  
|<span data-ttu-id="f63cb-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="f63cb-116">Attribute</span></span>|<span data-ttu-id="f63cb-117">Description</span><span class="sxs-lookup"><span data-stu-id="f63cb-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f63cb-118">scope</span><span class="sxs-lookup"><span data-stu-id="f63cb-118">scope</span></span>|<span data-ttu-id="f63cb-119">URI qui contient les informations de portée du point de terminaison à utiliser lors de la mise en correspondance des critères de recherche des services.</span><span class="sxs-lookup"><span data-stu-id="f63cb-119">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f63cb-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f63cb-120">Child Elements</span></span>  
 <span data-ttu-id="f63cb-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f63cb-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f63cb-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f63cb-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f63cb-123">Élément</span><span class="sxs-lookup"><span data-stu-id="f63cb-123">Element</span></span>|<span data-ttu-id="f63cb-124">Description</span><span class="sxs-lookup"><span data-stu-id="f63cb-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f63cb-125">\<scopes></span><span class="sxs-lookup"><span data-stu-id="f63cb-125">\<scopes></span></span>](scopes.md)|<span data-ttu-id="f63cb-126">Contient une collection d’éléments de configuration qui spécifient des URI de portée personnalisés à utiliser pour filtrer des points de terminaison de service pendant la requête.</span><span class="sxs-lookup"><span data-stu-id="f63cb-126">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f63cb-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f63cb-127">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>

---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: 5e586437e3b269d361c254744e820ee8e8c0ca0a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400401"
---
# <a name="discoveryclient"></a><span data-ttu-id="ea461-101">\<discoveryClient></span><span class="sxs-lookup"><span data-stu-id="ea461-101">\<discoveryClient></span></span>
<span data-ttu-id="ea461-102">Élément de configuration qui crée une liaison personnalisée permettant à une application cliente de rechercher automatiquement un service détectable et de trouver son adresse au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="ea461-102">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="ea461-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ea461-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ea461-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ea461-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ea461-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="ea461-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="ea461-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="ea461-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="ea461-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="ea461-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="ea461-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<discoveryClient >**</span><span class="sxs-lookup"><span data-stu-id="ea461-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClient>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea461-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea461-109">Syntax</span></span>  
  
```xml  
<discoveryClient discoveryEndpoint="String">
  <findCriteria duration="TimeSpan"
                maxResults="Integer"
                scopeMatchBy="Uri">
    <contractTypeNames>
      <add name="String"
           namespace="String" />
    </contractTypeNames>
    <extensions />
    <scopes>
      <add scope="URI"/>
    </scopes>
  </findCriteria>
</discoveryClient>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ea461-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ea461-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ea461-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ea461-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ea461-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="ea461-112">Attributes</span></span>  
  
|<span data-ttu-id="ea461-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="ea461-113">Attribute</span></span>|<span data-ttu-id="ea461-114">Description</span><span class="sxs-lookup"><span data-stu-id="ea461-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ea461-115">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="ea461-115">discoveryEndpoint</span></span>|<span data-ttu-id="ea461-116">Chaîne qui contient le nom du point de terminaison de découverte permettant à une application cliente de rechercher automatiquement un service détectable et de trouver son adresse au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="ea461-116">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ea461-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ea461-117">Child Elements</span></span>  
  
|<span data-ttu-id="ea461-118">Élément</span><span class="sxs-lookup"><span data-stu-id="ea461-118">Element</span></span>|<span data-ttu-id="ea461-119">Description</span><span class="sxs-lookup"><span data-stu-id="ea461-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ea461-120">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="ea461-120">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="ea461-121">Élément de configuration qui fournit un jeu de critères utilisé par une application cliente pour rechercher un service de découverte.</span><span class="sxs-lookup"><span data-stu-id="ea461-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="ea461-122">Vous pouvez regrouper les critères dans des critères de recherche (en spécifiant les services que vous recherchez) et rechercher les critères de fin (la durée de la recherche en dernier).</span><span class="sxs-lookup"><span data-stu-id="ea461-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ea461-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ea461-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ea461-124">Élément</span><span class="sxs-lookup"><span data-stu-id="ea461-124">Element</span></span>|<span data-ttu-id="ea461-125">Description</span><span class="sxs-lookup"><span data-stu-id="ea461-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ea461-126">\<binding></span><span class="sxs-lookup"><span data-stu-id="ea461-126">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="ea461-127">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="ea461-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ea461-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea461-128">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>

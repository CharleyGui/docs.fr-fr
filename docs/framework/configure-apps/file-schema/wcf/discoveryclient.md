---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: 71305720cad0206ec3dabb1863e2f1cd72eb85f0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739032"
---
# <a name="discoveryclient"></a><span data-ttu-id="276df-101">\<discoveryClient ></span><span class="sxs-lookup"><span data-stu-id="276df-101">\<discoveryClient></span></span>
<span data-ttu-id="276df-102">Élément de configuration qui crée une liaison personnalisée permettant à une application cliente de rechercher automatiquement un service détectable et de trouver son adresse au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="276df-102">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="276df-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="276df-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="276df-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="276df-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="276df-105">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<</span><span class="sxs-lookup"><span data-stu-id="276df-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\</span></span>
<span data-ttu-id="276df-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="276df-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="276df-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\< \**\**</span><span class="sxs-lookup"><span data-stu-id="276df-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\</span></span>
<span data-ttu-id="276df-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**discoveryClient >**</span><span class="sxs-lookup"><span data-stu-id="276df-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClient>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="276df-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="276df-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="276df-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="276df-110">Attributes and Elements</span></span>  
 <span data-ttu-id="276df-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="276df-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="276df-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="276df-112">Attributes</span></span>  
  
|<span data-ttu-id="276df-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="276df-113">Attribute</span></span>|<span data-ttu-id="276df-114">Description</span><span class="sxs-lookup"><span data-stu-id="276df-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="276df-115">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="276df-115">discoveryEndpoint</span></span>|<span data-ttu-id="276df-116">Chaîne qui contient le nom du point de terminaison de découverte permettant à une application cliente de rechercher automatiquement un service détectable et de trouver son adresse au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="276df-116">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="276df-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="276df-117">Child Elements</span></span>  
  
|<span data-ttu-id="276df-118">Élément</span><span class="sxs-lookup"><span data-stu-id="276df-118">Element</span></span>|<span data-ttu-id="276df-119">Description</span><span class="sxs-lookup"><span data-stu-id="276df-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="276df-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="276df-120">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="276df-121">Élément de configuration qui fournit un jeu de critères utilisé par une application cliente pour rechercher un service de découverte.</span><span class="sxs-lookup"><span data-stu-id="276df-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="276df-122">Vous pouvez regrouper les critères dans des critères de recherche (en spécifiant les services que vous recherchez) et rechercher les critères de fin (la durée de la recherche en dernier).</span><span class="sxs-lookup"><span data-stu-id="276df-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="276df-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="276df-123">Parent Elements</span></span>  
  
|<span data-ttu-id="276df-124">Élément</span><span class="sxs-lookup"><span data-stu-id="276df-124">Element</span></span>|<span data-ttu-id="276df-125">Description</span><span class="sxs-lookup"><span data-stu-id="276df-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="276df-126">liaison de \<</span><span class="sxs-lookup"><span data-stu-id="276df-126">\<binding></span></span>](bindings.md)|<span data-ttu-id="276df-127">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="276df-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="276df-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="276df-128">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>

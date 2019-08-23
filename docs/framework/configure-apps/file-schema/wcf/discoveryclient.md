---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: f9d7e3a4957d2a8f30724f0bfc04e58a57fc5f7d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919273"
---
# <a name="discoveryclient"></a><span data-ttu-id="7336f-101">\<discoveryClient></span><span class="sxs-lookup"><span data-stu-id="7336f-101">\<discoveryClient></span></span>
<span data-ttu-id="7336f-102">Élément de configuration qui crée une liaison personnalisée permettant à une application cliente de rechercher automatiquement un service détectable et de trouver son adresse au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="7336f-102">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="7336f-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7336f-103">\<system.serviceModel></span></span>  
<span data-ttu-id="7336f-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="7336f-104">\<bindings></span></span>  
<span data-ttu-id="7336f-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="7336f-105">\<customBinding></span></span>  
<span data-ttu-id="7336f-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="7336f-106">\<binding></span></span>  
<span data-ttu-id="7336f-107">\<discoveryClient></span><span class="sxs-lookup"><span data-stu-id="7336f-107">\<discoveryClient></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7336f-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7336f-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7336f-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7336f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7336f-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7336f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7336f-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="7336f-111">Attributes</span></span>  
  
|<span data-ttu-id="7336f-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="7336f-112">Attribute</span></span>|<span data-ttu-id="7336f-113">Description</span><span class="sxs-lookup"><span data-stu-id="7336f-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7336f-114">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="7336f-114">discoveryEndpoint</span></span>|<span data-ttu-id="7336f-115">Chaîne qui contient le nom du point de terminaison de découverte permettant à une application cliente de rechercher automatiquement un service détectable et de trouver son adresse au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="7336f-115">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7336f-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7336f-116">Child Elements</span></span>  
  
|<span data-ttu-id="7336f-117">Élément</span><span class="sxs-lookup"><span data-stu-id="7336f-117">Element</span></span>|<span data-ttu-id="7336f-118">Description</span><span class="sxs-lookup"><span data-stu-id="7336f-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7336f-119">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="7336f-119">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="7336f-120">Élément de configuration qui fournit un jeu de critères utilisé par une application cliente pour rechercher un service de découverte.</span><span class="sxs-lookup"><span data-stu-id="7336f-120">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="7336f-121">Vous pouvez regrouper les critères dans des critères de recherche (en spécifiant les services que vous recherchez) et rechercher les critères de fin (la durée de la recherche en dernier).</span><span class="sxs-lookup"><span data-stu-id="7336f-121">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7336f-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7336f-122">Parent Elements</span></span>  
  
|<span data-ttu-id="7336f-123">Élément</span><span class="sxs-lookup"><span data-stu-id="7336f-123">Element</span></span>|<span data-ttu-id="7336f-124">Description</span><span class="sxs-lookup"><span data-stu-id="7336f-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7336f-125">\<binding></span><span class="sxs-lookup"><span data-stu-id="7336f-125">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="7336f-126">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="7336f-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7336f-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7336f-127">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>

---
title: <add> de <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 690fd07159e07b7e037f7330b31fdcba423e80f9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920127"
---
# <a name="add-of-entries"></a><span data-ttu-id="0481c-102">\<Ajouter > d' \<entrées ></span><span class="sxs-lookup"><span data-stu-id="0481c-102">\<add> of \<entries></span></span>
<span data-ttu-id="0481c-103">Représente une entrée de routage qui mappe un filtre à un point de terminaison client défini précédemment.</span><span class="sxs-lookup"><span data-stu-id="0481c-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="0481c-104">Les messages correspondant à ce filtre sont envoyés à cette destination.</span><span class="sxs-lookup"><span data-stu-id="0481c-104">Messages matching this filter will be sent to this destination.</span></span>  
  
 <span data-ttu-id="0481c-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0481c-105">\<system.serviceModel></span></span>  
<span data-ttu-id="0481c-106">\<routing></span><span class="sxs-lookup"><span data-stu-id="0481c-106">\<routing></span></span>  
<span data-ttu-id="0481c-107">\<filterTables></span><span class="sxs-lookup"><span data-stu-id="0481c-107">\<filterTables></span></span>  
<span data-ttu-id="0481c-108">\<filterTable></span><span class="sxs-lookup"><span data-stu-id="0481c-108">\<filterTable></span></span>  
<span data-ttu-id="0481c-109">\<entries></span><span class="sxs-lookup"><span data-stu-id="0481c-109">\<entries></span></span>  
<span data-ttu-id="0481c-110">\<add></span><span class="sxs-lookup"><span data-stu-id="0481c-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0481c-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0481c-111">Syntax</span></span>  
  
```xml  
<routing>
  <filterTables>
    <filterTable name="String">
      <entries>
        <add backupList="String"
             endpointName="String"
             filterName="String"
             priority="Integer" />
      </entries>
    </filterTable>
  </filterTables>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0481c-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0481c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="0481c-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0481c-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0481c-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="0481c-114">Attributes</span></span>  
  
|<span data-ttu-id="0481c-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="0481c-115">Attribute</span></span>|<span data-ttu-id="0481c-116">Description</span><span class="sxs-lookup"><span data-stu-id="0481c-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0481c-117">backupList</span><span class="sxs-lookup"><span data-stu-id="0481c-117">backupList</span></span>|<span data-ttu-id="0481c-118">Chaîne qui spécifie une référence à une liste de sauvegarde de points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="0481c-118">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="0481c-119">endpoint</span><span class="sxs-lookup"><span data-stu-id="0481c-119">endpoint</span></span>|<span data-ttu-id="0481c-120">Chaîne qui spécifie une référence à un point de terminaison client qui reçoit les messages correspondant au filtre indiqué par l'attribut `filterName`.</span><span class="sxs-lookup"><span data-stu-id="0481c-120">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="0481c-121">filterName</span><span class="sxs-lookup"><span data-stu-id="0481c-121">filterName</span></span>|<span data-ttu-id="0481c-122">Chaîne qui spécifie une référence à un élément de filtre.</span><span class="sxs-lookup"><span data-stu-id="0481c-122">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="0481c-123">priority</span><span class="sxs-lookup"><span data-stu-id="0481c-123">priority</span></span>|<span data-ttu-id="0481c-124">Entier qui spécifie la priorité de cette entrée.</span><span class="sxs-lookup"><span data-stu-id="0481c-124">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="0481c-125">Les entrées dans la table de routage sont évaluées selon leur priorité, 0 correspondant à la priorité la plus basse.</span><span class="sxs-lookup"><span data-stu-id="0481c-125">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="0481c-126">Toutes les entrées d'une priorité donnée sont évaluées simultanément, si aucune entrée correspondante n'est trouvée pour la priorité actuelle, le niveau de priorité suivant est évalué.</span><span class="sxs-lookup"><span data-stu-id="0481c-126">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="0481c-127">Cette valeur est facultative.</span><span class="sxs-lookup"><span data-stu-id="0481c-127">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0481c-128">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0481c-128">Child Elements</span></span>  
 <span data-ttu-id="0481c-129">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0481c-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0481c-130">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0481c-130">Parent Elements</span></span>  
  
|<span data-ttu-id="0481c-131">Élément</span><span class="sxs-lookup"><span data-stu-id="0481c-131">Element</span></span>|<span data-ttu-id="0481c-132">Description</span><span class="sxs-lookup"><span data-stu-id="0481c-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0481c-133">\<routing></span><span class="sxs-lookup"><span data-stu-id="0481c-133">\<routing></span></span>](routing.md)|<span data-ttu-id="0481c-134">Section de configuration qui contient les entrées de mappage de routage.</span><span class="sxs-lookup"><span data-stu-id="0481c-134">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0481c-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0481c-135">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>

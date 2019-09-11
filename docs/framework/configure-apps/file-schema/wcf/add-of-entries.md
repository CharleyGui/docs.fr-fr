---
title: <add> de <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 23b0a825ea593f85ade870d5b93367571eaa3ec0
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850507"
---
# <a name="add-of-entries"></a><span data-ttu-id="52142-102">\<Ajouter > d' \<entrées ></span><span class="sxs-lookup"><span data-stu-id="52142-102">\<add> of \<entries></span></span>
<span data-ttu-id="52142-103">Représente une entrée de routage qui mappe un filtre à un point de terminaison client défini précédemment.</span><span class="sxs-lookup"><span data-stu-id="52142-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="52142-104">Les messages correspondant à ce filtre sont envoyés à cette destination.</span><span class="sxs-lookup"><span data-stu-id="52142-104">Messages matching this filter will be sent to this destination.</span></span>  
  
<span data-ttu-id="52142-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="52142-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="52142-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="52142-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="52142-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de routage**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="52142-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="52142-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<filterTables >** ](filtertables.md)</span><span class="sxs-lookup"><span data-stu-id="52142-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)</span></span>\
<span data-ttu-id="52142-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<filterTable >** ](filtertable.md)</span><span class="sxs-lookup"><span data-stu-id="52142-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)</span></span>\
<span data-ttu-id="52142-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<entrées >** ](entries.md)</span><span class="sxs-lookup"><span data-stu-id="52142-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<entries>**](entries.md)</span></span>\
<span data-ttu-id="52142-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Ajouter >**</span><span class="sxs-lookup"><span data-stu-id="52142-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52142-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52142-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="52142-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="52142-113">Attributes and Elements</span></span>  
 <span data-ttu-id="52142-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="52142-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="52142-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="52142-115">Attributes</span></span>  
  
|<span data-ttu-id="52142-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="52142-116">Attribute</span></span>|<span data-ttu-id="52142-117">Description</span><span class="sxs-lookup"><span data-stu-id="52142-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="52142-118">backupList</span><span class="sxs-lookup"><span data-stu-id="52142-118">backupList</span></span>|<span data-ttu-id="52142-119">Chaîne qui spécifie une référence à une liste de sauvegarde de points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="52142-119">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="52142-120">endpoint</span><span class="sxs-lookup"><span data-stu-id="52142-120">endpoint</span></span>|<span data-ttu-id="52142-121">Chaîne qui spécifie une référence à un point de terminaison client qui reçoit les messages correspondant au filtre indiqué par l'attribut `filterName`.</span><span class="sxs-lookup"><span data-stu-id="52142-121">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="52142-122">filterName</span><span class="sxs-lookup"><span data-stu-id="52142-122">filterName</span></span>|<span data-ttu-id="52142-123">Chaîne qui spécifie une référence à un élément de filtre.</span><span class="sxs-lookup"><span data-stu-id="52142-123">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="52142-124">priority</span><span class="sxs-lookup"><span data-stu-id="52142-124">priority</span></span>|<span data-ttu-id="52142-125">Entier qui spécifie la priorité de cette entrée.</span><span class="sxs-lookup"><span data-stu-id="52142-125">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="52142-126">Les entrées dans la table de routage sont évaluées selon leur priorité, 0 correspondant à la priorité la plus basse.</span><span class="sxs-lookup"><span data-stu-id="52142-126">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="52142-127">Toutes les entrées d'une priorité donnée sont évaluées simultanément, si aucune entrée correspondante n'est trouvée pour la priorité actuelle, le niveau de priorité suivant est évalué.</span><span class="sxs-lookup"><span data-stu-id="52142-127">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="52142-128">Cette valeur est facultative.</span><span class="sxs-lookup"><span data-stu-id="52142-128">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="52142-129">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="52142-129">Child Elements</span></span>  
 <span data-ttu-id="52142-130">Aucun.</span><span class="sxs-lookup"><span data-stu-id="52142-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="52142-131">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="52142-131">Parent Elements</span></span>  
  
|<span data-ttu-id="52142-132">Élément</span><span class="sxs-lookup"><span data-stu-id="52142-132">Element</span></span>|<span data-ttu-id="52142-133">Description</span><span class="sxs-lookup"><span data-stu-id="52142-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="52142-134">\<routing></span><span class="sxs-lookup"><span data-stu-id="52142-134">\<routing></span></span>](routing.md)|<span data-ttu-id="52142-135">Section de configuration qui contient les entrées de mappage de routage.</span><span class="sxs-lookup"><span data-stu-id="52142-135">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="52142-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52142-136">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>

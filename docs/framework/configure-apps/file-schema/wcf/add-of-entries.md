---
title: <add> de <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 156d8b8d9d0eb05efbf306434ab4555a98bc317e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149047"
---
# <a name="add-of-entries"></a><span data-ttu-id="6fc90-102">\<add> de \<entries></span><span class="sxs-lookup"><span data-stu-id="6fc90-102">\<add> of \<entries></span></span>

<span data-ttu-id="6fc90-103">Représente une entrée de routage qui mappe un filtre à un point de terminaison client défini précédemment.</span><span class="sxs-lookup"><span data-stu-id="6fc90-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="6fc90-104">Les messages correspondant à ce filtre sont envoyés à cette destination.</span><span class="sxs-lookup"><span data-stu-id="6fc90-104">Messages matching this filter will be sent to this destination.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<entries>**](entries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="6fc90-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6fc90-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6fc90-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6fc90-106">Attributes and Elements</span></span>  

 <span data-ttu-id="6fc90-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6fc90-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6fc90-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="6fc90-108">Attributes</span></span>  
  
|<span data-ttu-id="6fc90-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="6fc90-109">Attribute</span></span>|<span data-ttu-id="6fc90-110">Description</span><span class="sxs-lookup"><span data-stu-id="6fc90-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6fc90-111">backupList</span><span class="sxs-lookup"><span data-stu-id="6fc90-111">backupList</span></span>|<span data-ttu-id="6fc90-112">Chaîne qui spécifie une référence à une liste de sauvegarde de points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="6fc90-112">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="6fc90-113">endpoint</span><span class="sxs-lookup"><span data-stu-id="6fc90-113">endpoint</span></span>|<span data-ttu-id="6fc90-114">Chaîne qui spécifie une référence à un point de terminaison client qui reçoit les messages correspondant au filtre indiqué par l'attribut `filterName`.</span><span class="sxs-lookup"><span data-stu-id="6fc90-114">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="6fc90-115">filterName</span><span class="sxs-lookup"><span data-stu-id="6fc90-115">filterName</span></span>|<span data-ttu-id="6fc90-116">Chaîne qui spécifie une référence à un élément de filtre.</span><span class="sxs-lookup"><span data-stu-id="6fc90-116">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="6fc90-117">priority</span><span class="sxs-lookup"><span data-stu-id="6fc90-117">priority</span></span>|<span data-ttu-id="6fc90-118">Entier qui spécifie la priorité de cette entrée.</span><span class="sxs-lookup"><span data-stu-id="6fc90-118">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="6fc90-119">Les entrées dans la table de routage sont évaluées selon leur priorité, 0 correspondant à la priorité la plus basse.</span><span class="sxs-lookup"><span data-stu-id="6fc90-119">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="6fc90-120">Toutes les entrées d'une priorité donnée sont évaluées simultanément, si aucune entrée correspondante n'est trouvée pour la priorité actuelle, le niveau de priorité suivant est évalué.</span><span class="sxs-lookup"><span data-stu-id="6fc90-120">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="6fc90-121">Cette valeur est facultative.</span><span class="sxs-lookup"><span data-stu-id="6fc90-121">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6fc90-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6fc90-122">Child Elements</span></span>  

 <span data-ttu-id="6fc90-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6fc90-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6fc90-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6fc90-124">Parent Elements</span></span>  
  
|<span data-ttu-id="6fc90-125">Élément</span><span class="sxs-lookup"><span data-stu-id="6fc90-125">Element</span></span>|<span data-ttu-id="6fc90-126">Description</span><span class="sxs-lookup"><span data-stu-id="6fc90-126">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="6fc90-127">Section de configuration qui contient les entrées de mappage de routage.</span><span class="sxs-lookup"><span data-stu-id="6fc90-127">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6fc90-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6fc90-128">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>

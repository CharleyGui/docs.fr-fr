---
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: 610ba29ec98f4b1f2a9b1db3542bcb3aefb46457
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925648"
---
# <a name="entries"></a><span data-ttu-id="8af82-101">\<entries></span><span class="sxs-lookup"><span data-stu-id="8af82-101">\<entries></span></span>
<span data-ttu-id="8af82-102">Entrée de routage qui contient des mappages entre les filtres de routage et les points de terminaison cibles vers lesquels envoyer des messages lorsque le filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="8af82-102">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="8af82-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8af82-103">\<system.serviceModel></span></span>  
<span data-ttu-id="8af82-104">\<routing></span><span class="sxs-lookup"><span data-stu-id="8af82-104">\<routing></span></span>  
<span data-ttu-id="8af82-105">\<routingTables></span><span class="sxs-lookup"><span data-stu-id="8af82-105">\<routingTables></span></span>  
<span data-ttu-id="8af82-106">\<table></span><span class="sxs-lookup"><span data-stu-id="8af82-106">\<table></span></span>  
<span data-ttu-id="8af82-107">\<entries></span><span class="sxs-lookup"><span data-stu-id="8af82-107">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8af82-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8af82-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8af82-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8af82-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8af82-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8af82-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8af82-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="8af82-111">Attributes</span></span>  
 <span data-ttu-id="8af82-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8af82-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8af82-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8af82-113">Child Elements</span></span>  
  
|<span data-ttu-id="8af82-114">Élément</span><span class="sxs-lookup"><span data-stu-id="8af82-114">Element</span></span>|<span data-ttu-id="8af82-115">Description</span><span class="sxs-lookup"><span data-stu-id="8af82-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8af82-116">\<filtres></span><span class="sxs-lookup"><span data-stu-id="8af82-116">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="8af82-117">Mappe un filtre à un point de terminaison client précédemment défini.</span><span class="sxs-lookup"><span data-stu-id="8af82-117">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="8af82-118">Les messages correspondant à ce filtre sont envoyés à cette destination.</span><span class="sxs-lookup"><span data-stu-id="8af82-118">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8af82-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8af82-119">Parent Elements</span></span>  
  
|<span data-ttu-id="8af82-120">Élément</span><span class="sxs-lookup"><span data-stu-id="8af82-120">Element</span></span>|<span data-ttu-id="8af82-121">Description</span><span class="sxs-lookup"><span data-stu-id="8af82-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8af82-122">\<routing></span><span class="sxs-lookup"><span data-stu-id="8af82-122">\<routing></span></span>](routing.md)|<span data-ttu-id="8af82-123">Section de configuration qui contient une table de routage.</span><span class="sxs-lookup"><span data-stu-id="8af82-123">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8af82-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8af82-124">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>

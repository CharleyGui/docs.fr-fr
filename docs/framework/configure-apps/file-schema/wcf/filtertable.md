---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: f9e64e667befb70d617574b2a03c3e6bebb2a143
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925604"
---
# <a name="filtertable"></a><span data-ttu-id="cc447-101">\<filterTable></span><span class="sxs-lookup"><span data-stu-id="cc447-101">\<filterTable></span></span>
<span data-ttu-id="cc447-102">Représente une table de routage qui contient une liste de filtres par rapport auxquels évaluer les messages et le point de terminaison client vers lequel acheminer les messages si le filtre prend la valeur true.</span><span class="sxs-lookup"><span data-stu-id="cc447-102">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="cc447-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="cc447-103">\<system.serviceModel></span></span>  
<span data-ttu-id="cc447-104">\<routing></span><span class="sxs-lookup"><span data-stu-id="cc447-104">\<routing></span></span>  
<span data-ttu-id="cc447-105">\<routingTables></span><span class="sxs-lookup"><span data-stu-id="cc447-105">\<routingTables></span></span>  
<span data-ttu-id="cc447-106">\<table></span><span class="sxs-lookup"><span data-stu-id="cc447-106">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc447-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc447-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc447-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="cc447-108">Attributes and Elements</span></span>  
 <span data-ttu-id="cc447-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="cc447-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc447-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="cc447-110">Attributes</span></span>  
  
|<span data-ttu-id="cc447-111">Élément</span><span class="sxs-lookup"><span data-stu-id="cc447-111">Element</span></span>|<span data-ttu-id="cc447-112">Description</span><span class="sxs-lookup"><span data-stu-id="cc447-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cc447-113">name</span><span class="sxs-lookup"><span data-stu-id="cc447-113">name</span></span>|<span data-ttu-id="cc447-114">Chaîne qui contient le nom unique de cet élément de configuration.</span><span class="sxs-lookup"><span data-stu-id="cc447-114">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cc447-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cc447-115">Child Elements</span></span>  
  
|<span data-ttu-id="cc447-116">Élément</span><span class="sxs-lookup"><span data-stu-id="cc447-116">Element</span></span>|<span data-ttu-id="cc447-117">Description</span><span class="sxs-lookup"><span data-stu-id="cc447-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc447-118">\<filtres></span><span class="sxs-lookup"><span data-stu-id="cc447-118">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="cc447-119">Mappages entre les filtres de routage et les points de terminaison cibles auxquels envoyer des messages lorsque le filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="cc447-119">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cc447-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cc447-120">Parent Elements</span></span>  
  
|<span data-ttu-id="cc447-121">Élément</span><span class="sxs-lookup"><span data-stu-id="cc447-121">Element</span></span>|<span data-ttu-id="cc447-122">Description</span><span class="sxs-lookup"><span data-stu-id="cc447-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc447-123">\<routing></span><span class="sxs-lookup"><span data-stu-id="cc447-123">\<routing></span></span>](routing.md)|<span data-ttu-id="cc447-124">Section de configuration qui contient des tables de routage.</span><span class="sxs-lookup"><span data-stu-id="cc447-124">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cc447-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc447-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>

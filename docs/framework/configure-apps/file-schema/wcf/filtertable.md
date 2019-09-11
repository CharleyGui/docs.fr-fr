---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: 918a365004efea82f4ef4c8868f6821d4bb6da18
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855190"
---
# <a name="filtertable"></a><span data-ttu-id="e393a-101">\<filterTable></span><span class="sxs-lookup"><span data-stu-id="e393a-101">\<filterTable></span></span>
<span data-ttu-id="e393a-102">Représente une table de routage qui contient une liste de filtres par rapport auxquels évaluer les messages et le point de terminaison client vers lequel acheminer les messages si le filtre prend la valeur true.</span><span class="sxs-lookup"><span data-stu-id="e393a-102">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
<span data-ttu-id="e393a-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e393a-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e393a-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e393a-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e393a-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de routage**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="e393a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="e393a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<filterTables >** ](filtertables.md)</span><span class="sxs-lookup"><span data-stu-id="e393a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)</span></span>\
<span data-ttu-id="e393a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<filterTable >**</span><span class="sxs-lookup"><span data-stu-id="e393a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTable>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e393a-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e393a-108">Syntax</span></span>  
  
```xml  
<routing>
  <filterTables>
     name="String">
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e393a-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e393a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e393a-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e393a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e393a-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="e393a-111">Attributes</span></span>  
  
|<span data-ttu-id="e393a-112">Élément</span><span class="sxs-lookup"><span data-stu-id="e393a-112">Element</span></span>|<span data-ttu-id="e393a-113">Description</span><span class="sxs-lookup"><span data-stu-id="e393a-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e393a-114">name</span><span class="sxs-lookup"><span data-stu-id="e393a-114">name</span></span>|<span data-ttu-id="e393a-115">Chaîne qui contient le nom unique de cet élément de configuration.</span><span class="sxs-lookup"><span data-stu-id="e393a-115">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e393a-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e393a-116">Child Elements</span></span>  
  
|<span data-ttu-id="e393a-117">Élément</span><span class="sxs-lookup"><span data-stu-id="e393a-117">Element</span></span>|<span data-ttu-id="e393a-118">Description</span><span class="sxs-lookup"><span data-stu-id="e393a-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e393a-119">\<filtres></span><span class="sxs-lookup"><span data-stu-id="e393a-119">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="e393a-120">Mappages entre les filtres de routage et les points de terminaison cibles auxquels envoyer des messages lorsque le filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="e393a-120">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e393a-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e393a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e393a-122">Élément</span><span class="sxs-lookup"><span data-stu-id="e393a-122">Element</span></span>|<span data-ttu-id="e393a-123">Description</span><span class="sxs-lookup"><span data-stu-id="e393a-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e393a-124">\<routing></span><span class="sxs-lookup"><span data-stu-id="e393a-124">\<routing></span></span>](routing.md)|<span data-ttu-id="e393a-125">Section de configuration qui contient des tables de routage.</span><span class="sxs-lookup"><span data-stu-id="e393a-125">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e393a-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e393a-126">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>

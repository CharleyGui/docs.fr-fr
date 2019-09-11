---
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: ffe2538fa2c3cb680285cfaa68c975c0f9d4b1bd
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855274"
---
# <a name="entries"></a><span data-ttu-id="8cf12-101">\<entries></span><span class="sxs-lookup"><span data-stu-id="8cf12-101">\<entries></span></span>
<span data-ttu-id="8cf12-102">Entrée de routage qui contient des mappages entre les filtres de routage et les points de terminaison cibles vers lesquels envoyer des messages lorsque le filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="8cf12-102">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
<span data-ttu-id="8cf12-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8cf12-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8cf12-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8cf12-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8cf12-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de routage**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="8cf12-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="8cf12-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<filterTables >** ](filtertables.md)</span><span class="sxs-lookup"><span data-stu-id="8cf12-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)</span></span>\
<span data-ttu-id="8cf12-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<filterTable >** ](filtertable.md)</span><span class="sxs-lookup"><span data-stu-id="8cf12-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)</span></span>\
<span data-ttu-id="8cf12-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<entrées >**</span><span class="sxs-lookup"><span data-stu-id="8cf12-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<entries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cf12-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8cf12-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8cf12-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8cf12-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8cf12-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8cf12-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8cf12-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="8cf12-112">Attributes</span></span>  
 <span data-ttu-id="8cf12-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8cf12-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8cf12-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8cf12-114">Child Elements</span></span>  
  
|<span data-ttu-id="8cf12-115">Élément</span><span class="sxs-lookup"><span data-stu-id="8cf12-115">Element</span></span>|<span data-ttu-id="8cf12-116">Description</span><span class="sxs-lookup"><span data-stu-id="8cf12-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8cf12-117">\<filtres></span><span class="sxs-lookup"><span data-stu-id="8cf12-117">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="8cf12-118">Mappe un filtre à un point de terminaison client précédemment défini.</span><span class="sxs-lookup"><span data-stu-id="8cf12-118">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="8cf12-119">Les messages correspondant à ce filtre sont envoyés à cette destination.</span><span class="sxs-lookup"><span data-stu-id="8cf12-119">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8cf12-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8cf12-120">Parent Elements</span></span>  
  
|<span data-ttu-id="8cf12-121">Élément</span><span class="sxs-lookup"><span data-stu-id="8cf12-121">Element</span></span>|<span data-ttu-id="8cf12-122">Description</span><span class="sxs-lookup"><span data-stu-id="8cf12-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8cf12-123">\<routing></span><span class="sxs-lookup"><span data-stu-id="8cf12-123">\<routing></span></span>](routing.md)|<span data-ttu-id="8cf12-124">Section de configuration qui contient une table de routage.</span><span class="sxs-lookup"><span data-stu-id="8cf12-124">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8cf12-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8cf12-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>

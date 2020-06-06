---
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: ffe2538fa2c3cb680285cfaa68c975c0f9d4b1bd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855274"
---
# \<entries>
<span data-ttu-id="f9811-101">Entrée de routage qui contient des mappages entre les filtres de routage et les points de terminaison cibles vers lesquels envoyer des messages lorsque le filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="f9811-101">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<entries>**  
  
## <a name="syntax"></a><span data-ttu-id="f9811-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9811-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9811-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f9811-103">Attributes and Elements</span></span>  
 <span data-ttu-id="f9811-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f9811-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9811-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="f9811-105">Attributes</span></span>  
 <span data-ttu-id="f9811-106">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f9811-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f9811-107">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f9811-107">Child Elements</span></span>  
  
|<span data-ttu-id="f9811-108">Élément</span><span class="sxs-lookup"><span data-stu-id="f9811-108">Element</span></span>|<span data-ttu-id="f9811-109">Description</span><span class="sxs-lookup"><span data-stu-id="f9811-109">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="f9811-110">Mappe un filtre à un point de terminaison client précédemment défini.</span><span class="sxs-lookup"><span data-stu-id="f9811-110">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="f9811-111">Les messages correspondant à ce filtre sont envoyés à cette destination.</span><span class="sxs-lookup"><span data-stu-id="f9811-111">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f9811-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f9811-112">Parent Elements</span></span>  
  
|<span data-ttu-id="f9811-113">Élément</span><span class="sxs-lookup"><span data-stu-id="f9811-113">Element</span></span>|<span data-ttu-id="f9811-114">Description</span><span class="sxs-lookup"><span data-stu-id="f9811-114">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="f9811-115">Section de configuration qui contient une table de routage.</span><span class="sxs-lookup"><span data-stu-id="f9811-115">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f9811-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9811-116">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>

---
title: <filterTables>
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: c68479737cefe542a10a404a8b31a4820a430ffb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855198"
---
# \<filterTables>
<span data-ttu-id="2d23f-101">Représente une section de configuration permettant de définir des tables de routage qui contiennent des mappages entre les filtres de routage et les points de terminaison cibles auxquels envoyer des messages lorsque le filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="2d23f-101">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTables>**  
  
## <a name="syntax"></a><span data-ttu-id="2d23f-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d23f-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d23f-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2d23f-103">Attributes and Elements</span></span>  
 <span data-ttu-id="2d23f-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2d23f-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d23f-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="2d23f-105">Attributes</span></span>  
 <span data-ttu-id="2d23f-106">Aucun.</span><span class="sxs-lookup"><span data-stu-id="2d23f-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2d23f-107">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2d23f-107">Child Elements</span></span>  
  
|<span data-ttu-id="2d23f-108">Élément</span><span class="sxs-lookup"><span data-stu-id="2d23f-108">Element</span></span>|<span data-ttu-id="2d23f-109">Description</span><span class="sxs-lookup"><span data-stu-id="2d23f-109">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="2d23f-110">Table de routage qui contient des mappages entre les filtres de routage et les points de terminaison cibles vers lesquels envoyer des messages lorsque le filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="2d23f-110">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2d23f-111">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2d23f-111">Parent Elements</span></span>  
  
|<span data-ttu-id="2d23f-112">Élément</span><span class="sxs-lookup"><span data-stu-id="2d23f-112">Element</span></span>|<span data-ttu-id="2d23f-113">Description</span><span class="sxs-lookup"><span data-stu-id="2d23f-113">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="2d23f-114">Section de configuration qui contient des filtres de routage et des tables de routage.</span><span class="sxs-lookup"><span data-stu-id="2d23f-114">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2d23f-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d23f-115">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>

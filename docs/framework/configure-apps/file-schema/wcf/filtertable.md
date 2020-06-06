---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: 918a365004efea82f4ef4c8868f6821d4bb6da18
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855190"
---
# \<filterTable>
<span data-ttu-id="0322f-101">Représente une table de routage qui contient une liste de filtres par rapport auxquels évaluer les messages et le point de terminaison client vers lequel acheminer les messages si le filtre prend la valeur True.</span><span class="sxs-lookup"><span data-stu-id="0322f-101">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTable>**  
  
## <a name="syntax"></a><span data-ttu-id="0322f-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0322f-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0322f-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0322f-103">Attributes and Elements</span></span>  
 <span data-ttu-id="0322f-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0322f-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0322f-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="0322f-105">Attributes</span></span>  
  
|<span data-ttu-id="0322f-106">Élément</span><span class="sxs-lookup"><span data-stu-id="0322f-106">Element</span></span>|<span data-ttu-id="0322f-107">Description</span><span class="sxs-lookup"><span data-stu-id="0322f-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0322f-108">name</span><span class="sxs-lookup"><span data-stu-id="0322f-108">name</span></span>|<span data-ttu-id="0322f-109">Chaîne qui contient le nom unique de cet élément de configuration.</span><span class="sxs-lookup"><span data-stu-id="0322f-109">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0322f-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0322f-110">Child Elements</span></span>  
  
|<span data-ttu-id="0322f-111">Élément</span><span class="sxs-lookup"><span data-stu-id="0322f-111">Element</span></span>|<span data-ttu-id="0322f-112">Description</span><span class="sxs-lookup"><span data-stu-id="0322f-112">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="0322f-113">Mappages entre les filtres de routage et les points de terminaison cibles auxquels envoyer des messages lorsque le filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="0322f-113">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0322f-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0322f-114">Parent Elements</span></span>  
  
|<span data-ttu-id="0322f-115">Élément</span><span class="sxs-lookup"><span data-stu-id="0322f-115">Element</span></span>|<span data-ttu-id="0322f-116">Description</span><span class="sxs-lookup"><span data-stu-id="0322f-116">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="0322f-117">Section de configuration qui contient des tables de routage.</span><span class="sxs-lookup"><span data-stu-id="0322f-117">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0322f-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0322f-118">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>

---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: fb36feedc5fb2cbdf3827cbe44242c7ac6ab8a9b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185689"
---
# \<filterTable>

<span data-ttu-id="3cb0d-101">Représente une table de routage qui contient une liste de filtres par rapport auxquels évaluer les messages et le point de terminaison client vers lequel acheminer les messages si le filtre prend la valeur True.</span><span class="sxs-lookup"><span data-stu-id="3cb0d-101">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTable>**  
  
## <a name="syntax"></a><span data-ttu-id="3cb0d-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3cb0d-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3cb0d-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3cb0d-103">Attributes and Elements</span></span>  

 <span data-ttu-id="3cb0d-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3cb0d-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3cb0d-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="3cb0d-105">Attributes</span></span>  
  
|<span data-ttu-id="3cb0d-106">Élément</span><span class="sxs-lookup"><span data-stu-id="3cb0d-106">Element</span></span>|<span data-ttu-id="3cb0d-107">Description</span><span class="sxs-lookup"><span data-stu-id="3cb0d-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3cb0d-108">name</span><span class="sxs-lookup"><span data-stu-id="3cb0d-108">name</span></span>|<span data-ttu-id="3cb0d-109">Chaîne qui contient le nom unique de cet élément de configuration.</span><span class="sxs-lookup"><span data-stu-id="3cb0d-109">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3cb0d-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3cb0d-110">Child Elements</span></span>  
  
|<span data-ttu-id="3cb0d-111">Élément</span><span class="sxs-lookup"><span data-stu-id="3cb0d-111">Element</span></span>|<span data-ttu-id="3cb0d-112">Description</span><span class="sxs-lookup"><span data-stu-id="3cb0d-112">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="3cb0d-113">Mappages entre les filtres de routage et les points de terminaison cibles auxquels envoyer des messages lorsque le filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="3cb0d-113">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3cb0d-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3cb0d-114">Parent Elements</span></span>  
  
|<span data-ttu-id="3cb0d-115">Élément</span><span class="sxs-lookup"><span data-stu-id="3cb0d-115">Element</span></span>|<span data-ttu-id="3cb0d-116">Description</span><span class="sxs-lookup"><span data-stu-id="3cb0d-116">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="3cb0d-117">Section de configuration qui contient des tables de routage.</span><span class="sxs-lookup"><span data-stu-id="3cb0d-117">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3cb0d-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3cb0d-118">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>

---
title: <filterTables>
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: faa26ca108010330475725f83dfd0c6668cfc6b1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178201"
---
# \<filterTables>

<span data-ttu-id="23e9c-101">Représente une section de configuration permettant de définir des tables de routage qui contiennent des mappages entre les filtres de routage et les points de terminaison cibles auxquels envoyer des messages lorsque le filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="23e9c-101">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTables>**  
  
## <a name="syntax"></a><span data-ttu-id="23e9c-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23e9c-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23e9c-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="23e9c-103">Attributes and Elements</span></span>  

 <span data-ttu-id="23e9c-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="23e9c-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23e9c-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="23e9c-105">Attributes</span></span>  

 <span data-ttu-id="23e9c-106">Aucun.</span><span class="sxs-lookup"><span data-stu-id="23e9c-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="23e9c-107">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="23e9c-107">Child Elements</span></span>  
  
|<span data-ttu-id="23e9c-108">Élément</span><span class="sxs-lookup"><span data-stu-id="23e9c-108">Element</span></span>|<span data-ttu-id="23e9c-109">Description</span><span class="sxs-lookup"><span data-stu-id="23e9c-109">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="23e9c-110">Table de routage qui contient des mappages entre les filtres de routage et les points de terminaison cibles vers lesquels envoyer des messages lorsque le filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="23e9c-110">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="23e9c-111">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="23e9c-111">Parent Elements</span></span>  
  
|<span data-ttu-id="23e9c-112">Élément</span><span class="sxs-lookup"><span data-stu-id="23e9c-112">Element</span></span>|<span data-ttu-id="23e9c-113">Description</span><span class="sxs-lookup"><span data-stu-id="23e9c-113">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="23e9c-114">Section de configuration qui contient des filtres de routage et des tables de routage.</span><span class="sxs-lookup"><span data-stu-id="23e9c-114">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="23e9c-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23e9c-115">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>

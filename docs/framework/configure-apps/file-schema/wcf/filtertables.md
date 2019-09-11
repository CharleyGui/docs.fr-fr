---
title: <filterTables>
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: c68479737cefe542a10a404a8b31a4820a430ffb
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855198"
---
# <a name="filtertables"></a><span data-ttu-id="88ec3-101">\<filterTables></span><span class="sxs-lookup"><span data-stu-id="88ec3-101">\<filterTables></span></span>
<span data-ttu-id="88ec3-102">Représente une section de configuration permettant de définir des tables de routage qui contiennent des mappages entre les filtres de routage et les points de terminaison cibles auxquels envoyer des messages lorsque le filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="88ec3-102">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
<span data-ttu-id="88ec3-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="88ec3-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="88ec3-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="88ec3-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="88ec3-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de routage**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="88ec3-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="88ec3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<filterTables >**</span><span class="sxs-lookup"><span data-stu-id="88ec3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTables>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88ec3-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88ec3-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="88ec3-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="88ec3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="88ec3-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="88ec3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="88ec3-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="88ec3-110">Attributes</span></span>  
 <span data-ttu-id="88ec3-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="88ec3-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="88ec3-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="88ec3-112">Child Elements</span></span>  
  
|<span data-ttu-id="88ec3-113">Élément</span><span class="sxs-lookup"><span data-stu-id="88ec3-113">Element</span></span>|<span data-ttu-id="88ec3-114">Description</span><span class="sxs-lookup"><span data-stu-id="88ec3-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="88ec3-115">\<filtres></span><span class="sxs-lookup"><span data-stu-id="88ec3-115">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="88ec3-116">Table de routage qui contient des mappages entre les filtres de routage et les points de terminaison cibles vers lesquels envoyer des messages lorsque le filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="88ec3-116">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="88ec3-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="88ec3-117">Parent Elements</span></span>  
  
|<span data-ttu-id="88ec3-118">Élément</span><span class="sxs-lookup"><span data-stu-id="88ec3-118">Element</span></span>|<span data-ttu-id="88ec3-119">Description</span><span class="sxs-lookup"><span data-stu-id="88ec3-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="88ec3-120">\<routing></span><span class="sxs-lookup"><span data-stu-id="88ec3-120">\<routing></span></span>](routing.md)|<span data-ttu-id="88ec3-121">Section de configuration qui contient des filtres de routage et des tables de routage.</span><span class="sxs-lookup"><span data-stu-id="88ec3-121">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="88ec3-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88ec3-122">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>

---
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: fcf2d4eec93fd7127c6f800e1c739ad1fac49203
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399974"
---
# \<routing>

<span data-ttu-id="2d3e4-101">Représente une section de configuration permettant de définir un jeu de filtres de routage, qui détermine le type de Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> à utiliser lors de l’évaluation des messages entrants, ainsi que les tables de routage qui définissent les points de terminaison cibles auxquels envoyer des messages lorsqu’un filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="2d3e4-101">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**
  
## <a name="syntax"></a><span data-ttu-id="2d3e4-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d3e4-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String"
              filterData="String"
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
              name="String" />
    </filters>
    <routingTables>
      <table name="String">
        <entries>
          <add endpoint="String"
               filterName="String"
               priority="Integer" />
        </entries>
      </table>
    </routingTables>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d3e4-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2d3e4-103">Attributes and elements</span></span>

<span data-ttu-id="2d3e4-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2d3e4-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="2d3e4-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="2d3e4-105">Attributes</span></span>

<span data-ttu-id="2d3e4-106">Aucune</span><span class="sxs-lookup"><span data-stu-id="2d3e4-106">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="2d3e4-107">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2d3e4-107">Child elements</span></span>

|     | <span data-ttu-id="2d3e4-108">Description</span><span class="sxs-lookup"><span data-stu-id="2d3e4-108">Description</span></span> |
| --- | ----------- |
| [**\<filters>**](filters-of-routing.md) | <span data-ttu-id="2d3e4-109">Contient un ensemble de filtres de routage qui déterminent le type de Windows Communication Foundation (WCF) MessageFilter sera utilisé lors de l’évaluation des messages entrants.</span><span class="sxs-lookup"><span data-stu-id="2d3e4-109">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [**\<filterTables>**](filtertables.md) | <span data-ttu-id="2d3e4-110">Contient les mappages entre les filtres de routage et les points de terminaison cibles permettant de spécifier le point de terminaison à utiliser lorsque le filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="2d3e4-110">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="2d3e4-111">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2d3e4-111">Parent elements</span></span>

|     | <span data-ttu-id="2d3e4-112">Description</span><span class="sxs-lookup"><span data-stu-id="2d3e4-112">Description</span></span> |
| --- | ----------- |
| **\<system.ServiceModel>** | <span data-ttu-id="2d3e4-113">Élément racine de tous les éléments de configuration WCF.</span><span class="sxs-lookup"><span data-stu-id="2d3e4-113">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="2d3e4-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d3e4-114">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>

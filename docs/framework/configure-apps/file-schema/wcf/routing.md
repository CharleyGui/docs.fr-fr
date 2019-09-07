---
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: fcf2d4eec93fd7127c6f800e1c739ad1fac49203
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399974"
---
# <a name="routing"></a><span data-ttu-id="8d034-101">\<routing></span><span class="sxs-lookup"><span data-stu-id="8d034-101">\<routing></span></span>

<span data-ttu-id="8d034-102">Représente une section de configuration permettant de définir un jeu de filtres de routage, qui détermine le type de Windows Communication Foundation <xref:System.ServiceModel.Dispatcher.MessageFilter> (WCF) à utiliser lors de l’évaluation des messages entrants, ainsi que les tables de routage qui définissent les points de terminaison cibles Envoyer des messages à lorsqu’un filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="8d034-102">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="8d034-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8d034-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8d034-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8d034-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8d034-105">&nbsp;&nbsp;&nbsp;&nbsp; **\<> de routage**</span><span class="sxs-lookup"><span data-stu-id="8d034-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="8d034-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d034-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d034-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8d034-107">Attributes and elements</span></span>

<span data-ttu-id="8d034-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8d034-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8d034-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="8d034-109">Attributes</span></span>

<span data-ttu-id="8d034-110">Aucun</span><span class="sxs-lookup"><span data-stu-id="8d034-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="8d034-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8d034-111">Child elements</span></span>

|     | <span data-ttu-id="8d034-112">Description</span><span class="sxs-lookup"><span data-stu-id="8d034-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="8d034-113"> **\<filters>** </span><span class="sxs-lookup"><span data-stu-id="8d034-113">**\<filters>**</span></span>](filters-of-routing.md) | <span data-ttu-id="8d034-114">Contient un ensemble de filtres de routage qui déterminent le type de Windows Communication Foundation (WCF) MessageFilter sera utilisé lors de l’évaluation des messages entrants.</span><span class="sxs-lookup"><span data-stu-id="8d034-114">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="8d034-115"> **\<filterTables>** </span><span class="sxs-lookup"><span data-stu-id="8d034-115">**\<filterTables>**</span></span>](filtertables.md) | <span data-ttu-id="8d034-116">Contient les mappages entre les filtres de routage et les points de terminaison cibles permettant de spécifier le point de terminaison à utiliser lorsque le filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="8d034-116">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="8d034-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8d034-117">Parent elements</span></span>

|     | <span data-ttu-id="8d034-118">Description</span><span class="sxs-lookup"><span data-stu-id="8d034-118">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="8d034-119">**\<system.ServiceModel>**</span><span class="sxs-lookup"><span data-stu-id="8d034-119">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="8d034-120">Élément racine de tous les éléments de configuration WCF.</span><span class="sxs-lookup"><span data-stu-id="8d034-120">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="8d034-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d034-121">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>

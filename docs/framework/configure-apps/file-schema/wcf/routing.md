---
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: 3c7e9cb1284ab55c8dd199d9fb47a223698814f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934123"
---
# <a name="routing"></a><span data-ttu-id="6dd39-101">\<routing></span><span class="sxs-lookup"><span data-stu-id="6dd39-101">\<routing></span></span>

<span data-ttu-id="6dd39-102">Représente une section de configuration permettant de définir un jeu de filtres de routage, qui détermine le type de Windows Communication Foundation <xref:System.ServiceModel.Dispatcher.MessageFilter> (WCF) à utiliser lors de l’évaluation des messages entrants, ainsi que les tables de routage qui définissent les points de terminaison cibles Envoyer des messages à lorsqu’un filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="6dd39-102">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="6dd39-103">[ **\<system.serviceModel>** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="6dd39-103">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="6dd39-104">&nbsp;&nbsp; **\<routing>**</span><span class="sxs-lookup"><span data-stu-id="6dd39-104">&nbsp;&nbsp;**\<routing>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="6dd39-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6dd39-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6dd39-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6dd39-106">Attributes and elements</span></span>

<span data-ttu-id="6dd39-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6dd39-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="6dd39-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="6dd39-108">Attributes</span></span>

<span data-ttu-id="6dd39-109">Aucun</span><span class="sxs-lookup"><span data-stu-id="6dd39-109">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="6dd39-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6dd39-110">Child elements</span></span>

|     | <span data-ttu-id="6dd39-111">Description</span><span class="sxs-lookup"><span data-stu-id="6dd39-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="6dd39-112"> **\<filters>** </span><span class="sxs-lookup"><span data-stu-id="6dd39-112">**\<filters>**</span></span>](filters-of-routing.md) | <span data-ttu-id="6dd39-113">Contient un ensemble de filtres de routage qui déterminent le type de Windows Communication Foundation (WCF) MessageFilter sera utilisé lors de l’évaluation des messages entrants.</span><span class="sxs-lookup"><span data-stu-id="6dd39-113">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="6dd39-114"> **\<filterTables>** </span><span class="sxs-lookup"><span data-stu-id="6dd39-114">**\<filterTables>**</span></span>](filtertables.md) | <span data-ttu-id="6dd39-115">Contient les mappages entre les filtres de routage et les points de terminaison cibles permettant de spécifier le point de terminaison à utiliser lorsque le filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="6dd39-115">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="6dd39-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6dd39-116">Parent elements</span></span>

|     | <span data-ttu-id="6dd39-117">Description</span><span class="sxs-lookup"><span data-stu-id="6dd39-117">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="6dd39-118">**\<system.ServiceModel>**</span><span class="sxs-lookup"><span data-stu-id="6dd39-118">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="6dd39-119">Élément racine de tous les éléments de configuration WCF.</span><span class="sxs-lookup"><span data-stu-id="6dd39-119">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="6dd39-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6dd39-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>

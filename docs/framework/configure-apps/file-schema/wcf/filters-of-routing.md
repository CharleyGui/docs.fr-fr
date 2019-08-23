---
title: <filters> de <routing>
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: ba60958ad33b46b40285f3f70001273bb3af3a63
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925616"
---
# <a name="filters-of-routing"></a><span data-ttu-id="531d1-102">\<filtre > de \<> de routage</span><span class="sxs-lookup"><span data-stu-id="531d1-102">\<filters> of \<routing></span></span>

<span data-ttu-id="531d1-103">Représente une section de configuration pour la définition d’un jeu de filtres de routage, qui détermine le type de <xref:System.ServiceModel.Dispatcher.MessageFilter> Windows Communication Foundation (WCF) à utiliser lors de l’évaluation des messages entrants.</span><span class="sxs-lookup"><span data-stu-id="531d1-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

<span data-ttu-id="531d1-104">[ **\<system.serviceModel>** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="531d1-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="531d1-105">&nbsp;&nbsp;[ **\<routing>** ](routing.md) </span><span class="sxs-lookup"><span data-stu-id="531d1-105">&nbsp;&nbsp;[**\<routing>**](routing.md) </span></span>  
<span data-ttu-id="531d1-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<filters>**</span><span class="sxs-lookup"><span data-stu-id="531d1-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="531d1-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="531d1-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String"
              filterData="String"
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
              name="String" />
    </filters>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="531d1-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="531d1-108">Attributes and elements</span></span>

<span data-ttu-id="531d1-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="531d1-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="531d1-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="531d1-110">Attributes</span></span>

<span data-ttu-id="531d1-111">Aucun</span><span class="sxs-lookup"><span data-stu-id="531d1-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="531d1-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="531d1-112">Child elements</span></span>

|     | <span data-ttu-id="531d1-113">Description</span><span class="sxs-lookup"><span data-stu-id="531d1-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="531d1-114"> **\<filter>** </span><span class="sxs-lookup"><span data-stu-id="531d1-114">**\<filter>**</span></span>](filter.md) | <span data-ttu-id="531d1-115">Contient un filtre de routage qui détermine le type de Windows Communication Foundation (WCF<xref:System.ServiceModel.Dispatcher.MessageFilter> ) sera utilisé lors de l’évaluation des messages entrants.</span><span class="sxs-lookup"><span data-stu-id="531d1-115">Contains a routing filter that determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="531d1-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="531d1-116">Parent elements</span></span>

|     | <span data-ttu-id="531d1-117">Description</span><span class="sxs-lookup"><span data-stu-id="531d1-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="531d1-118"> **\<routing>** </span><span class="sxs-lookup"><span data-stu-id="531d1-118">**\<routing>**</span></span>](routing.md) | <span data-ttu-id="531d1-119">Représente une section de configuration permettant de définir un jeu de filtres de routage, qui détermine le type de Windows Communication Foundation<xref:System.ServiceModel.Dispatcher.MessageFilter> (WCF) à utiliser lors de l’évaluation des messages entrants, ainsi que les tables de routage qui définissent les points de terminaison cibles Envoyer des messages à lorsqu’un filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="531d1-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="531d1-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="531d1-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>

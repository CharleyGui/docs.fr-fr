---
title: <filters> de <routing>
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: c9bc3a2c379e14d8cf687676a3ec40702d150e1e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855237"
---
# <a name="filters-of-routing"></a><span data-ttu-id="64672-102">\<filtre > de \<> de routage</span><span class="sxs-lookup"><span data-stu-id="64672-102">\<filters> of \<routing></span></span>

<span data-ttu-id="64672-103">Représente une section de configuration pour la définition d’un jeu de filtres de routage, qui détermine le type de <xref:System.ServiceModel.Dispatcher.MessageFilter> Windows Communication Foundation (WCF) à utiliser lors de l’évaluation des messages entrants.</span><span class="sxs-lookup"><span data-stu-id="64672-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

<span data-ttu-id="64672-104">[ **\<system.serviceModel>** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="64672-104">[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="64672-105">&nbsp;&nbsp;[ **\<routing>** ](routing.md)</span><span class="sxs-lookup"><span data-stu-id="64672-105">&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="64672-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<filters>**</span><span class="sxs-lookup"><span data-stu-id="64672-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64672-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64672-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="64672-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="64672-108">Attributes and elements</span></span>

<span data-ttu-id="64672-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="64672-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="64672-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="64672-110">Attributes</span></span>

<span data-ttu-id="64672-111">Aucun</span><span class="sxs-lookup"><span data-stu-id="64672-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="64672-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="64672-112">Child elements</span></span>

|     | <span data-ttu-id="64672-113">Description</span><span class="sxs-lookup"><span data-stu-id="64672-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="64672-114"> **\<filter>** </span><span class="sxs-lookup"><span data-stu-id="64672-114">**\<filter>**</span></span>](filter.md) | <span data-ttu-id="64672-115">Contient un filtre de routage qui détermine le type de Windows Communication Foundation (WCF<xref:System.ServiceModel.Dispatcher.MessageFilter> ) sera utilisé lors de l’évaluation des messages entrants.</span><span class="sxs-lookup"><span data-stu-id="64672-115">Contains a routing filter that determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="64672-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="64672-116">Parent elements</span></span>

|     | <span data-ttu-id="64672-117">Description</span><span class="sxs-lookup"><span data-stu-id="64672-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="64672-118"> **\<routing>** </span><span class="sxs-lookup"><span data-stu-id="64672-118">**\<routing>**</span></span>](routing.md) | <span data-ttu-id="64672-119">Représente une section de configuration permettant de définir un jeu de filtres de routage, qui détermine le type de Windows Communication Foundation<xref:System.ServiceModel.Dispatcher.MessageFilter> (WCF) à utiliser lors de l’évaluation des messages entrants, ainsi que les tables de routage qui définissent les points de terminaison cibles Envoyer des messages à lorsqu’un filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="64672-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="64672-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64672-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>

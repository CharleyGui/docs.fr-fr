---
title: <filters> de <routing>
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: c9bc3a2c379e14d8cf687676a3ec40702d150e1e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855237"
---
# <a name="filters-of-routing"></a><span data-ttu-id="10eb5-102">\<filters> de \<routing></span><span class="sxs-lookup"><span data-stu-id="10eb5-102">\<filters> of \<routing></span></span>

<span data-ttu-id="10eb5-103">Représente une section de configuration pour la définition d’un jeu de filtres de routage, qui détermine le type de Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> à utiliser lors de l’évaluation des messages entrants.</span><span class="sxs-lookup"><span data-stu-id="10eb5-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**  
  
## <a name="syntax"></a><span data-ttu-id="10eb5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10eb5-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10eb5-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="10eb5-105">Attributes and elements</span></span>

<span data-ttu-id="10eb5-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="10eb5-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="10eb5-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="10eb5-107">Attributes</span></span>

<span data-ttu-id="10eb5-108">Aucune</span><span class="sxs-lookup"><span data-stu-id="10eb5-108">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="10eb5-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="10eb5-109">Child elements</span></span>

|     | <span data-ttu-id="10eb5-110">Description</span><span class="sxs-lookup"><span data-stu-id="10eb5-110">Description</span></span> |
| --- | ----------- |
| [**\<filter>**](filter.md) | <span data-ttu-id="10eb5-111">Contient un filtre de routage qui détermine le type de Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> sera utilisé lors de l’évaluation des messages entrants.</span><span class="sxs-lookup"><span data-stu-id="10eb5-111">Contains a routing filter that determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="10eb5-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="10eb5-112">Parent elements</span></span>

|     | <span data-ttu-id="10eb5-113">Description</span><span class="sxs-lookup"><span data-stu-id="10eb5-113">Description</span></span> |
| --- | ----------- |
| [**\<routing>**](routing.md) | <span data-ttu-id="10eb5-114">Représente une section de configuration permettant de définir un jeu de filtres de routage, qui détermine le type de Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> à utiliser lors de l’évaluation des messages entrants, ainsi que les tables de routage qui définissent les points de terminaison cibles auxquels envoyer des messages lorsqu’un filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="10eb5-114">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="10eb5-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10eb5-115">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>

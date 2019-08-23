---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 68de255b9f11dc4377159d1cc3efa575633db316
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918893"
---
# <a name="filter"></a><span data-ttu-id="9c737-101">\<filter></span><span class="sxs-lookup"><span data-stu-id="9c737-101">\<filter></span></span>

<span data-ttu-id="9c737-102">Définit un filtre de routage qui détermine le type de Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> à utiliser lors de l’évaluation des messages entrants, ainsi que les données de prise en charge ou les paramètres requis par le filtre.</span><span class="sxs-lookup"><span data-stu-id="9c737-102">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

<span data-ttu-id="9c737-103">\<system.serviceModel> \<routing> \<filters> \<filter></span><span class="sxs-lookup"><span data-stu-id="9c737-103">\<system.serviceModel> \<routing> \<filters> \<filter></span></span>
  
## <a name="syntax"></a><span data-ttu-id="9c737-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c737-104">Syntax</span></span>  
  
```xml  
<routing>
  <filters>
    <filter customType="String"
            filterData="String"
            filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
            name="String" />
  </filters>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c737-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9c737-105">Attributes and elements</span></span>

<span data-ttu-id="9c737-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9c737-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9c737-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="9c737-107">Attributes</span></span>

| <span data-ttu-id="9c737-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="9c737-108">Attribute</span></span>  | <span data-ttu-id="9c737-109">Description</span><span class="sxs-lookup"><span data-stu-id="9c737-109">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="9c737-110">customType</span><span class="sxs-lookup"><span data-stu-id="9c737-110">customType</span></span> | <span data-ttu-id="9c737-111">Chaîne qui contient le nom qualifié complet du type personnalisé à utiliser comme filtre.</span><span class="sxs-lookup"><span data-stu-id="9c737-111">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="9c737-112">Si `filterType` a la `custom`valeur, cet attribut contient le nom de type qualifié complet de la classe à créer.</span><span class="sxs-lookup"><span data-stu-id="9c737-112">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="9c737-113">`filterData`peut également contenir des valeurs à utiliser pendant l’évaluation du filtre de type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="9c737-113">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="9c737-114">filterData</span><span class="sxs-lookup"><span data-stu-id="9c737-114">filterData</span></span> | <span data-ttu-id="9c737-115">Chaîne qui contient la données de filtre.</span><span class="sxs-lookup"><span data-stu-id="9c737-115">A string containing the filter data.</span></span> <span data-ttu-id="9c737-116">Pour plus d'informations sur la spécification de cet attribut, consultez <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="9c737-116">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="9c737-117">filterType</span><span class="sxs-lookup"><span data-stu-id="9c737-117">filterType</span></span> | <span data-ttu-id="9c737-118">Chaîne qui contient le type de filtre.</span><span class="sxs-lookup"><span data-stu-id="9c737-118">A string containing the filter type.</span></span> <span data-ttu-id="9c737-119">Cet attribut est de type <xref:System.ServiceModel.Routing.Configuration.FilterType>.</span><span class="sxs-lookup"><span data-stu-id="9c737-119">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="9c737-120">Pour plus d'informations sur l'utilisation de cet attribut avec l'attribut `filterData`, consultez <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="9c737-120">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="9c737-121">name</span><span class="sxs-lookup"><span data-stu-id="9c737-121">name</span></span>       | <span data-ttu-id="9c737-122">Chaîne qui contient le nom unique de cet élément de filtre.</span><span class="sxs-lookup"><span data-stu-id="9c737-122">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="9c737-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9c737-123">Child elements</span></span>

<span data-ttu-id="9c737-124">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9c737-124">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9c737-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9c737-125">Parent elements</span></span>

| <span data-ttu-id="9c737-126">Élément</span><span class="sxs-lookup"><span data-stu-id="9c737-126">Element</span></span> | <span data-ttu-id="9c737-127">Description</span><span class="sxs-lookup"><span data-stu-id="9c737-127">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="9c737-128">\<routing></span><span class="sxs-lookup"><span data-stu-id="9c737-128">\<routing></span></span>](routing.md) | <span data-ttu-id="9c737-129">Section de configuration permettant de définir un jeu de filtres de routage, qui détermine le type de Windows Communication Foundation (<xref:System.ServiceModel.Dispatcher.MessageFilter> WCF) à utiliser lors de l’évaluation des messages entrants.</span><span class="sxs-lookup"><span data-stu-id="9c737-129">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="9c737-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c737-130">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>

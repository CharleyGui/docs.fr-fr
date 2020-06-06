---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 6e78275aaeb202405e327302455d56fa431d7f27
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855259"
---
# \<filter>

<span data-ttu-id="35102-101">Définit un filtre de routage qui détermine le type de Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> à utiliser lors de l’évaluation des messages entrants, ainsi que les données de prise en charge ou les paramètres requis par le filtre.</span><span class="sxs-lookup"><span data-stu-id="35102-101">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters-of-routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**  
  
## <a name="syntax"></a><span data-ttu-id="35102-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35102-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35102-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="35102-103">Attributes and elements</span></span>

<span data-ttu-id="35102-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="35102-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="35102-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="35102-105">Attributes</span></span>

| <span data-ttu-id="35102-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="35102-106">Attribute</span></span>  | <span data-ttu-id="35102-107">Description</span><span class="sxs-lookup"><span data-stu-id="35102-107">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="35102-108">customType</span><span class="sxs-lookup"><span data-stu-id="35102-108">customType</span></span> | <span data-ttu-id="35102-109">Chaîne qui contient le nom qualifié complet du type personnalisé à utiliser comme filtre.</span><span class="sxs-lookup"><span data-stu-id="35102-109">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="35102-110">Si `filterType` a la valeur `custom` , cet attribut contient le nom de type qualifié complet de la classe à créer.</span><span class="sxs-lookup"><span data-stu-id="35102-110">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="35102-111">`filterData`peut également contenir des valeurs à utiliser pendant l’évaluation du filtre de type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="35102-111">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="35102-112">filterData</span><span class="sxs-lookup"><span data-stu-id="35102-112">filterData</span></span> | <span data-ttu-id="35102-113">Chaîne qui contient la données de filtre.</span><span class="sxs-lookup"><span data-stu-id="35102-113">A string containing the filter data.</span></span> <span data-ttu-id="35102-114">Pour plus d'informations sur la spécification de cet attribut, consultez <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="35102-114">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="35102-115">filterType</span><span class="sxs-lookup"><span data-stu-id="35102-115">filterType</span></span> | <span data-ttu-id="35102-116">Chaîne qui contient le type de filtre.</span><span class="sxs-lookup"><span data-stu-id="35102-116">A string containing the filter type.</span></span> <span data-ttu-id="35102-117">Cet attribut est de type <xref:System.ServiceModel.Routing.Configuration.FilterType>.</span><span class="sxs-lookup"><span data-stu-id="35102-117">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="35102-118">Pour plus d'informations sur l'utilisation de cet attribut avec l'attribut `filterData`, consultez <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="35102-118">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="35102-119">name</span><span class="sxs-lookup"><span data-stu-id="35102-119">name</span></span>       | <span data-ttu-id="35102-120">Chaîne qui contient le nom unique de cet élément de filtre.</span><span class="sxs-lookup"><span data-stu-id="35102-120">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="35102-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="35102-121">Child elements</span></span>

<span data-ttu-id="35102-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="35102-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="35102-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="35102-123">Parent elements</span></span>

| <span data-ttu-id="35102-124">Élément</span><span class="sxs-lookup"><span data-stu-id="35102-124">Element</span></span> | <span data-ttu-id="35102-125">Description</span><span class="sxs-lookup"><span data-stu-id="35102-125">Description</span></span> |
| ------- | ----------- |
| [\<routing>](routing.md) | <span data-ttu-id="35102-126">Section de configuration permettant de définir un jeu de filtres de routage, qui détermine le type de Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> à utiliser lors de l’évaluation des messages entrants.</span><span class="sxs-lookup"><span data-stu-id="35102-126">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="35102-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35102-127">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>

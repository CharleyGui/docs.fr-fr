---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 6e78275aaeb202405e327302455d56fa431d7f27
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855259"
---
# <a name="filter"></a><span data-ttu-id="f150b-101">\<filter></span><span class="sxs-lookup"><span data-stu-id="f150b-101">\<filter></span></span>

<span data-ttu-id="f150b-102">Définit un filtre de routage qui détermine le type de Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> à utiliser lors de l’évaluation des messages entrants, ainsi que les données de prise en charge ou les paramètres requis par le filtre.</span><span class="sxs-lookup"><span data-stu-id="f150b-102">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

<span data-ttu-id="f150b-103">[ **\<system.serviceModel>** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f150b-103">[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f150b-104">&nbsp;&nbsp;[ **\<routing>** ](routing.md)</span><span class="sxs-lookup"><span data-stu-id="f150b-104">&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="f150b-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Filtres >** ](filters-of-routing.md)</span><span class="sxs-lookup"><span data-stu-id="f150b-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters-of-routing.md)</span></span>\
<span data-ttu-id="f150b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<filtre >**</span><span class="sxs-lookup"><span data-stu-id="f150b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f150b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f150b-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f150b-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f150b-108">Attributes and elements</span></span>

<span data-ttu-id="f150b-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f150b-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f150b-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="f150b-110">Attributes</span></span>

| <span data-ttu-id="f150b-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="f150b-111">Attribute</span></span>  | <span data-ttu-id="f150b-112">Description</span><span class="sxs-lookup"><span data-stu-id="f150b-112">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="f150b-113">customType</span><span class="sxs-lookup"><span data-stu-id="f150b-113">customType</span></span> | <span data-ttu-id="f150b-114">Chaîne qui contient le nom qualifié complet du type personnalisé à utiliser comme filtre.</span><span class="sxs-lookup"><span data-stu-id="f150b-114">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="f150b-115">Si `filterType` a la `custom`valeur, cet attribut contient le nom de type qualifié complet de la classe à créer.</span><span class="sxs-lookup"><span data-stu-id="f150b-115">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="f150b-116">`filterData`peut également contenir des valeurs à utiliser pendant l’évaluation du filtre de type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f150b-116">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="f150b-117">filterData</span><span class="sxs-lookup"><span data-stu-id="f150b-117">filterData</span></span> | <span data-ttu-id="f150b-118">Chaîne qui contient la données de filtre.</span><span class="sxs-lookup"><span data-stu-id="f150b-118">A string containing the filter data.</span></span> <span data-ttu-id="f150b-119">Pour plus d'informations sur la spécification de cet attribut, consultez <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="f150b-119">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="f150b-120">filterType</span><span class="sxs-lookup"><span data-stu-id="f150b-120">filterType</span></span> | <span data-ttu-id="f150b-121">Chaîne qui contient le type de filtre.</span><span class="sxs-lookup"><span data-stu-id="f150b-121">A string containing the filter type.</span></span> <span data-ttu-id="f150b-122">Cet attribut est de type <xref:System.ServiceModel.Routing.Configuration.FilterType>.</span><span class="sxs-lookup"><span data-stu-id="f150b-122">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="f150b-123">Pour plus d'informations sur l'utilisation de cet attribut avec l'attribut `filterData`, consultez <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="f150b-123">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="f150b-124">name</span><span class="sxs-lookup"><span data-stu-id="f150b-124">name</span></span>       | <span data-ttu-id="f150b-125">Chaîne qui contient le nom unique de cet élément de filtre.</span><span class="sxs-lookup"><span data-stu-id="f150b-125">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="f150b-126">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f150b-126">Child elements</span></span>

<span data-ttu-id="f150b-127">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f150b-127">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f150b-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f150b-128">Parent elements</span></span>

| <span data-ttu-id="f150b-129">Élément</span><span class="sxs-lookup"><span data-stu-id="f150b-129">Element</span></span> | <span data-ttu-id="f150b-130">Description</span><span class="sxs-lookup"><span data-stu-id="f150b-130">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="f150b-131">\<routing></span><span class="sxs-lookup"><span data-stu-id="f150b-131">\<routing></span></span>](routing.md) | <span data-ttu-id="f150b-132">Section de configuration permettant de définir un jeu de filtres de routage, qui détermine le type de Windows Communication Foundation (<xref:System.ServiceModel.Dispatcher.MessageFilter> WCF) à utiliser lors de l’évaluation des messages entrants.</span><span class="sxs-lookup"><span data-stu-id="f150b-132">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="f150b-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f150b-133">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>

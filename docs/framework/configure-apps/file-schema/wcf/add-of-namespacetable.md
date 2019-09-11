---
title: <add> de <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 3b3b4a1584b37601269368ee0e4e973626ddf9cf
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850397"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="ad8b5-102">\<Ajouter > de \<la > namespaceTable</span><span class="sxs-lookup"><span data-stu-id="ad8b5-102">\<add> of \<namespaceTable></span></span>
<span data-ttu-id="ad8b5-103">Représente un élément de configuration qui contient un mappage espace de noms-préfixe à utiliser dans des filtres XPath pour le routage.</span><span class="sxs-lookup"><span data-stu-id="ad8b5-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
<span data-ttu-id="ad8b5-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ad8b5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ad8b5-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ad8b5-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ad8b5-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de routage**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="ad8b5-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="ad8b5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<namespaceTable >** ](namespacetable.md)</span><span class="sxs-lookup"><span data-stu-id="ad8b5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namespaceTable>**](namespacetable.md)</span></span>\
<span data-ttu-id="ad8b5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Ajouter >**</span><span class="sxs-lookup"><span data-stu-id="ad8b5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad8b5-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad8b5-109">Syntax</span></span>  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad8b5-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ad8b5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ad8b5-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ad8b5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad8b5-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="ad8b5-112">Attributes</span></span>  
  
|<span data-ttu-id="ad8b5-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="ad8b5-113">Attribute</span></span>|<span data-ttu-id="ad8b5-114">Description</span><span class="sxs-lookup"><span data-stu-id="ad8b5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ad8b5-115">namespace</span><span class="sxs-lookup"><span data-stu-id="ad8b5-115">namespace</span></span>|<span data-ttu-id="ad8b5-116">Chaîne qui contient l'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="ad8b5-116">A string containing the namespace.</span></span>|  
|<span data-ttu-id="ad8b5-117">prefix</span><span class="sxs-lookup"><span data-stu-id="ad8b5-117">prefix</span></span>|<span data-ttu-id="ad8b5-118">Chaîne qui contient le préfixe de cet espace de noms.</span><span class="sxs-lookup"><span data-stu-id="ad8b5-118">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ad8b5-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ad8b5-119">Child Elements</span></span>  
 <span data-ttu-id="ad8b5-120">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ad8b5-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ad8b5-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ad8b5-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ad8b5-122">Élément</span><span class="sxs-lookup"><span data-stu-id="ad8b5-122">Element</span></span>|<span data-ttu-id="ad8b5-123">Description</span><span class="sxs-lookup"><span data-stu-id="ad8b5-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ad8b5-124">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="ad8b5-124">\<namespaceTable></span></span>](namespacetable.md)|<span data-ttu-id="ad8b5-125">Représente une section de configuration qui permet de définir un ensemble d’éléments contenant des mappages espace de noms-préfixe qui peuvent ensuite être utilisés dans des filtres XPath pour le routage.</span><span class="sxs-lookup"><span data-stu-id="ad8b5-125">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ad8b5-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad8b5-126">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>

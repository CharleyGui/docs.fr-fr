---
title: <add> de <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 3b3b4a1584b37601269368ee0e4e973626ddf9cf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850397"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="89f4c-102">\<add> de \<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="89f4c-102">\<add> of \<namespaceTable></span></span>
<span data-ttu-id="89f4c-103">Représente un élément de configuration qui contient un mappage espace de noms-préfixe à utiliser dans des filtres XPath pour le routage.</span><span class="sxs-lookup"><span data-stu-id="89f4c-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namespaceTable>**](namespacetable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="89f4c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89f4c-104">Syntax</span></span>  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89f4c-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="89f4c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="89f4c-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="89f4c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89f4c-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="89f4c-107">Attributes</span></span>  
  
|<span data-ttu-id="89f4c-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="89f4c-108">Attribute</span></span>|<span data-ttu-id="89f4c-109">Description</span><span class="sxs-lookup"><span data-stu-id="89f4c-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="89f4c-110">espace de noms</span><span class="sxs-lookup"><span data-stu-id="89f4c-110">namespace</span></span>|<span data-ttu-id="89f4c-111">Chaîne qui contient l'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="89f4c-111">A string containing the namespace.</span></span>|  
|<span data-ttu-id="89f4c-112">prefix</span><span class="sxs-lookup"><span data-stu-id="89f4c-112">prefix</span></span>|<span data-ttu-id="89f4c-113">Chaîne qui contient le préfixe de cet espace de noms.</span><span class="sxs-lookup"><span data-stu-id="89f4c-113">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89f4c-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="89f4c-114">Child Elements</span></span>  
 <span data-ttu-id="89f4c-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="89f4c-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="89f4c-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="89f4c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="89f4c-117">Élément</span><span class="sxs-lookup"><span data-stu-id="89f4c-117">Element</span></span>|<span data-ttu-id="89f4c-118">Description</span><span class="sxs-lookup"><span data-stu-id="89f4c-118">Description</span></span>|  
|-------------|-----------------|  
|[\<namespaceTable>](namespacetable.md)|<span data-ttu-id="89f4c-119">Représente une section de configuration qui permet de définir un ensemble d’éléments contenant des mappages espace de noms-préfixe qui peuvent ensuite être utilisés dans des filtres XPath pour le routage.</span><span class="sxs-lookup"><span data-stu-id="89f4c-119">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="89f4c-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89f4c-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>

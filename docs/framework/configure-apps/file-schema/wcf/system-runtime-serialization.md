---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: b67f51e634d1294830690dad8c8cffb1fc9a6cd2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399460"
---
# <a name="systemruntimeserialization"></a><span data-ttu-id="702bb-102">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="702bb-102">\<system.runtime.serialization></span></span>
<span data-ttu-id="702bb-103">Représente l'élément racine correspondant à la section d'espace de noms <xref:System.Runtime.Serialization> et contient des éléments permettant de définir les options du <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="702bb-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  

<span data-ttu-id="702bb-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="702bb-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="702bb-105">&nbsp;&nbsp; **\<System. Runtime. Serialization >**</span><span class="sxs-lookup"><span data-stu-id="702bb-105">&nbsp;&nbsp;**\<system.runtime.serialization>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="702bb-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="702bb-106">Syntax</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer ignoreExtensionDataObject="Boolean"
                            maxItemsInObjectGraph="Integer">
      <declaredTypes>
        <add type="String">
          <knownType type="String">
            <parameter index="Integer" />
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="702bb-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="702bb-107">Attributes and Elements</span></span>  
 <span data-ttu-id="702bb-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="702bb-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="702bb-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="702bb-109">Attributes</span></span>  
 <span data-ttu-id="702bb-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="702bb-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="702bb-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="702bb-111">Child Elements</span></span>  
  
|<span data-ttu-id="702bb-112">Élément</span><span class="sxs-lookup"><span data-stu-id="702bb-112">Element</span></span>|<span data-ttu-id="702bb-113">Description</span><span class="sxs-lookup"><span data-stu-id="702bb-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="702bb-114">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="702bb-114">\<dataContractSerializer></span></span>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="702bb-115">Active l'ajout de types connus à utiliser lors de la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="702bb-115">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="702bb-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="702bb-116">Parent Elements</span></span>  
  
|<span data-ttu-id="702bb-117">Élément</span><span class="sxs-lookup"><span data-stu-id="702bb-117">Element</span></span>|<span data-ttu-id="702bb-118">Description</span><span class="sxs-lookup"><span data-stu-id="702bb-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="702bb-119">\<configuration>, élément</span><span class="sxs-lookup"><span data-stu-id="702bb-119">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="702bb-120">Élément de niveau supérieur de la configuration.</span><span class="sxs-lookup"><span data-stu-id="702bb-120">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="702bb-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="702bb-121">See also</span></span>

- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="702bb-122">Utilisation de contrats de données</span><span class="sxs-lookup"><span data-stu-id="702bb-122">Using Data Contracts</span></span>](../../../wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="702bb-123">Types connus de contrats de données</span><span class="sxs-lookup"><span data-stu-id="702bb-123">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
 
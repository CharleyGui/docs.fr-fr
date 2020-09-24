---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: 84ced06691ce3b3c9c9573fc9d114335096a849d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157107"
---
# \<system.runtime.serialization>

<span data-ttu-id="abcb5-102">Représente l'élément racine correspondant à la section d'espace de noms <xref:System.Runtime.Serialization> et contient des éléments permettant de définir les options du <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="abcb5-102">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.runtime.serialization>**  
  
## <a name="syntax"></a><span data-ttu-id="abcb5-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="abcb5-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="abcb5-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="abcb5-104">Attributes and Elements</span></span>  

 <span data-ttu-id="abcb5-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="abcb5-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="abcb5-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="abcb5-106">Attributes</span></span>  

 <span data-ttu-id="abcb5-107">Aucun.</span><span class="sxs-lookup"><span data-stu-id="abcb5-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="abcb5-108">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="abcb5-108">Child Elements</span></span>  
  
|<span data-ttu-id="abcb5-109">Élément</span><span class="sxs-lookup"><span data-stu-id="abcb5-109">Element</span></span>|<span data-ttu-id="abcb5-110">Description</span><span class="sxs-lookup"><span data-stu-id="abcb5-110">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="abcb5-111">Active l'ajout de types connus à utiliser lors de la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="abcb5-111">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="abcb5-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="abcb5-112">Parent Elements</span></span>  
  
|<span data-ttu-id="abcb5-113">Élément</span><span class="sxs-lookup"><span data-stu-id="abcb5-113">Element</span></span>|<span data-ttu-id="abcb5-114">Description</span><span class="sxs-lookup"><span data-stu-id="abcb5-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="abcb5-115">\<configuration> Appartient</span><span class="sxs-lookup"><span data-stu-id="abcb5-115">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="abcb5-116">Élément de niveau supérieur de la configuration.</span><span class="sxs-lookup"><span data-stu-id="abcb5-116">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="abcb5-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="abcb5-117">See also</span></span>

- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="abcb5-118">Utilisation de contrats de données</span><span class="sxs-lookup"><span data-stu-id="abcb5-118">Using Data Contracts</span></span>](../../../wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="abcb5-119">Types connus de contrats de données</span><span class="sxs-lookup"><span data-stu-id="abcb5-119">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)

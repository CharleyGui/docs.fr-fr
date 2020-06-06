---
title: <declaredTypes>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- declaredTypes element
- DataContractSerializer
- KnownTypes
- <declaredTypes> element
ms.assetid: f35184e4-9d9e-4d37-8fb4-d5b58220eb3e
ms.openlocfilehash: c45a4e67d0a2d98c0e9c1a91e07f25b81370244c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398061"
---
# \<declaredTypes>
<span data-ttu-id="9c0b0-101">Contient les types connus utilisés par le <xref:System.Runtime.Serialization.DataContractSerializer> lors de la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="9c0b0-101">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="9c0b0-102">Pour plus d’informations sur les contrats de données et les types connus, consultez [types connus de contrat de données](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="9c0b0-102">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<declaredTypes>**  
  
## <a name="syntax"></a><span data-ttu-id="9c0b0-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c0b0-103">Syntax</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer>
      <declaredTypes>
        <add type="String ">
          <knownType type="String">
            <parameter index="Integer"/>
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c0b0-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9c0b0-104">Attributes and Elements</span></span>  
 <span data-ttu-id="9c0b0-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9c0b0-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c0b0-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="9c0b0-106">Attributes</span></span>  
 <span data-ttu-id="9c0b0-107">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9c0b0-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9c0b0-108">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9c0b0-108">Child Elements</span></span>  
  
|<span data-ttu-id="9c0b0-109">Élément</span><span class="sxs-lookup"><span data-stu-id="9c0b0-109">Element</span></span>|<span data-ttu-id="9c0b0-110">Description</span><span class="sxs-lookup"><span data-stu-id="9c0b0-110">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-declaredtypes-element.md)|<span data-ttu-id="9c0b0-111">Ajoute des types qui requièrent des types connus.</span><span class="sxs-lookup"><span data-stu-id="9c0b0-111">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9c0b0-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9c0b0-112">Parent Elements</span></span>  
  
|<span data-ttu-id="9c0b0-113">Élément</span><span class="sxs-lookup"><span data-stu-id="9c0b0-113">Element</span></span>|<span data-ttu-id="9c0b0-114">Description</span><span class="sxs-lookup"><span data-stu-id="9c0b0-114">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="9c0b0-115">Contient les données de configuration correspondant au <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="9c0b0-115">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c0b0-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="9c0b0-116">Remarks</span></span>  
 <span data-ttu-id="9c0b0-117">Pour plus d’informations sur les types connus, consultez [types connus de contrat de données](../../../wcf/feature-details/data-contract-known-types.md) et <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="9c0b0-117">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c0b0-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="9c0b0-118">Example</span></span>  
 <span data-ttu-id="9c0b0-119">Le code XML suivant affiche les types déclarés et les types connus ajoutés à un `DataContractSerializer` élément.</span><span class="sxs-lookup"><span data-stu-id="9c0b0-119">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="9c0b0-120">L'exemple montre l'ajout de trois types.</span><span class="sxs-lookup"><span data-stu-id="9c0b0-120">The example shows three types being added.</span></span> <span data-ttu-id="9c0b0-121">Le premier est un type personnalisé nommé « Orders » qui utilise un type connu nommé « Item ».</span><span class="sxs-lookup"><span data-stu-id="9c0b0-121">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="9c0b0-122">Le deuxième est un <xref:System.Collections.Generic.List%601> qui utilise `Item` comme un type connu.</span><span class="sxs-lookup"><span data-stu-id="9c0b0-122">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="9c0b0-123">Le troisième et dernier est un <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="9c0b0-123">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="9c0b0-124">Le type de classe <xref:System.Collections.Generic.Dictionary%602> est un type générique contenant deux paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="9c0b0-124">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="9c0b0-125">Le premier représente la clé et le second représente la valeur.</span><span class="sxs-lookup"><span data-stu-id="9c0b0-125">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="9c0b0-126">L'exemple suivant ajoute un <xref:System.Collections.Generic.List%601> du deuxième type (la valeur) à la liste de types connus.</span><span class="sxs-lookup"><span data-stu-id="9c0b0-126">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="9c0b0-127">Vous devez utiliser l'attribut `index` pour spécifier le paramètre de type à utiliser dans le type connu.</span><span class="sxs-lookup"><span data-stu-id="9c0b0-127">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="9c0b0-128">Dans ce cas, le type de valeur est indiqué par l'ensemble d'attributs d'index ayant la valeur "1" (la collection est de base zéro).</span><span class="sxs-lookup"><span data-stu-id="9c0b0-128">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer>
      <declaredTypes>
        <add type="Examples.Types.Orders, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />
        </add>
        <add type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />
        </add>
        <add type="System.Collections.Generic.Dictionary`2, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
          <knownType type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">
            <parameter index="1"/>
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="9c0b0-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c0b0-129">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [<span data-ttu-id="9c0b0-130">Types connus de contrats de données</span><span class="sxs-lookup"><span data-stu-id="9c0b0-130">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<add>](add-of-declaredtypes-element.md)

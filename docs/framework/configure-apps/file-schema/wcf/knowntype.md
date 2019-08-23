---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: a0794314cfcb87df00d66b6832356fb130787eba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928866"
---
# <a name="knowntype"></a><span data-ttu-id="41297-101">\<knownType></span><span class="sxs-lookup"><span data-stu-id="41297-101">\<knownType></span></span>
<span data-ttu-id="41297-102">Indique un type devant être utilisé par le <xref:System.Runtime.Serialization.DataContractSerializer> pendant la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="41297-102">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="41297-103">L'élément indique un « type connu » renvoyé par un champ ou une propriété d'un « type déclaré ».</span><span class="sxs-lookup"><span data-stu-id="41297-103">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="41297-104">Pour plus d’informations, consultez [types connus de contrat de données](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="41297-104">For more information, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="41297-105">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="41297-105">\<system.runtime.serialization></span></span>  
<span data-ttu-id="41297-106">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="41297-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="41297-107">\<declaredTypes >, élément</span><span class="sxs-lookup"><span data-stu-id="41297-107">\<declaredTypes> Element</span></span>  
<span data-ttu-id="41297-108">\<Ajouter > de \<la > declaredTypes</span><span class="sxs-lookup"><span data-stu-id="41297-108">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="41297-109">\<knownType >, élément</span><span class="sxs-lookup"><span data-stu-id="41297-109">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41297-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41297-110">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="41297-111">Type</span><span class="sxs-lookup"><span data-stu-id="41297-111">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41297-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="41297-112">Attributes and Elements</span></span>  
 <span data-ttu-id="41297-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="41297-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41297-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="41297-114">Attributes</span></span>  
  
|<span data-ttu-id="41297-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="41297-115">Attribute</span></span>|<span data-ttu-id="41297-116">Description</span><span class="sxs-lookup"><span data-stu-id="41297-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="41297-117">type</span><span class="sxs-lookup"><span data-stu-id="41297-117">type</span></span>|<span data-ttu-id="41297-118">Indique le type (espace de noms compris), le nom de l'assembly, la version, la culture et le jeton de clé publique.</span><span class="sxs-lookup"><span data-stu-id="41297-118">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="41297-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="41297-119">Child Elements</span></span>  
  
|<span data-ttu-id="41297-120">Élément</span><span class="sxs-lookup"><span data-stu-id="41297-120">Element</span></span>|<span data-ttu-id="41297-121">Description</span><span class="sxs-lookup"><span data-stu-id="41297-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="41297-122">\<parameter></span><span class="sxs-lookup"><span data-stu-id="41297-122">\<parameter></span></span>](parameter.md)|<span data-ttu-id="41297-123">Indique un index de paramètre lorsque le type déclaré est générique.</span><span class="sxs-lookup"><span data-stu-id="41297-123">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="41297-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="41297-124">Parent Elements</span></span>  
  
|<span data-ttu-id="41297-125">Élément</span><span class="sxs-lookup"><span data-stu-id="41297-125">Element</span></span>|<span data-ttu-id="41297-126">Description</span><span class="sxs-lookup"><span data-stu-id="41297-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="41297-127">\<add></span><span class="sxs-lookup"><span data-stu-id="41297-127">\<add></span></span>](add-of-declaredtypes-element.md)|<span data-ttu-id="41297-128">Ajoute un type déclaré à la collection de types déclarés.</span><span class="sxs-lookup"><span data-stu-id="41297-128">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41297-129">Notes</span><span class="sxs-lookup"><span data-stu-id="41297-129">Remarks</span></span>  
 <span data-ttu-id="41297-130">Pour plus d’informations sur les types connus, consultez [types connus](../../../wcf/feature-details/data-contract-known-types.md) de <xref:System.Runtime.Serialization.DataContractSerializer>contrat de données et.</span><span class="sxs-lookup"><span data-stu-id="41297-130">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="41297-131">Pour obtenir un exemple d’utilisation de cet élément, consultez la [ \<> DataContractSerializer](datacontractserializer-element.md) .</span><span class="sxs-lookup"><span data-stu-id="41297-131">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41297-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="41297-132">Example</span></span>  
  
```xml  
<add type="MyCompany.Library.Shape,
           MyAssembly, Version=2.0.0.0, Culture=neutral,
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">
  <knownType type="MyCompany.Library.Circle,
                   MyAssembly, Version=2.0.0.0, Culture=neutral,
                   PublicKeyToken=XXXXXX,
                   processorArchitecture=MSIL"/>
</add>
```  
  
## <a name="see-also"></a><span data-ttu-id="41297-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41297-133">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="41297-134">Types connus de contrats de données</span><span class="sxs-lookup"><span data-stu-id="41297-134">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="41297-135">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="41297-135">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="41297-136">\<add></span><span class="sxs-lookup"><span data-stu-id="41297-136">\<add></span></span>](add-of-declaredtypes-element.md)

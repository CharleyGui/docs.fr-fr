---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 61f51b2ecd572ba254317a01e0f514503c7cc9e4
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397873"
---
# <a name="knowntype"></a><span data-ttu-id="b9b76-101">\<knownType></span><span class="sxs-lookup"><span data-stu-id="b9b76-101">\<knownType></span></span>
<span data-ttu-id="b9b76-102">Indique un type devant être utilisé par le <xref:System.Runtime.Serialization.DataContractSerializer> pendant la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="b9b76-102">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="b9b76-103">L'élément indique un « type connu » renvoyé par un champ ou une propriété d'un « type déclaré ».</span><span class="sxs-lookup"><span data-stu-id="b9b76-103">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="b9b76-104">Pour plus d’informations, consultez [types connus de contrat de données](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="b9b76-104">For more information, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
<span data-ttu-id="b9b76-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b9b76-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b9b76-106">&nbsp;&nbsp;[ **\<System. Runtime. Serialization >** ](system-runtime-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="b9b76-106">&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)</span></span>\
<span data-ttu-id="b9b76-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> dataContractSerializer**](datacontractserializer.md)</span><span class="sxs-lookup"><span data-stu-id="b9b76-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)</span></span>\
<span data-ttu-id="b9b76-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<declaredTypes >** ](declaredtypes.md)</span><span class="sxs-lookup"><span data-stu-id="b9b76-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)</span></span>\
<span data-ttu-id="b9b76-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Ajouter >** ](add-of-declaredtypes-element.md)</span><span class="sxs-lookup"><span data-stu-id="b9b76-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)</span></span>\
<span data-ttu-id="b9b76-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<knownType >**</span><span class="sxs-lookup"><span data-stu-id="b9b76-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9b76-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9b76-111">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="b9b76-112">Type</span><span class="sxs-lookup"><span data-stu-id="b9b76-112">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b9b76-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b9b76-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b9b76-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b9b76-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b9b76-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="b9b76-115">Attributes</span></span>  
  
|<span data-ttu-id="b9b76-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="b9b76-116">Attribute</span></span>|<span data-ttu-id="b9b76-117">Description</span><span class="sxs-lookup"><span data-stu-id="b9b76-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b9b76-118">type</span><span class="sxs-lookup"><span data-stu-id="b9b76-118">type</span></span>|<span data-ttu-id="b9b76-119">Indique le type (espace de noms compris), le nom de l'assembly, la version, la culture et le jeton de clé publique.</span><span class="sxs-lookup"><span data-stu-id="b9b76-119">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b9b76-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b9b76-120">Child Elements</span></span>  
  
|<span data-ttu-id="b9b76-121">Élément</span><span class="sxs-lookup"><span data-stu-id="b9b76-121">Element</span></span>|<span data-ttu-id="b9b76-122">Description</span><span class="sxs-lookup"><span data-stu-id="b9b76-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b9b76-123">\<parameter></span><span class="sxs-lookup"><span data-stu-id="b9b76-123">\<parameter></span></span>](parameter.md)|<span data-ttu-id="b9b76-124">Indique un index de paramètre lorsque le type déclaré est générique.</span><span class="sxs-lookup"><span data-stu-id="b9b76-124">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b9b76-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b9b76-125">Parent Elements</span></span>  
  
|<span data-ttu-id="b9b76-126">Élément</span><span class="sxs-lookup"><span data-stu-id="b9b76-126">Element</span></span>|<span data-ttu-id="b9b76-127">Description</span><span class="sxs-lookup"><span data-stu-id="b9b76-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b9b76-128">\<add></span><span class="sxs-lookup"><span data-stu-id="b9b76-128">\<add></span></span>](add-of-declaredtypes-element.md)|<span data-ttu-id="b9b76-129">Ajoute un type déclaré à la collection de types déclarés.</span><span class="sxs-lookup"><span data-stu-id="b9b76-129">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9b76-130">Notes</span><span class="sxs-lookup"><span data-stu-id="b9b76-130">Remarks</span></span>  
 <span data-ttu-id="b9b76-131">Pour plus d’informations sur les types connus, consultez [types connus](../../../wcf/feature-details/data-contract-known-types.md) de <xref:System.Runtime.Serialization.DataContractSerializer>contrat de données et.</span><span class="sxs-lookup"><span data-stu-id="b9b76-131">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="b9b76-132">Pour obtenir un exemple d’utilisation de cet élément, consultez la [ \<> DataContractSerializer](datacontractserializer-element.md) .</span><span class="sxs-lookup"><span data-stu-id="b9b76-132">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9b76-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="b9b76-133">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b9b76-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9b76-134">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="b9b76-135">Types connus de contrats de données</span><span class="sxs-lookup"><span data-stu-id="b9b76-135">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="b9b76-136">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="b9b76-136">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="b9b76-137">\<add></span><span class="sxs-lookup"><span data-stu-id="b9b76-137">\<add></span></span>](add-of-declaredtypes-element.md)

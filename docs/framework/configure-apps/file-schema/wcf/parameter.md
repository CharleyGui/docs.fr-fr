---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: 07fa410109a7bd2fa315132c4737301698bb3a93
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400109"
---
# <a name="parameter"></a><span data-ttu-id="2eeff-101">\<parameter></span><span class="sxs-lookup"><span data-stu-id="2eeff-101">\<parameter></span></span>
<span data-ttu-id="2eeff-102">Indique le paramètre générique lorsqu'un type déclaré est générique.</span><span class="sxs-lookup"><span data-stu-id="2eeff-102">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
<span data-ttu-id="2eeff-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2eeff-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2eeff-104">&nbsp;&nbsp;[ **\<System. Runtime. Serialization >** ](system-runtime-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="2eeff-104">&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)</span></span>\
<span data-ttu-id="2eeff-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> dataContractSerializer**](datacontractserializer.md)</span><span class="sxs-lookup"><span data-stu-id="2eeff-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)</span></span>\
<span data-ttu-id="2eeff-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<declaredTypes >** ](declaredtypes.md)</span><span class="sxs-lookup"><span data-stu-id="2eeff-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)</span></span>\
<span data-ttu-id="2eeff-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Ajouter >** ](add-of-declaredtypes-element.md)</span><span class="sxs-lookup"><span data-stu-id="2eeff-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)</span></span>\
<span data-ttu-id="2eeff-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<knownType >** ](knowntype.md)</span><span class="sxs-lookup"><span data-stu-id="2eeff-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownType>**](knowntype.md)</span></span>\
<span data-ttu-id="2eeff-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de paramètres**</span><span class="sxs-lookup"><span data-stu-id="2eeff-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<parameter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2eeff-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2eeff-110">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2eeff-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2eeff-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2eeff-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2eeff-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2eeff-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="2eeff-113">Attributes</span></span>  
  
|<span data-ttu-id="2eeff-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="2eeff-114">Attribute</span></span>|<span data-ttu-id="2eeff-115">Description</span><span class="sxs-lookup"><span data-stu-id="2eeff-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2eeff-116">index</span><span class="sxs-lookup"><span data-stu-id="2eeff-116">index</span></span>|<span data-ttu-id="2eeff-117">Lorsque le type déclaré est générique, spécifie le paramètre générique qui renverra le type connu.</span><span class="sxs-lookup"><span data-stu-id="2eeff-117">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="2eeff-118">type</span><span class="sxs-lookup"><span data-stu-id="2eeff-118">type</span></span>|<span data-ttu-id="2eeff-119">Chaîne décrivant le type connu utilisé pour la sérialisation et la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="2eeff-119">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="2eeff-120">Indexer l'Attribut</span><span class="sxs-lookup"><span data-stu-id="2eeff-120">index Attribute</span></span>  
  
|<span data-ttu-id="2eeff-121">Valeur</span><span class="sxs-lookup"><span data-stu-id="2eeff-121">Value</span></span>|<span data-ttu-id="2eeff-122">Description</span><span class="sxs-lookup"><span data-stu-id="2eeff-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2eeff-123">"0"</span><span class="sxs-lookup"><span data-stu-id="2eeff-123">"0"</span></span>|<span data-ttu-id="2eeff-124">Premier paramètre du type générique.</span><span class="sxs-lookup"><span data-stu-id="2eeff-124">The first parameter in the generic type.</span></span> <span data-ttu-id="2eeff-125">Par exemple, <xref:System.Collections.Generic.List%601> dispose d'un seul paramètre.</span><span class="sxs-lookup"><span data-stu-id="2eeff-125">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="2eeff-126">S'il est utilisé comme type déclaré, l'index a la valeur « 0 ».</span><span class="sxs-lookup"><span data-stu-id="2eeff-126">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="2eeff-127">"1"</span><span class="sxs-lookup"><span data-stu-id="2eeff-127">"1"</span></span>|<span data-ttu-id="2eeff-128">Second paramètre d'un type générique.</span><span class="sxs-lookup"><span data-stu-id="2eeff-128">The second parameter in a generic type.</span></span> <span data-ttu-id="2eeff-129">Par exemple, <xref:System.Collections.Generic.Dictionary%602> dispose de deux paramètres.</span><span class="sxs-lookup"><span data-stu-id="2eeff-129">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="2eeff-130">Si le type connu est renvoyé par le second paramètre, affectez à l'attribut d'index la valeur « 1 ».</span><span class="sxs-lookup"><span data-stu-id="2eeff-130">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2eeff-131">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2eeff-131">Child Elements</span></span>  
 <span data-ttu-id="2eeff-132">Aucun.</span><span class="sxs-lookup"><span data-stu-id="2eeff-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2eeff-133">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2eeff-133">Parent Elements</span></span>  
  
|<span data-ttu-id="2eeff-134">Élément</span><span class="sxs-lookup"><span data-stu-id="2eeff-134">Element</span></span>|<span data-ttu-id="2eeff-135">Description</span><span class="sxs-lookup"><span data-stu-id="2eeff-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2eeff-136">\<knownType></span><span class="sxs-lookup"><span data-stu-id="2eeff-136">\<knownType></span></span>](knowntype.md)|<span data-ttu-id="2eeff-137">Spécifie un type connu pouvant être renvoyé par un champ ou une propriété du type déclaré.</span><span class="sxs-lookup"><span data-stu-id="2eeff-137">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2eeff-138">Notes</span><span class="sxs-lookup"><span data-stu-id="2eeff-138">Remarks</span></span>  
 <span data-ttu-id="2eeff-139">Pour plus d’informations sur les types connus, consultez [types connus](../../../wcf/feature-details/data-contract-known-types.md) de <xref:System.Runtime.Serialization.DataContractSerializer>contrat de données et.</span><span class="sxs-lookup"><span data-stu-id="2eeff-139">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="2eeff-140">Pour obtenir un exemple d’utilisation de cet élément, consultez la [ \<> DataContractSerializer](datacontractserializer-element.md) .</span><span class="sxs-lookup"><span data-stu-id="2eeff-140">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="2eeff-141">Cet élément de configuration ne peut pas contenir les deux attributs simultanément.</span><span class="sxs-lookup"><span data-stu-id="2eeff-141">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="2eeff-142">Si c'est le cas, un <xref:System.Configuration.ConfigurationErrorsException> survient.</span><span class="sxs-lookup"><span data-stu-id="2eeff-142">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2eeff-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2eeff-143">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="2eeff-144">Types connus de contrats de données</span><span class="sxs-lookup"><span data-stu-id="2eeff-144">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="2eeff-145">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="2eeff-145">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="2eeff-146">\<add></span><span class="sxs-lookup"><span data-stu-id="2eeff-146">\<add></span></span>](add-of-declaredtypes-element.md)

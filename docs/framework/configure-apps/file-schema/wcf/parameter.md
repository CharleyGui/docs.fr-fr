---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: 07fa410109a7bd2fa315132c4737301698bb3a93
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400109"
---
# \<parameter>
<span data-ttu-id="4e27f-101">Indique le paramètre générique lorsqu'un type déclaré est générique.</span><span class="sxs-lookup"><span data-stu-id="4e27f-101">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownType>**](knowntype.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<parameter>**  
  
## <a name="syntax"></a><span data-ttu-id="4e27f-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e27f-102">Syntax</span></span>  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4e27f-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4e27f-103">Attributes and Elements</span></span>  
 <span data-ttu-id="4e27f-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4e27f-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4e27f-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="4e27f-105">Attributes</span></span>  
  
|<span data-ttu-id="4e27f-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="4e27f-106">Attribute</span></span>|<span data-ttu-id="4e27f-107">Description</span><span class="sxs-lookup"><span data-stu-id="4e27f-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4e27f-108">index</span><span class="sxs-lookup"><span data-stu-id="4e27f-108">index</span></span>|<span data-ttu-id="4e27f-109">Lorsque le type déclaré est générique, spécifie le paramètre générique qui renverra le type connu.</span><span class="sxs-lookup"><span data-stu-id="4e27f-109">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="4e27f-110">type</span><span class="sxs-lookup"><span data-stu-id="4e27f-110">type</span></span>|<span data-ttu-id="4e27f-111">Chaîne décrivant le type connu utilisé pour la sérialisation et la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="4e27f-111">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="4e27f-112">Indexer l'Attribut</span><span class="sxs-lookup"><span data-stu-id="4e27f-112">index Attribute</span></span>  
  
|<span data-ttu-id="4e27f-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="4e27f-113">Value</span></span>|<span data-ttu-id="4e27f-114">Description</span><span class="sxs-lookup"><span data-stu-id="4e27f-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4e27f-115">"0"</span><span class="sxs-lookup"><span data-stu-id="4e27f-115">"0"</span></span>|<span data-ttu-id="4e27f-116">Premier paramètre du type générique.</span><span class="sxs-lookup"><span data-stu-id="4e27f-116">The first parameter in the generic type.</span></span> <span data-ttu-id="4e27f-117">Par exemple, <xref:System.Collections.Generic.List%601> dispose d'un seul paramètre.</span><span class="sxs-lookup"><span data-stu-id="4e27f-117">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="4e27f-118">S'il est utilisé comme type déclaré, l'index a la valeur « 0 ».</span><span class="sxs-lookup"><span data-stu-id="4e27f-118">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="4e27f-119">"1"</span><span class="sxs-lookup"><span data-stu-id="4e27f-119">"1"</span></span>|<span data-ttu-id="4e27f-120">Second paramètre d'un type générique.</span><span class="sxs-lookup"><span data-stu-id="4e27f-120">The second parameter in a generic type.</span></span> <span data-ttu-id="4e27f-121">Par exemple, <xref:System.Collections.Generic.Dictionary%602> dispose de deux paramètres.</span><span class="sxs-lookup"><span data-stu-id="4e27f-121">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="4e27f-122">Si le type connu est renvoyé par le second paramètre, affectez à l'attribut d'index la valeur « 1 ».</span><span class="sxs-lookup"><span data-stu-id="4e27f-122">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4e27f-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4e27f-123">Child Elements</span></span>  
 <span data-ttu-id="4e27f-124">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4e27f-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4e27f-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4e27f-125">Parent Elements</span></span>  
  
|<span data-ttu-id="4e27f-126">Élément</span><span class="sxs-lookup"><span data-stu-id="4e27f-126">Element</span></span>|<span data-ttu-id="4e27f-127">Description</span><span class="sxs-lookup"><span data-stu-id="4e27f-127">Description</span></span>|  
|-------------|-----------------|  
|[\<knownType>](knowntype.md)|<span data-ttu-id="4e27f-128">Spécifie un type connu pouvant être renvoyé par un champ ou une propriété du type déclaré.</span><span class="sxs-lookup"><span data-stu-id="4e27f-128">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e27f-129">Remarques</span><span class="sxs-lookup"><span data-stu-id="4e27f-129">Remarks</span></span>  
 <span data-ttu-id="4e27f-130">Pour plus d’informations sur les types connus, consultez [types connus de contrat de données](../../../wcf/feature-details/data-contract-known-types.md) et <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="4e27f-130">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="4e27f-131">[\<dataContractSerializer>](datacontractserializer-element.md)Pour obtenir un exemple d’utilisation de cet élément, consultez.</span><span class="sxs-lookup"><span data-stu-id="4e27f-131">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="4e27f-132">Cet élément de configuration ne peut pas contenir les deux attributs simultanément.</span><span class="sxs-lookup"><span data-stu-id="4e27f-132">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="4e27f-133">Si c'est le cas, un <xref:System.Configuration.ConfigurationErrorsException> survient.</span><span class="sxs-lookup"><span data-stu-id="4e27f-133">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e27f-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e27f-134">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="4e27f-135">Types connus de contrats de données</span><span class="sxs-lookup"><span data-stu-id="4e27f-135">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<add>](add-of-declaredtypes-element.md)

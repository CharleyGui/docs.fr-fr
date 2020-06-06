---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 61f51b2ecd572ba254317a01e0f514503c7cc9e4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397873"
---
# \<knownType>
<span data-ttu-id="0c766-101">Indique un type devant être utilisé par le <xref:System.Runtime.Serialization.DataContractSerializer> pendant la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="0c766-101">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="0c766-102">L'élément indique un « type connu » renvoyé par un champ ou une propriété d'un « type déclaré ».</span><span class="sxs-lookup"><span data-stu-id="0c766-102">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="0c766-103">Pour plus d’informations, consultez [types connus de contrat de données](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="0c766-103">For more information, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-of-declaredtypes-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownType>**  
  
## <a name="syntax"></a><span data-ttu-id="0c766-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c766-104">Syntax</span></span>  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a><span data-ttu-id="0c766-105">Type</span><span class="sxs-lookup"><span data-stu-id="0c766-105">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c766-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0c766-106">Attributes and Elements</span></span>  
 <span data-ttu-id="0c766-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0c766-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c766-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="0c766-108">Attributes</span></span>  
  
|<span data-ttu-id="0c766-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="0c766-109">Attribute</span></span>|<span data-ttu-id="0c766-110">Description</span><span class="sxs-lookup"><span data-stu-id="0c766-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0c766-111">type</span><span class="sxs-lookup"><span data-stu-id="0c766-111">type</span></span>|<span data-ttu-id="0c766-112">Indique le type (espace de noms compris), le nom de l'assembly, la version, la culture et le jeton de clé publique.</span><span class="sxs-lookup"><span data-stu-id="0c766-112">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c766-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0c766-113">Child Elements</span></span>  
  
|<span data-ttu-id="0c766-114">Élément</span><span class="sxs-lookup"><span data-stu-id="0c766-114">Element</span></span>|<span data-ttu-id="0c766-115">Description</span><span class="sxs-lookup"><span data-stu-id="0c766-115">Description</span></span>|  
|-------------|-----------------|  
|[\<parameter>](parameter.md)|<span data-ttu-id="0c766-116">Indique un index de paramètre lorsque le type déclaré est générique.</span><span class="sxs-lookup"><span data-stu-id="0c766-116">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0c766-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0c766-117">Parent Elements</span></span>  
  
|<span data-ttu-id="0c766-118">Élément</span><span class="sxs-lookup"><span data-stu-id="0c766-118">Element</span></span>|<span data-ttu-id="0c766-119">Description</span><span class="sxs-lookup"><span data-stu-id="0c766-119">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-declaredtypes-element.md)|<span data-ttu-id="0c766-120">Ajoute un type déclaré à la collection de types déclarés.</span><span class="sxs-lookup"><span data-stu-id="0c766-120">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c766-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="0c766-121">Remarks</span></span>  
 <span data-ttu-id="0c766-122">Pour plus d’informations sur les types connus, consultez [types connus de contrat de données](../../../wcf/feature-details/data-contract-known-types.md) et <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="0c766-122">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="0c766-123">[\<dataContractSerializer>](datacontractserializer-element.md)Pour obtenir un exemple d’utilisation de cet élément, consultez.</span><span class="sxs-lookup"><span data-stu-id="0c766-123">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c766-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="0c766-124">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0c766-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c766-125">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="0c766-126">Types connus de contrats de données</span><span class="sxs-lookup"><span data-stu-id="0c766-126">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<add>](add-of-declaredtypes-element.md)

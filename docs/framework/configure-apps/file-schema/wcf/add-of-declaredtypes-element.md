---
title: <add>d' <declaredTypes> élément
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: a001e8743b2c24f68b1b23cbccf3e5ac162c4e71
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400660"
---
# <a name="add-of-declaredtypes-element"></a><span data-ttu-id="a784e-102">\<Ajouter > de \<l’élément de > declaredTypes</span><span class="sxs-lookup"><span data-stu-id="a784e-102">\<add> of \<declaredTypes> Element</span></span>
<span data-ttu-id="a784e-103">Ajoute un type utilisé par le <xref:System.Runtime.Serialization.DataContractSerializer> pendant la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="a784e-103">Adds a type used by the <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="a784e-104">Chaque type déclaré inclut les types connus qui seront renvoyés comme champ ou propriété du type déclaré.</span><span class="sxs-lookup"><span data-stu-id="a784e-104">Each declared type includes the known types that will be returned as a field or property of the declared type.</span></span>  
  
<span data-ttu-id="a784e-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a784e-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a784e-106">&nbsp;&nbsp;[ **\<System. Runtime. Serialization >** ](system-runtime-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="a784e-106">&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)</span></span>\
<span data-ttu-id="a784e-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> dataContractSerializer**](datacontractserializer.md)</span><span class="sxs-lookup"><span data-stu-id="a784e-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)</span></span>\
<span data-ttu-id="a784e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<declaredTypes >** ](declaredtypes.md)</span><span class="sxs-lookup"><span data-stu-id="a784e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)</span></span>\
<span data-ttu-id="a784e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Ajouter >**</span><span class="sxs-lookup"><span data-stu-id="a784e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a784e-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a784e-110">Syntax</span></span>  
  
```xml  
<add type="String">
  <knownType type="String">
    <parameter index="Integer"
               type="String" />
  </knownType>
</add>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a784e-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a784e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a784e-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a784e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a784e-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="a784e-113">Attributes</span></span>  
  
|<span data-ttu-id="a784e-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="a784e-114">Attribute</span></span>|<span data-ttu-id="a784e-115">Description</span><span class="sxs-lookup"><span data-stu-id="a784e-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a784e-116">type</span><span class="sxs-lookup"><span data-stu-id="a784e-116">type</span></span>|<span data-ttu-id="a784e-117">Attribut de chaîne requis.</span><span class="sxs-lookup"><span data-stu-id="a784e-117">Required string attribute.</span></span><br /><br /> <span data-ttu-id="a784e-118">Indique le nom du type (espace de noms compris), celui de l'assembly, le numéro de version, la culture et le jeton de clé publique.</span><span class="sxs-lookup"><span data-stu-id="a784e-118">Specifies the type name (including namespace), assembly name, version number, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a784e-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a784e-119">Child Elements</span></span>  
  
|<span data-ttu-id="a784e-120">Élément</span><span class="sxs-lookup"><span data-stu-id="a784e-120">Element</span></span>|<span data-ttu-id="a784e-121">Description</span><span class="sxs-lookup"><span data-stu-id="a784e-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a784e-122">\<knownType></span><span class="sxs-lookup"><span data-stu-id="a784e-122">\<knownType></span></span>](knowntype.md)|<span data-ttu-id="a784e-123">Spécifie le type connu correspondant au type déclaré en cours d'ajout.</span><span class="sxs-lookup"><span data-stu-id="a784e-123">Specifies the known type for the declared type that is being added.</span></span> <span data-ttu-id="a784e-124">Si le type déclaré est un type générique, vous devez également ajouter un élément de paramètre à l'élément `<knownType>` pour spécifier le paramètre générique utilisé pour renvoyer le type connu.</span><span class="sxs-lookup"><span data-stu-id="a784e-124">If the declared type is a generic type, then you must also add a parameter element to the `<knownType>` element to specify which generic parameter is used to return the known type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a784e-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a784e-125">Parent Elements</span></span>  
  
|<span data-ttu-id="a784e-126">Élément</span><span class="sxs-lookup"><span data-stu-id="a784e-126">Element</span></span>|<span data-ttu-id="a784e-127">Description</span><span class="sxs-lookup"><span data-stu-id="a784e-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a784e-128">\<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="a784e-128">\<declaredTypes></span></span>](declaredtypes.md)|<span data-ttu-id="a784e-129">Contient les types qui requièrent des types connus pendant la désérialisation effectuée par le <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="a784e-129">Contains the types that require known types during deserialization by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a784e-130">Notes</span><span class="sxs-lookup"><span data-stu-id="a784e-130">Remarks</span></span>  
 <span data-ttu-id="a784e-131">Pour plus d’informations sur les types connus, consultez [types connus](../../../wcf/feature-details/data-contract-known-types.md) de <xref:System.Runtime.Serialization.DataContractSerializer>contrat de données et.</span><span class="sxs-lookup"><span data-stu-id="a784e-131">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="a784e-132">Pour obtenir un exemple d’utilisation de cet élément, consultez la [ \<> DataContractSerializer](datacontractserializer-element.md) .</span><span class="sxs-lookup"><span data-stu-id="a784e-132">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a784e-133">Si vous ajoutez le type <xref:System.Object> comme `<declaredType>`, une <xref:System.Configuration.ConfigurationErrorsException> est levée.</span><span class="sxs-lookup"><span data-stu-id="a784e-133">If you add the <xref:System.Object> type as a `<declaredType>`, a <xref:System.Configuration.ConfigurationErrorsException> is thrown.</span></span> <span data-ttu-id="a784e-134">Ceci est dû au fait que le type <xref:System.Object> ne peut pas être utilisé comme type déclaré dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="a784e-134">This is because the <xref:System.Object> type cannot be used as a declared type in configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a784e-135">Exemples</span><span class="sxs-lookup"><span data-stu-id="a784e-135">Example</span></span>  
  
```xml  
<add type="MyCompany.Library.Shape,
           MyAssembly, Version=2.0.0.0, Culture=neutral,
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">
  <knownType type="MyCompany.Library.Circle,
                   MyAssembly, Version=2.0.0.0, Culture=neutral,
                   PublicKeyToken=XXXXXX,
                   processorArchitecture=MSIL" />
</add>
```  
  
## <a name="see-also"></a><span data-ttu-id="a784e-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a784e-136">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="a784e-137">Types connus de contrats de données</span><span class="sxs-lookup"><span data-stu-id="a784e-137">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="a784e-138">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="a784e-138">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="a784e-139">\<Ajouter > de \<la > declaredTypes</span><span class="sxs-lookup"><span data-stu-id="a784e-139">\<add> of \<declaredTypes></span></span>](add-of-declaredtypes-element.md)

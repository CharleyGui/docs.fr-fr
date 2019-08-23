---
title: <add>d' <declaredTypes> élément
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: 1ea008dcc72d555b00e9648ace95bb9522ffc2c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920185"
---
# <a name="add-of-declaredtypes-element"></a><span data-ttu-id="76745-102">\<Ajouter > de \<l’élément de > declaredTypes</span><span class="sxs-lookup"><span data-stu-id="76745-102">\<add> of \<declaredTypes> Element</span></span>
<span data-ttu-id="76745-103">Ajoute un type utilisé par le <xref:System.Runtime.Serialization.DataContractSerializer> pendant la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="76745-103">Adds a type used by the <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="76745-104">Chaque type déclaré inclut les types connus qui seront renvoyés comme champ ou propriété du type déclaré.</span><span class="sxs-lookup"><span data-stu-id="76745-104">Each declared type includes the known types that will be returned as a field or property of the declared type.</span></span>  
  
 <span data-ttu-id="76745-105">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="76745-105">system.runtime.serialization</span></span>  
<span data-ttu-id="76745-106">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="76745-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="76745-107">\<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="76745-107">\<declaredTypes></span></span>  
<span data-ttu-id="76745-108">\<Ajouter > de \<la > declaredTypes</span><span class="sxs-lookup"><span data-stu-id="76745-108">\<add> of \<declaredTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76745-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76745-109">Syntax</span></span>  
  
```xml  
<add type="String">
  <knownType type="String">
    <parameter index="Integer"
               type="String" />
  </knownType>
</add>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76745-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="76745-110">Attributes and Elements</span></span>  
 <span data-ttu-id="76745-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="76745-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76745-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="76745-112">Attributes</span></span>  
  
|<span data-ttu-id="76745-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="76745-113">Attribute</span></span>|<span data-ttu-id="76745-114">Description</span><span class="sxs-lookup"><span data-stu-id="76745-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="76745-115">type</span><span class="sxs-lookup"><span data-stu-id="76745-115">type</span></span>|<span data-ttu-id="76745-116">Attribut de chaîne requis.</span><span class="sxs-lookup"><span data-stu-id="76745-116">Required string attribute.</span></span><br /><br /> <span data-ttu-id="76745-117">Indique le nom du type (espace de noms compris), celui de l'assembly, le numéro de version, la culture et le jeton de clé publique.</span><span class="sxs-lookup"><span data-stu-id="76745-117">Specifies the type name (including namespace), assembly name, version number, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="76745-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="76745-118">Child Elements</span></span>  
  
|<span data-ttu-id="76745-119">Élément</span><span class="sxs-lookup"><span data-stu-id="76745-119">Element</span></span>|<span data-ttu-id="76745-120">Description</span><span class="sxs-lookup"><span data-stu-id="76745-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76745-121">\<knownType></span><span class="sxs-lookup"><span data-stu-id="76745-121">\<knownType></span></span>](knowntype.md)|<span data-ttu-id="76745-122">Spécifie le type connu correspondant au type déclaré en cours d'ajout.</span><span class="sxs-lookup"><span data-stu-id="76745-122">Specifies the known type for the declared type that is being added.</span></span> <span data-ttu-id="76745-123">Si le type déclaré est un type générique, vous devez également ajouter un élément de paramètre à l'élément `<knownType>` pour spécifier le paramètre générique utilisé pour renvoyer le type connu.</span><span class="sxs-lookup"><span data-stu-id="76745-123">If the declared type is a generic type, then you must also add a parameter element to the `<knownType>` element to specify which generic parameter is used to return the known type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="76745-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="76745-124">Parent Elements</span></span>  
  
|<span data-ttu-id="76745-125">Élément</span><span class="sxs-lookup"><span data-stu-id="76745-125">Element</span></span>|<span data-ttu-id="76745-126">Description</span><span class="sxs-lookup"><span data-stu-id="76745-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76745-127">\<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="76745-127">\<declaredTypes></span></span>](declaredtypes.md)|<span data-ttu-id="76745-128">Contient les types qui requièrent des types connus pendant la désérialisation effectuée par le <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="76745-128">Contains the types that require known types during deserialization by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76745-129">Notes</span><span class="sxs-lookup"><span data-stu-id="76745-129">Remarks</span></span>  
 <span data-ttu-id="76745-130">Pour plus d’informations sur les types connus, consultez [types connus](../../../wcf/feature-details/data-contract-known-types.md) de <xref:System.Runtime.Serialization.DataContractSerializer>contrat de données et.</span><span class="sxs-lookup"><span data-stu-id="76745-130">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="76745-131">Pour obtenir un exemple d’utilisation de cet élément, consultez la [ \<> DataContractSerializer](datacontractserializer-element.md) .</span><span class="sxs-lookup"><span data-stu-id="76745-131">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="76745-132">Si vous ajoutez le type <xref:System.Object> comme `<declaredType>`, une <xref:System.Configuration.ConfigurationErrorsException> est levée.</span><span class="sxs-lookup"><span data-stu-id="76745-132">If you add the <xref:System.Object> type as a `<declaredType>`, a <xref:System.Configuration.ConfigurationErrorsException> is thrown.</span></span> <span data-ttu-id="76745-133">Ceci est dû au fait que le type <xref:System.Object> ne peut pas être utilisé comme type déclaré dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="76745-133">This is because the <xref:System.Object> type cannot be used as a declared type in configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76745-134">Exemples</span><span class="sxs-lookup"><span data-stu-id="76745-134">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="76745-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="76745-135">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="76745-136">Types connus de contrats de données</span><span class="sxs-lookup"><span data-stu-id="76745-136">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="76745-137">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="76745-137">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="76745-138">\<Ajouter > de \<la > declaredTypes</span><span class="sxs-lookup"><span data-stu-id="76745-138">\<add> of \<declaredTypes></span></span>](add-of-declaredtypes-element.md)

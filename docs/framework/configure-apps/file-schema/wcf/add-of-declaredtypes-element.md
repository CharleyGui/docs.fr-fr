---
title: <add> d' <declaredTypes> élément
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: 9af47848b03074ec88f38a5884089bc50239ee50
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201666"
---
# <a name="add-of-declaredtypes-element"></a><span data-ttu-id="12715-102">\<add> d' \<declaredTypes> élément</span><span class="sxs-lookup"><span data-stu-id="12715-102">\<add> of \<declaredTypes> Element</span></span>

<span data-ttu-id="12715-103">Ajoute un type utilisé par le <xref:System.Runtime.Serialization.DataContractSerializer> pendant la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="12715-103">Adds a type used by the <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="12715-104">Chaque type déclaré inclut les types connus qui seront renvoyés comme champ ou propriété du type déclaré.</span><span class="sxs-lookup"><span data-stu-id="12715-104">Each declared type includes the known types that will be returned as a field or property of the declared type.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="12715-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12715-105">Syntax</span></span>  
  
```xml  
<add type="String">
  <knownType type="String">
    <parameter index="Integer"
               type="String" />
  </knownType>
</add>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="12715-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="12715-106">Attributes and Elements</span></span>  

 <span data-ttu-id="12715-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="12715-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="12715-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="12715-108">Attributes</span></span>  
  
|<span data-ttu-id="12715-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="12715-109">Attribute</span></span>|<span data-ttu-id="12715-110">Description</span><span class="sxs-lookup"><span data-stu-id="12715-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="12715-111">type</span><span class="sxs-lookup"><span data-stu-id="12715-111">type</span></span>|<span data-ttu-id="12715-112">Attribut de chaîne requis.</span><span class="sxs-lookup"><span data-stu-id="12715-112">Required string attribute.</span></span><br /><br /> <span data-ttu-id="12715-113">Indique le nom du type (espace de noms compris), celui de l'assembly, le numéro de version, la culture et le jeton de clé publique.</span><span class="sxs-lookup"><span data-stu-id="12715-113">Specifies the type name (including namespace), assembly name, version number, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="12715-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="12715-114">Child Elements</span></span>  
  
|<span data-ttu-id="12715-115">Élément</span><span class="sxs-lookup"><span data-stu-id="12715-115">Element</span></span>|<span data-ttu-id="12715-116">Description</span><span class="sxs-lookup"><span data-stu-id="12715-116">Description</span></span>|  
|-------------|-----------------|  
|[\<knownType>](knowntype.md)|<span data-ttu-id="12715-117">Spécifie le type connu correspondant au type déclaré en cours d'ajout.</span><span class="sxs-lookup"><span data-stu-id="12715-117">Specifies the known type for the declared type that is being added.</span></span> <span data-ttu-id="12715-118">Si le type déclaré est un type générique, vous devez également ajouter un élément de paramètre à l'élément `<knownType>` pour spécifier le paramètre générique utilisé pour renvoyer le type connu.</span><span class="sxs-lookup"><span data-stu-id="12715-118">If the declared type is a generic type, then you must also add a parameter element to the `<knownType>` element to specify which generic parameter is used to return the known type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="12715-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="12715-119">Parent Elements</span></span>  
  
|<span data-ttu-id="12715-120">Élément</span><span class="sxs-lookup"><span data-stu-id="12715-120">Element</span></span>|<span data-ttu-id="12715-121">Description</span><span class="sxs-lookup"><span data-stu-id="12715-121">Description</span></span>|  
|-------------|-----------------|  
|[\<declaredTypes>](declaredtypes.md)|<span data-ttu-id="12715-122">Contient les types qui requièrent des types connus pendant la désérialisation effectuée par le <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="12715-122">Contains the types that require known types during deserialization by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12715-123">Notes</span><span class="sxs-lookup"><span data-stu-id="12715-123">Remarks</span></span>  

 <span data-ttu-id="12715-124">Pour plus d’informations sur les types connus, consultez [types connus de contrat de données](../../../wcf/feature-details/data-contract-known-types.md) et <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="12715-124">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="12715-125">[\<dataContractSerializer>](datacontractserializer-element.md)Pour obtenir un exemple d’utilisation de cet élément, consultez.</span><span class="sxs-lookup"><span data-stu-id="12715-125">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12715-126">Si vous ajoutez le type <xref:System.Object> comme `<declaredType>`, une <xref:System.Configuration.ConfigurationErrorsException> est levée.</span><span class="sxs-lookup"><span data-stu-id="12715-126">If you add the <xref:System.Object> type as a `<declaredType>`, a <xref:System.Configuration.ConfigurationErrorsException> is thrown.</span></span> <span data-ttu-id="12715-127">Ceci est dû au fait que le type <xref:System.Object> ne peut pas être utilisé comme type déclaré dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="12715-127">This is because the <xref:System.Object> type cannot be used as a declared type in configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12715-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="12715-128">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="12715-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12715-129">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="12715-130">Types connus de contrats de données</span><span class="sxs-lookup"><span data-stu-id="12715-130">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [<span data-ttu-id="12715-131">\<add> of \<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="12715-131">\<add> of \<declaredTypes></span></span>](add-of-declaredtypes-element.md)

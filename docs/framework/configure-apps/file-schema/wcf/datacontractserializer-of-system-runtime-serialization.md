---
title: <dataContractSerializer>de < System. Runtime. Serialization >
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: eb556f533af1f99049382e9a2e34465f88d563db
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398077"
---
# <a name="datacontractserializer-of-systemruntimeserialization"></a><span data-ttu-id="8b2e0-102">\<> DataContractSerializer de \<System. Runtime. Serialization ></span><span class="sxs-lookup"><span data-stu-id="8b2e0-102">\<dataContractSerializer> of \<system.runtime.serialization></span></span>
<span data-ttu-id="8b2e0-103">Contient les données de configuration correspondant au <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="8b2e0-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
<span data-ttu-id="8b2e0-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8b2e0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8b2e0-105">&nbsp;&nbsp;[ **\<System. Runtime. Serialization >** ](system-runtime-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="8b2e0-105">&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)</span></span>\
<span data-ttu-id="8b2e0-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<> dataContractSerializer**</span><span class="sxs-lookup"><span data-stu-id="8b2e0-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b2e0-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b2e0-107">Syntax</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer ignoreExtensionDataObject="Boolean"
                            maxItemsInObjectGraph="Integer">
      <declaredTypes>
        <add type="String">
          <knownType type="String">
            <parameter index="Integer"
                       type="String" />
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8b2e0-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8b2e0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8b2e0-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8b2e0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8b2e0-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="8b2e0-110">Attributes</span></span>  
  
|<span data-ttu-id="8b2e0-111">Élément</span><span class="sxs-lookup"><span data-stu-id="8b2e0-111">Element</span></span>|<span data-ttu-id="8b2e0-112">Description</span><span class="sxs-lookup"><span data-stu-id="8b2e0-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8b2e0-113">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="8b2e0-113">ignoreExtensionDataObject</span></span>|<span data-ttu-id="8b2e0-114">Valeur booléenne indiquant si les données fournies par le point de terminaison doivent être ignorées ou non lors d'une sérialisation ou d'une désérialisation.</span><span class="sxs-lookup"><span data-stu-id="8b2e0-114">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="8b2e0-115">Cet attribut peut uniquement être défini sur le `<dataContractSerializer>` situé sous l'élément `<behavior>`.</span><span class="sxs-lookup"><span data-stu-id="8b2e0-115">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="8b2e0-116">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="8b2e0-116">maxItemsInObjectGraph</span></span>|<span data-ttu-id="8b2e0-117">Entier indiquant le nombre maximal d'éléments à sérialiser ou à désérialiser.</span><span class="sxs-lookup"><span data-stu-id="8b2e0-117">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="8b2e0-118">Cet attribut a la valeur 65 536.</span><span class="sxs-lookup"><span data-stu-id="8b2e0-118">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8b2e0-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8b2e0-119">Child Elements</span></span>  
  
|<span data-ttu-id="8b2e0-120">Élément</span><span class="sxs-lookup"><span data-stu-id="8b2e0-120">Element</span></span>|<span data-ttu-id="8b2e0-121">Description</span><span class="sxs-lookup"><span data-stu-id="8b2e0-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8b2e0-122">\<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="8b2e0-122">\<declaredTypes></span></span>](declaredtypes.md)|<span data-ttu-id="8b2e0-123">Contient les types connus utilisés par le <xref:System.Runtime.Serialization.DataContractSerializer> lors de la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="8b2e0-123">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="8b2e0-124">Pour plus d’informations sur les contrats de données et les types connus, consultez [types connus de contrat de données](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="8b2e0-124">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8b2e0-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8b2e0-125">Parent Elements</span></span>  
  
|<span data-ttu-id="8b2e0-126">Élément</span><span class="sxs-lookup"><span data-stu-id="8b2e0-126">Element</span></span>|<span data-ttu-id="8b2e0-127">Description</span><span class="sxs-lookup"><span data-stu-id="8b2e0-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8b2e0-128">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="8b2e0-128">\<system.runtime.serialization></span></span>](system-runtime-serialization.md)|<span data-ttu-id="8b2e0-129">Représente l'élément racine correspondant à la section d'espace de noms <xref:System.Runtime.Serialization> et contient des éléments permettant de définir les options du <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="8b2e0-129">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b2e0-130">Notes</span><span class="sxs-lookup"><span data-stu-id="8b2e0-130">Remarks</span></span>  
 <span data-ttu-id="8b2e0-131">Pour plus d’informations sur les types connus <xref:System.Runtime.Serialization.DataContractSerializer> , consultez et [types connus de contrat de données](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="8b2e0-131">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b2e0-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b2e0-132">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- [<span data-ttu-id="8b2e0-133">Types connus de contrats de données</span><span class="sxs-lookup"><span data-stu-id="8b2e0-133">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)

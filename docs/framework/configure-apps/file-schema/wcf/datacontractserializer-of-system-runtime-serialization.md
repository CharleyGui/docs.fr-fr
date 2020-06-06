---
title: <dataContractSerializer>de <System. Runtime. Serialization>
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: eb556f533af1f99049382e9a2e34465f88d563db
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398077"
---
# <a name="datacontractserializer-of-systemruntimeserialization"></a><span data-ttu-id="2c58d-102">\<dataContractSerializer> de \<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="2c58d-102">\<dataContractSerializer> of \<system.runtime.serialization></span></span>
<span data-ttu-id="2c58d-103">Contient les données de configuration correspondant au <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="2c58d-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="2c58d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c58d-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c58d-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2c58d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="2c58d-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2c58d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c58d-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="2c58d-107">Attributes</span></span>  
  
|<span data-ttu-id="2c58d-108">Élément</span><span class="sxs-lookup"><span data-stu-id="2c58d-108">Element</span></span>|<span data-ttu-id="2c58d-109">Description</span><span class="sxs-lookup"><span data-stu-id="2c58d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2c58d-110">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="2c58d-110">ignoreExtensionDataObject</span></span>|<span data-ttu-id="2c58d-111">Valeur booléenne indiquant si les données fournies par le point de terminaison doivent être ignorées ou non lors d'une sérialisation ou d'une désérialisation.</span><span class="sxs-lookup"><span data-stu-id="2c58d-111">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="2c58d-112">Cet attribut peut uniquement être défini sur le `<dataContractSerializer>` situé sous l'élément `<behavior>`.</span><span class="sxs-lookup"><span data-stu-id="2c58d-112">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="2c58d-113">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="2c58d-113">maxItemsInObjectGraph</span></span>|<span data-ttu-id="2c58d-114">Entier indiquant le nombre maximal d'éléments à sérialiser ou à désérialiser.</span><span class="sxs-lookup"><span data-stu-id="2c58d-114">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="2c58d-115">Cet attribut a la valeur 65 536.</span><span class="sxs-lookup"><span data-stu-id="2c58d-115">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2c58d-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2c58d-116">Child Elements</span></span>  
  
|<span data-ttu-id="2c58d-117">Élément</span><span class="sxs-lookup"><span data-stu-id="2c58d-117">Element</span></span>|<span data-ttu-id="2c58d-118">Description</span><span class="sxs-lookup"><span data-stu-id="2c58d-118">Description</span></span>|  
|-------------|-----------------|  
|[\<declaredTypes>](declaredtypes.md)|<span data-ttu-id="2c58d-119">Contient les types connus utilisés par le <xref:System.Runtime.Serialization.DataContractSerializer> lors de la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="2c58d-119">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="2c58d-120">Pour plus d’informations sur les contrats de données et les types connus, consultez [types connus de contrat de données](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="2c58d-120">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2c58d-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2c58d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="2c58d-122">Élément</span><span class="sxs-lookup"><span data-stu-id="2c58d-122">Element</span></span>|<span data-ttu-id="2c58d-123">Description</span><span class="sxs-lookup"><span data-stu-id="2c58d-123">Description</span></span>|  
|-------------|-----------------|  
|[\<system.runtime.serialization>](system-runtime-serialization.md)|<span data-ttu-id="2c58d-124">Représente l'élément racine correspondant à la section d'espace de noms <xref:System.Runtime.Serialization> et contient des éléments permettant de définir les options du <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="2c58d-124">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c58d-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="2c58d-125">Remarks</span></span>  
 <span data-ttu-id="2c58d-126">Pour plus d’informations sur les types connus, consultez <xref:System.Runtime.Serialization.DataContractSerializer> et [types connus de contrat de données](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="2c58d-126">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c58d-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2c58d-127">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- [<span data-ttu-id="2c58d-128">Types connus de contrats de données</span><span class="sxs-lookup"><span data-stu-id="2c58d-128">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)

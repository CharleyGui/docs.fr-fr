---
title: <dataContractSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: 2a994a8ba97d4c65fdaba5a85e779dd9935e3074
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195029"
---
# \<dataContractSerializer>

<span data-ttu-id="0fbe1-101">Contient les données de configuration correspondant au <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="0fbe1-101">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="0fbe1-102">Cet élément se produit dans deux hiérarchies différentes :</span><span class="sxs-lookup"><span data-stu-id="0fbe1-102">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="0fbe1-103">l'une est répertoriée dans la section Hiérarchie de schéma suivante et l'autre dans la section Notes.</span><span class="sxs-lookup"><span data-stu-id="0fbe1-103">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="0fbe1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0fbe1-104">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0fbe1-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0fbe1-105">Attributes and Elements</span></span>  

 <span data-ttu-id="0fbe1-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0fbe1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0fbe1-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="0fbe1-107">Attributes</span></span>  
  
|<span data-ttu-id="0fbe1-108">Élément</span><span class="sxs-lookup"><span data-stu-id="0fbe1-108">Element</span></span>|<span data-ttu-id="0fbe1-109">Description</span><span class="sxs-lookup"><span data-stu-id="0fbe1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0fbe1-110">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="0fbe1-110">ignoreExtensionDataObject</span></span>|<span data-ttu-id="0fbe1-111">Valeur booléenne indiquant si les données fournies par le point de terminaison doivent être ignorées ou non lors d'une sérialisation ou d'une désérialisation.</span><span class="sxs-lookup"><span data-stu-id="0fbe1-111">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="0fbe1-112">Cet attribut peut uniquement être défini sur le `<dataContractSerializer>` situé sous l'élément `<behavior>`.</span><span class="sxs-lookup"><span data-stu-id="0fbe1-112">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="0fbe1-113">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="0fbe1-113">maxItemsInObjectGraph</span></span>|<span data-ttu-id="0fbe1-114">Entier indiquant le nombre maximal d'éléments à sérialiser ou à désérialiser.</span><span class="sxs-lookup"><span data-stu-id="0fbe1-114">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="0fbe1-115">Cet attribut a la valeur 65 536.</span><span class="sxs-lookup"><span data-stu-id="0fbe1-115">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0fbe1-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0fbe1-116">Child Elements</span></span>  

 <span data-ttu-id="0fbe1-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0fbe1-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0fbe1-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0fbe1-118">Parent Elements</span></span>  
  
|<span data-ttu-id="0fbe1-119">Élément</span><span class="sxs-lookup"><span data-stu-id="0fbe1-119">Element</span></span>|<span data-ttu-id="0fbe1-120">Description</span><span class="sxs-lookup"><span data-stu-id="0fbe1-120">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-servicebehaviors.md)|<span data-ttu-id="0fbe1-121">Collection de paramètres correspondant au comportement d’un service.</span><span class="sxs-lookup"><span data-stu-id="0fbe1-121">A collection of settings for the behavior of a service.</span></span>|  
|[\<system.runtime.serialization>](system-runtime-serialization.md)|<span data-ttu-id="0fbe1-122">Représente l'élément racine correspondant à la section d'espace de noms <xref:System.Runtime.Serialization> et contient des éléments permettant de définir les options du <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="0fbe1-122">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0fbe1-123">Notes</span><span class="sxs-lookup"><span data-stu-id="0fbe1-123">Remarks</span></span>  

 <span data-ttu-id="0fbe1-124">Comme indiqué dans l’introduction de cette rubrique, il s’agit de la deuxième hiérarchie dans laquelle l' \<X509Extension> élément se produit.</span><span class="sxs-lookup"><span data-stu-id="0fbe1-124">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [\<system.runtime.serialization>](system-runtime-serialization.md)  
  
 [\<dataContractSerializer>](datacontractserializer-element.md)  
  
 <span data-ttu-id="0fbe1-125">Pour plus d'informations sur les types connus, consultez <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="0fbe1-125">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fbe1-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0fbe1-126">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="0fbe1-127">Types connus de contrats de données</span><span class="sxs-lookup"><span data-stu-id="0fbe1-127">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="0fbe1-128">Transfert de données et sérialisation</span><span class="sxs-lookup"><span data-stu-id="0fbe1-128">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)

---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: e6524c18780c062c3b5b7dfc2509449cb208e270
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400430"
---
# <a name="datacontractserializer"></a><span data-ttu-id="71e45-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="71e45-102">dataContractSerializer</span></span>
<span data-ttu-id="71e45-103">Contient les données de configuration correspondant au <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="71e45-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
<span data-ttu-id="71e45-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="71e45-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="71e45-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="71e45-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="71e45-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="71e45-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="71e45-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="71e45-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="71e45-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="71e45-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="71e45-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> dataContractSerializer**</span><span class="sxs-lookup"><span data-stu-id="71e45-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71e45-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71e45-110">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71e45-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="71e45-111">Attributes and Elements</span></span>  
 <span data-ttu-id="71e45-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="71e45-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71e45-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="71e45-113">Attributes</span></span>  
  
|<span data-ttu-id="71e45-114">Élément</span><span class="sxs-lookup"><span data-stu-id="71e45-114">Element</span></span>|<span data-ttu-id="71e45-115">Description</span><span class="sxs-lookup"><span data-stu-id="71e45-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="71e45-116">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="71e45-116">ignoreExtensionDataObject</span></span>|<span data-ttu-id="71e45-117">Valeur booléenne qui spécifie si les données fournies par le point de terminaison doivent être ignorées lorsqu'il est sérialisé ou désérialisé.</span><span class="sxs-lookup"><span data-stu-id="71e45-117">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="71e45-118">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="71e45-118">maxItemsInObjectGraph</span></span>|<span data-ttu-id="71e45-119">Entier indiquant le nombre maximal d'éléments à sérialiser ou à désérialiser.</span><span class="sxs-lookup"><span data-stu-id="71e45-119">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="71e45-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="71e45-120">Child Elements</span></span>  
 <span data-ttu-id="71e45-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="71e45-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="71e45-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="71e45-122">Parent Elements</span></span>  
  
|<span data-ttu-id="71e45-123">Élément</span><span class="sxs-lookup"><span data-stu-id="71e45-123">Element</span></span>|<span data-ttu-id="71e45-124">Description</span><span class="sxs-lookup"><span data-stu-id="71e45-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="71e45-125">\<behavior></span><span class="sxs-lookup"><span data-stu-id="71e45-125">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="71e45-126">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="71e45-126">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71e45-127">Notes</span><span class="sxs-lookup"><span data-stu-id="71e45-127">Remarks</span></span>  
 <span data-ttu-id="71e45-128">Pour plus d'informations les types connus, consultez la documentation <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="71e45-128">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="71e45-129">L'élément de comportement (si présent) `<dataContractSerializer>` doit toujours apparaître avant l'élément de comportement `<enableWebScript>` dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="71e45-129">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="71e45-130">Sinon, le comportement résultant n'est pas défini.</span><span class="sxs-lookup"><span data-stu-id="71e45-130">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71e45-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71e45-131">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="71e45-132">Types connus de contrats de données</span><span class="sxs-lookup"><span data-stu-id="71e45-132">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="71e45-133">Transfert de données et sérialisation</span><span class="sxs-lookup"><span data-stu-id="71e45-133">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)

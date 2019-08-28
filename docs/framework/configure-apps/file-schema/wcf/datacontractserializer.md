---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: 7952e6cc4d2fe7eaa77e297a650f7ffbd7aec785
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040930"
---
# <a name="datacontractserializer"></a><span data-ttu-id="7f48c-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="7f48c-102">dataContractSerializer</span></span>
<span data-ttu-id="7f48c-103">Contient les données de configuration correspondant au <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="7f48c-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="7f48c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7f48c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7f48c-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="7f48c-105">\<behaviors></span></span>  
<span data-ttu-id="7f48c-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="7f48c-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="7f48c-107">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="7f48c-107">\<behavior></span></span>  
<span data-ttu-id="7f48c-108">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="7f48c-108">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f48c-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f48c-109">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f48c-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7f48c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7f48c-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7f48c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f48c-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="7f48c-112">Attributes</span></span>  
  
|<span data-ttu-id="7f48c-113">Élément</span><span class="sxs-lookup"><span data-stu-id="7f48c-113">Element</span></span>|<span data-ttu-id="7f48c-114">Description</span><span class="sxs-lookup"><span data-stu-id="7f48c-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7f48c-115">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="7f48c-115">ignoreExtensionDataObject</span></span>|<span data-ttu-id="7f48c-116">Valeur booléenne qui spécifie si les données fournies par le point de terminaison doivent être ignorées lorsqu'il est sérialisé ou désérialisé.</span><span class="sxs-lookup"><span data-stu-id="7f48c-116">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="7f48c-117">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="7f48c-117">maxItemsInObjectGraph</span></span>|<span data-ttu-id="7f48c-118">Entier indiquant le nombre maximal d'éléments à sérialiser ou à désérialiser.</span><span class="sxs-lookup"><span data-stu-id="7f48c-118">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f48c-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7f48c-119">Child Elements</span></span>  
 <span data-ttu-id="7f48c-120">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7f48c-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7f48c-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7f48c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="7f48c-122">Élément</span><span class="sxs-lookup"><span data-stu-id="7f48c-122">Element</span></span>|<span data-ttu-id="7f48c-123">Description</span><span class="sxs-lookup"><span data-stu-id="7f48c-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f48c-124">\<behavior></span><span class="sxs-lookup"><span data-stu-id="7f48c-124">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="7f48c-125">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="7f48c-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f48c-126">Notes</span><span class="sxs-lookup"><span data-stu-id="7f48c-126">Remarks</span></span>  
 <span data-ttu-id="7f48c-127">Pour plus d'informations les types connus, consultez la documentation <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="7f48c-127">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="7f48c-128">L'élément de comportement (si présent) `<dataContractSerializer>` doit toujours apparaître avant l'élément de comportement `<enableWebScript>` dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="7f48c-128">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="7f48c-129">Sinon, le comportement résultant n'est pas défini.</span><span class="sxs-lookup"><span data-stu-id="7f48c-129">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f48c-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f48c-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="7f48c-131">Types connus de contrats de données</span><span class="sxs-lookup"><span data-stu-id="7f48c-131">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="7f48c-132">Transfert de données et sérialisation</span><span class="sxs-lookup"><span data-stu-id="7f48c-132">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)

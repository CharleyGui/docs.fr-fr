---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: 8814a48df8933cf08db78e397c24d42f2da26026
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919233"
---
# <a name="datacontractserializer"></a><span data-ttu-id="b73f3-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="b73f3-102">dataContractSerializer</span></span>
<span data-ttu-id="b73f3-103">Contient les données de configuration correspondant au <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="b73f3-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="b73f3-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b73f3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b73f3-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="b73f3-105">\<behaviors></span></span>  
<span data-ttu-id="b73f3-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="b73f3-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="b73f3-107">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="b73f3-107">\<behavior></span></span>  
<span data-ttu-id="b73f3-108">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="b73f3-108">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b73f3-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b73f3-109">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b73f3-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b73f3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b73f3-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b73f3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b73f3-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="b73f3-112">Attributes</span></span>  
  
|<span data-ttu-id="b73f3-113">Élément</span><span class="sxs-lookup"><span data-stu-id="b73f3-113">Element</span></span>|<span data-ttu-id="b73f3-114">Description</span><span class="sxs-lookup"><span data-stu-id="b73f3-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b73f3-115">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="b73f3-115">ignoreExtensionDataObject</span></span>|<span data-ttu-id="b73f3-116">Valeur booléenne qui spécifie si les données fournies par le point de terminaison doivent être ignorées lorsqu'il est sérialisé ou désérialisé.</span><span class="sxs-lookup"><span data-stu-id="b73f3-116">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="b73f3-117">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="b73f3-117">maxItemsInObjectGraph</span></span>|<span data-ttu-id="b73f3-118">Entier indiquant le nombre maximal d'éléments à sérialiser ou à désérialiser.</span><span class="sxs-lookup"><span data-stu-id="b73f3-118">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b73f3-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b73f3-119">Child Elements</span></span>  
 <span data-ttu-id="b73f3-120">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b73f3-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b73f3-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b73f3-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b73f3-122">Élément</span><span class="sxs-lookup"><span data-stu-id="b73f3-122">Element</span></span>|<span data-ttu-id="b73f3-123">Description</span><span class="sxs-lookup"><span data-stu-id="b73f3-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b73f3-124">\<behavior></span><span class="sxs-lookup"><span data-stu-id="b73f3-124">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="b73f3-125">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="b73f3-125">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b73f3-126">Notes</span><span class="sxs-lookup"><span data-stu-id="b73f3-126">Remarks</span></span>  
 <span data-ttu-id="b73f3-127">Pour plus d'informations les types connus, consultez la documentation <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="b73f3-127">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="b73f3-128">L'élément de comportement (si présent) `<dataContractSerializer>` doit toujours apparaître avant l'élément de comportement `<enableWebScript>` dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="b73f3-128">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="b73f3-129">Sinon, le comportement résultant n'est pas défini.</span><span class="sxs-lookup"><span data-stu-id="b73f3-129">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b73f3-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b73f3-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="b73f3-131">Types connus de contrats de données</span><span class="sxs-lookup"><span data-stu-id="b73f3-131">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="b73f3-132">Transfert de données et sérialisation</span><span class="sxs-lookup"><span data-stu-id="b73f3-132">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)

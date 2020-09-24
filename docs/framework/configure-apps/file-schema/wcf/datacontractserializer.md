---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: 0e4cbc50c25d4fa1f67f283f2b52d4b174428cd3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153922"
---
# <a name="datacontractserializer"></a><span data-ttu-id="6e1b4-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="6e1b4-102">dataContractSerializer</span></span>

<span data-ttu-id="6e1b4-103">Contient les données de configuration correspondant au <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="6e1b4-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="6e1b4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e1b4-104">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e1b4-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6e1b4-105">Attributes and Elements</span></span>  

 <span data-ttu-id="6e1b4-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6e1b4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e1b4-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="6e1b4-107">Attributes</span></span>  
  
|<span data-ttu-id="6e1b4-108">Élément</span><span class="sxs-lookup"><span data-stu-id="6e1b4-108">Element</span></span>|<span data-ttu-id="6e1b4-109">Description</span><span class="sxs-lookup"><span data-stu-id="6e1b4-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6e1b4-110">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="6e1b4-110">ignoreExtensionDataObject</span></span>|<span data-ttu-id="6e1b4-111">Valeur booléenne qui spécifie si les données fournies par le point de terminaison doivent être ignorées lorsqu'il est sérialisé ou désérialisé.</span><span class="sxs-lookup"><span data-stu-id="6e1b4-111">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="6e1b4-112">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="6e1b4-112">maxItemsInObjectGraph</span></span>|<span data-ttu-id="6e1b4-113">Entier indiquant le nombre maximal d'éléments à sérialiser ou à désérialiser.</span><span class="sxs-lookup"><span data-stu-id="6e1b4-113">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6e1b4-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6e1b4-114">Child Elements</span></span>  

 <span data-ttu-id="6e1b4-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6e1b4-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6e1b4-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6e1b4-116">Parent Elements</span></span>  
  
|<span data-ttu-id="6e1b4-117">Élément</span><span class="sxs-lookup"><span data-stu-id="6e1b4-117">Element</span></span>|<span data-ttu-id="6e1b4-118">Description</span><span class="sxs-lookup"><span data-stu-id="6e1b4-118">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="6e1b4-119">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="6e1b4-119">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e1b4-120">Notes</span><span class="sxs-lookup"><span data-stu-id="6e1b4-120">Remarks</span></span>  

 <span data-ttu-id="6e1b4-121">Pour plus d'informations les types connus, consultez la documentation <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="6e1b4-121">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="6e1b4-122">L'élément de comportement (si présent) `<dataContractSerializer>` doit toujours apparaître avant l'élément de comportement `<enableWebScript>` dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="6e1b4-122">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="6e1b4-123">Sinon, le comportement résultant n'est pas défini.</span><span class="sxs-lookup"><span data-stu-id="6e1b4-123">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e1b4-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e1b4-124">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="6e1b4-125">Types connus de contrats de données</span><span class="sxs-lookup"><span data-stu-id="6e1b4-125">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="6e1b4-126">Transfert de données et sérialisation</span><span class="sxs-lookup"><span data-stu-id="6e1b4-126">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)

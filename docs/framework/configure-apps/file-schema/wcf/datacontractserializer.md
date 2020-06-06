---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: e6524c18780c062c3b5b7dfc2509449cb208e270
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400430"
---
# <a name="datacontractserializer"></a><span data-ttu-id="14998-102">dataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="14998-102">dataContractSerializer</span></span>
<span data-ttu-id="14998-103">Contient les données de configuration correspondant au <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="14998-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="14998-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14998-104">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14998-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="14998-105">Attributes and Elements</span></span>  
 <span data-ttu-id="14998-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="14998-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14998-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="14998-107">Attributes</span></span>  
  
|<span data-ttu-id="14998-108">Élément</span><span class="sxs-lookup"><span data-stu-id="14998-108">Element</span></span>|<span data-ttu-id="14998-109">Description</span><span class="sxs-lookup"><span data-stu-id="14998-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="14998-110">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="14998-110">ignoreExtensionDataObject</span></span>|<span data-ttu-id="14998-111">Valeur booléenne qui spécifie si les données fournies par le point de terminaison doivent être ignorées lorsqu'il est sérialisé ou désérialisé.</span><span class="sxs-lookup"><span data-stu-id="14998-111">A Boolean value that specifies whether to ignore data supplied by the endpoint, when it is being serialized or deserialized.</span></span>|  
|<span data-ttu-id="14998-112">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="14998-112">maxItemsInObjectGraph</span></span>|<span data-ttu-id="14998-113">Entier indiquant le nombre maximal d'éléments à sérialiser ou à désérialiser.</span><span class="sxs-lookup"><span data-stu-id="14998-113">An integer that specifies the maximum number of items to serialize or deserialize.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="14998-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="14998-114">Child Elements</span></span>  
 <span data-ttu-id="14998-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="14998-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="14998-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="14998-116">Parent Elements</span></span>  
  
|<span data-ttu-id="14998-117">Élément</span><span class="sxs-lookup"><span data-stu-id="14998-117">Element</span></span>|<span data-ttu-id="14998-118">Description</span><span class="sxs-lookup"><span data-stu-id="14998-118">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="14998-119">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="14998-119">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14998-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="14998-120">Remarks</span></span>  
 <span data-ttu-id="14998-121">Pour plus d'informations les types connus, consultez la documentation <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="14998-121">See the <xref:System.Runtime.Serialization.DataContractSerializer> documentation for more information about known types.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="14998-122">L'élément de comportement (si présent) `<dataContractSerializer>` doit toujours apparaître avant l'élément de comportement `<enableWebScript>` dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="14998-122">The `<dataContractSerializer>` behavior element (if present) should always appear before the `<enableWebScript>` behavior element in the configuration file.</span></span> <span data-ttu-id="14998-123">Sinon, le comportement résultant n'est pas défini.</span><span class="sxs-lookup"><span data-stu-id="14998-123">Otherwise, the resulting behavior is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14998-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14998-124">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="14998-125">Types connus de contrats de données</span><span class="sxs-lookup"><span data-stu-id="14998-125">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="14998-126">Transfert de données et sérialisation</span><span class="sxs-lookup"><span data-stu-id="14998-126">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)

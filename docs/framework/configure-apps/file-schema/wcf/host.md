---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: 21d53df12c2b2d703b771e2b9cb5ee87dafc410e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918705"
---
# <a name="host"></a><span data-ttu-id="a29b1-101">\<host></span><span class="sxs-lookup"><span data-stu-id="a29b1-101">\<host></span></span>
<span data-ttu-id="a29b1-102">Spécifie les paramètres d'un hôte de service.</span><span class="sxs-lookup"><span data-stu-id="a29b1-102">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="a29b1-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a29b1-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="a29b1-104">\<services></span><span class="sxs-lookup"><span data-stu-id="a29b1-104">\<services></span></span>  
<span data-ttu-id="a29b1-105">\<service></span><span class="sxs-lookup"><span data-stu-id="a29b1-105">\<service></span></span>  
<span data-ttu-id="a29b1-106">\<host></span><span class="sxs-lookup"><span data-stu-id="a29b1-106">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a29b1-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a29b1-107">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="a29b1-108">Type</span><span class="sxs-lookup"><span data-stu-id="a29b1-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a29b1-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a29b1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a29b1-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a29b1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a29b1-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="a29b1-111">Attributes</span></span>  
 <span data-ttu-id="a29b1-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a29b1-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a29b1-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a29b1-113">Child Elements</span></span>  
  
|<span data-ttu-id="a29b1-114">Élément</span><span class="sxs-lookup"><span data-stu-id="a29b1-114">Element</span></span>|<span data-ttu-id="a29b1-115">Description</span><span class="sxs-lookup"><span data-stu-id="a29b1-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a29b1-116">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="a29b1-116">\<baseAddresses></span></span>](baseaddresses.md)|<span data-ttu-id="a29b1-117">Collection d’éléments `baseAddress` qui spécifie les adresses de base utilisées par l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="a29b1-117">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="a29b1-118">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="a29b1-118">\<timeOuts></span></span>](timeouts.md)|<span data-ttu-id="a29b1-119">Élément de configuration qui spécifie la durée d'ouverture ou de fermeture autorisée de l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="a29b1-119">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a29b1-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a29b1-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a29b1-121">Élément</span><span class="sxs-lookup"><span data-stu-id="a29b1-121">Element</span></span>|<span data-ttu-id="a29b1-122">Description</span><span class="sxs-lookup"><span data-stu-id="a29b1-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a29b1-123">\<service></span><span class="sxs-lookup"><span data-stu-id="a29b1-123">\<service></span></span>](service.md)|<span data-ttu-id="a29b1-124">Spécifie les paramètres d’un service Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a29b1-124">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a29b1-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a29b1-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="a29b1-126">Hébergement</span><span class="sxs-lookup"><span data-stu-id="a29b1-126">Hosting</span></span>](../../../wcf/feature-details/hosting.md)

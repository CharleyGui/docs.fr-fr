---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: b764bc21e9c4555b39c3d096212b6e6bcabb62ff
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855215"
---
# <a name="host"></a><span data-ttu-id="575b4-101">\<host></span><span class="sxs-lookup"><span data-stu-id="575b4-101">\<host></span></span>
<span data-ttu-id="575b4-102">Spécifie les paramètres d'un hôte de service.</span><span class="sxs-lookup"><span data-stu-id="575b4-102">Specifies settings for a service host.</span></span>  
  
<span data-ttu-id="575b4-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="575b4-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="575b4-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="575b4-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="575b4-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<services >** ](services.md)</span><span class="sxs-lookup"><span data-stu-id="575b4-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)</span></span>\
<span data-ttu-id="575b4-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de service**](service.md)</span><span class="sxs-lookup"><span data-stu-id="575b4-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)</span></span>\
<span data-ttu-id="575b4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> d’hôte**</span><span class="sxs-lookup"><span data-stu-id="575b4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<host>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="575b4-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="575b4-108">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="575b4-109">Type</span><span class="sxs-lookup"><span data-stu-id="575b4-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="575b4-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="575b4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="575b4-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="575b4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="575b4-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="575b4-112">Attributes</span></span>  
 <span data-ttu-id="575b4-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="575b4-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="575b4-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="575b4-114">Child Elements</span></span>  
  
|<span data-ttu-id="575b4-115">Élément</span><span class="sxs-lookup"><span data-stu-id="575b4-115">Element</span></span>|<span data-ttu-id="575b4-116">Description</span><span class="sxs-lookup"><span data-stu-id="575b4-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="575b4-117">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="575b4-117">\<baseAddresses></span></span>](baseaddresses.md)|<span data-ttu-id="575b4-118">Collection d’éléments `baseAddress` qui spécifie les adresses de base utilisées par l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="575b4-118">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="575b4-119">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="575b4-119">\<timeOuts></span></span>](timeouts.md)|<span data-ttu-id="575b4-120">Élément de configuration qui spécifie la durée d'ouverture ou de fermeture autorisée de l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="575b4-120">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="575b4-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="575b4-121">Parent Elements</span></span>  
  
|<span data-ttu-id="575b4-122">Élément</span><span class="sxs-lookup"><span data-stu-id="575b4-122">Element</span></span>|<span data-ttu-id="575b4-123">Description</span><span class="sxs-lookup"><span data-stu-id="575b4-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="575b4-124">\<service></span><span class="sxs-lookup"><span data-stu-id="575b4-124">\<service></span></span>](service.md)|<span data-ttu-id="575b4-125">Spécifie les paramètres d’un service Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="575b4-125">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="575b4-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="575b4-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="575b4-127">Hébergement</span><span class="sxs-lookup"><span data-stu-id="575b4-127">Hosting</span></span>](../../../wcf/feature-details/hosting.md)

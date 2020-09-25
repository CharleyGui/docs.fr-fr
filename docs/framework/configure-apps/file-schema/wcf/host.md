---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: 524226cbb826486def18c1b3b66c5b4a3c456dec
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185676"
---
# \<host>

<span data-ttu-id="ef766-101">Spécifie les paramètres d'un hôte de service.</span><span class="sxs-lookup"><span data-stu-id="ef766-101">Specifies settings for a service host.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<host>**  
  
## <a name="syntax"></a><span data-ttu-id="ef766-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef766-102">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="ef766-103">Type</span><span class="sxs-lookup"><span data-stu-id="ef766-103">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef766-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ef766-104">Attributes and Elements</span></span>  

 <span data-ttu-id="ef766-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ef766-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef766-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="ef766-106">Attributes</span></span>  

 <span data-ttu-id="ef766-107">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ef766-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ef766-108">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ef766-108">Child Elements</span></span>  
  
|<span data-ttu-id="ef766-109">Élément</span><span class="sxs-lookup"><span data-stu-id="ef766-109">Element</span></span>|<span data-ttu-id="ef766-110">Description</span><span class="sxs-lookup"><span data-stu-id="ef766-110">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddresses>](baseaddresses.md)|<span data-ttu-id="ef766-111">Collection d’éléments `baseAddress` qui spécifie les adresses de base utilisées par l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="ef766-111">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[\<timeOuts>](timeouts.md)|<span data-ttu-id="ef766-112">Élément de configuration qui spécifie la durée d'ouverture ou de fermeture autorisée de l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="ef766-112">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ef766-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ef766-113">Parent Elements</span></span>  
  
|<span data-ttu-id="ef766-114">Élément</span><span class="sxs-lookup"><span data-stu-id="ef766-114">Element</span></span>|<span data-ttu-id="ef766-115">Description</span><span class="sxs-lookup"><span data-stu-id="ef766-115">Description</span></span>|  
|-------------|-----------------|  
|[\<service>](service.md)|<span data-ttu-id="ef766-116">Spécifie les paramètres d’un service Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ef766-116">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ef766-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef766-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="ef766-118">Hosting</span><span class="sxs-lookup"><span data-stu-id="ef766-118">Hosting</span></span>](../../../wcf/feature-details/hosting.md)

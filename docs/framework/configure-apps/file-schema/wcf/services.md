---
title: <services>
ms.date: 03/30/2017
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
ms.openlocfilehash: 02d1d530f37f5082153c9aa6b9993fc4009917f5
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854979"
---
# <a name="services"></a><span data-ttu-id="2cf28-101">\<services></span><span class="sxs-lookup"><span data-stu-id="2cf28-101">\<services></span></span>
<span data-ttu-id="2cf28-102">Les services sont définis dans la section `services` du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="2cf28-102">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="2cf28-103">Chacun dispose de sa propre section de configuration de `service`.</span><span class="sxs-lookup"><span data-stu-id="2cf28-103">Each service has its own `service` configuration section.</span></span>  
  
<span data-ttu-id="2cf28-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2cf28-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2cf28-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2cf28-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2cf28-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<services >**</span><span class="sxs-lookup"><span data-stu-id="2cf28-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<services>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cf28-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2cf28-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service>
    </service>
  </services>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2cf28-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2cf28-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2cf28-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2cf28-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2cf28-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="2cf28-110">Attributes</span></span>  
 <span data-ttu-id="2cf28-111">Aucun</span><span class="sxs-lookup"><span data-stu-id="2cf28-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2cf28-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2cf28-112">Child Elements</span></span>  
  
|<span data-ttu-id="2cf28-113">Élément</span><span class="sxs-lookup"><span data-stu-id="2cf28-113">Element</span></span>|<span data-ttu-id="2cf28-114">Description</span><span class="sxs-lookup"><span data-stu-id="2cf28-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2cf28-115">\<service></span><span class="sxs-lookup"><span data-stu-id="2cf28-115">\<service></span></span>](service.md)|<span data-ttu-id="2cf28-116">Définissez le contrat de service, le comportement et les points de terminaison du service particulier.</span><span class="sxs-lookup"><span data-stu-id="2cf28-116">Define the service contract, behavior, and endpoints of the particular service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2cf28-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2cf28-117">Parent Elements</span></span>  
  
|<span data-ttu-id="2cf28-118">Élément</span><span class="sxs-lookup"><span data-stu-id="2cf28-118">Element</span></span>|<span data-ttu-id="2cf28-119">Description</span><span class="sxs-lookup"><span data-stu-id="2cf28-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2cf28-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2cf28-120">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="2cf28-121">Élément racine de tous les éléments de configuration Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="2cf28-121">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2cf28-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2cf28-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServicesSection>

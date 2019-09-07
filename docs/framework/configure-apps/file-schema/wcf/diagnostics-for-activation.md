---
title: <diagnostics>pour l’activation
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 33b2cd4c5ae1b4076892a61aa7e2b927efa1ddc1
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400407"
---
# <a name="diagnostics-for-activation"></a><span data-ttu-id="0d534-102">\<> de diagnostic pour l’activation</span><span class="sxs-lookup"><span data-stu-id="0d534-102">\<diagnostics> for Activation</span></span>
<span data-ttu-id="0d534-103">Configure les fonctionnalités de diagnostics de l’écouteur Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="0d534-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
<span data-ttu-id="0d534-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0d534-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0d534-105">&nbsp;&nbsp;[ **\<System. serviceModel. activation >** ](system-servicemodel-activation.md)</span><span class="sxs-lookup"><span data-stu-id="0d534-105">&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)</span></span>\
<span data-ttu-id="0d534-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<> de diagnostic**</span><span class="sxs-lookup"><span data-stu-id="0d534-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d534-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d534-107">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="0d534-108">Type</span><span class="sxs-lookup"><span data-stu-id="0d534-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d534-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0d534-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0d534-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0d534-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d534-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="0d534-111">Attributes</span></span>  
  
|<span data-ttu-id="0d534-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="0d534-112">Attribute</span></span>|<span data-ttu-id="0d534-113">Description</span><span class="sxs-lookup"><span data-stu-id="0d534-113">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="0d534-114">Valeur booléenne qui indique si les compteurs de performance sont activés à des fins de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="0d534-114">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0d534-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0d534-115">Child Elements</span></span>  
 <span data-ttu-id="0d534-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0d534-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0d534-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0d534-117">Parent Elements</span></span>  
  
|<span data-ttu-id="0d534-118">Élément</span><span class="sxs-lookup"><span data-stu-id="0d534-118">Element</span></span>|<span data-ttu-id="0d534-119">Description</span><span class="sxs-lookup"><span data-stu-id="0d534-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0d534-120">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="0d534-120">\<system.serviceModel.activation></span></span>](system-servicemodel-activation.md)|<span data-ttu-id="0d534-121">Contient les paramètres de configuration du processus de l'écouteur SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="0d534-121">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0d534-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d534-122">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>

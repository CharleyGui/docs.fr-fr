---
title: <diagnostics>pour l’activation
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 33b2cd4c5ae1b4076892a61aa7e2b927efa1ddc1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400407"
---
# <a name="diagnostics-for-activation"></a><span data-ttu-id="ee006-102">\<diagnostics>pour l’activation</span><span class="sxs-lookup"><span data-stu-id="ee006-102">\<diagnostics> for Activation</span></span>
<span data-ttu-id="ee006-103">Configure les fonctionnalités de diagnostics de l’écouteur Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ee006-103">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**  
  
## <a name="syntax"></a><span data-ttu-id="ee006-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee006-104">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="ee006-105">Type</span><span class="sxs-lookup"><span data-stu-id="ee006-105">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee006-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ee006-106">Attributes and Elements</span></span>  
 <span data-ttu-id="ee006-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ee006-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee006-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="ee006-108">Attributes</span></span>  
  
|<span data-ttu-id="ee006-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="ee006-109">Attribute</span></span>|<span data-ttu-id="ee006-110">Description</span><span class="sxs-lookup"><span data-stu-id="ee006-110">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="ee006-111">Valeur booléenne qui indique si les compteurs de performance sont activés à des fins de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="ee006-111">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ee006-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ee006-112">Child Elements</span></span>  
 <span data-ttu-id="ee006-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ee006-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ee006-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ee006-114">Parent Elements</span></span>  
  
|<span data-ttu-id="ee006-115">Élément</span><span class="sxs-lookup"><span data-stu-id="ee006-115">Element</span></span>|<span data-ttu-id="ee006-116">Description</span><span class="sxs-lookup"><span data-stu-id="ee006-116">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|<span data-ttu-id="ee006-117">Contient les paramètres de configuration du processus de l'écouteur SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="ee006-117">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ee006-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee006-118">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>

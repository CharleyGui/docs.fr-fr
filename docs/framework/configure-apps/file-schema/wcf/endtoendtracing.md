---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 1a274f15800c6a132994a2437943c83982de9de0
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855297"
---
# <a name="endtoendtracing"></a><span data-ttu-id="db70f-101">\<endToEndTracing></span><span class="sxs-lookup"><span data-stu-id="db70f-101">\<endToEndTracing></span></span>
<span data-ttu-id="db70f-102">Élément de configuration qui vous permet d'activer et désactiver différents aspects du suivi de bout en bout pendant l'exécution d'une application de service.</span><span class="sxs-lookup"><span data-stu-id="db70f-102">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
<span data-ttu-id="db70f-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="db70f-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="db70f-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="db70f-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="db70f-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de diagnostic**](diagnostics.md)</span><span class="sxs-lookup"><span data-stu-id="db70f-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)</span></span>\
<span data-ttu-id="db70f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<endToEndTracing >**</span><span class="sxs-lookup"><span data-stu-id="db70f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endToEndTracing>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db70f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db70f-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db70f-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="db70f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="db70f-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="db70f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db70f-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="db70f-110">Attributes</span></span>  
  
|<span data-ttu-id="db70f-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="db70f-111">Attribute</span></span>|<span data-ttu-id="db70f-112">Description</span><span class="sxs-lookup"><span data-stu-id="db70f-112">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="db70f-113">Valeur booléenne qui spécifie si le suivi d'activité est activé.</span><span class="sxs-lookup"><span data-stu-id="db70f-113">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="db70f-114">Valeur booléenne qui spécifie si le suivi de flux de messages est activé.</span><span class="sxs-lookup"><span data-stu-id="db70f-114">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="db70f-115">Valeur booléenne qui spécifie si l'attribut de propagation a la valeur True.</span><span class="sxs-lookup"><span data-stu-id="db70f-115">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="db70f-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="db70f-116">Child Elements</span></span>  
 <span data-ttu-id="db70f-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="db70f-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="db70f-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="db70f-118">Parent Elements</span></span>  
  
|<span data-ttu-id="db70f-119">Élément</span><span class="sxs-lookup"><span data-stu-id="db70f-119">Element</span></span>|<span data-ttu-id="db70f-120">Description</span><span class="sxs-lookup"><span data-stu-id="db70f-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="db70f-121">\<diagnostics></span><span class="sxs-lookup"><span data-stu-id="db70f-121">\<diagnostics></span></span>](diagnostics.md)|<span data-ttu-id="db70f-122">Définit des paramètres WCF pour l'inspection et le contrôle au moment de l'exécution pour l'administrateur.</span><span class="sxs-lookup"><span data-stu-id="db70f-122">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="db70f-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db70f-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="db70f-124">Suivi de bout en bout</span><span class="sxs-lookup"><span data-stu-id="db70f-124">End-to-End Tracing</span></span>](../../../wcf/diagnostics/tracing/end-to-end-tracing.md)

---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 6b23728451a051f21ad3863b9a29e6290c3c837a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919016"
---
# <a name="endtoendtracing"></a><span data-ttu-id="91bd9-101">\<endToEndTracing></span><span class="sxs-lookup"><span data-stu-id="91bd9-101">\<endToEndTracing></span></span>
<span data-ttu-id="91bd9-102">Élément de configuration qui vous permet d'activer et désactiver différents aspects du suivi de bout en bout pendant l'exécution d'une application de service.</span><span class="sxs-lookup"><span data-stu-id="91bd9-102">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
 <span data-ttu-id="91bd9-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="91bd9-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="91bd9-104">\<> de diagnostic</span><span class="sxs-lookup"><span data-stu-id="91bd9-104">\<diagnostic></span></span>  
<span data-ttu-id="91bd9-105">\<endToEndTracing></span><span class="sxs-lookup"><span data-stu-id="91bd9-105">\<endToEndTracing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91bd9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91bd9-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91bd9-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="91bd9-107">Attributes and Elements</span></span>  
 <span data-ttu-id="91bd9-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="91bd9-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91bd9-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="91bd9-109">Attributes</span></span>  
  
|<span data-ttu-id="91bd9-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="91bd9-110">Attribute</span></span>|<span data-ttu-id="91bd9-111">Description</span><span class="sxs-lookup"><span data-stu-id="91bd9-111">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="91bd9-112">Valeur booléenne qui spécifie si le suivi d'activité est activé.</span><span class="sxs-lookup"><span data-stu-id="91bd9-112">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="91bd9-113">Valeur booléenne qui spécifie si le suivi de flux de messages est activé.</span><span class="sxs-lookup"><span data-stu-id="91bd9-113">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="91bd9-114">Valeur booléenne qui spécifie si l'attribut de propagation a la valeur True.</span><span class="sxs-lookup"><span data-stu-id="91bd9-114">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="91bd9-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="91bd9-115">Child Elements</span></span>  
 <span data-ttu-id="91bd9-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="91bd9-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="91bd9-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="91bd9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="91bd9-118">Élément</span><span class="sxs-lookup"><span data-stu-id="91bd9-118">Element</span></span>|<span data-ttu-id="91bd9-119">Description</span><span class="sxs-lookup"><span data-stu-id="91bd9-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91bd9-120">\<diagnostics></span><span class="sxs-lookup"><span data-stu-id="91bd9-120">\<diagnostics></span></span>](diagnostics.md)|<span data-ttu-id="91bd9-121">Définit des paramètres WCF pour l'inspection et le contrôle au moment de l'exécution pour l'administrateur.</span><span class="sxs-lookup"><span data-stu-id="91bd9-121">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="91bd9-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91bd9-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="91bd9-123">Suivi de bout en bout</span><span class="sxs-lookup"><span data-stu-id="91bd9-123">End-to-End Tracing</span></span>](../../../wcf/diagnostics/tracing/end-to-end-tracing.md)

---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 1a274f15800c6a132994a2437943c83982de9de0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855297"
---
# \<endToEndTracing>
<span data-ttu-id="5fdfd-101">Élément de configuration qui vous permet d'activer et désactiver différents aspects du suivi de bout en bout pendant l'exécution d'une application de service.</span><span class="sxs-lookup"><span data-stu-id="5fdfd-101">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endToEndTracing>**  
  
## <a name="syntax"></a><span data-ttu-id="5fdfd-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5fdfd-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5fdfd-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5fdfd-103">Attributes and Elements</span></span>  
 <span data-ttu-id="5fdfd-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5fdfd-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5fdfd-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="5fdfd-105">Attributes</span></span>  
  
|<span data-ttu-id="5fdfd-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="5fdfd-106">Attribute</span></span>|<span data-ttu-id="5fdfd-107">Description</span><span class="sxs-lookup"><span data-stu-id="5fdfd-107">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="5fdfd-108">Valeur booléenne qui spécifie si le suivi d'activité est activé.</span><span class="sxs-lookup"><span data-stu-id="5fdfd-108">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="5fdfd-109">Valeur booléenne qui spécifie si le suivi de flux de messages est activé.</span><span class="sxs-lookup"><span data-stu-id="5fdfd-109">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="5fdfd-110">Valeur booléenne qui spécifie si l'attribut de propagation a la valeur True.</span><span class="sxs-lookup"><span data-stu-id="5fdfd-110">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5fdfd-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5fdfd-111">Child Elements</span></span>  
 <span data-ttu-id="5fdfd-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5fdfd-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5fdfd-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5fdfd-113">Parent Elements</span></span>  
  
|<span data-ttu-id="5fdfd-114">Élément</span><span class="sxs-lookup"><span data-stu-id="5fdfd-114">Element</span></span>|<span data-ttu-id="5fdfd-115">Description</span><span class="sxs-lookup"><span data-stu-id="5fdfd-115">Description</span></span>|  
|-------------|-----------------|  
|[\<diagnostics>](diagnostics.md)|<span data-ttu-id="5fdfd-116">Définit des paramètres WCF pour l'inspection et le contrôle au moment de l'exécution pour l'administrateur.</span><span class="sxs-lookup"><span data-stu-id="5fdfd-116">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5fdfd-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5fdfd-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="5fdfd-118">Suivi de bout en bout</span><span class="sxs-lookup"><span data-stu-id="5fdfd-118">End-to-End Tracing</span></span>](../../../wcf/diagnostics/tracing/end-to-end-tracing.md)

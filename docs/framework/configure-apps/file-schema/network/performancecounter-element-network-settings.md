---
title: <performanceCounter>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounter element
- <performanceCounter> element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
ms.openlocfilehash: 3fe6b19d0055aafad859b55960800d9786d7fa08
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697999"
---
# <a name="performancecounter-element-network-settings"></a><span data-ttu-id="ebc1f-102">\<performanceCounter >, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="ebc1f-102">\<performanceCounter> Element (Network Settings)</span></span>
<span data-ttu-id="ebc1f-103">Active ou désactive les compteurs de performance réseau.</span><span class="sxs-lookup"><span data-stu-id="ebc1f-103">Enables or disables networking performance counters.</span></span>  
  
[<span data-ttu-id="ebc1f-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="ebc1f-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="ebc1f-105">&nbsp; @ no__t-1[ **@no__t -4System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="ebc1f-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="ebc1f-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<settings >** ](settings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="ebc1f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)</span></span>  
<span data-ttu-id="ebc1f-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<performanceCounters >**</span><span class="sxs-lookup"><span data-stu-id="ebc1f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebc1f-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ebc1f-108">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ebc1f-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ebc1f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ebc1f-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ebc1f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ebc1f-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="ebc1f-111">Attributes</span></span>  
  
|<span data-ttu-id="ebc1f-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="ebc1f-112">Attribute</span></span>|<span data-ttu-id="ebc1f-113">Description</span><span class="sxs-lookup"><span data-stu-id="ebc1f-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="ebc1f-114">Spécifie si les compteurs de performance réseau sont activés.</span><span class="sxs-lookup"><span data-stu-id="ebc1f-114">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="ebc1f-115">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="ebc1f-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ebc1f-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ebc1f-116">Child Elements</span></span>  
 <span data-ttu-id="ebc1f-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ebc1f-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ebc1f-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ebc1f-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ebc1f-119">Élément</span><span class="sxs-lookup"><span data-stu-id="ebc1f-119">Element</span></span>|<span data-ttu-id="ebc1f-120">Description</span><span class="sxs-lookup"><span data-stu-id="ebc1f-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ebc1f-121">settings</span><span class="sxs-lookup"><span data-stu-id="ebc1f-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="ebc1f-122">Configure les options réseau de base pour l’espace de noms <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="ebc1f-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebc1f-123">Notes</span><span class="sxs-lookup"><span data-stu-id="ebc1f-123">Remarks</span></span>  
 <span data-ttu-id="ebc1f-124">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="ebc1f-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="ebc1f-125">Les compteurs de performance réseau doivent être activés dans le fichier de configuration pour pouvoir être utilisés.</span><span class="sxs-lookup"><span data-stu-id="ebc1f-125">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="ebc1f-126">L'ensemble des compteurs de performance réseau sont activés ou désactivés avec un paramètre unique dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="ebc1f-126">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="ebc1f-127">Il n'est pas possible d'activer ou de désactiver ces compteurs de manière individuelle.</span><span class="sxs-lookup"><span data-stu-id="ebc1f-127">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="ebc1f-128">Pour plus d’informations sur les compteurs de performances de mise en réseau spécifiques, consultez [compteurs de performances de mise en réseau](../../../debug-trace-profile/performance-counters.md#networking).</span><span class="sxs-lookup"><span data-stu-id="ebc1f-128">For more information on the specific networking performance counters, see [Networking Performance Counters](../../../debug-trace-profile/performance-counters.md#networking).</span></span>  
  
 <span data-ttu-id="ebc1f-129">La valeur par défaut est que les compteurs de performance réseau sont désactivés.</span><span class="sxs-lookup"><span data-stu-id="ebc1f-129">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="ebc1f-130">La propriété <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> peut être utilisée pour récupérer la valeur actuelle de l’attribut **activé** à partir des fichiers de configuration applicables.</span><span class="sxs-lookup"><span data-stu-id="ebc1f-130">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ebc1f-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="ebc1f-131">Example</span></span>  
 <span data-ttu-id="ebc1f-132">L’exemple suivant montre comment configurer le <xref:System.Net> et les espaces de noms associés pour activer les compteurs de performances de mise en réseau.</span><span class="sxs-lookup"><span data-stu-id="ebc1f-132">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <performanceCounters  
        enabled="true"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ebc1f-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ebc1f-133">See also</span></span>

- <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="ebc1f-134">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="ebc1f-134">Network Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ebc1f-135">Compteurs de performances de mise en réseau</span><span class="sxs-lookup"><span data-stu-id="ebc1f-135">Networking Performance Counters</span></span>](../../../debug-trace-profile/performance-counters.md#networking)

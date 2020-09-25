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
ms.openlocfilehash: 4859f3a9e6de4f1bf8a56212bfe01f94d66f5650
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190239"
---
# <a name="performancecounter-element-network-settings"></a><span data-ttu-id="83d53-102">\<performanceCounter>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="83d53-102">\<performanceCounter> Element (Network Settings)</span></span>

<span data-ttu-id="83d53-103">Active ou désactive les compteurs de performance réseau.</span><span class="sxs-lookup"><span data-stu-id="83d53-103">Enables or disables networking performance counters.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**

## <a name="syntax"></a><span data-ttu-id="83d53-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83d53-104">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83d53-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="83d53-105">Attributes and Elements</span></span>  

 <span data-ttu-id="83d53-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="83d53-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83d53-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="83d53-107">Attributes</span></span>  
  
|<span data-ttu-id="83d53-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="83d53-108">Attribute</span></span>|<span data-ttu-id="83d53-109">Description</span><span class="sxs-lookup"><span data-stu-id="83d53-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="83d53-110">Spécifie si les compteurs de performance réseau sont activés.</span><span class="sxs-lookup"><span data-stu-id="83d53-110">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="83d53-111">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="83d53-111">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="83d53-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="83d53-112">Child Elements</span></span>  

 <span data-ttu-id="83d53-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="83d53-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="83d53-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="83d53-114">Parent Elements</span></span>  
  
|<span data-ttu-id="83d53-115">Élément</span><span class="sxs-lookup"><span data-stu-id="83d53-115">Element</span></span>|<span data-ttu-id="83d53-116">Description</span><span class="sxs-lookup"><span data-stu-id="83d53-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="83d53-117">settings</span><span class="sxs-lookup"><span data-stu-id="83d53-117">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="83d53-118">Configure les options réseau de base pour l’espace de noms <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="83d53-118">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83d53-119">Notes</span><span class="sxs-lookup"><span data-stu-id="83d53-119">Remarks</span></span>  

 <span data-ttu-id="83d53-120">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="83d53-120">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="83d53-121">Les compteurs de performance réseau doivent être activés dans le fichier de configuration pour pouvoir être utilisés.</span><span class="sxs-lookup"><span data-stu-id="83d53-121">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="83d53-122">L'ensemble des compteurs de performance réseau sont activés ou désactivés avec un paramètre unique dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="83d53-122">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="83d53-123">Il n'est pas possible d'activer ou de désactiver ces compteurs de manière individuelle.</span><span class="sxs-lookup"><span data-stu-id="83d53-123">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="83d53-124">Pour plus d’informations sur les compteurs de performances de mise en réseau spécifiques, consultez [compteurs de performances de mise en réseau](../../../debug-trace-profile/performance-counters.md#networking-performance-counters).</span><span class="sxs-lookup"><span data-stu-id="83d53-124">For more information on the specific networking performance counters, see [Networking performance counters](../../../debug-trace-profile/performance-counters.md#networking-performance-counters).</span></span>  
  
 <span data-ttu-id="83d53-125">La valeur par défaut est que les compteurs de performance réseau sont désactivés.</span><span class="sxs-lookup"><span data-stu-id="83d53-125">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="83d53-126">La <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> propriété peut être utilisée pour récupérer la valeur actuelle de l’attribut **activé** à partir des fichiers de configuration applicables.</span><span class="sxs-lookup"><span data-stu-id="83d53-126">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83d53-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="83d53-127">Example</span></span>  

 <span data-ttu-id="83d53-128">L’exemple suivant montre comment configurer le <xref:System.Net> et les espaces de noms associés pour activer les compteurs de performances de mise en réseau.</span><span class="sxs-lookup"><span data-stu-id="83d53-128">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="83d53-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83d53-129">See also</span></span>

- <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="83d53-130">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="83d53-130">Network Settings Schema</span></span>](index.md)
- [<span data-ttu-id="83d53-131">Compteurs de performances de mise en réseau</span><span class="sxs-lookup"><span data-stu-id="83d53-131">Networking Performance Counters</span></span>](../../../debug-trace-profile/performance-counters.md#networking-performance-counters)

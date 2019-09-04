---
title: Élément <appDomainResourceMonitoring>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1395ee64d94e33693344b678c7a949665f994079
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252821"
---
# <a name="appdomainresourcemonitoring-element"></a><span data-ttu-id="196ee-102">\<appDomainResourceMonitoring >, élément</span><span class="sxs-lookup"><span data-stu-id="196ee-102">\<appDomainResourceMonitoring> Element</span></span>
<span data-ttu-id="196ee-103">Demande au runtime de collecter des statistiques sur tous les domaines d’application du processus sur toute sa durée.</span><span class="sxs-lookup"><span data-stu-id="196ee-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
<span data-ttu-id="196ee-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="196ee-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="196ee-105">&nbsp;&nbsp;[ **\<> d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="196ee-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="196ee-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<appDomainResourceMonitoring>**</span><span class="sxs-lookup"><span data-stu-id="196ee-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainResourceMonitoring>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="196ee-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="196ee-107">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="196ee-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="196ee-108">Attributes and Elements</span></span>  
 <span data-ttu-id="196ee-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="196ee-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="196ee-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="196ee-110">Attributes</span></span>  
  
|<span data-ttu-id="196ee-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="196ee-111">Attribute</span></span>|<span data-ttu-id="196ee-112">Description</span><span class="sxs-lookup"><span data-stu-id="196ee-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="196ee-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="196ee-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="196ee-114">Spécifie si le runtime collecte des statistiques pour l’analyse des ressources du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="196ee-114">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="196ee-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="196ee-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="196ee-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="196ee-116">Value</span></span>|<span data-ttu-id="196ee-117">Description</span><span class="sxs-lookup"><span data-stu-id="196ee-117">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="196ee-118">Les statistiques relatives à l’analyse des ressources de domaine d’application sont collectées.</span><span class="sxs-lookup"><span data-stu-id="196ee-118">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="196ee-119">Les statistiques pour l’analyse des ressources de domaine d’application ne sont pas collectées.</span><span class="sxs-lookup"><span data-stu-id="196ee-119">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="196ee-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="196ee-120">Child Elements</span></span>  
 <span data-ttu-id="196ee-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="196ee-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="196ee-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="196ee-122">Parent Elements</span></span>  
  
|<span data-ttu-id="196ee-123">Élément</span><span class="sxs-lookup"><span data-stu-id="196ee-123">Element</span></span>|<span data-ttu-id="196ee-124">Description</span><span class="sxs-lookup"><span data-stu-id="196ee-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="196ee-125">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="196ee-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="196ee-126">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="196ee-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="196ee-127">Notes</span><span class="sxs-lookup"><span data-stu-id="196ee-127">Remarks</span></span>  
 <span data-ttu-id="196ee-128">L’analyse des ressources de domaine d’application est disponible via la classe de domaine d’application managée, l’interface [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) d’hébergement et le suivi d’événements pour Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="196ee-128">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="196ee-129">Lorsque l’analyse est activée, les statistiques sont collectées pour tous les domaines d’application du processus pendant toute la durée de vie du processus.</span><span class="sxs-lookup"><span data-stu-id="196ee-129">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="196ee-130">Pour activer l’analyse à partir du code managé <xref:System.AppDomain.MonitoringIsEnabled%2A> , utilisez la propriété.</span><span class="sxs-lookup"><span data-stu-id="196ee-130">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="196ee-131">Cet élément de configuration n’est disponible que dans le .NET Framework 4 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="196ee-131">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="196ee-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="196ee-132">Example</span></span>  
 <span data-ttu-id="196ee-133">L’exemple suivant montre comment activer la surveillance des ressources du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="196ee-133">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="196ee-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="196ee-134">See also</span></span>

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="196ee-135">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="196ee-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="196ee-136">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="196ee-136">Configuration File Schema</span></span>](../index.md)

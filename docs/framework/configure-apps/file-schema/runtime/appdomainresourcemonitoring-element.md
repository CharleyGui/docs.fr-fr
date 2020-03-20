---
title: Élément <appDomainResourceMonitoring>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
ms.openlocfilehash: 3c6092b6c34bb13c0ad0e66df2d3b7e65ac3de7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154374"
---
# <a name="appdomainresourcemonitoring-element"></a><span data-ttu-id="219f9-102">\<appDomainResourceMonitoring> Element</span><span class="sxs-lookup"><span data-stu-id="219f9-102">\<appDomainResourceMonitoring> Element</span></span>
<span data-ttu-id="219f9-103">Demande au runtime de collecter des statistiques sur tous les domaines d’application du processus sur toute sa durée.</span><span class="sxs-lookup"><span data-stu-id="219f9-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
<span data-ttu-id="219f9-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="219f9-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="219f9-105">&nbsp;&nbsp;[**\<>de temps d’exécution**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="219f9-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="219f9-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainResourceMonitoring>**</span><span class="sxs-lookup"><span data-stu-id="219f9-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainResourceMonitoring>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="219f9-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="219f9-107">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="219f9-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="219f9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="219f9-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="219f9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="219f9-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="219f9-110">Attributes</span></span>  
  
|<span data-ttu-id="219f9-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="219f9-111">Attribute</span></span>|<span data-ttu-id="219f9-112">Description</span><span class="sxs-lookup"><span data-stu-id="219f9-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="219f9-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="219f9-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="219f9-114">Précise si le temps d’exécution recueille des statistiques pour la surveillance des ressources de domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="219f9-114">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="219f9-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="219f9-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="219f9-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="219f9-116">Value</span></span>|<span data-ttu-id="219f9-117">Description</span><span class="sxs-lookup"><span data-stu-id="219f9-117">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="219f9-118">Les statistiques relatives à la surveillance des ressources du domaine des applications sont recueillies.</span><span class="sxs-lookup"><span data-stu-id="219f9-118">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="219f9-119">Les statistiques relatives à la surveillance des ressources du domaine des applications ne sont pas recueillies.</span><span class="sxs-lookup"><span data-stu-id="219f9-119">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="219f9-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="219f9-120">Child Elements</span></span>  
 <span data-ttu-id="219f9-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="219f9-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="219f9-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="219f9-122">Parent Elements</span></span>  
  
|<span data-ttu-id="219f9-123">Élément</span><span class="sxs-lookup"><span data-stu-id="219f9-123">Element</span></span>|<span data-ttu-id="219f9-124">Description</span><span class="sxs-lookup"><span data-stu-id="219f9-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="219f9-125">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="219f9-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="219f9-126">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="219f9-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="219f9-127">Notes </span><span class="sxs-lookup"><span data-stu-id="219f9-127">Remarks</span></span>  
 <span data-ttu-id="219f9-128">La surveillance des ressources de domaine d’application est disponible via la classe de domaine d’application gérée, l’interface [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) et le traçage d’événements pour Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="219f9-128">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="219f9-129">Lorsque la surveillance est activée, des statistiques sont collectées pour tous les domaines d’application dans le processus pour la durée du processus.</span><span class="sxs-lookup"><span data-stu-id="219f9-129">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="219f9-130">Pour permettre la surveillance à <xref:System.AppDomain.MonitoringIsEnabled%2A> partir du code géré, utilisez la propriété.</span><span class="sxs-lookup"><span data-stu-id="219f9-130">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="219f9-131">Cet élément de configuration n’est disponible que dans le cadre .NET 4 et plus tard.</span><span class="sxs-lookup"><span data-stu-id="219f9-131">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="219f9-132"> Exemple</span><span class="sxs-lookup"><span data-stu-id="219f9-132">Example</span></span>  
 <span data-ttu-id="219f9-133">L’exemple suivant montre comment activer la surveillance des ressources de domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="219f9-133">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="219f9-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="219f9-134">See also</span></span>

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="219f9-135">Schéma des paramètres d'exécution</span><span class="sxs-lookup"><span data-stu-id="219f9-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="219f9-136">Configuration Fichier Schema</span><span class="sxs-lookup"><span data-stu-id="219f9-136">Configuration File Schema</span></span>](../index.md)

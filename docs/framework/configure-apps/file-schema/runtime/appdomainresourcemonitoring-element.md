---
title: Élément <appDomainResourceMonitoring>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad0ae023215eeb1f42f9351369ee77d41d537b88
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487732"
---
# <a name="appdomainresourcemonitoring-element"></a><span data-ttu-id="ac07d-102">\<appDomainResourceMonitoring > élément</span><span class="sxs-lookup"><span data-stu-id="ac07d-102">\<appDomainResourceMonitoring> Element</span></span>
<span data-ttu-id="ac07d-103">Demande au runtime de collecter des statistiques sur tous les domaines d’application du processus sur toute sa durée.</span><span class="sxs-lookup"><span data-stu-id="ac07d-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="ac07d-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="ac07d-104">\<configuration></span></span>  
<span data-ttu-id="ac07d-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="ac07d-105">\<runtime></span></span>  
<span data-ttu-id="ac07d-106">\<appDomainResourceMonitoring></span><span class="sxs-lookup"><span data-stu-id="ac07d-106">\<appDomainResourceMonitoring></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac07d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac07d-107">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ac07d-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ac07d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ac07d-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ac07d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ac07d-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="ac07d-110">Attributes</span></span>  
  
|<span data-ttu-id="ac07d-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="ac07d-111">Attribute</span></span>|<span data-ttu-id="ac07d-112">Description</span><span class="sxs-lookup"><span data-stu-id="ac07d-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="ac07d-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="ac07d-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="ac07d-114">Indique si le runtime collecte des statistiques pour l’analyse de ressource de domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="ac07d-114">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ac07d-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="ac07d-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="ac07d-116">Value</span><span class="sxs-lookup"><span data-stu-id="ac07d-116">Value</span></span>|<span data-ttu-id="ac07d-117">Description</span><span class="sxs-lookup"><span data-stu-id="ac07d-117">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="ac07d-118">Statistiques pour l’analyse de ressource de domaine d’application sont collectées.</span><span class="sxs-lookup"><span data-stu-id="ac07d-118">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="ac07d-119">Statistiques pour l’analyse de ressource de domaine d’application ne sont pas collectées.</span><span class="sxs-lookup"><span data-stu-id="ac07d-119">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ac07d-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ac07d-120">Child Elements</span></span>  
 <span data-ttu-id="ac07d-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ac07d-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ac07d-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ac07d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="ac07d-123">Élément</span><span class="sxs-lookup"><span data-stu-id="ac07d-123">Element</span></span>|<span data-ttu-id="ac07d-124">Description</span><span class="sxs-lookup"><span data-stu-id="ac07d-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ac07d-125">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ac07d-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ac07d-126">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="ac07d-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac07d-127">Notes</span><span class="sxs-lookup"><span data-stu-id="ac07d-127">Remarks</span></span>  
 <span data-ttu-id="ac07d-128">L’analyse de ressource de domaine d’application est disponible via la classe de domaine d’application managée, l’hébergement [ICLRAppDomainResourceMonitor](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface et le suivi d’événements pour Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="ac07d-128">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="ac07d-129">Lorsque l’analyse est activée, les statistiques sont collectées pour tous les domaines d’application dans le processus pour la durée de vie du processus.</span><span class="sxs-lookup"><span data-stu-id="ac07d-129">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="ac07d-130">Pour activer l’analyse du code managé, utilisez le <xref:System.AppDomain.MonitoringIsEnabled%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="ac07d-130">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="ac07d-131">Cet élément de configuration est disponible uniquement dans le .NET Framework 4 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="ac07d-131">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac07d-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="ac07d-132">Example</span></span>  
 <span data-ttu-id="ac07d-133">L’exemple suivant montre comment activer l’analyse de ressource de domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="ac07d-133">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac07d-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac07d-134">See also</span></span>

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="ac07d-135">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="ac07d-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="ac07d-136">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="ac07d-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)

---
title: Élément <appDomainResourceMonitoring>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
ms.openlocfilehash: 3c6092b6c34bb13c0ad0e66df2d3b7e65ac3de7e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154374"
---
# <a name="appdomainresourcemonitoring-element"></a><span data-ttu-id="561b1-102">Élément \<appDomainResourceMonitoring></span><span class="sxs-lookup"><span data-stu-id="561b1-102">\<appDomainResourceMonitoring> Element</span></span>
<span data-ttu-id="561b1-103">Demande au runtime de collecter des statistiques sur tous les domaines d’application du processus sur toute sa durée.</span><span class="sxs-lookup"><span data-stu-id="561b1-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainResourceMonitoring>**  
  
## <a name="syntax"></a><span data-ttu-id="561b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="561b1-104">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="561b1-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="561b1-105">Attributes and Elements</span></span>  
 <span data-ttu-id="561b1-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="561b1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="561b1-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="561b1-107">Attributes</span></span>  
  
|<span data-ttu-id="561b1-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="561b1-108">Attribute</span></span>|<span data-ttu-id="561b1-109">Description</span><span class="sxs-lookup"><span data-stu-id="561b1-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="561b1-110">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="561b1-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="561b1-111">Spécifie si le runtime collecte des statistiques pour l’analyse des ressources du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="561b1-111">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="561b1-112">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="561b1-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="561b1-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="561b1-113">Value</span></span>|<span data-ttu-id="561b1-114">Description</span><span class="sxs-lookup"><span data-stu-id="561b1-114">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="561b1-115">Les statistiques relatives à l’analyse des ressources de domaine d’application sont collectées.</span><span class="sxs-lookup"><span data-stu-id="561b1-115">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="561b1-116">Les statistiques pour l’analyse des ressources de domaine d’application ne sont pas collectées.</span><span class="sxs-lookup"><span data-stu-id="561b1-116">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="561b1-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="561b1-117">Child Elements</span></span>  
 <span data-ttu-id="561b1-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="561b1-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="561b1-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="561b1-119">Parent Elements</span></span>  
  
|<span data-ttu-id="561b1-120">Élément</span><span class="sxs-lookup"><span data-stu-id="561b1-120">Element</span></span>|<span data-ttu-id="561b1-121">Description</span><span class="sxs-lookup"><span data-stu-id="561b1-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="561b1-122">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="561b1-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="561b1-123">Contient des informations sur les liaisons d’assembly et l’opération garbage collection.</span><span class="sxs-lookup"><span data-stu-id="561b1-123">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="561b1-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="561b1-124">Remarks</span></span>  
 <span data-ttu-id="561b1-125">L’analyse des ressources de domaine d’application est disponible via la classe de domaine d’application managée, l’interface [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) d’hébergement et le suivi d’événements pour Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="561b1-125">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="561b1-126">Lorsque l’analyse est activée, les statistiques sont collectées pour tous les domaines d’application du processus pendant toute la durée de vie du processus.</span><span class="sxs-lookup"><span data-stu-id="561b1-126">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="561b1-127">Pour activer l’analyse à partir du code managé, utilisez la <xref:System.AppDomain.MonitoringIsEnabled%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="561b1-127">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="561b1-128">Cet élément de configuration n’est disponible que dans le .NET Framework 4 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="561b1-128">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="561b1-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="561b1-129">Example</span></span>  
 <span data-ttu-id="561b1-130">L’exemple suivant montre comment activer la surveillance des ressources du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="561b1-130">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="561b1-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="561b1-131">See also</span></span>

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="561b1-132">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="561b1-132">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="561b1-133">Schéma du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="561b1-133">Configuration File Schema</span></span>](../index.md)

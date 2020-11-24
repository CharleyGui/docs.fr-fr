---
title: ICLRAppDomainResourceMonitor, interface
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor
helpviewer_keywords:
- ICLRAppDomainResourceMonitor interface [.NET Framework hosting]
ms.assetid: 72fa83a1-8997-41d7-b355-ab177a24a303
topic_type:
- apiref
ms.openlocfilehash: 84c53f0666d0e04b898e28c1d8e146eab566ca1b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674695"
---
# <a name="iclrappdomainresourcemonitor-interface"></a>ICLRAppDomainResourceMonitor, interface

Fournit des méthodes qui inspectent la mémoire et l’utilisation de l’UC d’un domaine d’application.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetCurrentAllocated, méthode](iclrappdomainresourcemonitor-getcurrentallocated-method.md)|Obtient la taille totale, en octets, de toutes les allocations de mémoire effectuées par le domaine d’application depuis sa création, sans soustraire la mémoire qui a été récupérée par le garbage collector.|  
|[GetCurrentSurvived, méthode](iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|Obtient le nombre d’octets qui ont survécu au dernier garbage collection de blocage complet et qui sont référencés par le domaine d’application actuel.|  
|[GetCurrentCpuTime, méthode](iclrappdomainresourcemonitor-getcurrentcputime-method.md)|Obtient le temps processeur total utilisé par tous les threads lors de l’exécution dans le domaine d’application actuel, depuis la création du domaine d’application.|  
  
## <a name="remarks"></a>Remarques  

 L' `ICLRAppDomainResourceMonitor` interface fournit des fonctionnalités qui sont similaires aux propriétés managées suivantes :  
  
- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [\<appDomainResourceMonitoring> Appartient](../../configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)
- [Analyse des ressources du domaine d’application](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
- [Hébergement](index.md)

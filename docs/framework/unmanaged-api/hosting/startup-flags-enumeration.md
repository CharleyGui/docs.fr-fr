---
title: STARTUP_FLAGS, énumération
ms.date: 03/30/2017
api_name:
- STARTUP_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- STARTUP_FLAGS
helpviewer_keywords:
- STARTUP_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 4f043594-0c45-4bc6-988e-a6793f0d8d06
topic_type:
- apiref
ms.openlocfilehash: b4694efffa0a3dd6fed1f97fc2359c5eb335d440
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006413"
---
# <a name="startup_flags-enumeration"></a>STARTUP_FLAGS, énumération
Contient des valeurs qui indiquent le comportement de démarrage du common language runtime (CLR). Par défaut, garbage collection n’est pas simultanée et seule la bibliothèque de classes de base est chargée dans la zone indépendante du domaine.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    STARTUP_CONCURRENT_GC                         = 0x1,  
    STARTUP_LOADER_OPTIMIZATION_MASK              = 0x3<<1,  
    STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN     = 0x1<<1,  
    STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN      = 0x2<<1,  
    STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST = 0x3<<1,  
  
    STARTUP_LOADER_SAFEMODE                       = 0x10,  
    STARTUP_LOADER_SETPREFERENCE                  = 0x100,  
  
    STARTUP_SERVER_GC                             = 0x1000,  
    STARTUP_HOARD_GC_VM                           = 0x2000,  
  
    STARTUP_SINGLE_VERSION_HOSTING_INTERFACE      = 0x4000,  
    STARTUP_LEGACY_IMPERSONATION                  = 0x10000,  
    STARTUP_DISABLE_COMMITTHREADSTACK             = 0x20000,  
    STARTUP_ALWAYSFLOW_IMPERSONATION              = 0x40000,  
    STARTUP_TRIM_GC_COMMIT                        = 0x80000,  
  
    STARTUP_ETW                                   = 0x100000,  
    STARTUP_ARM                                   = 0x400000  
} STARTUP_FLAGS;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`STARTUP_CONCURRENT_GC`|Spécifie que les garbage collection simultanées doivent être utilisées. Si l’appelant demande la build du serveur et garbage collection simultané sur un ordinateur à un seul processeur, la build de la station de travail et les garbage collection non simultanés sont exécutés à la place. **Remarque :**  Le garbage collection simultané n’est pas pris en charge dans les applications qui exécutent l’émulateur WOW64 x86 sur les systèmes 64 bits qui implémentent l’architecture Intel Itanium (anciennement appelée IA-64). Pour plus d’informations sur l’utilisation de WOW64 sur les systèmes Windows 64 bits, consultez [exécution d’Applications 32 bits](/windows/desktop/WinProg64/running-32-bit-applications).|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|Spécifie que l’optimisation du chargeur doit se produire.|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|Spécifie qu’aucun assembly n’est chargé comme indépendant du domaine.|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|Spécifie que tous les assemblys sont chargés comme étant indépendants du domaine.|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|Spécifie que tous les assemblys avec nom fort sont chargés comme étant indépendants du domaine.|  
|`STARTUP_LOADER_SAFEMODE`|Spécifie que la stratégie de version du CLR ne sera pas appliquée à la version passée. La version exacte spécifiée du CLR sera chargée. Le shim n’évalue pas la stratégie pour déterminer la dernière version compatible.|  
|`STARTUP_LOADER_SETPREFERENCE`|Spécifie que le runtime préféré sera défini, mais pas réellement démarré.|  
|`STARTUP_SERVER_GC`|Spécifie que le serveur garbage collection sera utilisé.|  
|`STARTUP_HOARD_GC_VM`|Spécifie que garbage collection conserve l’adresse virtuelle utilisée.|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|Spécifie que la combinaison d’une interface d’hébergement ne sera pas autorisée.|  
|`STARTUP_LEGACY_IMPERSONATION`|Spécifie que l’emprunt d’identité ne doit pas être transmis entre des points asynchrones par défaut.|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|Spécifie que la pile de threads complète ne doit pas être validée lorsque le thread commence à s’exécuter.|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|Spécifie que les emprunts d’identité et les emprunts d’identité managés obtenus via l’appel de code non managé sont transmis entre des points asynchrones. Par défaut, seuls les emprunts d’identité managés sont transmis entre des points asynchrones.|  
|`STARTUP_TRIM_GC_COMMIT`|Spécifie que garbage collection utilise un espace moins validé lorsque la mémoire système est insuffisante. Voir `gcTrimCommitOnLowMemory` dans [optimisation de l’hébergement Web partagé](../../../standard/garbage-collection/optimization-for-shared-web-hosting.md).|  
|`STARTUP_ETW`|Spécifie que le suivi d’événements pour Windows (ETW) est activé pour les événements de common language runtime. À partir de Windows Vista, le suivi d’événements est toujours activé, donc cet indicateur n’a aucun effet. Consultez [contrôle de la journalisation des .NET Framework](../../performance/controlling-logging.md).|  
|`STARTUP_ARM`|Spécifie que l’analyse des ressources du domaine d’application est activée. Consultez la <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> propriété et l' [ \<appDomainResourceMonitoring> élément](../../configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations d'hébergement](hosting-enumerations.md)

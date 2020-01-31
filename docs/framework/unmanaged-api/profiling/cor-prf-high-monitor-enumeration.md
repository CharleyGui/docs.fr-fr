---
title: COR_PRF_MODULE_FLAGS, énumération
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
ms.openlocfilehash: 72324fd434f3f37f723988345514c8aaada07ca9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867150"
---
# <a name="cor_prf_high_monitor-enumeration"></a>COR_PRF_MODULE_FLAGS, énumération

[Pris en charge dans .NET Framework 4.5.2 et ultérieur]  
  
Fournit des indicateurs en plus de ceux figurant dans l’énumération [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) que le profileur peut spécifier à la méthode [ICorProfilerInfo5 :: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) lors du chargement.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef enum {  
    COR_PRF_HIGH_MONITOR_NONE                     = 0x00000000,  
    COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES          = 0x00000001,  
    COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED        = 0x00000002,
    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS = 0x00000004,
    COR_PRF_HIGH_DISABLE_TIERED_COMPILATION       = 0x00000008,
    COR_PRF_HIGH_BASIC_GC                         = 0x00000010,
    COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS         = 0x00000020,
    COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED    = 0x00000040,
    COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE            = 0,  
    COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH           = COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | 
                                                    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS |
                                                    COR_PRF_HIGH_BASIC_GC |
                                                    COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS |
                                                    COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED,  
    COR_PRF_HIGH_MONITOR_IMMUTABLE                = COR_PRF_HIGH_DISABLE_TIERED_COMPILATION  
} COR_PRF_HIGH_MONITOR;  
```  
  
## <a name="members"></a>Members  
  
|Member|Description|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|Aucun indicateur n'est défini.|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|Contrôle le rappel [ICorProfilerCallback6 :: GetAssemblyReference](icorprofilercallback6-getassemblyreferences-method.md) pour l’ajout de références d’assembly pendant le parcours de fermeture de référence de l’assembly CLR.|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|Contrôle le rappel [ICorProfilerCallback7 :: ModuleInMemorySymbolsUpdated](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) pour les mises à jour du flux de symboles associé à un module en mémoire.|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|Contrôle le rappel [ICorProfilerCallback9 ::D ynamicmethodunloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) pour indiquer quand une méthode dynamique a été récupérée par le garbage collector et déchargée. <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|.NET Core 3,0 et versions ultérieures uniquement : désactive la [compilation à plusieurs niveaux](../../../core/whats-new/dotnet-core-3-0.md) pour les profileurs.|
|`COR_PRF_HIGH_BASIC_GC`|.NET Core 3,0 et versions ultérieures uniquement : fournit une option de profilage GC légère comparée à [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md). Contrôle uniquement les rappels [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)et [GetGenerationBounds,](icorprofilerinfo2-getgenerationbounds-method.md) . Contrairement à l’indicateur `COR_PRF_MONITOR_GC`, `COR_PRF_HIGH_BASIC_GC` ne désactive pas les garbage collection simultanés.|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|.NET Core 3,0 et versions ultérieures uniquement : active les rappels [MovedReferences](icorprofilercallback-movedreferences-method.md) et [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) pour compacter les GC uniquement.|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|.NET Core 3,0 et versions ultérieures uniquement : comme [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md), mais fournit des informations sur les allocations d’objets pour le tas d’objets volumineux (LOH) uniquement.|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|Représente tous les indicateurs `COR_PRF_HIGH_MONITOR` qui requièrent des images à profil optimisé. Elle correspond à l’indicateur `COR_PRF_REQUIRE_PROFILE_IMAGE` dans l’énumération [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) .|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|Représente tous les indicateurs `COR_PRF_HIGH_MONITOR` qui peuvent être définis une fois que le profileur est attaché à une application en cours d'exécution.|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|Représente tous les indicateurs `COR_PRF_HIGH_MONITOR` qui peuvent être définis uniquement lors de l'initialisation. Les tentatives de modification d'un ou plusieurs de ces indicateurs autre part génèrent une valeur `HRESULT`, qui indique un échec.|  
  
## <a name="remarks"></a>Notes

Les indicateurs `COR_PRF_HIGH_MONITOR` sont utilisés avec le paramètre `pdwEventsHigh` des méthodes [ICorProfilerInfo5 :: GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) et [ICorProfilerInfo5 :: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) .  
  
À partir du .NET Framework 4.6.1, la valeur de la `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` est passée de 0 à `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002). À partir de la .NET Framework 4.7.2, sa valeur est passée de `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` à `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.   

`COR_PRF_HIGH_MONITOR_IMMUTABLE` est un masque de masque qui représente tous les indicateurs qui peuvent être définis uniquement pendant l’initialisation. Toute tentative de modification d’un de ces indicateurs ailleurs entraîne l’échec d’un `HRESULT`.

## <a name="requirements"></a>Configuration requise pour

**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
**En-tête :** CorProf.idl, CorProf.h  
  
**Bibliothèque :** CorGuids.lib  
  
**Versions du .NET Framework :** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de profilage](profiling-enumerations.md)
- [COR_PRF_MONITOR, énumération](cor-prf-monitor-enumeration.md)
- [ICorProfilerInfo5, interface](icorprofilerinfo5-interface.md)

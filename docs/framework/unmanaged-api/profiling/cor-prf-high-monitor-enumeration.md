---
title: COR_PRF_MODULE_FLAGS, énumération
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cbc66ef1eb5048d2c708a615a99ea363d29540f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752173"
---
# <a name="corprfhighmonitor-enumeration"></a>COR_PRF_MODULE_FLAGS, énumération
[Pris en charge dans .NET Framework 4.5.2 et ultérieur]  
  
 Fournit des indicateurs en plus de celles disponibles dans le [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) énumération le profileur peut spécifier à la [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) méthode lors de son chargement.  
  
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
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|Aucun indicateur n'est défini.|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|Contrôles le [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) rappel pour l’ajout de références d’assembly pendant le parcours de fermeture de référence assembly CLR.|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|Contrôles le [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) rappel des mises à jour dans le flux de symbole associé à un module en mémoire.|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|Contrôles le [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) rappel pour indiquer qu’une méthode dynamique a été garbage collectées et déchargé. <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|.NET core 3.0 et versions ultérieures uniquement : Désactive [à plusieurs niveaux de compilation](../../../core/whats-new/dotnet-core-3-0.md) pour les profileurs.|
|`COR_PRF_HIGH_BASIC_GC`|.NET core 3.0 et versions ultérieures uniquement : Fournit un léger GC option de profilage par rapport à [ `COR_PRF_MONITOR_GC` ](cor-prf-monitor-enumeration.md). Contrôle uniquement la [GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md), et [GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) rappels. Contrairement à la `COR_PRF_MONITOR_GC` indicateur, `COR_PRF_HIGH_BASIC_GC` ne désactive pas le garbage collection simultané.|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|.NET core 3.0 et versions ultérieures uniquement : Permet la [MovedReferences](icorprofilercallback-movedreferences-method.md) et [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) des rappels pour les catalogues globaux de compactage uniquement.|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|.NET core 3.0 et versions ultérieures uniquement : Semblable à [ `COR_PRF_MONITOR_OBJECT_ALLOCATED` ](cor-prf-monitor-enumeration.md), mais fournit des informations sur les allocations d’objets pour l’objet de tas volumineux (LOH) uniquement.|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|Représente tous les indicateurs `COR_PRF_HIGH_MONITOR` qui requièrent des images à profil optimisé. Il correspond à la `COR_PRF_REQUIRE_PROFILE_IMAGE` indicateur dans le [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) énumération.|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|Représente tous les indicateurs `COR_PRF_HIGH_MONITOR` qui peuvent être définis une fois que le profileur est attaché à une application en cours d'exécution.|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|Représente tous les indicateurs `COR_PRF_HIGH_MONITOR` qui peuvent être définis uniquement lors de l'initialisation. Les tentatives de modification d'un ou plusieurs de ces indicateurs autre part génèrent une valeur `HRESULT`, qui indique un échec.|  
  
## <a name="remarks"></a>Notes  
 Le `COR_PRF_HIGH_MONITOR` indicateurs sont utilisés avec la `pdwEventsHigh` paramètre de la [ICorProfilerInfo5::GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) et [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) méthodes.  
  
En commençant par le .NET Framework 4.6.1, la valeur de la `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` est passée de 0 à `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0 x 00000002). À compter de .NET Framework 4.7.2, sa valeur a été remplacée par `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` à `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.   

`COR_PRF_HIGH_MONITOR_IMMUTABLE` est destiné à être un masque de bits qui représente tous les indicateurs qui peuvent uniquement être définies lors de l’initialisation. Essayez de modifier un de ces indicateurs autre part génèrent un échec `HRESULT`.

## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
- [COR_PRF_MONITOR, énumération](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)
- [ICorProfilerInfo5, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)

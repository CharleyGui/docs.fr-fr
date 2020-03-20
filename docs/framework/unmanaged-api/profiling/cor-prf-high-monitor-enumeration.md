---
title: COR_PRF_MODULE_FLAGS, énumération
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
ms.openlocfilehash: 5c6e34746368a7658c43fe0e2472000c29292569
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175211"
---
# <a name="cor_prf_high_monitor-enumeration"></a>COR_PRF_MODULE_FLAGS, énumération

[Pris en charge dans .NET Framework 4.5.2 et ultérieur]  
  
Fournit des drapeaux en plus de ceux trouvés dans le [recensement COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) que le profileur peut spécifier à [l’ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) méthode quand il est de chargement.  
  
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
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|Contrôle le [ICorProfilerCallback6::GetAssemblyReference](icorprofilercallback6-getassemblyreferences-method.md) callback pour l’ajout de références d’assemblage au cours de la marche de fermeture de référence d’assemblage CLR.|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|Contrôle [l’ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) callback pour les mises à jour du flux de symboles associés à un module en mémoire.|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|Contrôle le rappel [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) pour indiquer quand une méthode dynamique a été recueillie et déchargée. <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|.NET Core 3.0 et versions ultérieures seulement: Disables [compilation à plusieurs niveaux](../../../core/whats-new/dotnet-core-3-0.md) pour les profileurs.|
|`COR_PRF_HIGH_BASIC_GC`|.NET Core 3.0 et versions ultérieures seulement: Fournit [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md)une option légère de profilage GC par rapport à . Contrôle seulement les [déchetsCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md), et [GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) rappels. Contrairement `COR_PRF_MONITOR_GC` au `COR_PRF_HIGH_BASIC_GC` drapeau, ne désactive pas la collecte simultanée des ordures.|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|.NET Core 3.0 et versions ultérieures seulement: Permet les [recoupements MovedReferences](icorprofilercallback-movedreferences-method.md) et [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) pour compacter les CGC seulement.|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|.NET Core 3.0 et versions [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md)ultérieures seulement: Similaire à , mais fournit des informations sur les allocations d’objets pour le tas grand objet (LOH) seulement.|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|Représente tous les indicateurs `COR_PRF_HIGH_MONITOR` qui requièrent des images à profil optimisé. Il correspond au `COR_PRF_REQUIRE_PROFILE_IMAGE` drapeau dans le [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) énumération.|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|Représente tous les indicateurs `COR_PRF_HIGH_MONITOR` qui peuvent être définis une fois que le profileur est attaché à une application en cours d'exécution.|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|Représente tous les indicateurs `COR_PRF_HIGH_MONITOR` qui peuvent être définis uniquement lors de l'initialisation. Les tentatives de modification d'un ou plusieurs de ces indicateurs autre part génèrent une valeur `HRESULT`, qui indique un échec.|  
  
## <a name="remarks"></a>Notes 

Les `COR_PRF_HIGH_MONITOR` drapeaux sont `pdwEventsHigh` utilisés avec le paramètre de [l’ICorProfilerInfo5::GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) et [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) méthodes.  
  
À partir du cadre .NET 4.6.1, la valeur du `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` changement de 0 à `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002). À partir du cadre .NET 4.7.2, sa valeur est passée de `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.

`COR_PRF_HIGH_MONITOR_IMMUTABLE`est destiné à être un bitmask qui représente tous les drapeaux qui ne peuvent être fixés pendant l’initialisation. Essayer de changer l’un de `HRESULT`ces drapeaux ailleurs se traduit par un échec .

## <a name="requirements"></a>Spécifications

**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
**En-tête :** CorProf.idl, CorProf.h  
  
**Bibliothèque :** CorGuids.lib  
  
**.NET Versions-cadre:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de profilage](profiling-enumerations.md)
- [COR_PRF_MONITOR, énumération](cor-prf-monitor-enumeration.md)
- [ICorProfilerInfo5, interface](icorprofilerinfo5-interface.md)

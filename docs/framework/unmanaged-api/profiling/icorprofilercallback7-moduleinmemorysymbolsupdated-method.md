---
title: 'ICorProfilerCallback7:: ModuleInMemorySymbolsUpdated, méthode'
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7.ModuleInMemorySymbolsUpdated
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: f362a896-3247-4894-9727-e48dbbcd2c78
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 860ecde22dead112a42b6ac868e34f0e9cd3531d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916198"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a>ICorProfilerCallback7:: ModuleInMemorySymbolsUpdated, méthode
[Prise en charge dans le .NET Framework 4.6.1 et versions ultérieures]  
  
 Notifie le profileur chaque fois que le flux de symboles associé à un module en mémoire est mis à jour.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 [in] `moduleId`  
 Identificateur du module en mémoire dont le flux de symboles est mis à jour.  
  
## <a name="remarks"></a>Notes  
 Ce rappel est contrôlé en définissant l’indicateur de masque d’événement [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) lors de l’appel de la méthode [ICorProfilerCallback5:: SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) .  
  
> [!NOTE]
> Cet événement n’est pas actuellement déclenché pour les symboles créés ou modifiés implicitement via <xref:System.Reflection.Emit> des API.  
  
 Même lorsque les symboles sont fournis au début d’un appel à l’une des surcharges des méthodes <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> managées qui incluent `rawSymbolStore` un argument pour spécifier les symboles pour l’assembly, le runtime peut ne pas associer réellement les données symboliques au module jusqu’à ce que le rappel [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) s’est produit. Cet événement permet ensuite de collecter des symboles pour ces modules.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf. idl, CorProf. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ModuleLoadFinished, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [SetEventMask2, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
- [ICorProfilerCallback7, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)

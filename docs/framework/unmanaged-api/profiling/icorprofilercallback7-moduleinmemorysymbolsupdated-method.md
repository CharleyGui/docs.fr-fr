---
title: 'ICorProfilerCallback7 :: ModuleInMemorySymbolsUpdated, méthode'
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7.ModuleInMemorySymbolsUpdated
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: f362a896-3247-4894-9727-e48dbbcd2c78
ms.openlocfilehash: f6dd10d196ffd3a653584e1bc8d1a5643850bc33
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136612"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a>ICorProfilerCallback7 :: ModuleInMemorySymbolsUpdated, méthode
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
 Ce rappel est contrôlé en définissant l’indicateur de masque d’événement [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) lors de l’appel de la méthode [ICorProfilerCallback5 :: SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) .  
  
> [!NOTE]
> Cet événement n’est pas actuellement déclenché pour les symboles créés ou modifiés implicitement via des API <xref:System.Reflection.Emit>.  
  
 Même lorsque les symboles sont fournis au début d’un appel à l’une des surcharges des méthodes de <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> managées qui incluent un argument `rawSymbolStore` pour spécifier les symboles de l’assembly, le runtime peut ne pas associer les données symboliques au module tant que Le rappel [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) s’est produit. Cet événement permet ensuite de collecter des symboles pour ces modules.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ModuleLoadFinished, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [SetEventMask2, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
- [ICorProfilerCallback7, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)

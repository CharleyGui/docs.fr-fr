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
ms.openlocfilehash: c7e53816c2f571fe6ff68b517ed827459a0f1562
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499088"
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
  
## <a name="remarks"></a>Remarques  
 Ce rappel est contrôlé en définissant l’indicateur de masque d’événement [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](cor-prf-high-monitor-enumeration.md) lors de l’appel de la méthode [ICorProfilerCallback5 :: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) .  
  
> [!NOTE]
> Cet événement n’est pas actuellement déclenché pour les symboles créés ou modifiés implicitement via des <xref:System.Reflection.Emit> API.  
  
 Même lorsque les symboles sont fournis à l’avance dans un appel à l’une des surcharges des <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> méthodes managées qui inclut un `rawSymbolStore` argument pour spécifier les symboles pour l’assembly, le runtime peut ne pas associer les données symboliques au module tant que le rappel [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) n’est pas survenu. Cet événement permet ensuite de collecter des symboles pour ces modules.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ModuleLoadFinished, méthode](icorprofilercallback-moduleloadfinished-method.md)
- [SetEventMask2, méthode](icorprofilerinfo5-seteventmask2-method.md)
- [Interface ICorProfilerCallback7](icorprofilercallback7-interface.md)

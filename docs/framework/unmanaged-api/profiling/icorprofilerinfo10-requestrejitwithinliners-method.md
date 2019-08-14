---
title: ICorProfilerInfo10::RequestReJITWithInliners
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.RequestReJITWithInliners
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 79a1c80f1c7582bd0751c43dea1d35a4d4d1c661
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973979"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a>ICorProfilerInfo10:: RequestReJITWithInliners, méthode
  
ReJITs les méthodes demandées, ainsi que les Inlines des méthodes demandées.   
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```  
  
#### <a name="parameters"></a>Paramètres  
 
 `dwRejitFlags` \
 dans Masque de [réCOR_PRF_REJIT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-rejit-flags-enumeration.md).
 
 `cFunctions`  
 [in] Nombre de fonctions à recompiler.  
  
 `moduleIds`  
 [in] Spécifie la partie `moduleId` des paires (`module`, `methodDef`) qui identifient les fonctions à recompiler.  
  
 `methodIds`  
 [in] Spécifie la partie `methodId` des paires (`module`, `methodDef`) qui identifient les fonctions à recompiler.  

## <a name="remarks"></a>Notes  
  [Requestrejit,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md) n’effectue aucun suivi des méthodes Inline. Le profileur devait bloquer l’incorporation ou suivre l’inline et appeler `RequestReJIT` pour tous les inlineers pour s’assurer que chaque instance d’une méthode Inline était ReJITted. Cela pose un problème avec ReJIT lors de l’attachement, car le profileur n’est pas présent pour surveiller l’incorporation. Cette méthode peut être appelée pour garantir que l’ensemble complet des Inlines sera également ReJITted.  

## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).  
  
 **En-tête :** CorProf. idl, CorProf. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions de .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]
  
## <a name="see-also"></a>Voir aussi
- [Interface ICorProfilerInfo10](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)


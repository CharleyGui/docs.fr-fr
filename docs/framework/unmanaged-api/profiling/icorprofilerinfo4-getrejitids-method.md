---
title: ICorProfilerInfo4::GetReJITIDs, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetReJITIDs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetReJITIDs
helpviewer_keywords:
- GetReJITIDs method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetReJITIDs method [.NET Framework profiling]
ms.assetid: 634ac28c-a5b7-4fc3-af84-256c24ca8177
topic_type:
- apiref
ms.openlocfilehash: f6d26abba649b608858fde8beaac750600493869
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442857"
---
# <a name="icorprofilerinfo4getrejitids-method"></a>ICorProfilerInfo4::GetReJITIDs, méthode
Retourne un tableau d’ID identifiant toutes les versions recompilées juste-à-temps de la fonction spécifiée qui sont toujours allouées. Cela inclut les versions recompilées par le JIT des fonctions qui ont été annulées par la suite, mais qui n’ont pas encore été libérées (par exemple, quand le domaine d’application qui contient la fonction restaurée est toujours utilisé).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
## <a name="parameters"></a>Paramètres  
 `functionId`  
 dans `FunctionID` de l’instance de fonction pour laquelle énumérer les versions.  
  
 `cReJitIds`  
 dans Nombre d’ID recompilés par le compilateur JIT alloués dans le tableau `reJitIds`.  
  
 `pcReJitIds`  
 à Nombre réel d’ID recompilés juste-à-temps.  
  
 `reJitIds`  
 à Tableau alloué par l’appelant qui contient les ID recompilés juste-à-temps pour la fonction spécifiée.  
  
## <a name="remarks"></a>Notes  
 `GetReJITIDs` énumère les ID recompilés JIT actifs pour une instance de fonction donnée. Il suit le même modèle d’utilisation que les autres fonctions de `ICorProfilerInfo` qui acceptent les mémoires tampons allouées par l’appelant.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo4, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilage](../../../../docs/framework/unmanaged-api/profiling/index.md)

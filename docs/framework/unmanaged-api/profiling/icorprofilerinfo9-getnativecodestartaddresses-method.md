---
title: ICorProfilerInfo9::GetNativeCodeStartAddresses
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetNativeCodeStartAddresses
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: f5c7f11a322e4cf3ed38608e0f380dd632bc8fb6
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973809"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a>ICorProfilerInfo9:: GetNativeCodeStartAddresses, méthode
  
 Étant donné une functionId et rejitId, énumère l’adresse de début du code natif de toutes les versions JIT de ce code qui existent actuellement.   
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```  
  
#### <a name="parameters"></a>Paramètres  
 `functionId`  
 dans ID de la fonction dont les adresses de début de code natif doivent être retournées.  
  
 `reJitId`  
 [in] Identité de la fonction recompilée juste-à-temps. 
  
 `cCodeStartAddresses` \
 [in] Taille maximale du tableau `codeStartAddresses`.

 `pcCodeStartAddresses` \
 à Nombre d’adresses disponibles.

 `codeStartAddresses` \
 à Tableau de `UINT_PTR`, chacun d’entre eux étant l’adresse de début d’un corps natif pour la fonction spécifiée. 

## <a name="remarks"></a>Notes  
 Lorsque la compilation à plusieurs niveaux est activée, une fonction peut avoir plusieurs corps de code natif. 

## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).  
  
 **En-tête :** CorProf. idl, CorProf. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions de .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)] 
  
## <a name="see-also"></a>Voir aussi
- [Interface ICorProfilerInfo9](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md)


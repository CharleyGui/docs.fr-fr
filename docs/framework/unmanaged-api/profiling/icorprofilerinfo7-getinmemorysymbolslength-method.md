---
title: 'ICorProfilerInfo7:: GetInMemorySymbolsLength, méthode'
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type:
- COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 157b0e215f8afa58cccb3d54a65baa9c307ba966
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955422"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a>ICorProfilerInfo7:: GetInMemorySymbolsLength, méthode
[Prise en charge dans le .NET Framework 4.6.1 et versions ultérieures]  
  
 Retourne la longueur d’un flux de symboles en mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `moduleId`  
 dans Identificateur du module contenant le flux en mémoire.  
  
 pCountSymbolBytes  
 à Pointeur vers une `DWORD` valeur qui, lorsque la méthode est retournée, contient la longueur du flux en octets.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `S_OK` si la longueur du flux de mémoire peut être déterminée, même si elle est égale à zéro (0).  
  
 La méthode retourne `CORPROF_E_MODULE_IS_DYNAMIC` si la méthode a été créée <xref:System.Reflection.Emit?displayProperty=nameWithType>à l’aide de.  
  
## <a name="remarks"></a>Notes  
 Si le module contient des symboles en mémoire, la longueur du flux est placée dans `pCountSymbolBytes`. Si le module n’a pas de symboles en mémoire `*pCountSymbolBytes = 0`,.  
  
> [!NOTE]
> L’implémentation actuelle ne prend pas en charge la réflexion. Emit. Si le module a été créé à l’aide de Reflection. Emit `CORPROF_E_MODULE_IS_DYNAMIC`, la méthode retourne.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf. idl, CorProf. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo7, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)

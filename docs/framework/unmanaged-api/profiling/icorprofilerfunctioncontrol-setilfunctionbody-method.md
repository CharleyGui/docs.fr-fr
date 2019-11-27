---
title: Méthode ICorProfilerFunctionControl::SetILFunctionBody
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 2c33f0f7-75b2-4c19-b2c7-c94b54997576
topic_type:
- apiref
ms.openlocfilehash: f6e2cfe47bdd212e39549544b06bf5b11033a956
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429885"
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a>Méthode ICorProfilerFunctionControl::SetILFunctionBody
Remplace le corps Common Intermediate Language (CIL) de la méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a>Paramètres  
 `cbNewILMethodHeader`  
 [in] La taille totale du nouveau CIL, y compris l'en-tête et toutes structures intervenant après le corps.  
  
 `pbNewILMethodHeader`  
 [in] Un pointeur vers le nouvel en-tête de CIL.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Le remplacement a été correctement effectué.|  
  
## <a name="remarks"></a>Notes  
 Contrairement à la méthode [ICorProfilerInfo :: SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) , la méthode `SetILFunctionBody` gère la mémoire requise pour le nouveau corps cil. Cela signifie que le corps CIL fourni par le profileur ne doit pas être alloué à l’aide de l’interface [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) ou alloué dans une plage particulière. Il peut être alloué sur n'importe quel segment de mémoire. Le profileur peut libérer la mémoire utilisée pour son corps CIL après le retour de `SetILFunctionBody`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerFunctionControl, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)

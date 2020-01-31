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
ms.openlocfilehash: bebc0cf6ac7912ea3a6641e0c729b759e865dac3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864659"
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a>Méthode ICorProfilerFunctionControl::SetILFunctionBody
Remplace le corps Common Intermediate Language (CIL) de la méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a>Parameters  
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
 Contrairement à la méthode [ICorProfilerInfo :: SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) , la méthode `SetILFunctionBody` gère la mémoire requise pour le nouveau corps cil. Cela signifie que le corps CIL fourni par le profileur ne doit pas être alloué à l’aide de l’interface [IMethodMalloc](imethodmalloc-interface.md) ou alloué dans une plage particulière. Il peut être alloué sur n'importe quel segment de mémoire. Le profileur peut libérer la mémoire utilisée pour son corps CIL après le retour de `SetILFunctionBody`.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerFunctionControl, interface](icorprofilerfunctioncontrol-interface.md)

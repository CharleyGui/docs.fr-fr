---
title: ICorProfilerInfo4::GetFunctionFromIP2, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetFunctionFromIP2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2
helpviewer_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2 method [.NET Framework profiling]
- GetFunctionFromIP2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 46ff70f4-13e9-40a0-802a-0a40abcfc6a0
topic_type:
- apiref
ms.openlocfilehash: 5153a25ef87d9c06bb46b74945c8eb68eb041682
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443146"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a>ICorProfilerInfo4::GetFunctionFromIP2, méthode
Mappe un pointeur d’instruction de code managé à la version recompilée juste-à-temps d’une fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ip`  
 dans Pointeur d’instruction dans du code managé.  
  
 `pFunctionId`  
 à ID de la fonction.  
  
 `pReJitId`  
 à Identité de la version recompilée juste-à-temps de la fonction.  
  
## <a name="remarks"></a>Notes  
 `GetFunctionFromIP2` est semblable à `GetFunctionFromIP`, à ceci près qu’elle obtient l’ID recompilé juste-à-temps au lieu de l’ID de fonction de la fonction qui contient l’adresse IP spécifiée.  
  
> [!NOTE]
> `GetFunctionFromIP2` pouvez déclencher un garbage collection, alors que `GetFunctionFromIP` ne le sera pas.  Pour plus d’informations, consultez [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

---
title: ICorProfilerInfo3::GetFunctionLeave3Info, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionLeave3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionLeave3Info
helpviewer_keywords:
- GetFunctionLeave3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionLeave3Info method [.NET Framework profiling]
ms.assetid: df7083d2-fd43-44c7-9ce5-912c25cef0ff
topic_type:
- apiref
ms.openlocfilehash: 0d3b93a293d4dda9dfe7b576708c832de2e25869
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862397"
---
# <a name="icorprofilerinfo3getfunctionleave3info-method"></a>ICorProfilerInfo3::GetFunctionLeave3Info, méthode
Fournit le frame de pile et la valeur de retour de la fonction qui est signalée au profileur par la fonction [FunctionLeave3WithInfo](functionleave3withinfo-function.md) . Cette méthode peut être appelée uniquement pendant le rappel de `FunctionLeave3WithInfo`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFunctionLeave3Info(  
            [in]  FunctionID functionId,  
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [out] COR_PRF_FUNCTION_ARGUMENT_RANGE *pRetvalRange);  
```  
  
## <a name="parameters"></a>Parameters  
 `functionId`  
 dans `FunctionID` de la fonction qui retourne.  
  
 `eltInfo`  
 [in] Handle opaque qui représente des informations sur un frame de pile donné. Le profileur doit fournir la même `eltInfo` que celle qui a été donnée au profileur par la fonction [FunctionLeave3WithInfo](functionleave3withinfo-function.md) .  
  
 `pFrameInfo`  
 [out] Handle opaque qui représente des informations génériques sur un frame de pile donné. Ce handle est uniquement valide pendant le rappel `FunctionLeave3WithInfo` au cours duquel le profileur a appelé la méthode `GetFunctionLeave3Info`.  
  
 `pRetvalRange`  
 à Pointeur vers une structure [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) qui contient la valeur retournée par la fonction. Pour accéder aux informations de valeur de retour, l’indicateur `COR_PRF_ENABLE_FUNCTION_RETVAL` doit être défini. Le profileur peut utiliser la [méthode ICorProfilerInfo :: SetEventMask](icorprofilerinfo-seteventmask-method.md) pour définir les indicateurs d’événement.  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [FunctionEnter3WithInfo](functionenter3withinfo-function.md)
- [FunctionLeave3WithInfo](functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)
- [ICorProfilerInfo3, interface](icorprofilerinfo3-interface.md)
- [Interfaces de profilage](profiling-interfaces.md)
- [Profilage](index.md)

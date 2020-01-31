---
title: ICorProfilerInfo3::GetFunctionEnter3Info, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionEnter3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionEnter3Info
helpviewer_keywords:
- GetFunctionEnter3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionEnter3Info method [.NET Framework profiling]
ms.assetid: 542c7c65-dd56-4651-b76f-5db2465e4a15
topic_type:
- apiref
ms.openlocfilehash: 55411f187e2ef73997633d94b37a7d5d2cfd74c9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868562"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a>ICorProfilerInfo3::GetFunctionEnter3Info, méthode
Fournit les informations sur le frame de pile et l’argument de la fonction qui est signalée au profileur par la fonction [FunctionEnter3WithInfo](functionenter3withinfo-function.md) . Cette méthode peut être appelée uniquement pendant le rappel de `FunctionEnter3WithInfo`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFunctionEnter3Info(  
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [in, out] ULONG *pcbArgumentInfo,  
            [out, size_is(*pcbArgumentInfo)]  
                  COR_PRF_FUNCTION_ARGUMENT_INFO *pArgumentInfo);  
```  
  
## <a name="parameters"></a>Parameters  
 `functionId`  
 [in] `FunctionID` de la fonction entrée.  
  
 `eltInfo`  
 [in] Handle opaque qui représente des informations sur un frame de pile donné. Le profileur doit fournir le même `eltInfo` qu’il a été fourni par la fonction [FunctionEnter3WithInfo](functionenter3withinfo-function.md) .  
  
 `pFrameInfo`  
 [out] Handle opaque qui représente des informations génériques sur un frame de pile donné. Ce handle est uniquement valide pendant le rappel `FunctionEnter3WithInfo` au cours duquel le profileur a appelé la méthode `GetFunctionEnter3Info`.  
  
 `pcbArgumentInfo`  
 [in, out] Pointeur vers la taille totale, en octets, de la structure [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) (plus toutes les structures de [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) supplémentaires pour les plages d’arguments pointées par `pArgumentInfo`). Si la taille spécifiée est insuffisante, ERROR_INSUFFICIENT_BUFFER est retourné et la taille attendue est stockée dans `pcbArgumentInfo`. Pour appeler `GetFunctionEnter3Info` pour récupérer uniquement la valeur attendue pour `*pcbArgumentInfo`, affectez à `*pcbArgumentInfo` la valeur 0 et à `pArgumentInfo` la valeur NULL.  
  
 `pArgumentInfo`  
 à Pointeur vers une structure [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) qui décrit les emplacements des arguments de la fonction en mémoire, dans l’ordre de gauche à droite.  
  
## <a name="remarks"></a>Notes  
 Le profileur doit allouer suffisamment d'espace à la structure `COR_PRF_FUNCTION_ARGUMENT_INFO` de la fonction inspectée et indiquer la taille dans le paramètre `pcbArgumentInfo`.  
  
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

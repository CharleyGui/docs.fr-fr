---
title: ICorProfilerInfo4::GetCodeInfo3, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetCodeInfo3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetCodeInfo3
helpviewer_keywords:
- GetCodeInfo3 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetCodeInfo3 method [.NET Framework profiling]
ms.assetid: bb8c105e-4d9a-4684-8c05-ed6909cc1b8c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 084007bd7ab20449c28d2c5e6125cbacfa280526
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912716"
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a>ICorProfilerInfo4::GetCodeInfo3, méthode
Obtient les étendues de code natif associées à la version recompilée juste-à-temps de la fonction spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a>Paramètres  
 `functionID`  
 [in] ID de la fonction à laquelle le code natif est associé.  
  
 `reJitId`  
 [in] Identité de la fonction recompilée juste-à-temps.  
  
 `cCodeInfos`  
 [in] Taille du tableau `codeInfos`.  
  
 `pcCodeInfos`  
 à Pointeur vers le nombre total de structures [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) disponibles.  
  
 `codeInfos`  
 [out] Mémoire tampon fournie par l'appelant. Suite au retour de la méthode, celle-ci contient un tableau de structures `COR_PRF_CODE_INFO` qui décrivent chacune un bloc de code natif.  
  
## <a name="remarks"></a>Notes  
 La `GetCodeInfo3` méthode est similaire à [GetCodeInfo2,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md), à ceci près qu’elle obtient l’ID recompilé juste-à-temps de la fonction qui contient l’adresse IP spécifiée.  
  
> [!NOTE]
> `GetCodeInfo3`peut déclencher un garbage collection, contrairement à [GetCodeInfo2,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) . Pour plus d’informations, consultez [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT.  
  
 Les étendues sont triées par ordre croissant des offsets du langage CIL (Common Intermediate Language).  
  
 Après `GetCodeInfo3` le retour de, vous devez vérifier `codeInfos` que la mémoire tampon est suffisamment grande pour contenir toutes les structures [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) . Pour ce faire, comparez la valeur de `cCodeInfos` à celle du paramètre `cchName`. Si `cCodeInfos` le fractionnement par la taille d’une structure [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) est `pcCodeInfos`inférieur à, allouez une mémoire `cCodeInfos` tampon plus grande `codeInfos` , mettez à jour avec la `GetCodeInfo3` nouvelle taille plus grande, puis rappelez.  
  
 Vous pouvez également commencer par appeler `GetCodeInfo3` avec un tampon `codeInfos` de longueur nulle pour obtenir la taille correcte du tampon. Vous pouvez ensuite affecter à la `codeInfos` taille de la mémoire tampon la valeur retournée dans `pcCodeInfos`, multipliée par la taille d’une structure [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md), puis rappeler `GetCodeInfo3`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf. idl, CorProf. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetCodeInfo2, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)
- [ICorProfilerInfo4, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilage](../../../../docs/framework/unmanaged-api/profiling/index.md)

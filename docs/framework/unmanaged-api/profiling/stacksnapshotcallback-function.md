---
title: StackSnapshotCallback (fonction)
ms.date: 03/30/2017
api_name:
- StackSnapshotCallback
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- StackSnapshotCallback
helpviewer_keywords:
- StackSnapshotCallback function [.NET Framework profiling]
ms.assetid: d0f235b2-91fe-4f82-b7d5-e5c64186eea8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6140ecda1d12c26e1936daee4eaad11cbd9b6ba4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781226"
---
# <a name="stacksnapshotcallback-function"></a>StackSnapshotCallback (fonction)
Fournit au profileur des informations sur chaque frame managé et chaque exécution de trames non gérées sur la pile pendant un parcours de pile, ce qui est lancée par le [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) (méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT __stdcall StackSnapshotCallback (  
    [in] FunctionID funcId,  
    [in] UINT_PTR ip,  
    [in] COR_PRF_FRAME_INFO frameInfo,  
    [in] ULONG32 contextSize,  
    [in] BYTE context[],  
    [in] void *clientData  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `funcId`  
 [in] Si cette valeur est zéro, ce rappel est pour une exécution de trames non gérées ; Sinon, il est l’identificateur d’une fonction managée et ce rappel est pour une trame gérée.  
  
 `ip`  
 [in] La valeur de pointeur d’instruction de code natif dans le cadre.  
  
 `frameInfo`  
 [in] Un `COR_PRF_FRAME_INFO` valeur qui fait référence aux informations sur le frame de pile. Cette valeur est valide pour une utilisation uniquement pendant ce rappel.  
  
 `contextSize`  
 [in] La taille de la `CONTEXT` structure, ce qui est référencé par le `context` paramètre.  
  
 `context`  
 [in] Un pointeur vers un Win32 `CONTEXT` structure qui représente l’état de l’UC pour ce frame.  
  
 Le `context` paramètre est valide uniquement si l’indicateur COR_PRF_SNAPSHOT_CONTEXT a été passé dans `ICorProfilerInfo2::DoStackSnapshot`.  
  
 `clientData`  
 [in] Un pointeur vers les données client, qui sont ensuite transmis directement à partir de `ICorProfilerInfo2::DoStackSnapshot`.  
  
## <a name="remarks"></a>Notes  
 Le `StackSnapshotCallback` fonction est implémentée par le writer de profileur. Vous devez limiter la complexité du travail effectué dans `StackSnapshotCallback`. Par exemple, lorsque vous utilisez `ICorProfilerInfo2::DoStackSnapshot` de manière asynchrone, le thread cible peut contenir des verrous. Si le code situé dans `StackSnapshotCallback` requiert les mêmes verrous, un interblocage susceptibles d’en découler.  
  
 Le `ICorProfilerInfo2::DoStackSnapshot` les appels de méthode le `StackSnapshotCallback` fonction une fois par trame gérée ou une fois par exécution de trames non gérées. Si `StackSnapshotCallback` est appelée pour une exécution de trames non gérées, le profileur peut utiliser le contexte de Registre (référencé par le `context` paramètre) pour effectuer son propre parcours de pile non géré. Dans ce cas, Win32 `CONTEXT` structure représente l’état de l’UC pour le frame de la plus récemment envoyée lors de l’exécution de trames non gérées. Bien que Win32 `CONTEXT` structure inclut des valeurs pour tous les registres, vous devez utiliser uniquement les valeurs de Registre de pointeur de pile, Registre de pointeur de frame, Registre de pointeur d’instruction et la non volatile (qui est, conservée) registres d’entiers.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [DoStackSnapshot, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)
- [Fonctions statiques globales de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)

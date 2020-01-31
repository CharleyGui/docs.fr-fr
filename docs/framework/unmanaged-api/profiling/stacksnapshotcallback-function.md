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
ms.openlocfilehash: 49e154ade91ea1a207645f924bd8aea1dbdb635c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868120"
---
# <a name="stacksnapshotcallback-function"></a>StackSnapshotCallback (fonction)
Fournit au profileur des informations sur chaque frame managé et chaque série de frames non managés sur la pile pendant un parcours de pile, qui est initié par la méthode [ICorProfilerInfo2 ::D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md) .  
  
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
  
## <a name="parameters"></a>Parameters  
 `funcId`  
 dans Si cette valeur est égale à zéro, ce rappel est destiné à une exécution de frames non managés. dans le cas contraire, il s’agit de l’identificateur d’une fonction managée et ce rappel est destiné à un frame managé.  
  
 `ip`  
 dans Valeur du pointeur d’instruction de code natif dans le frame.  
  
 `frameInfo`  
 dans Valeur `COR_PRF_FRAME_INFO` qui référence des informations sur le frame de pile. Cette valeur est valide pour une utilisation uniquement pendant ce rappel.  
  
 `contextSize`  
 dans Taille de la structure `CONTEXT`, qui est référencée par le paramètre `context`.  
  
 `context`  
 dans Pointeur vers une structure de `CONTEXT` Win32 qui représente l’état de l’UC pour ce frame.  
  
 Le paramètre `context` est valide uniquement si l’indicateur COR_PRF_SNAPSHOT_CONTEXT a été passé dans `ICorProfilerInfo2::DoStackSnapshot`.  
  
 `clientData`  
 dans Pointeur vers les données du client, qui est transmis directement à partir de `ICorProfilerInfo2::DoStackSnapshot`.  
  
## <a name="remarks"></a>Notes  
 La fonction `StackSnapshotCallback` est implémentée par le writer du profileur. Vous devez limiter la complexité du travail effectué dans `StackSnapshotCallback`. Par exemple, lorsque vous utilisez `ICorProfilerInfo2::DoStackSnapshot` de manière asynchrone, le thread cible peut contenir des verrous. Si le code dans `StackSnapshotCallback` requiert les mêmes verrous, un interblocage peut se défaire.  
  
 La méthode `ICorProfilerInfo2::DoStackSnapshot` appelle la fonction `StackSnapshotCallback` une fois par frame managé ou une fois par exécution de frames non managés. Si `StackSnapshotCallback` est appelée pour une série de frames non managés, le profileur peut utiliser le contexte de Registre (référencé par le paramètre `context`) pour effectuer son propre parcours de pile non managé. Dans ce cas, la structure de `CONTEXT` Win32 représente l’état du processeur pour le dernier frame ayant fait l’objet d’un push dans l’exécution de frames non managés. Bien que la structure de `CONTEXT` Win32 comprenne des valeurs pour tous les registres, vous devez vous fier uniquement aux valeurs du registre de pointeur de pile, du registre de pointeur de frame, du registre de pointeur d’instruction et des registres d’entiers non volatiles (autrement dit, conservés).  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf. idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [DoStackSnapshot, méthode](icorprofilerinfo2-dostacksnapshot-method.md)
- [Fonctions statiques globales de profilage](profiling-global-static-functions.md)

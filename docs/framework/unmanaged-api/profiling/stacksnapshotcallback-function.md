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
ms.openlocfilehash: a0f5316900dedc6c8983f9e670f60767ed783a40
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493992"
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
  
## <a name="parameters"></a>Paramètres  
 `funcId`  
 dans Si cette valeur est égale à zéro, ce rappel est destiné à une exécution de frames non managés. dans le cas contraire, il s’agit de l’identificateur d’une fonction managée et ce rappel est destiné à un frame managé.  
  
 `ip`  
 dans Valeur du pointeur d’instruction de code natif dans le frame.  
  
 `frameInfo`  
 dans `COR_PRF_FRAME_INFO`Valeur qui référence les informations relatives au frame de pile. Cette valeur est valide pour une utilisation uniquement pendant ce rappel.  
  
 `contextSize`  
 dans Taille de la `CONTEXT` structure, qui est référencée par le `context` paramètre.  
  
 `context`  
 dans Pointeur vers une structure Win32 `CONTEXT` qui représente l’état de l’UC pour ce frame.  
  
 Le `context` paramètre n’est valide que si l’indicateur COR_PRF_SNAPSHOT_CONTEXT a été passé `ICorProfilerInfo2::DoStackSnapshot` .  
  
 `clientData`  
 dans Pointeur vers les données du client, qui est passé directement à partir de `ICorProfilerInfo2::DoStackSnapshot` .  
  
## <a name="remarks"></a>Remarques  
 La `StackSnapshotCallback` fonction est implémentée par le writer du profileur. Vous devez limiter la complexité du travail effectué dans `StackSnapshotCallback` . Par exemple, lors de l’utilisation `ICorProfilerInfo2::DoStackSnapshot` de de manière asynchrone, le thread cible peut contenir des verrous. Si le code dans `StackSnapshotCallback` requiert les mêmes verrous, un blocage peut se défaire.  
  
 La `ICorProfilerInfo2::DoStackSnapshot` méthode appelle la `StackSnapshotCallback` fonction une fois par frame managé ou une fois par exécution de frames non managés. Si `StackSnapshotCallback` est appelé pour une exécution de frames non managés, le profileur peut utiliser le contexte de Registre (référencé par le `context` paramètre) pour effectuer son propre parcours de pile non managé. Dans ce cas, la `CONTEXT` structure Win32 représente l’état du processeur pour le dernier frame ayant fait l’objet d’un push dans l’exécution de frames non managés. Bien que la `CONTEXT` structure Win32 comprenne des valeurs pour tous les registres, vous devez vous appuyer uniquement sur les valeurs du registre de pointeur de pile, du registre de pointeur de frame, du registre de pointeur d’instruction et des registres d’entiers non volatils (autrement dit, conservés).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf. idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [DoStackSnapshot, méthode](icorprofilerinfo2-dostacksnapshot-method.md)
- [Fonctions statiques globales du profilage](profiling-global-static-functions.md)

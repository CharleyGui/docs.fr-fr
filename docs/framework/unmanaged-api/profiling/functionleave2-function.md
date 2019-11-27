---
title: FunctionLeave2 (fonction)
ms.date: 03/30/2017
api_name:
- FunctionLeave2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave2
helpviewer_keywords:
- FunctionLeave2 function [.NET Framework profiling]
ms.assetid: 8cdac941-8b94-4497-b874-4e571785f3fe
topic_type:
- apiref
ms.openlocfilehash: e40687f7f843dc563801bb01b503d2ae94a094fc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446018"
---
# <a name="functionleave2-function"></a>FunctionLeave2 (fonction)
Notifie le profileur qu’une fonction va retourner à l’appelant et fournit des informations sur le frame de pile et la valeur de retour de fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `funcId`  
 dans Identificateur de la fonction qui retourne.  
  
 `clientData`  
 dans Identificateur de fonction remappée, que le profileur a précédemment spécifié via la fonction [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) .  
  
 `func`  
 dans Valeur `COR_PRF_FRAME_INFO` qui pointe vers les informations sur le frame de pile.  
  
 Le profileur doit traiter ceci comme un handle opaque qui peut être retourné au moteur d’exécution dans la méthode [ICorProfilerInfo2 :: GetFunctionInfo2,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) .  
  
 `retvalRange`  
 dans Pointeur vers une structure [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) qui spécifie l’emplacement de la mémoire de la valeur de retour de la fonction.  
  
 Pour accéder aux informations de valeur de retour, l’indicateur `COR_PRF_ENABLE_FUNCTION_RETVAL` doit être défini. Le profileur peut utiliser la méthode [ICorProfilerInfo :: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) pour définir les indicateurs d’événement.  
  
## <a name="remarks"></a>Notes  
 Les valeurs des paramètres `func` et `retvalRange` ne sont pas valides après le retour de la fonction `FunctionLeave2`, car les valeurs peuvent changer ou être détruites.  
  
 La fonction `FunctionLeave2` est un rappel ; vous devez l’implémenter. L’implémentation doit utiliser l’attribut de classe de stockage `__declspec`(`naked`).  
  
 Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.  
  
- À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).  
  
- À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.  
  
 L’implémentation de `FunctionLeave2` ne doit pas être bloquée, car elle retardera garbage collection. L’implémentation ne doit pas essayer un garbage collection, car la pile n’est peut-être pas dans un État garbage collection. Si une garbage collection est tentée, le runtime se bloque jusqu’à ce que `FunctionLeave2` retourne.  
  
 En outre, la fonction `FunctionLeave2` ne doit pas appeler dans du code managé ou de quelque manière qu’elle génère une allocation de mémoire managée.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf. idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [FunctionEnter2, fonction](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [FunctionTailcall2, fonction](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Fonctions statiques globales de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)

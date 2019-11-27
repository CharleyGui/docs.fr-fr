---
title: FunctionEnter2 (fonction)
ms.date: 03/30/2017
api_name:
- FunctionEnter2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter2
helpviewer_keywords:
- FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type:
- apiref
ms.openlocfilehash: f4deec3e2b49b5cd6a924af8024e775c5c549f97
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440860"
---
# <a name="functionenter2-function"></a>FunctionEnter2 (fonction)
Notifie le profileur que le contrôle est passé à une fonction et fournit des informations sur le frame de pile et les arguments de fonction. Cette fonction remplace la fonction [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,   
    [in]  UINT_PTR                         clientData,   
    [in]  COR_PRF_FRAME_INFO               func,   
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `funcId`  
 dans Identificateur de la fonction à laquelle le contrôle est passé.  
  
 `clientData`  
 dans Identificateur de fonction remappée, que le profileur a précédemment spécifié à l’aide de la fonction [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) .  
  
 `func`  
 dans Valeur `COR_PRF_FRAME_INFO` qui pointe vers les informations sur le frame de pile.  
  
 Le profileur doit traiter ceci comme un handle opaque qui peut être retourné au moteur d’exécution dans la méthode [ICorProfilerInfo2 :: GetFunctionInfo2,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) .  
  
 `argumentInfo`  
 dans Pointeur vers une structure [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) qui spécifie les emplacements en mémoire des arguments de la fonction.  
  
 Pour accéder aux informations d’argument, l’indicateur `COR_PRF_ENABLE_FUNCTION_ARGS` doit être défini. Le profileur peut utiliser la méthode [ICorProfilerInfo :: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) pour définir les indicateurs d’événement.  
  
## <a name="remarks"></a>Notes  
 Les valeurs des paramètres `func` et `argumentInfo` ne sont pas valides après le retour de la fonction `FunctionEnter2`, car les valeurs peuvent changer ou être détruites.  
  
 La fonction `FunctionEnter2` est un rappel ; vous devez l’implémenter. L’implémentation doit utiliser l’attribut de classe de stockage `__declspec`(`naked`).  
  
 Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.  
  
- À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).  
  
- À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.  
  
 L’implémentation de `FunctionEnter2` ne doit pas être bloquée, car elle retardera garbage collection. L’implémentation ne doit pas essayer un garbage collection, car la pile n’est peut-être pas dans un État garbage collection. Si une garbage collection est tentée, le runtime se bloque jusqu’à ce que `FunctionEnter2` retourne.  
  
 En outre, la fonction `FunctionEnter2` ne doit pas appeler dans du code managé ou de quelque manière qu’elle génère une allocation de mémoire managée.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf. idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [FunctionLeave2, fonction](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [FunctionTailcall2, fonction](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Fonctions statiques globales de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)

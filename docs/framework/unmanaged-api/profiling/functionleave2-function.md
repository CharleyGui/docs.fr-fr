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
ms.openlocfilehash: 0b1ecd1266528f8a08ef114de2f111dd0f71ca8b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866929"
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
  
## <a name="parameters"></a>Parameters

- `funcId`

  \[in] identificateur de la fonction qui retourne.

- `clientData`

  \[dans] identificateur de fonction remappée, que le profileur a précédemment spécifié via la fonction [FunctionIDMapper](functionidmapper-function.md) .

- `func`

  \[dans] valeur `COR_PRF_FRAME_INFO` qui pointe vers les informations sur le frame de pile.

  Le profileur doit traiter ceci comme un handle opaque qui peut être retourné au moteur d’exécution dans la méthode [ICorProfilerInfo2 :: GetFunctionInfo2,](icorprofilerinfo2-getfunctioninfo2-method.md) .  
  
- `retvalRange`

  \[in] pointeur vers une structure [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) qui spécifie l’emplacement de mémoire de la valeur de retour de la fonction.

  Pour accéder aux informations de valeur de retour, l’indicateur `COR_PRF_ENABLE_FUNCTION_RETVAL` doit être défini. Le profileur peut utiliser la méthode [ICorProfilerInfo :: SetEventMask](icorprofilerinfo-seteventmask-method.md) pour définir les indicateurs d’événement.

## <a name="remarks"></a>Notes  
 Les valeurs des paramètres `func` et `retvalRange` ne sont pas valides après le retour de la fonction `FunctionLeave2`, car les valeurs peuvent changer ou être détruites.  
  
 La fonction `FunctionLeave2` est un rappel ; vous devez l’implémenter. L’implémentation doit utiliser l’attribut de classe de stockage `__declspec`(`naked`).  
  
 Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.  
  
- À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).  
  
- À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.  
  
 L’implémentation de `FunctionLeave2` ne doit pas être bloquée, car elle retardera garbage collection. L’implémentation ne doit pas essayer un garbage collection, car la pile n’est peut-être pas dans un État garbage collection. Si une garbage collection est tentée, le runtime se bloque jusqu’à ce que `FunctionLeave2` retourne.  
  
 En outre, la fonction `FunctionLeave2` ne doit pas appeler dans du code managé ou de quelque manière qu’elle génère une allocation de mémoire managée.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf. idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [FunctionEnter2, fonction](functionenter2-function.md)
- [FunctionTailcall2, fonction](functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2, méthode](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Fonctions statiques globales de profilage](profiling-global-static-functions.md)

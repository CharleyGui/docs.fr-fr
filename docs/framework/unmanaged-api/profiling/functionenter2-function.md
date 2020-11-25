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
ms.openlocfilehash: e8466970a1c137276e842b37f0305fdfd9169be6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717239"
---
# <a name="functionenter2-function"></a>FunctionEnter2 (fonction)

Notifie le profileur que le contrôle est passé à une fonction et fournit des informations sur le frame de pile et les arguments de fonction. Cette fonction remplace la fonction [FunctionEnter](functionenter-function.md) .  
  
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

- `funcId`

  \[in] identificateur de la fonction vers laquelle le contrôle est passé.

- `clientData`

  \[dans] identificateur de fonction remappée, que le profileur a précédemment spécifié à l’aide de la fonction [FunctionIDMapper](functionidmapper-function.md) .
  
- `func`

  \[in] `COR_PRF_FRAME_INFO` valeur qui pointe vers les informations sur le frame de pile.
  
  Le profileur doit traiter ceci comme un handle opaque qui peut être retourné au moteur d’exécution dans la méthode [ICorProfilerInfo2 :: GetFunctionInfo2,](icorprofilerinfo2-getfunctioninfo2-method.md) .  
  
- `argumentInfo`

  \[in] pointeur vers une structure [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) qui spécifie les emplacements en mémoire des arguments de la fonction.

  Pour accéder aux informations d’argument, l' `COR_PRF_ENABLE_FUNCTION_ARGS` indicateur doit être défini. Le profileur peut utiliser la méthode [ICorProfilerInfo :: SetEventMask](icorprofilerinfo-seteventmask-method.md) pour définir les indicateurs d’événement.

## <a name="remarks"></a>Remarques  

 Les valeurs des `func` paramètres et ne `argumentInfo` sont pas valides après le retour de la `FunctionEnter2` fonction, car les valeurs peuvent changer ou être détruites.  
  
 La `FunctionEnter2` fonction est un rappel ; vous devez l’implémenter. L’implémentation doit utiliser l' `__declspec` `naked` attribut de classe de stockage ().  
  
 Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.  
  
- À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).  
  
- À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.  
  
 L’implémentation de ne `FunctionEnter2` doit pas être bloquée, car elle retardera garbage collection. L’implémentation ne doit pas essayer un garbage collection, car la pile n’est peut-être pas dans un État garbage collection. Si une garbage collection est tentée, le runtime se bloque jusqu’à ce que `FunctionEnter2` retourne la valeur.  
  
 En outre, la `FunctionEnter2` fonction ne doit pas appeler dans du code managé ou de quelque manière provoquer une allocation de mémoire managée.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf. idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [FunctionLeave2 (fonction)](functionleave2-function.md)
- [FunctionTailcall2 (fonction)](functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2, méthode](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Fonctions statiques globales du profilage](profiling-global-static-functions.md)

---
title: FunctionTailcall2 (fonction)
ms.date: 03/30/2017
api_name:
- FunctionTailcall2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall2
helpviewer_keywords:
- FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type:
- apiref
ms.openlocfilehash: cb7e21e0c6aad5ebb328ae5d1a993716f96e8d47
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500570"
---
# <a name="functiontailcall2-function"></a>FunctionTailcall2 (fonction)
Indique au profileur que la fonction en cours d’exécution est sur le paragraphe d’effectuer un appel tail à une autre fonction et fournit des informations sur le frame de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,
    [in] UINT_PTR           clientData,
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a>Paramètres

- `funcId`

  \[in] identificateur de la fonction en cours d’exécution qui est sur le paragraphe d’effectuer un appel tail.

- `clientData`

  \[dans] identificateur de fonction remappée, que le profileur a précédemment spécifié via le [FunctionIDMapper](functionidmapper-function.md), de la fonction en cours d’exécution qui est sur le paragraphe d’effectuer un appel tail.
  
- `func`

  \[in] `COR_PRF_FRAME_INFO` valeur qui pointe vers les informations sur le frame de pile.

  Le profileur doit traiter ceci comme un handle opaque qui peut être retourné au moteur d’exécution dans la méthode [ICorProfilerInfo2 :: GetFunctionInfo2,](icorprofilerinfo2-getfunctioninfo2-method.md) .

## <a name="remarks"></a>Remarques  
 La fonction cible de l’appel tail utilise le frame de pile actuel et retourne directement à l’appelant de la fonction qui a effectué l’appel tail. Cela signifie qu’un rappel [FunctionLeave2](functionleave2-function.md) ne sera pas émis pour une fonction qui est la cible d’un appel tail.  
  
 La valeur du `func` paramètre n’est pas valide après le `FunctionTailcall2` retour de la fonction, car la valeur peut changer ou être détruite.  
  
 La `FunctionTailcall2` fonction est un rappel ; vous devez l’implémenter. L’implémentation doit utiliser l' `__declspec` `naked` attribut de classe de stockage ().  
  
 Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.  
  
- À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).  
  
- À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.  
  
 L’implémentation de ne `FunctionTailcall2` doit pas être bloquée, car elle retardera garbage collection. L’implémentation ne doit pas essayer un garbage collection, car la pile n’est peut-être pas dans un État garbage collection. Si une garbage collection est tentée, le runtime se bloque jusqu’à ce que `FunctionTailcall2` retourne la valeur.  
  
 En outre, la `FunctionTailcall2` fonction ne doit pas appeler dans du code managé ou de quelque manière provoquer une allocation de mémoire managée.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf. idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [FunctionEnter2 (fonction)](functionenter2-function.md)
- [FunctionLeave2 (fonction)](functionleave2-function.md)
- [SetEnterLeaveFunctionHooks2, méthode](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Fonctions statiques globales du profilage](profiling-global-static-functions.md)

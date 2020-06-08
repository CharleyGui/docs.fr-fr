---
title: FunctionLeave (fonction)
ms.date: 03/30/2017
api_name:
- FunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave
helpviewer_keywords:
- FunctionLeave function [.NET Framework profiling]
ms.assetid: 18e89f45-e068-426a-be16-9f53a4346860
topic_type:
- apiref
ms.openlocfilehash: 836e4843ead940bc9f76ff6bdd0433e21e400afd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500635"
---
# <a name="functionleave-function"></a>FunctionLeave (fonction)
Notifie le profileur qu’une fonction va retourner à l’appelant.  
  
> [!NOTE]
> La `FunctionLeave` fonction est dépréciée dans le .NET Framework 2,0. Il continuera à fonctionner, mais entraînera une baisse des performances. Utilisez la fonction [FunctionLeave2](functionleave2-function.md) à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a>Paramètres

- `funcID`

  \[in] identificateur de la fonction qui retourne.

## <a name="remarks"></a>Remarques  
 La `FunctionLeave` fonction est un rappel ; vous devez l’implémenter. L’implémentation doit utiliser l' `__declspec` `naked` attribut de classe de stockage ().  
  
 Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.  
  
- À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).  
  
- À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.  
  
 L’implémentation de ne `FunctionLeave` doit pas être bloquée, car elle retardera garbage collection. L’implémentation ne doit pas essayer un garbage collection, car la pile n’est peut-être pas dans un État garbage collection. Si une garbage collection est tentée, le runtime se bloque jusqu’à ce que `FunctionLeave` retourne la valeur.  
  
 En outre, la `FunctionLeave` fonction ne doit pas appeler dans du code managé ou de quelque manière provoquer une allocation de mémoire managée.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf. idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :** 1,1, 1,0  
  
## <a name="see-also"></a>Voir aussi

- [FunctionEnter2 (fonction)](functionenter2-function.md)
- [FunctionLeave2 (fonction)](functionleave2-function.md)
- [FunctionTailcall2 (fonction)](functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2, méthode](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Fonctions statiques globales du profilage](profiling-global-static-functions.md)

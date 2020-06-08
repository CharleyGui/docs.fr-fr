---
title: FunctionEnter (fonction)
ms.date: 03/30/2017
api_name:
- FunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter
helpviewer_keywords:
- FunctionEnter function [.NET Framework profiling]
ms.assetid: bf4ffa50-4506-4dd4-aa13-a0457b47ca74
topic_type:
- apiref
ms.openlocfilehash: 52870c7446987817ff00b90db26c3265bccdd096
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500726"
---
# <a name="functionenter-function"></a>FunctionEnter (fonction)
Indique au profileur que le contrôle est passé à une fonction.  
  
> [!NOTE]
> La `FunctionEnter` fonction est déconseillée dans la version 2,0 de .NET Framework, et son utilisation entraîne une baisse des performances. Utilisez la fonction [FunctionEnter2](functionenter2-function.md) à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
## <a name="parameters"></a>Paramètres

- `funcID`

  \[in] identificateur de la fonction vers laquelle le contrôle est passé.

## <a name="remarks"></a>Remarques  
 La `FunctionEnter` fonction est un rappel ; vous devez l’implémenter. L’implémentation doit utiliser l' `__declspec` `naked` attribut de classe de stockage ().  
  
 Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.  
  
- À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).  
  
- À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.  
  
 L’implémentation de ne `FunctionEnter` doit pas être bloquée, car elle retardera garbage collection. L’implémentation ne doit pas essayer un garbage collection, car la pile n’est peut-être pas dans un État garbage collection. Si une garbage collection est tentée, le runtime se bloque jusqu’à ce que `FunctionEnter` retourne la valeur.  
  
 En outre, la `FunctionEnter` fonction ne doit pas appeler dans du code managé ou de quelque manière provoquer une allocation de mémoire managée.  
  
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

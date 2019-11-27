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
ms.openlocfilehash: ad34592223433f0bf541c390674bcf96839b6ca8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440820"
---
# <a name="functionenter-function"></a>FunctionEnter (fonction)
Indique au profileur que le contrôle est passé à une fonction.  
  
> [!NOTE]
> La fonction `FunctionEnter` est déconseillée dans la version .NET Framework 2,0, et son utilisation entraîne une baisse des performances. Utilisez la fonction [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `funcID`  
 dans Identificateur de la fonction à laquelle le contrôle est passé.  
  
## <a name="remarks"></a>Notes  
 La fonction `FunctionEnter` est un rappel ; vous devez l’implémenter. L’implémentation doit utiliser l’attribut de classe de stockage `__declspec`(`naked`).  
  
 Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.  
  
- À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).  
  
- À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.  
  
 L’implémentation de `FunctionEnter` ne doit pas être bloquée, car elle retardera garbage collection. L’implémentation ne doit pas essayer un garbage collection, car la pile n’est peut-être pas dans un État garbage collection. Si une garbage collection est tentée, le runtime se bloque jusqu’à ce que `FunctionEnter` retourne.  
  
 En outre, la fonction `FunctionEnter` ne doit pas appeler dans du code managé ou de quelque manière qu’elle génère une allocation de mémoire managée.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf. idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :** 1,1, 1,0  
  
## <a name="see-also"></a>Voir aussi

- [FunctionEnter2, fonction](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [FunctionLeave2, fonction](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [FunctionTailcall2, fonction](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Fonctions statiques globales de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)

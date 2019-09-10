---
title: FunctionTailcall (fonction)
ms.date: 03/30/2017
api_name:
- FunctionTailcall
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall
helpviewer_keywords:
- FunctionTailcall function [.NET Framework profiling]
ms.assetid: 66347e03-9a97-41e8-8f9d-89b80803f7b5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 12ec27277fe57bd1a291c2cfe491ea2c6f40c30e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851159"
---
# <a name="functiontailcall-function"></a>FunctionTailcall (fonction)
Indique au profileur que la fonction en cours d’exécution est sur le paragraphe d’effectuer un appel tail à une autre fonction.  
  
> [!NOTE]
> La `FunctionTailcall` fonction est déconseillée dans la version 2,0 de .NET Framework. Il continuera à fonctionner, mais entraînera une baisse des performances. Utilisez à la place la fonction [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `funcID`  
 dans Identificateur de la fonction en cours d’exécution qui va effectuer un appel tail.  
  
## <a name="remarks"></a>Notes  
 La fonction cible de l’appel tail utilise le frame de pile actuel et retourne directement à l’appelant de la fonction qui a effectué l’appel tail. Cela signifie qu’un rappel [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) ne sera pas émis pour une fonction qui est la cible d’un appel tail.  
  
 La `FunctionTailcall` fonction est un rappel ; vous devez l’implémenter. L’implémentation doit utiliser l' `__declspec`attribut`naked`de classe de stockage ().  
  
 Le moteur d’exécution n’enregistre aucun registre avant d’appeler cette fonction.  
  
- À l’entrée, vous devez enregistrer tous les registres que vous utilisez, y compris ceux de l’unité à virgule flottante (FPU).  
  
- À la sortie, vous devez restaurer la pile en dépilant tous les paramètres qui ont été envoyés par son appelant.  
  
 L’implémentation de `FunctionTailcall` ne doit pas être bloquée, car elle retardera garbage collection. L’implémentation ne doit pas essayer un garbage collection, car la pile n’est peut-être pas dans un État garbage collection. Si une garbage collection est tentée, le runtime se bloque jusqu’à ce que `FunctionTailcall` retourne la valeur.  
  
 En outre, `FunctionTailcall` la fonction ne doit pas appeler dans du code managé ou de quelque manière provoquer une allocation de mémoire managée.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions de .NET Framework :** 1.1, 1.0  
  
## <a name="see-also"></a>Voir aussi

- [FunctionEnter2, fonction](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [FunctionLeave2, fonction](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [SetEnterLeaveFunctionHooks2, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Fonctions statiques globales de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)

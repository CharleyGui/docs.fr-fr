---
title: ICorProfilerCallback8 ::D méthode ynamicMethodJITCompilationStarted
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 46a25fc6e9119481f728275e0569429cc6c46dc9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725428"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a>ICorProfilerCallback8 ::D méthode ynamicMethodJITCompilationStarted

[Pris en charge dans le .NET Framework 4,7 et versions ultérieures]  
  
Notifie le profileur chaque fois que la compilation JIT d’une méthode dynamique a démarré.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,
     [in]  BOOL        fIsSafeToBlock,
     [in]  LPCBYTE     pILHeader,
     [in]  LONG        cbILHeader
);  
```  
  
## <a name="parameters"></a>Paramètres  

[in] `functionId`  
Identificateur de la fonction en mémoire pour laquelle la compilation JIT est démarrée.

[in] `fIsSafeToBlock` 
 `true` pour indiquer que le blocage peut amener le runtime à attendre que le thread appelant retourne à partir de ce rappel ; `false`pour indiquer que le blocage n’affectera pas le fonctionnement du Runtime.  

[in] `pILHeader` Pointeur vers le premier octet de l’en-tête IL de la méthode.

[in] `cbILHeader` Nombre d’octets dans l’en-tête IL.

## <a name="remarks"></a>Remarques  

Ce rappel est déclenché chaque fois qu’une méthode dynamique est compilée juste-à-temps. Cela comprend plusieurs stubs IL et méthodes LCG. Son objectif est de fournir aux rédacteurs de profileur suffisamment d’informations pour identifier la méthode compilée pour les utilisateurs.

> [!NOTE]
> `functionId` les valeurs ne peuvent pas être utilisées pour la résolution de leurs jetons de métadonnées, car les méthodes dynamiques n’ont pas de métadonnées.

Le `pILHeader` pointeur est valide uniquement pendant le rappel.

## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [DynamicMethodJITCompilationFinished, méthode](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [ICorProfilerCallback8, interface](icorprofilercallback8-interface.md)

---
title: ICorProfilerCallback::JITCachedFunctionSearchStarted, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchStarted
helpviewer_keywords:
- JITCachedFunctionSearchStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchStarted method [.NET Framework profiling]
ms.assetid: 5cba642c-0d80-48ee-889d-198c5044d821
topic_type:
- apiref
ms.openlocfilehash: 938da4e3b7cc45c24dcac872ab504755116197a0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684016"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a>ICorProfilerCallback::JITCachedFunctionSearchStarted, méthode

Notifie le profileur qu’une recherche a démarré pour une fonction qui a été compilée précédemment à l’aide du générateur d’images natives (NGen.exe).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
## <a name="parameters"></a>Paramètres

- `functionId`

  \[in] ID de la fonction pour laquelle la recherche est effectuée.

- `pbUseCachedFunction`

  \[out] `true` si le moteur d’exécution doit utiliser la version mise en cache d’une fonction (si disponible); sinon, `false` . Si la valeur est `false` , le moteur d’exécution exécute une compilation JIT de la fonction au lieu d’une version qui n’est pas compilée juste-à-temps.

## <a name="remarks"></a>Remarques  

 Dans la version de .NET Framework 2,0, les `JITCachedFunctionSearchStarted` rappels de [méthode et ICorProfilerCallback :: JITCachedFunctionSearchFinished](icorprofilercallback-jitcachedfunctionsearchfinished-method.md) ne seront pas effectués pour toutes les fonctions dans les images NGen normales. Seules les images NGen optimisées pour un profil génèrent des rappels pour toutes les fonctions dans l’image. Toutefois, en raison de la surcharge supplémentaire, un profileur doit demander des images NGen optimisées par le profileur uniquement s’il envisage d’utiliser ces rappels pour forcer une fonction à être compilée juste-à-temps (JIT). Dans le cas contraire, le profileur doit utiliser une stratégie paresseuse pour la collecte d’informations sur les fonctions.  
  
 Les profileurs doivent prendre en charge les cas où plusieurs threads d’une application profilée appellent la même méthode simultanément. Par exemple, le thread A appelle `JITCachedFunctionSearchStarted` et le profileur répond en affectant à *pbUseCachedFunction* la valeur false pour forcer la compilation JIT. Le thread A appelle ensuite [ICorProfilerCallback :: JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) et [ICorProfilerCallback :: JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md).  
  
 Désormais, le thread B appelle `JITCachedFunctionSearchStarted` pour la même fonction. Même si le profileur a indiqué son intention de compiler la fonction juste-à-temps, le profileur reçoit le deuxième rappel, car le thread B envoie le rappel avant que le profileur ait répondu à l’appel de thread A à `JITCachedFunctionSearchStarted` . L’ordre dans lequel les threads effectuent des appels dépend de la façon dont les threads sont planifiés.  
  
 Quand le profileur reçoit des rappels en double, il doit définir la valeur référencée par `pbUseCachedFunction` à la même valeur pour tous les rappels en double. Autrement dit, lorsque `JITCachedFunctionSearchStarted` est appelé plusieurs fois avec la même `functionId` valeur, le profileur doit répondre de la même façon à chaque fois.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)

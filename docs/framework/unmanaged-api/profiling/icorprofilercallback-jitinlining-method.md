---
title: ICorProfilerCallback::JITInlining, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITInlining
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITInlining
helpviewer_keywords:
- JITInlining method [.NET Framework profiling]
- ICorProfilerCallback::JITInlining method [.NET Framework profiling]
ms.assetid: c2f45801-dd38-4b78-b6b7-64397dc73f83
topic_type:
- apiref
ms.openlocfilehash: 62035d623d56f7521e0a599a13bc20778e3f18d1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449903"
---
# <a name="icorprofilercallbackjitinlining-method"></a>ICorProfilerCallback::JITInlining, méthode
Indique au profileur que le compilateur juste-à-temps (JIT) est sur le point d’insérer une fonction en ligne avec une autre fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
## <a name="parameters"></a>Paramètres  
 `callerId`  
 dans ID de la fonction dans laquelle la fonction `calleeId` sera insérée.  
  
 `calleeId`  
 dans ID de la fonction à insérer.  
  
 `pfShouldInline`  
 [out] `true` pour permettre l’insertion ; Sinon, `false`.  
  
## <a name="remarks"></a>Notes  
 Le profileur peut définir `pfShouldInline` sur `false` pour empêcher l’insertion de la fonction `calleeId` dans la fonction `callerId`. En outre, le profileur peut désactiver globalement l’insertion inline à l’aide de la COR_PRF_DISABLE_INLINING valeur de l’énumération [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) .  
  
 Les fonctions insérées Inline ne déclenchent pas d’événements pour l’entrée ou la sortie. Par conséquent, le profileur doit définir `pfShouldInline` à `false` afin de produire un graphique des appels précis. La définition de `pfShouldInline` sur `false` affecte les performances, car l’insertion inline augmente généralement la vitesse et réduit le nombre d’événements de compilation JIT distincts pour la méthode insérée.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)

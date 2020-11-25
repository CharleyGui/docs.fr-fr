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
ms.openlocfilehash: cf68594620b24f2a5823aa423c5911f2d9d6b328
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725493"
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
 dans ID de la fonction dans laquelle la `calleeId` fonction sera insérée.  
  
 `calleeId`  
 dans ID de la fonction à insérer.  
  
 `pfShouldInline`  
 [out] `true` pour permettre l’insertion ; Sinon, `false` .  
  
## <a name="remarks"></a>Remarques  

 Le profileur peut avoir la valeur pour `pfShouldInline` `false` empêcher l’insertion de la `calleeId` fonction dans la `callerId` fonction. En outre, le profileur peut désactiver globalement l’insertion inline à l’aide de la COR_PRF_DISABLE_INLINING valeur de l’énumération [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) .  
  
 Les fonctions insérées Inline ne déclenchent pas d’événements pour l’entrée ou la sortie. Par conséquent, le profileur doit définir sur afin de `pfShouldInline` `false` produire un graphique des appels précis. La définition de la valeur `pfShouldInline` sur `false` affecte les performances, car l’insertion inline augmente généralement la vitesse et réduit le nombre d’événements de compilation JIT distincts pour la méthode insérée.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)

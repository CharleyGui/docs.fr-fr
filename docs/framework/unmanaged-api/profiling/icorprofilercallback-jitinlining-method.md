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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82af06837ead9a00923c23d4ce145015308fbbf7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782804"
---
# <a name="icorprofilercallbackjitinlining-method"></a>ICorProfilerCallback::JITInlining, méthode
Notifie le profileur que le compilateur juste-à-temps (JIT) est sur le point d’insertion d’une fonction conformément à une autre fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
## <a name="parameters"></a>Paramètres  
 `callerId`  
 [in] L’ID de la fonction dans laquelle le `calleeId` fonction sera insérée.  
  
 `calleeId`  
 [in] L’ID de la fonction doit être inséré.  
  
 `pfShouldInline`  
 [out] `true` pour permettre l’insertion ; sinon, `false`.  
  
## <a name="remarks"></a>Notes  
 Le profileur peut définir `pfShouldInline` à `false` pour empêcher le `calleeId` fonction à partir de laquelle elle est insérée la `callerId` (fonction). En outre, le profileur peut désactiver globalement l’insertion de ligne à l’aide de la valeur COR_PRF_DISABLE_INLINING de le [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) énumération.  
  
 Fonctions insérées inline ne déclenchent pas d’événements pour entrer ou de quitter. Par conséquent, le profileur doit définir `pfShouldInline` à `false` afin de produire un graphique des appels précis. Paramètre `pfShouldInline` à `false` affecte les performances, car l’insertion inline généralement augmente la vitesse et réduit le nombre d’événements de compilation JIT séparés pour la méthode insérée.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)

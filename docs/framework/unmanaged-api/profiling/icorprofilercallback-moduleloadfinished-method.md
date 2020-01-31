---
title: ICorProfilerCallback::ModuleLoadFinished, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadFinished
helpviewer_keywords:
- ModuleLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadFinished method [.NET Framework profiling]
ms.assetid: 050649e5-ffc0-4458-a0a4-d9ee128a219e
topic_type:
- apiref
ms.openlocfilehash: 661229e5fbd5d106662f0e823a1753bd76c33311
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866167"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a>ICorProfilerCallback::ModuleLoadFinished, méthode
Notifie le profileur qu’un module a fini de se charger.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a>Parameters  
 `moduleId`  
 dans ID du module dont le chargement est terminé.  
  
 `hrStatus`  
 dans HRESULT qui indique si le module a été chargé avec succès.  
  
## <a name="remarks"></a>Notes  
 La valeur de `moduleId` n’est pas valide pour une demande d’informations jusqu’à ce que la méthode `ModuleLoadFinished` soit appelée.  
  
 Certaines parties du chargement du module peuvent continuer après le rappel `ModuleLoadFinished`. Un HRESULT d’échec dans `hrStatus` indique un échec. Toutefois, un HRESULT de réussite dans `hrStatus` indique uniquement que la première partie du chargement du module a réussi.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)
- [ModuleLoadStarted, méthode](icorprofilercallback-moduleloadstarted-method.md)

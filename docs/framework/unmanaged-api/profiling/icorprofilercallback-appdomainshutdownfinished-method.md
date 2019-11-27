---
title: ICorProfilerCallback::AppDomainShutdownFinished, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownFinished
helpviewer_keywords:
- AppDomainShutdownFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownFinished method [.NET Framework profiling]
ms.assetid: 52794819-0a59-4bb1-a265-0f158cd5cd65
topic_type:
- apiref
ms.openlocfilehash: 8ff7d5a593388bd3a584e031aea411dfdb6c9845
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445197"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a>ICorProfilerCallback::AppDomainShutdownFinished, méthode
Notifie le profileur qu’un domaine d’application a été déchargé d’un processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a>Paramètres  
 `appDomainId`  
 dans Identifie le domaine dans lequel les assemblys de l’application sont stockés.  
  
 `hrStatus`  
 dans HRESULT qui indique si le domaine d’application a été déchargé avec succès.  
  
## <a name="remarks"></a>Notes  
 La valeur de `appDomainId` n’est pas valide pour une demande d’informations après le retour de la méthode [ICorProfilerCallback :: AppDomainShutdownStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) .  
  
 Certaines parties du déchargement du domaine d’application peuvent continuer après le rappel `AppDomainCreationFinished`. Un HRESULT d’échec dans `hrStatus` indique un échec. Toutefois, un HRESULT de réussite dans `hrStatus` indique uniquement que la première partie du déchargement du domaine d’application a réussi.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)

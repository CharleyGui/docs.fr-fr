---
title: ICorProfilerCallback::AppDomainCreationFinished, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationFinished
helpviewer_keywords:
- AppDomainCreationFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationFinished method [.NET Framework profiling]
ms.assetid: dbab7d90-d515-4dc9-8195-294d5d04bab6
topic_type:
- apiref
ms.openlocfilehash: 76f56971223154d3ed966c272081049adf30de54
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500492"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a>ICorProfilerCallback::AppDomainCreationFinished, méthode
Notifie le profileur qu’un domaine d’application a été créé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);
```  
  
## <a name="parameters"></a>Paramètres

- `appDomainId`

  \[in] identifie le domaine qui a été créé.

- `hrStatus`

  \[dans] HRESULT qui indique si la création du domaine d’application s’est terminée avec succès.

## <a name="remarks"></a>Remarques  
 L’ID d’application n’est valide pour aucune demande d’informations tant que la `AppDomainCreationFinished` méthode n’est pas appelée.  
  
 Certaines parties du chargement du domaine d’application peuvent continuer après le `AppDomainCreationFinished` rappel. Un HRESULT d’échec dans `hrStatus` indique un échec. Toutefois, un HRESULT de réussite dans `hrStatus` indique uniquement que la première partie de la création du domaine d’application a réussi.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)

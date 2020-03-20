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
ms.openlocfilehash: 8b3f7712436c001e5cd44f214f6edb06390abd41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177070"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a>ICorProfilerCallback::AppDomainCreationFinished, méthode
Informe le profileur qu’un domaine d’application a été créé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);
```  
  
## <a name="parameters"></a>Paramètres

- `appDomainId`

  \[dans) Identifie le domaine qui a été créé.

- `hrStatus`

  \[dans] Un HRESULT qui indique si la création du domaine d’application a été complétée avec succès.

## <a name="remarks"></a>Notes   
 L’ID de demande n’est `AppDomainCreationFinished` pas valide pour toute demande d’information jusqu’à ce que la méthode soit appelée.  
  
 Certaines parties du chargement du `AppDomainCreationFinished` domaine d’application peuvent continuer après le rappel. Un échec HRESULT dans `hrStatus` indique une défaillance. Cependant, un succès HRESULT indique `hrStatus` seulement que la première partie de la création du domaine de l’application a réussi.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)

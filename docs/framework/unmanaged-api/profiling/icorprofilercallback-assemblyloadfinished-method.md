---
title: ICorProfilerCallback::AssemblyLoadFinished, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadFinished
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadFinished method [.NET Framework profiling]
- AssemblyLoadFinished method [.NET Framework profiling]
ms.assetid: 86d98f39-52e6-4c61-a625-9760f695ff12
topic_type:
- apiref
ms.openlocfilehash: ce4a842bc71ff144e46efb0d6f7068dfca9d207d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500440"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a>ICorProfilerCallback::AssemblyLoadFinished, méthode
Notifie le profileur qu’un chargement de l’assembly est terminé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a>Paramètres

- `assemblyId`

  \[in] identifie l’assembly qui a été chargé.

- `hrStatus`

  \[dans] HRESULT qui indique si le chargement de l’assembly s’est terminé correctement.

## <a name="remarks"></a>Remarques  
 La valeur de `assemblyId` n’est pas valide pour une demande d’informations tant que la `AssemblyLoadFinished` méthode n’est pas appelée.  
  
 Certaines parties du chargement de l’assembly peuvent continuer après le `AssemblyLoadFinished` rappel. Un HRESULT d’échec dans `hrStatus` indique un échec. Toutefois, un HRESULT de réussite dans `hrStatus` indique uniquement que la première partie du chargement de l’assembly a réussi.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)

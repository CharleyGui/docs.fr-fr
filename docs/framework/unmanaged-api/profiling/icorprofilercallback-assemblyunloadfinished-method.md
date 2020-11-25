---
title: ICorProfilerCallback::AssemblyUnloadFinished, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadFinished
helpviewer_keywords:
- AssemblyUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::AssemblyUnloadFinished method [.NET Framework profiling]
ms.assetid: 53fca564-84b1-44d4-9e21-17a492d2aae7
topic_type:
- apiref
ms.openlocfilehash: 3f2b4a64b3f17b043f193e054c56601d706a10e1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700377"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a>ICorProfilerCallback::AssemblyUnloadFinished, méthode

Notifie le profileur qu’un assembly a été déchargé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a>Paramètres

- `assemblyId`

  \[in] identifie l’assembly qui est déchargé.

- `hrStatus`

  \[dans] HRESULT qui indique si l’assembly a été déchargé avec succès.

## <a name="remarks"></a>Remarques  

 La valeur de `assemblyId` n’est pas valide pour une demande d’informations après le retour de la méthode [ICorProfilerCallback :: AssemblyUnloadStarted,](icorprofilercallback-assemblyunloadstarted-method.md) .  
  
 Certaines parties du déchargement de l’assembly peuvent continuer après le `AssemblyUnloadFinished` rappel. Un HRESULT d’échec dans `hrStatus` indique un échec. Toutefois, un HRESULT de réussite dans `hrStatus` indique uniquement que la première partie du déchargement de l’assembly a réussi.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)

---
title: ICorDebugProcess::GetHelperThreadID, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHelperThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHelperThreadID
helpviewer_keywords:
- GetHelperThreadID method [.NET Framework debugging]
- ICorDebugProcess::GetHelperThreadID method [.NET Framework debugging]
ms.assetid: 84e1e605-37c1-49a5-8e12-35db85654622
topic_type:
- apiref
ms.openlocfilehash: 77cc658e28c7a69d8c4aeeed2f3e7ea40f0d2af6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724570"
---
# <a name="icordebugprocessgethelperthreadid-method"></a>ICorDebugProcess::GetHelperThreadID, méthode

Obtient l’ID de thread (se) du système d’exploitation du thread d’assistance interne du débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pThreadID`  
 à Pointeur vers l’ID de thread de système d’exploitation du thread d’assistance interne du débogueur.  
  
## <a name="remarks"></a>Remarques  

 Lors du débogage managé et non managé, il incombe au débogueur de s’assurer que le thread avec l’ID spécifié reste en cours d’exécution s’il atteint un point d’arrêt placé par le débogueur. Un débogueur peut également souhaiter masquer ce thread à l’utilisateur. Si aucun thread d’assistance n’existe encore dans le processus, la `GetHelperThreadID` méthode retourne zéro dans * `pThreadID` .  
  
 Vous ne pouvez pas mettre en cache l’ID de thread du thread d’assistance, car il peut changer au fil du temps. Vous devez relancer l’interrogation de l’ID de thread à chaque événement d’arrêt.  
  
 L’ID de thread du thread d’assistance du débogueur est correct sur chaque événement [ICorDebugManagedCallback :: CreateThread](icordebugmanagedcallback-createthread-method.md) non managé, ce qui permet à un débogueur de déterminer l’ID de thread de son thread d’assistance et de le masquer à l’utilisateur. Un thread identifié comme un thread d’assistance pendant un événement non managé `ICorDebugManagedCallback::CreateThread` n’exécutera jamais le code utilisateur managé.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug. idl. CorDebug. h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

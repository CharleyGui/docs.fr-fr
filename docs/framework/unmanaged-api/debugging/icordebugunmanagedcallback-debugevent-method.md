---
title: ICorDebugUnmanagedCallback::DebugEvent, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugUnmanagedCallback.DebugEvent
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnmanagedCallback::DebugEvent
helpviewer_keywords:
- DebugEvent method [.NET Framework debugging]
- ICorDebugUnmanagedCallback::DebugEvent method [.NET Framework debugging]
ms.assetid: be9cab04-65ec-44d5-a39a-f90709fdd043
topic_type:
- apiref
ms.openlocfilehash: 75341b1af034972c861b75f29a06eaa2c4e33c3a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703030"
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a>ICorDebugUnmanagedCallback::DebugEvent, méthode

Notifie le débogueur qu’un événement natif a été déclenché.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pDebugEvent`  
 dans Pointeur vers l’événement natif.  
  
 `fOutOfBand`  
 [in] `true` , si l’interaction avec l’état de processus managé est impossible après un événement non managé, jusqu’à ce que le débogueur appelle [ICorDebugController :: continue](icordebugcontroller-continue-method.md); sinon, `false` .  
  
## <a name="remarks"></a>Remarques  

 Si le thread en cours de débogage est un thread Win32, n’utilisez pas les membres de l’interface de débogage Win32. Vous pouvez appeler `ICorDebugController::Continue` uniquement sur un thread Win32 et uniquement en cas de dépassement d’un événement hors bande.  
  
 Le `DebugEvent` rappel ne suit pas les règles standard pour les rappels. Lorsque vous appelez `DebugEvent` , le processus sera à l’état d’arrêt de débogage du système d’exploitation brut. Le processus ne sera pas synchronisé. Elle entrera automatiquement en état synchronisé si nécessaire pour répondre aux demandes d’informations sur le code managé, ce qui peut entraîner d’autres `DebugEvent` rappels imbriqués.  
  
 Appelez [ICorDebugProcess :: ClearCurrentException](icordebugprocess-clearcurrentexception-method.md) sur le processus pour ignorer un événement d’exception avant de poursuivre le processus. L’appel de cette méthode envoie DBG_CONTINUE au lieu de DBG_EXCEPTION_NOT_HANDLED sur la demande de reprise, et efface automatiquement les points d’arrêt hors bande et les exceptions en une seule étape. Les événements hors bande peuvent se trouver à tout moment, même lorsque l’application en cours de débogage apparaît comme arrêtée et lorsqu’un événement intrabande en suspens existe déjà.  
  
 Dans la version de .NET Framework 2,0, le débogueur doit immédiatement continuer après un événement de point d’arrêt hors plage. Le débogueur doit utiliser les méthodes [ICorDebugProcess2 :: SetUnmanagedBreakpoint,](icordebugprocess2-setunmanagedbreakpoint-method.md) et [ICorDebugProcess2 :: ClearUnmanagedBreakpoint,](icordebugprocess2-clearunmanagedbreakpoint-method.md) pour ajouter et supprimer des points d’arrêt. Ces méthodes ignorent automatiquement les points d’arrêt hors bande. Ainsi, les seuls points d’arrêt hors bande qui sont distribués doivent être des points d’arrêt bruts qui se trouvent déjà dans le flux d’instructions, par exemple un appel à la `DebugBreak` fonction Win32. N’essayez pas d’utiliser `ICorDebugProcess::ClearCurrentException` , [ICorDebugProcess :: GetThreadContext](icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess :: SetThreadContext](icordebugprocess-setthreadcontext-method.md)ni un autre membre de l' [API de débogage](index.md).  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugUnmanagedCallback, interface](icordebugunmanagedcallback-interface.md)

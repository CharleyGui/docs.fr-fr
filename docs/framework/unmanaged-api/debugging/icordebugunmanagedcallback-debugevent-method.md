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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1c75e1844fca4e592faa924a55432dd42fa7355
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772623"
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
 [in] Pointeur vers l’événement natif.  
  
 `fOutOfBand`  
 [in] `true`, si l’interaction avec l’état de processus managé est impossible après un événement non managé, jusqu'à ce que le débogueur appelle [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); sinon, `false`.  
  
## <a name="remarks"></a>Notes  
 Si le thread en cours de débogage est un thread Win32, n’utilisez pas tous les membres de Win32 interface de débogage. Vous pouvez appeler `ICorDebugController::Continue` uniquement sur un thread Win32 et uniquement lorsque vous continuez après un événement hors-bande.  
  
 Le `DebugEvent` rappel ne suit pas les règles standard pour les rappels. Lorsque vous appelez `DebugEvent`, le processus est dans le texte brut, état arrêté du débogage de système d’exploitation. Le processus ne seront pas synchronisé. Il insère automatiquement l’état synchronisé lorsque cela est nécessaire pour répondre aux demandes d’informations sur le code managé, ce qui peut aboutir dans d’autres imbriqués `DebugEvent` rappels.  
  
 Appelez [ICorDebugProcess::ClearCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) sur le processus pour ignorer un événement d’exception avant de poursuivre le processus. Appelez cette méthode envoie DBG_CONTINUE au lieu de DBG_EXCEPTION_NOT_HANDLED sur la demande de continuer et efface automatiquement les points d’arrêt hors-bande et les exceptions de la seule étape. Out-of-band événements peuvent provenir à tout moment, même lorsque l’application en cours de débogage s’affiche arrêtée et lorsqu’un événement dans la bande en attente existe déjà.  
  
 Dans le .NET Framework version 2.0, le débogueur doit continuer immédiatement après un événement de point d’arrêt hors-bande. Le débogueur doit être à l’aide de la [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) et [ICorDebugProcess2::ClearUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) méthodes pour ajouter et supprimer des points d’arrêt. Ces méthodes ignoreront automatiquement les points d’arrêt hors-bande. Par conséquent, les points d’arrêt uniquement out-of-band distribuer doivent être des points d’arrêt bruts qui sont déjà dans le flux d’instructions, tel qu’un appel à la constante Win32 `DebugBreak` (fonction). N’essayez pas d’utiliser `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess::GetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess::SetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md), ou tout autre membre de la [API de débogage](../../../../docs/framework/unmanaged-api/debugging/index.md).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugUnmanagedCallback, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)

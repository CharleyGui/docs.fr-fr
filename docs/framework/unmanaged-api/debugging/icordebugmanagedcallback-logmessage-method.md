---
title: ICorDebugManagedCallback::LogMessage, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LogMessage
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogMessage
helpviewer_keywords:
- ICorDebugManagedCallback::LogMessage method [.NET Framework debugging]
- LogMessage method [.NET Framework debugging]
ms.assetid: d218554a-bf42-4d88-833d-ede30de67a53
topic_type:
- apiref
ms.openlocfilehash: 92b2a7f7f1dd98f0d847119a6431e3816c16d5da
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679570"
---
# <a name="icordebugmanagedcallbacklogmessage-method"></a>ICorDebugManagedCallback::LogMessage, méthode

Notifie le débogueur qu’un thread managé common language runtime (CLR) a appelé une méthode dans la <xref:System.Diagnostics.EventLog> classe pour enregistrer un événement.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT LogMessage (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pMessage  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pAppDomain`  
 dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant le thread managé qui a enregistré l’événement.  
  
 `pThread`  
 dans Pointeur vers un objet ICorDebugThread qui représente le thread managé.  
  
 `lLevel`  
 dans Valeur de l’énumération [LoggingLevelEnum,](logginglevelenum-enumeration.md) qui indique le niveau de gravité du message descriptif écrit dans le journal des événements.  
  
 `pLogSwitchName`  
 dans Pointeur vers le nom du commutateur de traçage.  
  
 `pMessage`  
 dans Pointeur vers le message qui a été écrit dans le journal des événements.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugManagedCallback, interface](icordebugmanagedcallback-interface.md)

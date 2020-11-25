---
title: ICorDebugManagedCallback::LogSwitch, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LogSwitch
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogSwitch
helpviewer_keywords:
- LogSwitch method [.NET Framework debugging]
- ICorDebugManagedCallback::LogSwitch method [.NET Framework debugging]
ms.assetid: 0ac59d27-783f-4a87-b7a8-baa3ccc54582
topic_type:
- apiref
ms.openlocfilehash: db6ccd63bbeadd7dcff1c7f8491b59017d431d12
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720696"
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a>ICorDebugManagedCallback::LogSwitch, méthode

Notifie le débogueur qu’un thread managé common language runtime (CLR) a appelé une méthode dans la <xref:System.Diagnostics.Switch> classe pour créer, modifier ou supprimer un commutateur de débogage/traçage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
## <a name="parameters"></a>Paramètres  

 `PAppDomain`  
 dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant le thread managé qui a créé, modifié ou supprimé un commutateur de débogage/traçage.  
  
 `pThread`  
 dans Pointeur vers un objet ICorDebugThread qui représente le thread managé.  
  
 `lLevel`  
 dans Valeur qui indique le niveau de gravité du message descriptif qui a été écrit dans le journal des événements.  
  
 `ulReason`  
 dans Valeur de l’énumération [LogSwitchCallReason,](logswitchcallreason-enumeration.md) qui indique l’opération effectuée sur le commutateur de débogage/traçage.  
  
 `pLogSwitchName`  
 dans Pointeur vers le nom du commutateur de débogage/traçage.  
  
 `pParentName`  
 dans Pointeur vers le nom du parent du commutateur de débogage/traçage.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugManagedCallback, interface](icordebugmanagedcallback-interface.md)

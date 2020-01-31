---
title: ICorDebugManagedCallback2::ExceptionUnwind, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ExceptionUnwind
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind
helpviewer_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind method [.NET Framework debugging]
- ExceptionUnwind method [.NET Framework debugging]
ms.assetid: aaf5938d-179c-4eaa-8d35-8523a4fadded
topic_type:
- apiref
ms.openlocfilehash: 482afd09ce370fb1247864b9ac2032ee7e3a1dca
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788277"
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a>ICorDebugManagedCallback2::ExceptionUnwind, méthode
Fournit une notification d’État pendant le processus de déroulement de l’exception.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `pAppDomain`  
 dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant le thread sur lequel l’exception a été levée.  
  
 `pThread`  
 dans Pointeur vers un objet ICorDebugThread qui représente le thread sur lequel l’exception a été levée.  
  
 `dwEventType`  
 dans Valeur de l’énumération CorDebugExceptionUnwindCallbackType, qui spécifie l’événement signalé par le rappel au cours de la phase de déroulement.  
  
 `dwFlags`  
 dans Valeur de l’énumération [CorDebugExceptionFlags,](cordebugexceptionflags-enumeration.md) qui spécifie des informations supplémentaires sur l’exception.  
  
## <a name="remarks"></a>Notes  
 `ExceptionUnwind` est appelé à différents points pendant la phase de déroulement du processus de gestion des exceptions. `ExceptionUnwind` peut être appelé plusieurs fois tout en déroulant une seule exception.  
  
 Si `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, le pointeur d’instruction se trouve dans le frame de feuille du thread, au point de séquence avant (il peut y avoir plusieurs instructions avant) l’instruction qui a mené à l’exception.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugManagedCallback2, interface](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback, interface](icordebugmanagedcallback-interface.md)

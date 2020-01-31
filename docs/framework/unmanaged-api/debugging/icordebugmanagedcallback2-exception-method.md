---
title: ICorDebugManagedCallback2::Exception, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::Exception
helpviewer_keywords:
- ICorDebugManagedCallback2::Exception method [.NET Framework debugging]
- Exception method, ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: 78b0f14f-2fae-4e63-8412-4df119ee8468
topic_type:
- apiref
ms.openlocfilehash: e7125d923fb1d3757bb4ca53f5a7db806b241dd9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781524"
---
# <a name="icordebugmanagedcallback2exception-method"></a>ICorDebugManagedCallback2::Exception, méthode
Notifie le débogueur qu’une recherche d’un gestionnaire d’exceptions a démarré.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `pAppDomain`  
 dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant le thread sur lequel l’exception a été levée.  
  
 `pThread`  
 dans Pointeur vers un objet ICorDebugThread qui représente le thread sur lequel l’exception a été levée.  
  
 `pFrame`  
 dans Pointeur vers un objet ICorDebugFrame qui représente un frame, tel que déterminé par le paramètre `dwEventType`. Pour plus d’informations, consultez le tableau dans la section Notes.  
  
 `nOffset`  
 dans Entier qui spécifie un décalage, tel que déterminé par le paramètre `dwEventType`. Pour plus d’informations, consultez le tableau dans la section Notes.  
  
 `dwEventType`  
 dans Valeur de l’énumération CorDebugExceptionCallbackType, qui spécifie le type de ce rappel d’exception.  
  
 `dwFlags`  
 dans Valeur de l’énumération [CorDebugExceptionFlags,](cordebugexceptionflags-enumeration.md) qui spécifie des informations supplémentaires sur l’exception.  
  
## <a name="remarks"></a>Notes  
 Le rappel `Exception` est appelé à différents moments pendant la phase de recherche du processus de gestion des exceptions. Autrement dit, il peut être appelé plusieurs fois tout en déroulant une exception.  
  
 L’exception en cours de traitement peut être récupérée à partir de l’objet ICorDebugThread référencé par le paramètre `pThread`.  
  
 Le frame et le décalage particuliers sont déterminés par le paramètre `dwEventType` comme suit :  
  
|Valeur de `dwEventType`|Valeur de `pFrame`|Valeur de `nOffset`|  
|----------------------------|-----------------------|------------------------|  
|DEBUG_EXCEPTION_FIRST_CHANCE|Frame qui a levé l’exception.|Pointeur d’instruction dans le frame.|  
|DEBUG_EXCEPTION_USER_FIRST_CHANCE|Frame de code utilisateur le plus proche du point de l’exception levée.|Pointeur d’instruction dans le frame.|  
|DEBUG_EXCEPTION_CATCH_HANDLER_FOUND|Frame qui contient le gestionnaire catch.|Offset MSIL (Microsoft Intermediate Language) du début du gestionnaire catch.|  
|DEBUG_EXCEPTION_UNHANDLED|NULL|Non défini.|  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugManagedCallback2, interface](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback, interface](icordebugmanagedcallback-interface.md)

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
ms.openlocfilehash: c5be9231bcd5aaddfa0cf1b0051f8e1184faef04
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687630"
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
  
## <a name="parameters"></a>Paramètres  

 `pAppDomain`  
 dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant le thread sur lequel l’exception a été levée.  
  
 `pThread`  
 dans Pointeur vers un objet ICorDebugThread qui représente le thread sur lequel l’exception a été levée.  
  
 `pFrame`  
 dans Pointeur vers un objet ICorDebugFrame qui représente un frame, tel que déterminé par le `dwEventType` paramètre. Pour plus d’informations, consultez le tableau dans la section Notes.  
  
 `nOffset`  
 dans Entier qui spécifie un décalage, tel que déterminé par le `dwEventType` paramètre. Pour plus d’informations, consultez le tableau dans la section Notes.  
  
 `dwEventType`  
 dans Valeur de l’énumération CorDebugExceptionCallbackType, qui spécifie le type de ce rappel d’exception.  
  
 `dwFlags`  
 dans Valeur de l’énumération [CorDebugExceptionFlags,](cordebugexceptionflags-enumeration.md) qui spécifie des informations supplémentaires sur l’exception.  
  
## <a name="remarks"></a>Remarques  

 Le `Exception` rappel est appelé à différents moments pendant la phase de recherche du processus de gestion des exceptions. Autrement dit, il peut être appelé plusieurs fois tout en déroulant une exception.  
  
 L’exception en cours de traitement peut être récupérée à partir de l’objet ICorDebugThread référencé par le `pThread` paramètre.  
  
 Le frame et le décalage particuliers sont déterminés par le `dwEventType` paramètre comme suit :  
  
|Valeur de `dwEventType`|Valeur de `pFrame`|Valeur de `nOffset`|  
|----------------------------|-----------------------|------------------------|  
|DEBUG_EXCEPTION_FIRST_CHANCE|Frame qui a levé l’exception.|Pointeur d’instruction dans le frame.|  
|DEBUG_EXCEPTION_USER_FIRST_CHANCE|Frame de code utilisateur le plus proche du point de l’exception levée.|Pointeur d’instruction dans le frame.|  
|DEBUG_EXCEPTION_CATCH_HANDLER_FOUND|Frame qui contient le gestionnaire catch.|Offset MSIL (Microsoft Intermediate Language) du début du gestionnaire catch.|  
|DEBUG_EXCEPTION_UNHANDLED|NULL|Non défini.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugManagedCallback2, interface](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback, interface](icordebugmanagedcallback-interface.md)

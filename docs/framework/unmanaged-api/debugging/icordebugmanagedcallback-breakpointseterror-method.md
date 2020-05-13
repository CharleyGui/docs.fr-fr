---
title: ICorDebugManagedCallback::BreakpointSetError, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.BreakpointSetError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::BreakpointSetError
helpviewer_keywords:
- BreakpointSetError method [.NET Framework debugging]
- ICorDebugManagedCallback::BreakpointSetError method [.NET Framework debugging]
ms.assetid: f2b773a4-c4d0-429c-9717-51d6e2ed86af
topic_type:
- apiref
ms.openlocfilehash: 0fa25dd33223ad2a9521aed0917ce35a2a33fa2f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213385"
---
# <a name="icordebugmanagedcallbackbreakpointseterror-method"></a>ICorDebugManagedCallback::BreakpointSetError, méthode
Notifie le débogueur que le common language runtime n’a pas pu lier avec précision un point d’arrêt qui a été défini avant qu’une fonction ait été compilée juste-à-temps (JIT).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT BreakpointSetError (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint,  
    [in] DWORD                dwError  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pAppDomain`  
 dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application qui contient le point d’arrêt non lié.  
  
 `pThread`  
 dans Pointeur vers un objet ICorDebugThread qui représente le thread qui contient le point d’arrêt non lié.  
  
 `pBreakpoint`  
 dans Pointeur vers un objet ICorDebugBreakpoint qui représente le point d’arrêt non lié.  
  
 `dwError`  
 dans Entier qui indique l’erreur.  
  
## <a name="remarks"></a>Remarks  
 Le point d’arrêt donné ne sera jamais atteint. Le débogueur doit le désactiver et le lier de nouveau.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugManagedCallback, interface](icordebugmanagedcallback-interface.md)

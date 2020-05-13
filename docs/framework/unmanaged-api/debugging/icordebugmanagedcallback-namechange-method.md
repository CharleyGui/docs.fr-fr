---
title: ICorDebugManagedCallback::NameChange, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.NameChange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::NameChange
helpviewer_keywords:
- ICorDebugManagedCallback::NameChange method [.NET Framework debugging]
- NameChange method [.NET Framework debugging]
ms.assetid: a7018a0e-880e-4b68-b52a-1cd22c7aad62
topic_type:
- apiref
ms.openlocfilehash: 48bfce9966ff12fe1b425fbcd9a81860628a54e6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212670"
---
# <a name="icordebugmanagedcallbacknamechange-method"></a>ICorDebugManagedCallback::NameChange, méthode
Notifie le débogueur que le nom d’un domaine d’application ou d’un thread a changé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pAppDomain`  
 dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application dont le nom a été modifié ou qui contient le thread qui a subi un changement de nom.  
  
 `pThread`  
 dans Pointeur vers un objet ICorDebugThread qui représente le thread dont le nom a été modifié.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugManagedCallback, interface](icordebugmanagedcallback-interface.md)

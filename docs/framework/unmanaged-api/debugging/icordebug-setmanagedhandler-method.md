---
title: ICorDebug::SetManagedHandler, méthode
ms.date: 03/30/2017
api_name:
- ICorDebug.SetManagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetManagedHandler
helpviewer_keywords:
- ICorDebug::SetManagedHandler method [.NET Framework debugging]
- SetManagedHandler method [.NET Framework debugging]
ms.assetid: d079131b-685b-4869-95be-826b88d28bd2
topic_type:
- apiref
ms.openlocfilehash: 54ef1cab27a39de39b39996729be6b8160570745
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788967"
---
# <a name="icordebugsetmanagedhandler-method"></a>ICorDebug::SetManagedHandler, méthode
Spécifie l’objet de gestionnaire d’événements pour les événements managés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `pCallback`  
 dans Pointeur vers un objet [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) , qui est l’objet de gestionnaire d’événements.  
  
## <a name="remarks"></a>Notes  
 `SetManagedHandler` doit être appelée au moment de la création.  
  
 Si l’implémentation de `ICorDebugManagedCallback` ne contient pas d’interfaces suffisantes pour gérer les événements de débogage de l’application en cours de débogage, `SetManagedHandler` retourne un HRESULT de E_NOINTERFACE.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebug, interface](icordebug-interface.md)

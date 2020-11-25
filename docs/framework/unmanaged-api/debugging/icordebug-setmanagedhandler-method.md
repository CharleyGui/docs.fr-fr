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
ms.openlocfilehash: 97a4a464d3dfb7b333f44ac4206bd880fd171e16
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723413"
---
# <a name="icordebugsetmanagedhandler-method"></a>ICorDebug::SetManagedHandler, méthode

Spécifie l’objet de gestionnaire d’événements pour les événements managés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pCallback`  
 dans Pointeur vers un objet [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) , qui est l’objet de gestionnaire d’événements.  
  
## <a name="remarks"></a>Remarques  

 `SetManagedHandler` doit être appelé au moment de la création.  
  
 Si l' `ICorDebugManagedCallback` implémentation ne contient pas suffisamment d’interfaces pour gérer les événements de débogage de l’application en cours de débogage, `SetManagedHandler` retourne un HRESULT de E_NOINTERFACE.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebug, interface](icordebug-interface.md)

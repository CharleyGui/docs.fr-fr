---
title: ICorDebug::SetUnmanagedHandler, méthode
ms.date: 03/30/2017
api_name:
- ICorDebug.SetUnmanagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetUnmanagerHandler
helpviewer_keywords:
- SetUnmanagedHandler method [.NET Framework debugging]
- ICorDebug::SetUnmanagedHandler method [.NET Framework debugging]
ms.assetid: 6b546be4-f86d-4536-8cfc-1d08e5066eb6
topic_type:
- apiref
ms.openlocfilehash: 0bce14a6853c872d27057b9fffc32b54c59abf13
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723387"
---
# <a name="icordebugsetunmanagedhandler-method"></a>ICorDebug::SetUnmanagedHandler, méthode

Spécifie l’objet de gestionnaire d’événements pour les événements non managés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pCallback`  
 dans Pointeur vers un objet [ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md) qui représente le gestionnaire d’événements pour les événements non managés.  
  
## <a name="remarks"></a>Remarques  

 L’objet de gestionnaire d’événements pour les événements non managés doit être défini après un appel à [ICorDebug :: Initialize](icordebug-initialize-method.md) et avant tout appel à [ICorDebug :: CreateProcess](icordebug-createprocess-method.md) ou [ICorDebug ::D ebugactiveprocess](icordebug-debugactiveprocess-method.md). Toutefois, pour des raisons d’héritage, vous n’êtes pas obligé de définir l’objet de gestionnaire d’événements pour les événements non managés tant que le premier événement de débogage natif n’est pas déclenché. En particulier, si `ICorDebug::CreateProcess` a défini l’indicateur CREATE_SUSPENDED, les événements de débogage natifs ne peuvent pas être distribués tant que le thread principal n’a pas repris.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebug, interface](icordebug-interface.md)

---
title: ICorDebugManagedCallback::ControlCTrap, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ControlCTrap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ControlCTrap
helpviewer_keywords:
- ICorDebugManagedCallback::ControlCTrap method [.NET Framework debugging]
- ControlCTrap method [.NET Framework debugging]
ms.assetid: 0500854e-2121-43d9-a028-64312da35258
topic_type:
- apiref
ms.openlocfilehash: 33a68d11a8d17e46533b4f83bbf87aafe171e612
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212397"
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a>ICorDebugManagedCallback::ControlCTrap, méthode
Notifie le débogueur qu’un CTRL + C est intercepté dans le processus en cours de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pProcess`  
 dans Pointeur vers un objet ICorDebugProcess qui représente le processus dans lequel CTRL + C est intercepté.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Le débogueur gère l’interruption CTRL + C.|  
|S_FALSE|Le débogueur ne gère pas l’interruption CTRL + C.|  
  
## <a name="remarks"></a>Remarks  
 Tous les domaines d’application au sein du processus sont arrêtés pour ce rappel.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugManagedCallback, interface](icordebugmanagedcallback-interface.md)

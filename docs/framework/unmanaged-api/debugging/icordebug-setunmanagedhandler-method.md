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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f50a4bedfee0c402bb76265371d3b9809263ef97
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738139"
---
# <a name="icordebugsetunmanagedhandler-method"></a>ICorDebug::SetUnmanagedHandler, méthode
Spécifie l’objet de gestionnaire d’événements pour les événements non gérés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pCallback`  
 [in] Un pointeur vers un [ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) objet qui représente le Gestionnaire d’événements pour les événements non gérés.  
  
## <a name="remarks"></a>Notes  
 Le Gestionnaire d’événements objet non managé événements doivent être définies après un appel à [ICorDebug::Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) et avant tous les appels à [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) ou [ICorDebug::DebugActiveProcess ](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md). Toutefois, pour des raisons d’héritage, vous n'êtes pas obligé définir l’objet de gestionnaire d’événements pour les événements non gérés jusqu'à ce que le premier événement de débogage natif est déclenché. Plus précisément, si `ICorDebug::CreateProcess` a défini l’indicateur CREATE_SUSPENDED, les événements ne peuvent pas être distribués jusqu'à ce que le thread principal est repris de débogage natif.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebug, interface](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

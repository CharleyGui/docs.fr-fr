---
title: ICorDebugThread4::HadUnhandledException, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.HadUnhandledException Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::HadUnhandledException
helpviewer_keywords:
- ICorDebugThread4::HadUnhandledException method [.NET Framework debugging]
- HadUnhandledException method [.NET Framework debugging]
ms.assetid: 05558daa-39e2-4c38-aeaf-e2aec4a09468
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9bbc3379ff9523564f4eae7da96fca2247601fcd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765155"
---
# <a name="icordebugthread4hadunhandledexception-method"></a>ICorDebugThread4::HadUnhandledException, méthode
Indique si le thread a déjà eu une exception non gérée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
## <a name="parameters"></a>Paramètres  
 `ppBlockingObjectEnum`  
 [out] Un pointeur vers l’adresse d’une énumération ordonnée de [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Le thread a eu une exception non gérée depuis sa création.|  
|S_FALSE|Le thread n’a jamais été une exception non gérée.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode indique si le thread a déjà eu une exception non gérée. Au moment où le rappel d’exception non gérée est déclenché ou natif JIT-attach est lancée, cette méthode renvoie toujours S_OK. Il n’existe aucune garantie que le [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) méthode retournera l’exception non gérée ; Cependant, cette opération si le processus n’a pas encore repris après avoir obtenu le rappel d’exception non gérée ou en cas de JIT natif. En outre, il est possible (bien qu’improbable) d’avoir plusieurs threads avec une exception non gérée au moment de JIT natif est déclenchée. Dans ce cas il n’existe aucun moyen pour déterminer quelle exception a déclenché la JIT-attach.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugThread4, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)

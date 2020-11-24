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
ms.openlocfilehash: 4e368b2c63e8e43b5c392bec4b79daac8bae249d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678532"
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
 à Pointeur vers l’adresse d’une énumération ordonnée de structures [CorDebugBlockingObject](cordebugblockingobject-structure.md) .  
  
## <a name="return-value"></a>Valeur renvoyée  

 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Le thread a rencontré une exception non gérée depuis sa création.|  
|S_FALSE|Le thread n’a jamais eu d’exception non gérée.|  
  
## <a name="remarks"></a>Remarques  

 Cette méthode indique si le thread a déjà eu une exception non gérée. Au moment où le rappel d’exception non gérée est déclenché ou que l’attachement JIT natif est initié, il est garanti que cette méthode retourne S_OK. Il n’y a aucune garantie que la méthode [ICorDebugThread. GetCurrentException](icordebugthread-getcurrentexception-method.md) retourne l’exception non gérée ; Toutefois, si le processus n’a pas encore été poursuivi après avoir obtenu le rappel d’exception non gérée ou en cas d’attachement JIT natif. En outre, il est possible (quoique improbable) d’avoir plusieurs threads avec une exception non gérée au moment où l’attachement JIT natif est déclenché. Dans ce cas, il n’existe aucun moyen de déterminer l’exception qui a déclenché l’attachement JIT.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugThread4, interface](icordebugthread4-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)

---
title: ICorDebugThread4, interface
ms.date: 03/30/2017
api_name:
- ICorDebugThread4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4
helpviewer_keywords:
- ICorDebugThread4 interface [.NET Framework debugging]
ms.assetid: a8c7719a-322b-4133-8566-4c27218dc104
topic_type:
- apiref
ms.openlocfilehash: 5c108420772be9e6d0932f3759f18da9446f99d6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727937"
---
# <a name="icordebugthread4-interface"></a>ICorDebugThread4, interface

Fournit des informations sur le blocage des threads.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetBlockingObjects, méthode](icordebugthread4-getblockingobjects-method.md)|Fournit une énumération ordonnée des structures [CorDebugBlockingObject](cordebugblockingobject-structure.md) qui fournissent des informations sur le blocage des threads.|  
|[HadUnhandledException, méthode](icordebugthread4-hadunhandledexception-method.md)|Indique si le thread a déjà eu une exception non gérée.|  
|[GetCurrentCustomDebuggerNotification, méthode](icordebugthread4-getcurrentcustomdebuggernotification-method.md)|Obtient l’objet [ICorDebugManagedCallback3 :: CustomNotification,](icordebugmanagedcallback3-customnotification-method.md) actuel sur le thread actuel.|  
  
## <a name="remarks"></a>Remarques  

 Cette interface est une extension logique des interfaces ICorDebugThread, ICorDebugThread2 et [ICorDebugThread3](icordebugthread3-interface.md) .  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)

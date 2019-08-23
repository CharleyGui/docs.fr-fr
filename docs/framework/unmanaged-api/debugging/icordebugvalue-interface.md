---
title: ICorDebugValue, interface
ms.date: 03/30/2017
api_name:
- ICorDebugValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue
helpviewer_keywords:
- ICorDebugValue interface [.NET Framework debugging]
ms.assetid: b2f7007f-c446-4b18-aed1-a25cff8aee31
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3bb2f6333f306c8a19c8b2f67986b23819b74ee0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966865"
---
# <a name="icordebugvalue-interface"></a>ICorDebugValue, interface
Représente une valeur dans le processus en cours de débogage. La valeur peut être une valeur de lecture ou d’écriture.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CreateBreakpoint, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|Cette méthode n’est pas implémentée actuellement.|  
|[GetAddress, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|Obtient l’adresse de cet `ICorDebugValue` objet, qui est en cours de débogage.|  
|[GetSize, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|Obtient la taille, en octets, de cet `ICorDebugValue` objet.|  
|[GetType, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|Obtient le type primitif de cet `ICorDebugValue` objet.|  
  
## <a name="remarks"></a>Notes  
 En général, la propriété d’un objet de valeur est passée lorsqu’elle est retournée. Le destinataire est responsable de la suppression d’une référence de l’objet lorsqu’il est terminé avec l’objet.  
  
 Selon l’emplacement à partir duquel la valeur a été récupérée, la valeur peut ne pas rester valide après la reprise du processus. Ainsi, en général, la valeur ne doit pas être maintenue à travers un appel de la méthode [ICorDebugController:: continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) .  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug. idl, CorDebug. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugValue3, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

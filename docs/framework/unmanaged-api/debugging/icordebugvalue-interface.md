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
ms.openlocfilehash: e1044386bd6251132703c4e98a0cf2ed267d34e0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791136"
---
# <a name="icordebugvalue-interface"></a>ICorDebugValue, interface
Représente une valeur dans le processus en cours de débogage. La valeur peut être une valeur de lecture ou d’écriture.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CreateBreakpoint, méthode](icordebugvalue-createbreakpoint-method.md)|Cette méthode n'est pas implémentée à l'heure actuelle.|  
|[GetAddress, méthode](icordebugvalue-getaddress-method.md)|Obtient l’adresse de cet objet `ICorDebugValue`, qui est en cours de débogage.|  
|[GetSize, méthode](icordebugvalue-getsize-method.md)|Obtient la taille, en octets, de cet objet `ICorDebugValue`.|  
|[GetType, méthode](icordebugvalue-gettype-method.md)|Obtient le type primitif de cet objet `ICorDebugValue`.|  
  
## <a name="remarks"></a>Notes  
 En général, la propriété d’un objet de valeur est passée lorsqu’elle est retournée. Le destinataire est responsable de la suppression d’une référence de l’objet lorsqu’il est terminé avec l’objet.  
  
 Selon l’emplacement à partir duquel la valeur a été récupérée, la valeur peut ne pas rester valide après la reprise du processus. Ainsi, en général, la valeur ne doit pas être maintenue à travers un appel de la méthode [ICorDebugController :: continue](icordebugcontroller-continue-method.md) .  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugValue3, interface](icordebugvalue3-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)

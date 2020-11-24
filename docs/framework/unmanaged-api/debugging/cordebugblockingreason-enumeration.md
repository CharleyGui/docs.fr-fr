---
title: CorDebugBlockingReason, énumération
ms.date: 03/30/2017
api_name:
- CorDebugBlockingReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingReason
helpviewer_keywords:
- CorDebugBlockingReason enumeration [.NET Framework debugging]
ms.assetid: a6ac2531-ddfe-46fd-88fe-8b1eabe0b255
topic_type:
- apiref
ms.openlocfilehash: ddd03d70656ad52fd9d577beedc60b51c7b305d5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672849"
---
# <a name="cordebugblockingreason-enumeration"></a>CorDebugBlockingReason, énumération

Spécifie les raisons pour lesquelles un thread peut être bloqué sur un objet donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`BLOCKING_NONE`|À usage interne uniquement|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|Un thread tente d’acquérir la section critique associée au verrou du moniteur sur un objet. En général, cela se produit lorsque vous appelez l’une des <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> méthodes ou.|  
|`BLOCKING_MONITOR_EVENT`|Un thread attend sur l’événement associé à un verrou de moniteur pour un objet. En général, cela se produit lorsque vous appelez l’une des <xref:System.Threading.Monitor?displayProperty=nameWithType> `Wait` méthodes.|  
  
## <a name="remarks"></a>Remarques  

 Quand le `BLOCKING_MONITOR_CRITICAL_SECTION` `BLOCKING_MONITOR_EVENT` membre ou est utilisé dans une structure [CorDebugBlockingObject](cordebugblockingobject-structure.md) , le `pBlockingObject` membre de la structure pointe vers une interface « ICorDebugValue » qui représente l’objet en cours d’entrée. Il est également garanti d’implémenter l’interface [ICorDebugHeapValue3](icordebugheapvalue3-interface.md) .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de débogage](debugging-enumerations.md)
- [Débogage](index.md)

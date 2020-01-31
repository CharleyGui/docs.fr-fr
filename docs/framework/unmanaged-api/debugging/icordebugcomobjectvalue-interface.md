---
title: Interface ICorDebugComObjectValue
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugComObjectValue
helpviewer_keywords:
- ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 505a7f6c-d92b-42b4-b539-433f5102ea9b
topic_type:
- apiref
ms.openlocfilehash: ed5b39ed4b2a14c071bf23fb04efbad6834e8a9d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783971"
---
# <a name="icordebugcomobjectvalue-interface"></a>Interface ICorDebugComObjectValue
Fournit des méthodes pour récupérer des informations associées à un wrapper RCW (Runtime Callable Wrapper).  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetCachedInterfacePointers, méthode](icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|Obtient les pointeurs d’interface bruts mis en cache sur le wrapper RCW actuel.|  
|[GetCachedInterfaceTypes, méthode](icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|Fournit un énumérateur pour les types d’interface dont la casse de l’objet actuel a été ou utilisée.|  
  
## <a name="remarks"></a>Notes  
 Pour vérifier si une instance d’une interface « ICorDebugValue » représente un wrapper RCW, un débogueur appelle `QueryInterface` sur « ICorDebugValue » avec `IID_ICorDebugComObjectValue`.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)

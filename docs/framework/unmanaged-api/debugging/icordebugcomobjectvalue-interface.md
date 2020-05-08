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
ms.openlocfilehash: 528db447df4d71d67441b05ad29e6a900c59afbb
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892821"
---
# <a name="icordebugcomobjectvalue-interface"></a>Interface ICorDebugComObjectValue
Fournit des méthodes pour récupérer des informations associées à un wrapper RCW (Runtime Callable Wrapper).  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetCachedInterfacePointers, méthode](icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|Obtient les pointeurs d’interface bruts mis en cache sur le wrapper RCW actuel.|  
|[GetCachedInterfaceTypes, méthode](icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|Fournit un énumérateur pour les types d’interface dont la casse de l’objet actuel a été ou utilisée.|  
  
## <a name="remarks"></a>Notes   
 Pour vérifier si une instance d’une interface « ICorDebugValue » représente un wrapper RCW, un débogueur `QueryInterface` appelle sur « ICorDebugValue » `IID_ICorDebugComObjectValue`avec.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)

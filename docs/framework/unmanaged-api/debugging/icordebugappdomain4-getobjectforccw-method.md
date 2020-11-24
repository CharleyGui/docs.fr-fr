---
title: ICorDebugAppDomain4::GetObjectForCCW, méthode
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
ms.openlocfilehash: f3e64def16fb2817244ef7669ff4bb7fef0bd07c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684446"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a>ICorDebugAppDomain4::GetObjectForCCW, méthode

Obtient un objet managé à partir d'un pointeur de wrapper CCW (COM Callable Wrapper).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `ccwPointer`  
 [in] Pointeur vers un wrapper CCW (COM Callable Wrapper)  
  
 `ppManagedObject`  
 à Pointeur vers l’adresse d’un objet « ICorDebugValue » qui représente l’objet managé qui correspond au pointeur CCW donné.  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>Spécifications  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugAppDomain4 (interface)](icordebugappdomain4-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)

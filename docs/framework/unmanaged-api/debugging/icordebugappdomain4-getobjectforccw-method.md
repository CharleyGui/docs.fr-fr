---
title: Méthode ICorDebugAppDomain4::GetObjectForCCW
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
ms.openlocfilehash: 50f46394c809321f0bd256e4c8d75b76fc7c2c70
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784861"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a>Méthode ICorDebugAppDomain4::GetObjectForCCW
Obtient un objet managé à partir d'un pointeur de wrapper CCW (COM Callable Wrapper).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,   
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `ccwPointer`  
 [in] Pointeur vers un wrapper CCW (COM Callable Wrapper)  
  
 `ppManagedObject`  
 à Pointeur vers l’adresse d’un objet « ICorDebugValue » qui représente l’objet managé qui correspond au pointeur CCW donné.  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugAppDomain4, interface](icordebugappdomain4-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)

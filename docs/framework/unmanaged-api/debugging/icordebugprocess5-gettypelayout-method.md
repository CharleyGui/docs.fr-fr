---
title: ICorDebugProcess5::GetTypeLayout, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeLayout
helpviewer_keywords:
- ICorDebugProcess5::GetTypeLayout method [.NET Framework debugging]
- GetTypeLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: bd62f5d1-e874-41f1-81e5-a29a7572c15d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee556f559a7dc4c271f110f7bba4c86b675c3511
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736496"
---
# <a name="icordebugprocess5gettypelayout-method"></a>ICorDebugProcess5::GetTypeLayout, méthode
Obtient des informations sur la disposition d’un objet en mémoire en fonction de son identificateur de type.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetTypeLayout(    [in] COR_TYPEID id,     [out] COR_TYPE_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a>Paramètres  
 `id`  
 [in] Un [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) jeton qui spécifie le type dont la disposition est souhaitée.  
  
 `pLayout`  
 [out] Un pointeur vers un [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) structure qui contient des informations sur la disposition de l’objet en mémoire.  
  
## <a name="remarks"></a>Notes  
 Le `ICorDebugProcess5::GetTypeLayout` méthode fournit des informations sur un objet basé sur son [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), qui est retourné par un nombre d’autres [ICorDebugProcess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md) méthodes. Les informations sont fournies par un [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) structure est remplie par la méthode.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [COR_TYPE_LAYOUT, structure](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)
- [ICorDebugProcess5, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

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
ms.openlocfilehash: 861af4ba9c6f4d4bdb16abb9d4e1fd79debac59b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205576"
---
# <a name="icordebugprocess5gettypelayout-method"></a>ICorDebugProcess5::GetTypeLayout, méthode
Obtient des informations sur la disposition d’un objet en mémoire en fonction de son identificateur de type.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetTypeLayout(    [in] COR_TYPEID id,     [out] COR_TYPE_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a>Paramètres  
 `id`  
 dans Jeton [COR_TYPEID](cor-typeid-structure.md) qui spécifie le type dont la disposition est souhaitée.  
  
 `pLayout`  
 à Pointeur vers une structure [COR_TYPE_LAYOUT](cor-type-layout-structure.md) qui contient des informations sur la disposition de l’objet en mémoire.  
  
## <a name="remarks"></a>Remarks  
 La `ICorDebugProcess5::GetTypeLayout` méthode fournit des informations à propos d’un objet en fonction de son [COR_TYPEID](cor-typeid-structure.md), qui est retourné par un certain nombre d’autres méthodes [ICorDebugProcess5](icordebugprocess5-interface.md) . Les informations sont fournies par une structure [COR_TYPE_LAYOUT](cor-type-layout-structure.md) qui est remplie par la méthode.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [COR_TYPE_LAYOUT, structure](cor-type-layout-structure.md)
- [ICorDebugProcess5, interface](icordebugprocess5-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)

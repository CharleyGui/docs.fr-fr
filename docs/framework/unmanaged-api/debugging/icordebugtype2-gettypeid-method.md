---
title: 'Méthode icordebugtype2 :: GetTypeID, méthode'
ms.date: 03/30/2017
api_name:
- ICorDebugType2.GetTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetTypeID
helpviewer_keywords:
- GetTypeID method, ICorDebugType2 interface [.NET Framework debugging]
- ICorDebugType2.GetTypeID method [.NET Framework debugging]
ms.assetid: 0b933686-226e-4373-92b7-fac579ee7b1a
topic_type:
- apiref
ms.openlocfilehash: 1c11946bc5ea69a090091c014aba859935b48b36
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396676"
---
# <a name="icordebugtype2gettypeid-method"></a>Méthode icordebugtype2 :: GetTypeID, méthode
Obtient une [COR_TYPEID](cor-typeid-structure.md) pour ce type.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `id`  
 à Pointeur vers le [COR_TYPEID](cor-typeid-structure.md) pour ce ICorDebugType.  
  
## <a name="return-value"></a>Valeur de retour  
 La valeur de retour est `S_OK` en cas de réussite ou un code d'échec `HRESULT` en cas d'échec. Les `HRESULT` codes sont les suivants :  
  
|Code de retour|Description|  
|-----------------|-----------------|  
|`S_OK`|La méthode a réussi. La méthode a récupéré une [COR_TYPEID](cor-typeid-structure.md)valide.|  
|`CORDBG_E_CLASS_NOT_LOADED`|Le type n’a pas été chargé.|  
|`CORDBG_E_UNSUPPORTED`|Le type n'est pas pris en charge.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode fournit un mappage à partir de ICorDebugType, qui représente un type qui peut ou non avoir été chargé dans le runtime, à un [COR_TYPEID](cor-typeid-structure.md), qui sert de handle opaque qui identifie un type chargé dans le Runtime.  
  
 Lorsque le type représenté par l’ICorDebugType n’a pas encore été chargé, cette méthode retourne `CORDBG_E_CLASS_NOT_LOADED` .  Si le type n’est pas pris en charge, il retourne `CORDBG_E_UNSUPPORTED` .  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugType2, interface](icordebugtype2-interface.md)

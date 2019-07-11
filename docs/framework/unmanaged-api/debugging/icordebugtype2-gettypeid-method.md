---
title: ICorDebugType2::GetTypeID (méthode)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3098911bab2878876b93ee1ce23d9794d7e6cdbd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772472"
---
# <a name="icordebugtype2gettypeid-method"></a>ICorDebugType2::GetTypeID (méthode)
Obtient un [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) pour ce type.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `id`  
 [out] Un pointeur vers le [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) pour ICorDebugType.  
  
## <a name="return-value"></a>Valeur de retour  
 La valeur de retour est `S_OK` en cas de réussite ou un code d'échec `HRESULT` en cas d'échec. Le `HRESULT` codes incluent les éléments suivants :  
  
|Code de retour|Description|  
|-----------------|-----------------|  
|`S_OK`|La méthode a réussi. La méthode a récupéré valide [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md).|  
|`CORDBG_E_CLASS_NOT_LOADED`|Le type n’a pas été chargé.|  
|`CORDBG_E_UNSUPPORTED`|Le type n’est pas pris en charge.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode fournit un mappage de ICorDebugType, qui représente un type qui peut ou ont ne peut-être pas été chargé dans l’exécution, à un [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), qui sert un opaque gérer qui identifie un type chargé dans le runtime.  
  
 Lorsque le type qui représente le ICorDebugType n’a pas encore été chargé, cette méthode retourne `CORDBG_E_CLASS_NOT_LOADED`.  Si le type n’est pas pris en charge, elle retourne `CORDBG_E_UNSUPPORTED`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugType2, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)

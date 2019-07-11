---
title: ICorDebugProcess5::GetTypeFields, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeFields
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeFields
helpviewer_keywords:
- GetTypeFields method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeFields method [.NET Framework debugging]
ms.assetid: 6a0ad3ee-dacb-47e9-abae-4536bcc4804b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d413b17da0b6f241f9078bfeb3bd035d4d07a81
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767630"
---
# <a name="icordebugprocess5gettypefields-method"></a>ICorDebugProcess5::GetTypeFields, méthode
Fournit des informations sur les champs qui appartiennent à un type.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],   
    [out] ULONG32 *pceltNeeded  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `id`  
 [in] L’identificateur du type dont les informations de champ sont récupérées.  
  
 `celt`  
 [in] Le nombre de [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objets dont les informations de champ doit être récupéré.  
  
 `fields`  
 [out] Un tableau de [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objets qui fournissent des informations sur les champs qui appartiennent au type.  
  
 `pceltNeeded`  
 [out] Un pointeur vers le nombre de [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objets inclus dans `fields`.  
  
## <a name="remarks"></a>Notes  
 Le `celt` paramètre qui spécifie le nombre de champs dont la méthode utilise pour remplir les informations de champ `fields`, doit correspondre à la valeur de la `COR_TYPE_LAYOUT::numFields` champ.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugProcess5, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

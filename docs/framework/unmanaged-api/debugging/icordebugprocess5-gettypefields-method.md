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
ms.openlocfilehash: 29006eba3d3a523fd24a461207ab12222a639782
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178587"
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
 [dans] L’identifiant du type dont les informations sur le terrain sont récupérées.  
  
 `celt`  
 [dans] Nombre d’objets [COR_FIELD](cor-field-structure.md) dont les informations sur le terrain doivent être récupérées.  
  
 `fields`  
 [out] Un éventail d’objets [COR_FIELD](cor-field-structure.md) qui fournissent des informations sur les champs qui appartiennent au type.  
  
 `pceltNeeded`  
 [out] Un pointeur sur le nombre d’objets [COR_FIELD](cor-field-structure.md) inclus dans `fields`.  
  
## <a name="remarks"></a>Notes   
 Le `celt` paramètre, qui précise le nombre de champs dont `fields`l’information sur le `COR_TYPE_LAYOUT::numFields` terrain utilisée par la méthode pour peupler, doit correspondre à la valeur du champ.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugProcess5, interface](icordebugprocess5-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)

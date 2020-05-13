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
ms.openlocfilehash: a2c7f7b722abac6acf71d3b64276862441695a5f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212787"
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
 dans Identificateur du type dont les informations de champ sont récupérées.  
  
 `celt`  
 dans Nombre d’objets [COR_FIELD](cor-field-structure.md) dont les informations de champ doivent être récupérées.  
  
 `fields`  
 à Tableau d’objets [COR_FIELD](cor-field-structure.md) qui fournissent des informations sur les champs qui appartiennent au type.  
  
 `pceltNeeded`  
 à Pointeur vers le nombre d’objets [COR_FIELD](cor-field-structure.md) inclus dans `fields` .  
  
## <a name="remarks"></a>Remarks  
 Le `celt` paramètre, qui spécifie le nombre de champs dont la méthode utilise les informations de champ pour remplir `fields` , doit correspondre à la valeur du `COR_TYPE_LAYOUT::numFields` champ.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugProcess5, interface](icordebugprocess5-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)

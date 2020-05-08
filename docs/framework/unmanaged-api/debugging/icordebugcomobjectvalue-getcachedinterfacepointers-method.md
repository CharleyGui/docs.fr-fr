---
title: ICorDebugComObjectValue::GetCachedInterfacePointers, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue::GetCachedInterfacePointers
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers
helpviewer_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers method [.NET Framework debugging]
- GetCachedInterfacePointers method, ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 08dbd558-bd39-4263-94c2-71e70687aaf0
topic_type:
- apiref
ms.openlocfilehash: fa22c17ed7d5bcd689f21d2d855d9be7a6a8e164
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892806"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a>ICorDebugComObjectValue::GetCachedInterfacePointers, méthode
Obtient les pointeurs d’interface bruts mis en cache sur le wrapper RCW (Runtime Callable Wrapper) actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
## <a name="parameters"></a>Paramètres  
 `bIInspectableOnly`  
 dans Valeur qui indique si la méthode retourne uniquement Windows Runtime interfaces (`IInspectable` interfaces) ou toutes les interfaces com mises en cache par le wrapper RCW (Runtime Callable Wrapper).  
  
 `celt`  
 dans Nombre d’objets dont les adresses doivent être récupérées.  
  
 `pceltFetched`  
 à Pointeur vers le nombre de `CORDB_ADDRESS` valeurs réellement retournées `ptrs`dans.  
  
 `ptrs`  
 Pointeur vers l’adresse de début d’un tableau de `CORDB_ADDRESS` valeurs qui contiennent les adresses des objets d’interface mis en cache.  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interface ICorDebugComObjectValue](icordebugcomobjectvalue-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)

---
title: ICorDebugComObjectValue::GetCachedInterfaceTypes, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue::GetCachedInterfaceTypes
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfaceTypes
helpviewer_keywords:
- GetCachedInterface method, ICorDebugComObjectValue interface [.NET Framework debugging]
- ICorDebugComObjectValue::GetCachedInterface method [.NET Framework debugging]
ms.assetid: d492284f-d3c5-4614-adb8-d718d5042500
topic_type:
- apiref
ms.openlocfilehash: 6b02657012870de4d0f888f6c05b115b25073fa2
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892833"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a>ICorDebugComObjectValue::GetCachedInterfaceTypes, méthode
Fournit un énumérateur pour les types d’interface sur lesquels l’objet actuel a fait l’objet d’un cast ou utilisé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
## <a name="parameters"></a>Paramètres  
 `bIInspectableOnly`  
 dans Valeur qui indique si la méthode retourne uniquement Windows Runtime interfaces (`IInspectable` interfaces) ou toutes les interfaces com mises en cache par le wrapper RCW (Runtime Callable Wrapper).  
  
 `ppInterfacesEnum`  
 à Pointeur vers l’adresse d’un énumérateur ICorDebugTypeEnum qui fournit l’accès aux objets ICorDebugType qui représentent des types d’interfaces mis en cache filtrés en fonction de `bIInspectableOnly`.  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interface ICorDebugComObjectValue](icordebugcomobjectvalue-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)

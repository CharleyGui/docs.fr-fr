---
title: ICorDebugValue::GetType, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetType
helpviewer_keywords:
- ICorDebugValue::GetType method [.NET Framework debugging]
- GetType method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: 41e2d503-e1f1-407b-abe0-6a29adb3e0d1
topic_type:
- apiref
ms.openlocfilehash: 284a74823b01305f8c6e025f70bb9209c8607b7b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137073"
---
# <a name="icordebugvaluegettype-method"></a>ICorDebugValue::GetType, méthode
Obtient le type primitif de cet objet « ICorDebugValue ».  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pType`  
 à Pointeur vers une valeur de l’énumération "CorElementType" qui indique le type de la valeur.  
  
## <a name="remarks"></a>Notes  
 Si l’objet est un type au moment de l’exécution complexe, ce type peut être examiné par le biais des sous-classes appropriées de l’interface `ICorDebugValue`. Par exemple, « ICorDebugObjectValue », qui hérite de `ICorDebugValue`, représente un type complexe.  
  
 Les méthodes `GetType` et [ICorDebugObjectValue :: GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) retournent toutes les informations relatives au type d’une valeur. Elles sont remplacées par la méthode [ICorDebugValue2 :: GetExactType,](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) qui prend en charge les génériques.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

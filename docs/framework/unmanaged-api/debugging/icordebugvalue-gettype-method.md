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
ms.openlocfilehash: 06f403f0b653866428a41240f99833ec1180eb86
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731070"
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
  
## <a name="remarks"></a>Remarques  

 Si l’objet est un type au moment de l’exécution complexe, ce type peut être examiné par le biais des sous-classes appropriées de l' `ICorDebugValue` interface. Par exemple, « ICorDebugObjectValue », qui hérite de `ICorDebugValue` , représente un type complexe.  
  
 Les `GetType` méthodes et [ICorDebugObjectValue :: GetClass](icordebugobjectvalue-getclass-method.md) retournent toutes les informations relatives au type d’une valeur. Elles sont remplacées par la méthode [ICorDebugValue2 :: GetExactType,](icordebugvalue2-getexacttype-method.md) qui prend en charge les génériques.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

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
ms.openlocfilehash: a3cd62384ad87d072cd715d23d0e9ee9dac23270
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396741"
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
 Si l’objet est un type au moment de l’exécution complexe, ce type peut être examiné par le biais des sous-classes appropriées de l' `ICorDebugValue` interface. Par exemple, « ICorDebugObjectValue », qui hérite de `ICorDebugValue` , représente un type complexe.  
  
 Les `GetType` méthodes et [ICorDebugObjectValue :: GetClass](icordebugobjectvalue-getclass-method.md) retournent toutes les informations relatives au type d’une valeur. Elles sont remplacées par la méthode [ICorDebugValue2 :: GetExactType,](icordebugvalue2-getexacttype-method.md) qui prend en charge les génériques.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

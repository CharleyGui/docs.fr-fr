---
title: ICorDebugType::GetFirstTypeParameter, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetFirstTypeParameter
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetFirstTypeParameter
helpviewer_keywords:
- ICorDebugType::GetFirstTypeParameter method [.NET Framework debugging]
- GetFirstTypeParameter method [.NET Framework debugging]
ms.assetid: 35bb594f-af6a-4349-83fe-e98702674e03
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3031cf2d9509f94b50c386b44e6d9e5d9ee5509c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768228"
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a>ICorDebugType::GetFirstTypeParameter, méthode
Obtient un pointeur d’interface ICorDebugType qui représente le premier <xref:System.Type> paramètre du type représenté par ce `ICorDebugType`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `value`  
 [out] Un pointeur vers l’adresse d’un `ICorDebugType` objet qui représente le premier paramètre.  
  
## <a name="remarks"></a>Notes  
 `GetFirstTypeParameter` peut être appelée dans les cas où les informations supplémentaires sur le type impliquent, au maximum, un paramètre de type. En particulier, il peut être utilisé si le type est un ELEMENT_TYPE_ARRAY ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF ou ELEMENT_TYPE_PTR, comme indiqué par le [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) (méthode).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

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
ms.openlocfilehash: 1a02190b595fb01bdc2df46182bfa64bfe638db4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791286"
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a>ICorDebugType::GetFirstTypeParameter, méthode
Obtient un pointeur d’interface vers un ICorDebugType qui représente le premier paramètre <xref:System.Type> du type représenté par cet `ICorDebugType`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `value`  
 à Pointeur vers l’adresse d’un objet `ICorDebugType` qui représente le premier paramètre.  
  
## <a name="remarks"></a>Notes  
 `GetFirstTypeParameter` peut être appelé dans les cas où les informations supplémentaires sur le type impliquent, au plus, un paramètre de type. En particulier, il peut être utilisé si le type est un ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF ou ELEMENT_TYPE_PTR, comme indiqué par la méthode [ICorDebugType :: GetType](icordebugtype-gettype-method.md) .  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

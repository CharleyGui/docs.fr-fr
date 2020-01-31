---
title: ICorDebugType::GetType, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetType
helpviewer_keywords:
- ICorDebugType::GetType method [.NET Framework debugging]
- GetType method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: d6e64534-4d47-4ad0-a340-7590e07e2b4a
topic_type:
- apiref
ms.openlocfilehash: 25ffbf73fbefbb3c584450283c3080dfc11ee598
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791238"
---
# <a name="icordebugtypegettype-method"></a>ICorDebugType::GetType, méthode
Obtient une valeur CorElementType qui décrit le type natif du <xref:System.Type> common language runtime (CLR) représenté par ce ICorDebugType.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `ty`  
 à Pointeur vers une valeur de l’énumération `CorElementType` qui indique la <xref:System.Type> CLR que cette `ICorDebugType` représente.  
  
## <a name="remarks"></a>Notes  
 Si la valeur de `ty` est ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE, la méthode [ICorDebugType :: GetClass](icordebugtype-getclass-method.md) peut être appelée pour obtenir le type non instancié d’un type générique ; Sinon, n’appelez pas `ICorDebugType::GetClass`.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

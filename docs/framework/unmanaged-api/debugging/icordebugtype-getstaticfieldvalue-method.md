---
title: ICorDebugType::GetStaticFieldValue, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 62eb5d55-53ee-4fb3-8d47-7b6c96808f9e
topic_type:
- apiref
ms.openlocfilehash: 37bf5abf66b613d8432af84c7d73aff60e9127cb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791275"
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a>ICorDebugType::GetStaticFieldValue, méthode
Obtient un pointeur d’interface vers un objet ICorDebugValue qui contient la valeur du champ statique référencé par le jeton de champ spécifié dans le frame de pile spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `fieldDef`  
 dans Jeton `mdFieldDef` qui spécifie le champ statique.  
  
 `pFrame`  
 dans Pointeur vers un ICorDebugFrame qui représente le frame de pile.  
  
 `ppValue`  
 à Pointeur vers l’adresse d’un `ICorDebugValue` qui contient la valeur du champ statique.  
  
## <a name="remarks"></a>Notes  
 La méthode `GetStaticFieldValue` peut être utilisée uniquement si le type est ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE, comme indiqué par la méthode [ICorDebugType :: GetType](icordebugtype-gettype-method.md) .  
  
 Pour les types non génériques, l’opération effectuée par `GetStaticFieldValue` est identique à l’appel de [ICorDebugClass :: GetStaticFieldValue](icordebugclass-getstaticfieldvalue-method.md) sur l’objet ICorDebugClass retourné par [ICorDebugType :: GetClass](icordebugtype-getclass-method.md).  
  
 Pour les types génériques, une valeur de champ statique sera relative à une instanciation particulière. En outre, si le champ statique peut être relatif à un thread, à un contexte ou à un domaine d’application, le frame de pile aide le débogueur à déterminer la valeur appropriée.  
  
## <a name="remarks"></a>Notes  
 `GetStaticFieldValue` peut être utilisé uniquement quand un appel à `ICorDebugType::GetType` retourne la valeur ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1054c7c977a487bb5a4bbf464322a65bcc039608
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755737"
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a>ICorDebugType::GetStaticFieldValue, méthode
Obtient un pointeur d’interface vers un objet ICorDebugValue qui contient la valeur du champ statique référencé par le champ spécifié de jetons dans le frame de pile spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `fieldDef`  
 [in] Un `mdFieldDef` jeton qui spécifie le champ statique.  
  
 `pFrame`  
 [in] Pointeur vers un ICorDebugFrame qui représente le frame de pile.  
  
 `ppValue`  
 [out] Un pointeur vers l’adresse d’un `ICorDebugValue` qui contient la valeur du champ statique.  
  
## <a name="remarks"></a>Notes  
 Le `GetStaticFieldValue` méthode peut être utilisée uniquement si le type est ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE, comme indiqué par le [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) (méthode).  
  
 Pour les types non génériques, l’opération effectuée par `GetStaticFieldValue` est identique à l’appel [ICorDebugClass::GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) sur l’objet ICorDebugClass qui est retourné par [ICorDebugType::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md).  
  
 Pour les types génériques, une valeur de champ statique sera par rapport à une instanciation particulière. En outre, si le champ statique ne peut être relatif à un thread, un contexte ou un domaine d’application, puis le frame de pile aidera le débogueur déterminer la valeur appropriée.  
  
## <a name="remarks"></a>Notes  
 `GetStaticFieldValue` peut être utilisé uniquement lorsqu’un appel à `ICorDebugType::GetType` retourne la valeur ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

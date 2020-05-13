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
ms.openlocfilehash: 83ac91133b226e2ac263356941c3fc3288355e7e
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379937"
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
  
## <a name="parameters"></a>Paramètres  
 `fieldDef`  
 dans `mdFieldDef`Jeton qui spécifie le champ statique.  
  
 `pFrame`  
 dans Pointeur vers un ICorDebugFrame qui représente le frame de pile.  
  
 `ppValue`  
 à Pointeur vers l’adresse d’un `ICorDebugValue` qui contient la valeur du champ statique.  
  
## <a name="remarks"></a>Remarks  
 La `GetStaticFieldValue` méthode peut être utilisée uniquement si le type est ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE, comme indiqué par la méthode [ICorDebugType :: GetType](icordebugtype-gettype-method.md) .  
  
 Pour les types non génériques, l’opération effectuée par `GetStaticFieldValue` est identique à l’appel de [ICorDebugClass :: GetStaticFieldValue](icordebugclass-getstaticfieldvalue-method.md) sur l’objet ICorDebugClass retourné par [ICorDebugType :: GetClass](icordebugtype-getclass-method.md).  
  
 Pour les types génériques, une valeur de champ statique sera relative à une instanciation particulière. En outre, si le champ statique peut être relatif à un thread, à un contexte ou à un domaine d’application, le frame de pile aide le débogueur à déterminer la valeur appropriée.  
  
## <a name="remarks"></a>Remarks  
 `GetStaticFieldValue`peut être utilisé uniquement quand un appel à `ICorDebugType::GetType` retourne une valeur de ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

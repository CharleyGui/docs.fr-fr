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
ms.openlocfilehash: ac42c6254182ea775377a448a54d527b234c97dc
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379926"
---
# <a name="icordebugtypegettype-method"></a>ICorDebugType::GetType, méthode
Obtient une valeur CorElementType qui décrit le type natif du common language runtime (CLR) <xref:System.Type> représenté par ce ICorDebugType.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ty`  
 à Pointeur vers une valeur de l' `CorElementType` énumération qui indique le CLR <xref:System.Type> que ce `ICorDebugType` représente.  
  
## <a name="remarks"></a>Remarks  
 Si la valeur de `ty` est ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE, la méthode [ICorDebugType :: GetClass](icordebugtype-getclass-method.md) peut être appelée pour obtenir le type non instancié pour un type générique ; sinon, n’appelez pas `ICorDebugType::GetClass` .  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

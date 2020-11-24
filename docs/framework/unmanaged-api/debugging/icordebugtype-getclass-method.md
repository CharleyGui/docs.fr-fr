---
title: ICorDebugType::GetClass, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetClass
helpviewer_keywords:
- ICorDebugType::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: 2644f48b-db3c-429f-ae62-76f1c98a1af5
topic_type:
- apiref
ms.openlocfilehash: 1cb9729f175a2e82e88386b0694467c6fe05636a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684458"
---
# <a name="icordebugtypegetclass-method"></a>ICorDebugType::GetClass, méthode

Obtient un pointeur d’interface vers une ICorDebugClass qui représente le type générique non instancié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `ppClass`  
 à Pointeur vers l’adresse d’une `ICorDebugClass` interface qui représente le type générique non instancié.  
  
## <a name="remarks"></a>Remarques  

 `GetClass` peut être appelé uniquement sous certaines conditions. Appelez [ICorDebugType :: GetType](icordebugtype-gettype-method.md) avant d’appeler `GetClass` . Si `ICorDebugType::GetType` retourne une valeur CorElementType qui est ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE, `GetClass` peut être appelé pour obtenir le type non instancié d’un type générique.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

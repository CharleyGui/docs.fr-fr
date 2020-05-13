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
ms.openlocfilehash: 878a57514af34730049864f17f4853c1237904c2
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379956"
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
  
## <a name="remarks"></a>Remarks  
 `GetClass`peut être appelé uniquement sous certaines conditions. Appelez [ICorDebugType :: GetType](icordebugtype-gettype-method.md) avant d’appeler `GetClass` . Si `ICorDebugType::GetType` retourne une valeur CorElementType qui est ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE, `GetClass` peut être appelé pour obtenir le type non instancié d’un type générique.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

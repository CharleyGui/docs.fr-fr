---
title: ICorDebugReferenceValue::IsNull, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.IsNull
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::IsNull
helpviewer_keywords:
- IsNull method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::IsNull method [.NET Framework debugging]
ms.assetid: 99e8c8d7-a1c0-47c8-9dbd-03e0b2bcb4d5
topic_type:
- apiref
ms.openlocfilehash: e8b778c0880040f5ffd639a445fd5663ce493219
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379083"
---
# <a name="icordebugreferencevalueisnull-method"></a>ICorDebugReferenceValue::IsNull, méthode
Obtient une valeur qui indique si ce ICorDebugReferenceValue est une valeur null, auquel cas le `ICorDebugReferenceValue` ne pointe pas vers un objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsNull (  
    [out] BOOL   *pbNull  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pbNull`  
 à Pointeur vers une valeur booléenne qui est `true` si cet `ICorDebugReferenceValue` objet est NULL ; sinon, `pbNull` est `false` .  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

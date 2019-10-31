---
title: ICorDebugHeapValue::IsValid, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue.IsValid
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue::IsValid
helpviewer_keywords:
- IsValid method [.NET Framework debugging]
- ICorDebugHeapValue::IsValid method [.NET Framework debugging]
ms.assetid: 68e20e62-203d-46d8-bb91-8d3c61cfacc3
topic_type:
- apiref
ms.openlocfilehash: 7edf0065fa7eb39dada167a682f2b634a438f1f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138402"
---
# <a name="icordebugheapvalueisvalid-method"></a>ICorDebugHeapValue::IsValid, méthode
Obtient une valeur qui indique si l’objet représenté par cet ICorDebugHeapValue est valide.  
  
 Cette méthode est déconseillée dans la version 2,0 de .NET Framework.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pbValid`  
 à Pointeur vers une valeur booléenne qui indique si cette valeur sur le tas est valide.  
  
## <a name="remarks"></a>Notes  
 La valeur n’est pas valide si elle a été récupérée par le garbage collector.  
  
 Cette méthode est dépréciée. Dans la .NET Framework 2,0, toutes les valeurs sont valides jusqu’à ce que [ICorDebugController :: continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) soit appelé, auquel les valeurs sont invalidées.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

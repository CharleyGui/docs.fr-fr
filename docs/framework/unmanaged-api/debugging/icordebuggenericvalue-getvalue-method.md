---
title: ICorDebugGenericValue::GetValue, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue.GetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue::GetValue
helpviewer_keywords:
- ICorDebugGenericValue::GetValue method [.NET Framework debugging]
- GetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: 4e95d7cb-144d-4ccf-8a69-d605f4744be2
topic_type:
- apiref
ms.openlocfilehash: 646b2661148e38f3c918fc18fce5c9cd0b1134a1
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213021"
---
# <a name="icordebuggenericvaluegetvalue-method"></a>ICorDebugGenericValue::GetValue, méthode
Copie la valeur de ce générique dans la mémoire tampon spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetValue (  
    [out] void     *pTo  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pTo`  
 à Pointeur vers la valeur représentée par cet objet ICorDebugGenericValue. La valeur peut être un type simple ou un type référence (autrement dit, un pointeur).  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

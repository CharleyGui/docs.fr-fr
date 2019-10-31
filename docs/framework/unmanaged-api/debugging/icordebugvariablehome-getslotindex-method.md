---
title: 'ICorDebugVariableHome :: GetSlotIndex, méthode'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetSlotIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetSlotIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetSlotIndex method [.NET Framework debugging]
- GetSlotIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 966da50d-5665-4fff-bf7b-1c72bbadd9a4
topic_type:
- apiref
ms.openlocfilehash: dfc2e91599e7f05d90d56af07b71313e9eecaa51
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121053"
---
# <a name="icordebugvariablehomegetslotindex-method"></a>ICorDebugVariableHome :: GetSlotIndex, méthode
Obtient l’index d’emplacement managé d’une variable locale.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pSlotIndex`  
 à Pointeur vers l’index d’emplacement d’une variable locale.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne les valeurs suivantes.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|L’appel de méthode a retourné une valeur d’index d’emplacement dans `pSlotIndex`.|  
|`E_FAIL`|L’instance [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) actuelle représente un argument de fonction.|  
  
## <a name="remarks"></a>Notes  
 L’index d’emplacement peut être utilisé pour récupérer les métadonnées de cette variable locale.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugVariableHome, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)

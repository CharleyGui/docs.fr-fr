---
title: ICorDebugValue3::GetSize64, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugValue3::GetSize64
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3::GetSize64
helpviewer_keywords:
- GetSize64 method, ICorDebugValue3 interface [.NET Framework debugging]
- ICorDebugValue3::GetSize64 method [.NET Framework debugging]
ms.assetid: fee56a29-3154-4192-958d-71da2ced3740
topic_type:
- apiref
ms.openlocfilehash: d1d057d38e16503175138c6ec978eb6c1f12bc6d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722334"
---
# <a name="icordebugvalue3getsize64-method"></a>ICorDebugValue3::GetSize64, méthode

Obtient la taille, en octets, de cet objet [icordebugvalue3,](icordebugvalue3-interface.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 pSize  
 à Pointeur vers la taille, en octets, de cet objet.  
  
## <a name="remarks"></a>Remarques  

 Si le type de cette valeur est un type référence, cette méthode retourne la taille du pointeur plutôt que la taille de l’objet.  
  
 La `ICorDebugValue3::GetSize` méthode diffère de la méthode [ICorDebugValue ::](icordebugvalue-getsize-method.md) Quantity dans le type de son paramètre de sortie. Dans [ICorDebugValue ::](icordebugvalue-getsize-method.md)dela, le paramètre de sortie est un `ULONG32` ; dans `ICorDebugValue3::GetSize` , il s’agit d’un `ULONG64` . Cela permet à l’interface [icordebugvalue3,](icordebugvalue3-interface.md) de signaler la taille des tableaux qui dépassent 2 Go.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugValue3, interface](icordebugvalue3-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)

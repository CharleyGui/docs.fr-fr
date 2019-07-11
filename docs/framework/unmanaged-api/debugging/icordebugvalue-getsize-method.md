---
title: ICorDebugValue::GetSize, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugValue interface [.NET Framework debugging]
- ICorDebugValue::GetSize method [.NET Framework debugging]
ms.assetid: 445a9ee3-e050-4f3a-931a-96b0efb00110
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 94d8fbf4d93bbfbaaeb7c1268004aada22b9b7df
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768914"
---
# <a name="icordebugvaluegetsize-method"></a>ICorDebugValue::GetSize, méthode
Obtient la taille, en octets, de cet objet « ICorDebugValue ».  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pSize`  
 [out] La taille, en octets, de cet objet de valeur.  
  
## <a name="remarks"></a>Notes  
 Si le type de valeur est un type référence, cette méthode retourne la taille du pointeur plutôt que la taille de l’objet.  
  
 Le `ICorDebugValue::GetSize` retourne de la méthode `COR_E_OVERFLOW` pour les objets qui sont supérieurs à 4 Go sur les plateformes 64 bits. Utilisez le [ICorDebugValue3::GetSize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) méthode à la place pour les objets qui sont supérieurs à 4 Go.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetSize64, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)

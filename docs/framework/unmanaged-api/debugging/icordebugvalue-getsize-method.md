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
ms.openlocfilehash: 9f5688ae4f76f9ddfde231aa6252d666c9152eec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731077"
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
 à Taille, en octets, de cet objet de valeur.  
  
## <a name="remarks"></a>Remarques  

 Si le type de la valeur est un type référence, cette méthode retourne la taille du pointeur plutôt que la taille de l’objet.  
  
 La `ICorDebugValue::GetSize` méthode retourne `COR_E_OVERFLOW` pour les objets dont la taille est supérieure à 4 Go sur les plateformes 64 bits. Utilisez plutôt la méthode [icordebugvalue3, :: getsize64,](icordebugvalue3-getsize64-method.md) pour les objets dont la taille est supérieure à 4 Go.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetSize64, méthode](icordebugvalue3-getsize64-method.md)

---
title: ICorDebugNativeFrame2::IsMatchingParentFrame, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.IsMatchingParentFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::IsMatchingParentFrame
helpviewer_keywords:
- IsMatchingParentFrame method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsMatchingParentFrame method [.NET Framework debugging]
ms.assetid: d2ca20db-df22-4528-a0dd-a09ea62c8998
topic_type:
- apiref
ms.openlocfilehash: 213bee96531fa0bbc9bf0ae76b2505019833abfc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724700"
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a>ICorDebugNativeFrame2::IsMatchingParentFrame, méthode

Détermine si le frame spécifié est le parent du frame actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pPotentialParentFrame`  
 dans Pointeur vers l’objet Frame que vous souhaitez évaluer pour l’état parent.  
  
 `pIsParent`  
 [out] `true` Si `pPotentialParentFrame` est le parent du frame actuel ; sinon, `false` .  
  
## <a name="return-value"></a>Valeur renvoyée  

 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|L’état parent a été retourné avec succès.|  
|E_FAIL|L’état parent n’a pas pu être retourné.|  
|E_INVALIDARG|`pPotentialParentFrame` ou `pIsParent` est null.|  
  
## <a name="exceptions"></a>Exceptions  
  
## <a name="remarks"></a>Remarques  

 `IsMatchingParentFrame` retourne `true` si l’objet Frame que vous transmettez à la méthode est le parent de l’objet Frame sur lequel la méthode a été appelée. Si vous appelez la méthode sur un frame qui n’est pas un enfant du frame spécifié, elle retourne une erreur.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugNativeFrame2, interface](icordebugnativeframe2-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)

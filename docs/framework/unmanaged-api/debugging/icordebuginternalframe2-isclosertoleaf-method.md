---
title: ICorDebugInternalFrame2::IsCloserToLeaf, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2.IsCloserToLeaf Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf
helpviewer_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf method [.NET Framework debugging]
- IsCloserToLeaf method [.NET Framework debugging]
ms.assetid: c1d3d1eb-8370-4f25-8297-3bd262b4740a
topic_type:
- apiref
ms.openlocfilehash: 8b9ec94184945c19b77247175e51bd5e8dc1ceee
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122668"
---
# <a name="icordebuginternalframe2isclosertoleaf-method"></a>ICorDebugInternalFrame2::IsCloserToLeaf, méthode
Vérifie si le `this` Frame interne est plus proche de la feuille que l’objet ICorDebugFrame spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsCloserToLeaf([in] ICorDebugFrame * pFrameToCompare,  
                       [out] BOOL * pIsCloser);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pFrameToCompare`  
 dans Pointeur vers l’objet de comparaison `ICorDebugFrame`.  
  
 `pIsCloser`  
 [out] `true` si le `this` Frame interne est plus proche de la feuille que le frame spécifié par `pFrameToCompare`; Sinon, `false`.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La comparaison a été effectuée avec succès.|  
|E_FAIL|La comparaison n’a pas pu être effectuée.|  
|E_INVALIDARG|`pFrameToCompare` ou `pIsCloser` est null.|  
  
## <a name="remarks"></a>Notes  
 `IsCloserToLeaf` peut être utilisé pour implémenter une stratégie pour entrelacer des frames internes avec d’autres frames sur la pile.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugInternalFrame2, interface](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)
- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)

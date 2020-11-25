---
title: ICorDebugInternalFrame2::GetFrameAddress, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2.GetFrameAddress Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2::GetFrameAddress
helpviewer_keywords:
- GetFrameAddress method [.NET Framework debugging]
- ICorDebugInternalFrame2::GetFrameAddress method [.NET Framework debugging]
ms.assetid: 4ee8d058-ffc8-4967-9133-a5adfef4e518
topic_type:
- apiref
ms.openlocfilehash: 05a9ab58acb3bf5829fd231ae6d8bcc96ae06da6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724869"
---
# <a name="icordebuginternalframe2getframeaddress-method"></a>ICorDebugInternalFrame2::GetFrameAddress, méthode

Retourne l’adresse de la pile du frame interne.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pAddress`  
 à Pointeur vers le `CORDB_ADDRESS` pour le frame interne.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|L’adresse du frame interne a été correctement retournée.|  
|E_FAIL|L’adresse du frame interne n’a pas pu être retournée.|  
|E_INVALIDARG|`pAddress` a la valeur `null`.|  
  
## <a name="remarks"></a>Remarques  

 La valeur retournée dans `pAddress` peut être utilisée pour déterminer l’emplacement du frame interne par rapport à d’autres frames sur la pile. Même sur les ordinateurs IA-64, le frame interne se trouve sur la pile uniquement et il n’y a aucun pointeur correspondant vers un magasin de stockage.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugInternalFrame2, interface](icordebuginternalframe2-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)

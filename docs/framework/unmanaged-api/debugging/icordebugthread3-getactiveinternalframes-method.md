---
title: ICorDebugThread3::GetActiveInternalFrames, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.GetActiveInternalFrames Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::GetActiveInternalFrames
helpviewer_keywords:
- ICorDebugThread3::GetActiveInternalFrames method [.NET Framework debugging]
- GetActiveInternalFrames method [.NET Framework debugging]
ms.assetid: d69796b4-5b6d-457c-85f6-2cf42e8a8773
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58aaf0445fe42d083c12541056cb362f9a994944
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765213"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a>ICorDebugThread3::GetActiveInternalFrames, méthode
Retourne un tableau de frames internes ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objets) sur la pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp 
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
## <a name="parameters"></a>Paramètres  
 `cInternalFrames`  
 [in] Le nombre de frames internes prévus dans `ppInternalFrames`.  
  
 `pcInternalFrames`  
 [out] Un pointeur vers un `ULONG32` qui contient le nombre de frames internes sur la pile.  
  
 `ppInternalFrames`  
 [in, out] Pointeur vers l’adresse d’un tableau de frames internes sur la pile.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Le [ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objet a été créé avec succès.|  
|E_INVALIDARG|`cInternalFrames` n’est pas égal à zéro et `ppInternalFrames` est `null`, ou `pcInternalFrames` est `null`.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|`ppInternalFrames` est inférieur au nombre de frames internes.|  
  
## <a name="exceptions"></a>Exceptions  
  
## <a name="remarks"></a>Notes  
 Frames internes sont des structures de données envoyées à la pile par le runtime pour stocker des données temporaires.  
  
 Lorsque vous appelez `GetActiveInternalFrames`, vous devez définir le `cInternalFrames` paramètre 0 (zéro) et le `ppInternalFrames` paramètre null. Lorsque `GetActiveInternalFrames` retourne en premier, `pcInternalFrames` contient le nombre de frames internes sur la pile.  
  
 `GetActiveInternalFrames` doit ensuite être appelé une deuxième fois. Vous devez passer le nombre correct (`pcInternalFrames`) dans le `cInternalFrames` paramètre, et spécifiez un pointeur vers un tableau de taille appropriée dans `ppInternalFrames`.  
  
 Utilisez le [ICorDebugStackWalk::GetFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) méthode pour retourner réelle des frames de pile.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)

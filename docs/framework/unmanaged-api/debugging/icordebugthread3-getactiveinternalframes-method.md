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
ms.openlocfilehash: 2ca3bf94298b45e404c930ffe52e101085ee482d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726208"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a>ICorDebugThread3::GetActiveInternalFrames, méthode

Retourne un tableau de frames internes (objets[ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) ) sur la pile.  
  
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
 dans Nombre de frames internes attendus dans `ppInternalFrames` .  
  
 `pcInternalFrames`  
 à Pointeur vers un `ULONG32` qui contient le nombre de frames internes sur la pile.  
  
 `ppInternalFrames`  
 [in, out] Pointeur vers l’adresse d’un tableau de frames internes sur la pile.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|L’objet [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) a été créé avec succès.|  
|E_INVALIDARG|`cInternalFrames` n’est pas égal à zéro et `ppInternalFrames` est `null` , ou a la valeur `pcInternalFrames` `null` .|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|`ppInternalFrames` est plus petit que le nombre de frames internes.|  
  
## <a name="exceptions"></a>Exceptions  
  
## <a name="remarks"></a>Remarques  

 Les frames internes sont des structures de données envoyées dans la pile par le runtime pour stocker des données temporaires.  
  
 Lorsque vous appelez `GetActiveInternalFrames` pour la première fois, vous devez affecter la valeur `cInternalFrames` 0 (zéro) au paramètre et la `ppInternalFrames` valeur null au paramètre. Lors `GetActiveInternalFrames` du premier retour, `pcInternalFrames` contient le nombre de frames internes sur la pile.  
  
 `GetActiveInternalFrames` doit ensuite être appelée une deuxième fois. Vous devez passer le nombre correct ( `pcInternalFrames` ) dans le `cInternalFrames` paramètre et spécifier un pointeur vers un tableau de taille appropriée dans `ppInternalFrames` .  
  
 Utilisez la méthode [ICorDebugStackWalk :: GetFrame](icordebugthread3-getactiveinternalframes-method.md) pour retourner des frames de pile réels.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)

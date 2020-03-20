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
ms.openlocfilehash: 680af5afa3ebef5bcaf9e34580e421dcc8093aaf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178462"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a>ICorDebugThread3::GetActiveInternalFrames, méthode
Retourne une gamme d’images internes (objets[ICorDebugInternalFrame2)](icordebuginternalframe2-interface.md) sur la pile.  
  
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
 [dans] Le nombre de cadres `ppInternalFrames`internes attendus dans .  
  
 `pcInternalFrames`  
 [out] Un pointeur `ULONG32` à un qui contient le nombre de cadres internes sur la pile.  
  
 `ppInternalFrames`  
 [dans, dehors] Un pointeur à l’adresse d’un tableau de cadres internes sur la pile.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|[L’objet ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) a été créé avec succès.|  
|E_INVALIDARG|`cInternalFrames`n’est `ppInternalFrames` pas `null`nul `pcInternalFrames` `null`et est , ou est .|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|`ppInternalFrames`est plus petit que le nombre de cadres internes.|  
  
## <a name="exceptions"></a>Exceptions  
  
## <a name="remarks"></a>Notes   
 Les cadres internes sont des structures de données poussées sur la pile par le temps d’exécution pour stocker des données temporaires.  
  
 Lorsque vous `GetActiveInternalFrames`appelez pour la `cInternalFrames` première fois, vous devez `ppInternalFrames` définir le paramètre à 0 (zéro), et le paramètre à annuler. Lors `GetActiveInternalFrames` de `pcInternalFrames` la première revient, contient le compte des cadres internes sur la pile.  
  
 `GetActiveInternalFrames`devrait alors être appelé une deuxième fois. Vous devez passer le`pcInternalFrames`bon nombre `cInternalFrames` ( ) dans le paramètre, `ppInternalFrames`et spécifier un pointeur à un tableau de taille appropriée dans .  
  
 Utilisez la méthode [ICorDebugStackWalk::GetFrame](icordebugthread3-getactiveinternalframes-method.md) pour retourner les cadres de pile réels.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)

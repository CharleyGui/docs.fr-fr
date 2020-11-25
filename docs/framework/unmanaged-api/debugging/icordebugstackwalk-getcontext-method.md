---
title: ICorDebugStackWalk::GetContext, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetContext
helpviewer_keywords:
- GetContext method, ICorDebugStackWalk interface [.NET Framework debugging]
- ICorDebugStackWalk::GetContext method [.NET Framework debugging]
ms.assetid: 081d1c95-152b-4797-8552-18453eb7b14b
topic_type:
- apiref
ms.openlocfilehash: 927f2077b4bb71177c24816774d06643ebdaa922
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711960"
---
# <a name="icordebugstackwalkgetcontext-method"></a>ICorDebugStackWalk::GetContext, méthode

Retourne le contexte du frame actuel dans l’objet [ICorDebugStackWalk](icordebugstackwalk-interface.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
## <a name="parameters"></a>Paramètres  

 `contextFlags`  
 dans Indicateurs qui indiquent le contenu demandé de la mémoire tampon de contexte (définie dans Winnt. h).  
  
 `contextBufSize`  
 dans Taille allouée de la mémoire tampon de contexte.  
  
 `contextSize`  
 à Taille réelle du contexte. Cette valeur doit être inférieure ou égale à la taille de la mémoire tampon de contexte.  
  
 `contextBuf`  
 à Mémoire tampon de contexte.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Le contexte du frame actuel a été retourné avec succès.|  
|E_FAIL|Le contexte n’a pas pu être retourné.|  
|HRESULT_FROM_WIN32 (MÉMOIRE TAMPON ERROR_INSUFFICIENT)|La mémoire tampon de contexte est trop petite.|  
|CORDBG_E_PAST_END_OF_STACK|Le pointeur de frame est déjà à la fin de la pile ; par conséquent, il n’est pas possible d’accéder à des frames supplémentaires.|  
  
## <a name="exceptions"></a>Exceptions  
  
## <a name="remarks"></a>Remarques  

 Étant donné que le déroulement de la restauration restaure uniquement un sous-ensemble des registres, tels que les registres non volatils, le contexte peut ne pas correspondre exactement à l’état du Registre au moment de l’appel.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)

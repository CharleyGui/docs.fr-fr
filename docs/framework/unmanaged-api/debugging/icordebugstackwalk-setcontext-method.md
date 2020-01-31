---
title: ICorDebugStackWalk::SetContext, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.SetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::SetContext
helpviewer_keywords:
- SetContext method [.NET Framework debugging]
- ICorDebugStackWalk::SetContext method [.NET Framework debugging]
ms.assetid: bac0b156-31a3-4e7f-be4d-ab21789c81f1
topic_type:
- apiref
ms.openlocfilehash: 23ad8882ad97e5ceaeb690dfae08a6be55b85f64
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791858"
---
# <a name="icordebugstackwalksetcontext-method"></a>ICorDebugStackWalk::SetContext, méthode
Affecte au contexte actuel de l’objet [ICorDebugStackWalk](icordebugstackwalk-interface.md) un contexte valide pour le thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
## <a name="parameters"></a>Parameters  
 `flag`  
 dans Indicateur [CorDebugSetContextFlag,](cordebugsetcontextflag-enumeration.md) qui indique si le contexte provient du frame actif sur la pile ou d’un contexte obtenu en déroulant la pile.  
  
 `contextSize`  
 dans Taille allouée de la mémoire tampon de `CONTEXT`.  
  
 `context`  
 dans Mémoire tampon de `CONTEXT`.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Le contexte de l’objet `ICorDebugStackWalk` a été correctement défini.|  
|E_FAIL|Le contexte de l’objet `ICorDebugStackWalk` n’a pas été défini.|  
|E_INVALIDARG|Le contexte a la valeur null.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|La mémoire tampon de contexte est trop petite.|  
  
## <a name="exceptions"></a>Exceptions  
  
## <a name="remarks"></a>Notes  
 Cette méthode ne modifie pas le contexte actuel du thread.  
  
 L’activation d’un contexte non valide dans le contexte actuel peut entraîner des résultats imprévisibles de l’Explorateur de pile.  
  
 Vous pouvez récupérer une copie au niveau du bit exacte de ce contexte en appelant immédiatement la méthode [ICorDebugStackWalk :: GetContext](icordebugstackwalk-getcontext-method.md) .  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)

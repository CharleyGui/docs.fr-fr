---
title: ICorDebugProcess::SetThreadContext, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::SetThreadContext
helpviewer_keywords:
- ICorDebugProcess::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a7b50175-2bf1-40be-8f65-64aec7aa1247
topic_type:
- apiref
ms.openlocfilehash: 3c57021061c1566b369cdd43847e3994cf54e2da
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139676"
---
# <a name="icordebugprocesssetthreadcontext-method"></a>ICorDebugProcess::SetThreadContext, méthode
Définit le contexte du thread donné dans ce processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a>Paramètres  
 `threadID`  
 dans ID du thread pour lequel définir le contexte.  
  
 `contextSize`  
 [in] Taille du tableau `context`.  
  
 `context`  
 dans Tableau d’octets qui décrivent le contexte du thread.  
  
 Le contexte spécifie l’architecture du processeur sur lequel le thread s’exécute.  
  
## <a name="remarks"></a>Notes  
 Le débogueur doit appeler cette méthode plutôt que la fonction `SetThreadContext` Win32, car le thread peut être dans un État « détourné », dans lequel son contexte a été modifié temporairement. Cette méthode doit être utilisée uniquement quand un thread est en code natif. Utilisez [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) pour les threads dans le code managé. Vous ne devez jamais modifier le contexte d’un thread pendant un événement de débogage hors bande (OOB).  
  
 Les données passées doivent être une structure de contexte pour la plateforme actuelle.  
  
 Cette méthode peut endommager le runtime si elle est utilisée de manière incorrecte.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

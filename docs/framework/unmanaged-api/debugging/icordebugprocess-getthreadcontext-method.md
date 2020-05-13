---
title: ICorDebugProcess::GetThreadContext, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetThreadContext
helpviewer_keywords:
- ICorDebugProcess::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: 5b132ef1-8d4b-4525-89b3-54123596c194
topic_type:
- apiref
ms.openlocfilehash: 2bdbf373144e2fb49074cfd035e7b0ffe3c8c291
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212884"
---
# <a name="icordebugprocessgetthreadcontext-method"></a>ICorDebugProcess::GetThreadContext, méthode
Obtient le contexte du thread donné dans ce processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a>Paramètres  
 `threadID`  
 dans ID du thread pour lequel récupérer le contexte.  
  
 `contextSize`  
 [in] Taille du tableau `context`.  
  
 `context`  
 [in, out] Tableau d’octets qui décrivent le contexte du thread.  
  
 Le contexte spécifie l’architecture du processeur sur lequel le thread s’exécute.  
  
## <a name="remarks"></a>Remarks  
 Le débogueur doit appeler cette méthode plutôt que la `GetThreadContext` méthode Win32, car le thread peut être dans un État « détourné », dans lequel son contexte a été modifié temporairement. Cette méthode doit être utilisée uniquement quand un thread est en code natif. Utilisez [ICorDebugRegisterSet](icordebugregisterset-interface.md) pour les threads dans le code managé.  
  
 Les données retournées sont une structure de contexte pour la plateforme actuelle. À l’instar de la `GetThreadContext` méthode Win32, l’appelant doit initialiser le `context` paramètre avant d’appeler cette méthode.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

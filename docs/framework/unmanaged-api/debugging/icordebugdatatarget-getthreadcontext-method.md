---
title: ICorDebugDataTarget::GetThreadContext, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetThreadContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetThreadContext
helpviewer_keywords:
- ICorDebugDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: c8954268-1821-4b23-b665-dbb55f2af31b
topic_type:
- apiref
ms.openlocfilehash: faacea6a2f04ef20025fd33adb4ce76eaf54f32c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679739"
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a>ICorDebugDataTarget::GetThreadContext, méthode

Retourne le contexte de thread actuel pour le thread spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
## <a name="parameters"></a>Paramètres  

 `dwThreadID`  
 dans Identificateur du thread dont le contexte doit être récupéré. L’identificateur est défini par le système d’exploitation.  
  
 `contextFlags`  
 dans Combinaison d’opérations de bits d’indicateurs dépendants de la plateforme qui indiquent les parties du contexte qui doivent être lues.  
  
 `contextSize`  
 [in] Taille de `pContext`.  
  
 `pContext`  
 à Mémoire tampon dans laquelle le contexte de thread sera stocké.  
  
## <a name="remarks"></a>Remarques  

 Sur les plateformes Windows, `pContext` doit être une `CONTEXT` structure (définie dans Winnt. h) qui est appropriée pour le type d’ordinateur spécifié par la méthode [ICorDebugDataTarget :: GetPlatform](icordebugdatatarget-getplatform-method.md) . `contextFlags` doit avoir les mêmes valeurs que le `ContextFlags` champ de la `CONTEXT` structure. La `CONTEXT` structure est spécifique au processeur ; pour plus d’informations, reportez-vous au fichier Winnt. h.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugDataTarget, interface](icordebugdatatarget-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)

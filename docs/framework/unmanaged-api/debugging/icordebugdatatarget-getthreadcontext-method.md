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
ms.openlocfilehash: 3eace2d91b3bb6e637a659b8b49a31450ebc2c42
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783726"
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
  
## <a name="parameters"></a>Parameters  
 `dwThreadID`  
 dans Identificateur du thread dont le contexte doit être récupéré. L’identificateur est défini par le système d’exploitation.  
  
 `contextFlags`  
 dans Combinaison d’opérations de bits d’indicateurs dépendants de la plateforme qui indiquent les parties du contexte qui doivent être lues.  
  
 `contextSize`  
 [in] Taille de `pContext`.  
  
 `pContext`  
 à Mémoire tampon dans laquelle le contexte de thread sera stocké.  
  
## <a name="remarks"></a>Notes  
 Sur les plateformes Windows, `pContext` doit être une structure de `CONTEXT` (définie dans Winnt. h) qui est appropriée pour le type d’ordinateur spécifié par la méthode [ICorDebugDataTarget :: GetPlatform](icordebugdatatarget-getplatform-method.md) . `contextFlags` doit avoir les mêmes valeurs que le champ `ContextFlags` de la structure `CONTEXT`. La structure `CONTEXT` est spécifique au processeur ; Pour plus d’informations, consultez le fichier Winnt. h.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugDataTarget, interface](icordebugdatatarget-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)

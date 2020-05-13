---
title: ICorDebugManagedCallback::EditAndContinueRemap, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EditAndContinueRemap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EditAndContinueRemap
helpviewer_keywords:
- EditAndContinueRemap method [.NET Framework debugging]
- ICorDebugManagedCallback::EditAndContinueRemap method [.NET Framework debugging]
ms.assetid: 24a8fcce-317e-48ff-aefc-d86123ada935
topic_type:
- apiref
ms.openlocfilehash: 78b87b5c566b0d760a205757430123665fb2fcd3
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213710"
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a>ICorDebugManagedCallback::EditAndContinueRemap, méthode
Cette méthode est dépréciée. Il informe le débogueur qu’un événement de remappage a été envoyé à l’environnement de développement intégré (IDE).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a>Notes   
 La `EditAndContinueRemap` méthode est appelée lorsque l’exécution du code dans une ancienne version d’une fonction mise à jour a été tentée. Le common language runtime appelle la `EditAndContinueRemap` méthode pour envoyer un événement de remappage à l’IDE.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugManagedCallback, interface](icordebugmanagedcallback-interface.md)

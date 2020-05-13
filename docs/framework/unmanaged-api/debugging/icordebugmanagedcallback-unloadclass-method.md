---
title: ICorDebugManagedCallback::UnloadClass, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadClass
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadClass method [.NET Framework debugging]
- UnloadClass method [.NET Framework debugging]
ms.assetid: 66a59b18-ce9a-41f4-b23b-4dd6753d6d36
topic_type:
- apiref
ms.openlocfilehash: a7b71170f58ddfe0295da28b8c9fc73286b074e6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212267"
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a>ICorDebugManagedCallback::UnloadClass, méthode
Notifie le débogueur qu’une classe est en cours de déchargement.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pAppDomain`  
 dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application contenant la classe.  
  
 `c`  
 dans Pointeur vers un objet ICorDebugClass qui représente la classe.  
  
## <a name="remarks"></a>Remarks  
 La classe ne doit pas être référencée après cet appel.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [LoadClass, méthode](icordebugmanagedcallback-loadclass-method.md)
- [ICorDebugManagedCallback, interface](icordebugmanagedcallback-interface.md)

---
title: ICorDebugManagedCallback::LoadClass, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadClass
helpviewer_keywords:
- ICorDebugManagedCallback::LoadClass method [.NET Framework debugging]
- LoadClass method [.NET Framework debugging]
ms.assetid: e58dac7b-85c3-41ca-b9aa-3a7fc9ae6680
topic_type:
- apiref
ms.openlocfilehash: 5d35ab4610ffa04d15dd2404fdf8010308bcb42a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212728"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a>ICorDebugManagedCallback::LoadClass, méthode
Notifie le débogueur qu’une classe a été chargée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pAppDomain`  
 dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application dans lequel la classe a été chargée.  
  
 `c`  
 dans Pointeur vers un objet ICorDebugClass qui représente la classe.  
  
## <a name="remarks"></a>Remarks  
 Ce rappel se produit uniquement si le chargement de la classe a été activé pour le module qui contient la classe. Le chargement de classe est toujours activé pour les modules dynamiques.  
  
 Le `LoadClass` rappel fournit un moment approprié pour lier les points d’arrêt aux classes nouvellement générées dans les modules dynamiques.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [UnloadClass, méthode](icordebugmanagedcallback-unloadclass-method.md)
- [ICorDebugManagedCallback, interface](icordebugmanagedcallback-interface.md)

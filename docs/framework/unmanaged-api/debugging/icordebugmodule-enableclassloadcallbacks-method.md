---
title: ICorDebugModule::EnableClassLoadCallbacks, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableClassLoadCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableClassLoadCallbacks
helpviewer_keywords:
- ICorDebugModule::EnableClassLoadCallbacks method [.NET Framework debugging]
- EnableClassLoadCallbacks method [.NET Framework debugging]
ms.assetid: 78dad5e4-8e2e-400f-bec3-92ff0205cd82
topic_type:
- apiref
ms.openlocfilehash: 1ca3adf30ad633fcfb10a4b43a435698d2899597
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213528"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a>ICorDebugModule::EnableClassLoadCallbacks, méthode
Contrôle si les rappels [ICorDebugManagedCallback :: LoadClass](icordebugmanagedcallback-loadclass-method.md) et [ICorDebugManagedCallback :: UnloadClass](icordebugmanagedcallback-unloadclass-method.md) sont appelés pour ce module.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `bClassLoadCallbacks`  
 dans Définissez cette valeur sur `true` pour permettre au Common Language Runtime (CLR) d’appeler les `ICorDebugManagedCallback::LoadClass` `ICorDebugManagedCallback::UnloadClass` méthodes et lorsque leurs événements associés se produisent.  
  
 La valeur par défaut est `false` pour les modules non dynamiques. La valeur est toujours `true` pour les modules dynamiques et ne peut pas être modifiée.  
  
## <a name="remarks"></a>Remarks  
 Les `ICorDebugManagedCallback::LoadClass` `ICorDebugManagedCallback::UnloadClass` rappels et sont toujours activés pour les modules dynamiques et ne peuvent pas être désactivés.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

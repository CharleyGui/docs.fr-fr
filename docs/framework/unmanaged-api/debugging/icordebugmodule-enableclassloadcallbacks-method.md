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
ms.openlocfilehash: d552b694787b5d9f0d5adc399eda6f75df93c385
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793019"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a>ICorDebugModule::EnableClassLoadCallbacks, méthode
Contrôle si les rappels [ICorDebugManagedCallback :: LoadClass](icordebugmanagedcallback-loadclass-method.md) et [ICorDebugManagedCallback :: UnloadClass](icordebugmanagedcallback-unloadclass-method.md) sont appelés pour ce module.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `bClassLoadCallbacks`  
 dans Définissez cette valeur sur `true` pour permettre au common language runtime (CLR) d’appeler les méthodes `ICorDebugManagedCallback::LoadClass` et `ICorDebugManagedCallback::UnloadClass` lorsque leurs événements associés se produisent.  
  
 La valeur par défaut est `false` pour les modules non dynamiques. La valeur est toujours `true` pour les modules dynamiques et ne peut pas être modifiée.  
  
## <a name="remarks"></a>Notes  
 Les rappels d' `ICorDebugManagedCallback::LoadClass` et de `ICorDebugManagedCallback::UnloadClass` sont toujours activés pour les modules dynamiques et ne peuvent pas être désactivés.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

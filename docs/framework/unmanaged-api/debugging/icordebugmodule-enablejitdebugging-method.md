---
title: ICorDebugModule::EnableJITDebugging, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableJITDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableJITDebugging
helpviewer_keywords:
- ICorDebugModule::EnableJITDebugging method [.NET Framework debugging]
- EnableJITDebugging method [.NET Framework debugging]
ms.assetid: 0a65e2a4-5bb6-496c-ae6f-40474426b5a6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8aeb6ed448539db2720fee0d42cfcc344fd3bbf7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762764"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a>ICorDebugModule::EnableJITDebugging, méthode
Contrôle si le compilateur juste-à-temps (JIT) conserve des informations de débogage pour les méthodes de ce module.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `bTrackJITInfo`  
 [in] Définissez cette valeur sur `true` pour permettre au compilateur JIT de conserver les informations de mappage entre la version de Microsoft intermediate language (MSIL) et la version compilé par JIT de chaque méthode dans ce module.  
  
 `bAllowJitOpts`  
 [in] Définissez cette valeur sur `true` pour permettre au compilateur JIT générer du code avec certaines optimisations spécifiques au JIT pour le débogage.  
  
## <a name="remarks"></a>Notes  
 Le débogage JIT est activé par défaut pour tous les modules sont chargés lorsque le débogueur est actif. Par programmation l’activation ou désactivation des paramètres substitue les paramètres globaux.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

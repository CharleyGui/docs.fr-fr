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
ms.openlocfilehash: bdf027f94c8416d052cb807d04be76a39868ccf7
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212930"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a>ICorDebugModule::EnableJITDebugging, méthode
Contrôle si le compilateur juste-à-temps (JIT) préserve les informations de débogage pour les méthodes dans ce module.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `bTrackJITInfo`  
 dans Définissez cette valeur sur `true` pour permettre au compilateur JIT de conserver les informations de mappage entre la version du langage MSIL (Microsoft Intermediate Language) et la version compilée juste-à-temps de chaque méthode de ce module.  
  
 `bAllowJitOpts`  
 dans Définissez cette valeur sur `true` pour permettre au compilateur JIT de générer du code avec certaines optimisations spécifiques au JIT pour le débogage.  
  
## <a name="remarks"></a>Remarks  
 Le débogage juste-à-temps est activé par défaut pour tous les modules qui sont chargés lorsque le débogueur est actif. L’activation ou la désactivation par programmation des paramètres remplace les paramètres globaux.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

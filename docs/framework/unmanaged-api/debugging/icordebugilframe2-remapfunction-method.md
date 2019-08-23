---
title: ICorDebugILFrame2::RemapFunction, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2.RemapFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::RemapFunction
helpviewer_keywords:
- ICorDebugILFrame2::RemapFunction method [.NET Framework debugging]
- RemapFunction method [.NET Framework debugging]
ms.assetid: dd639ba0-f77b-426d-9ff6-f92706840348
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75004f646c01897ef3e3016b073220ad33a0d925
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967576"
---
# <a name="icordebugilframe2remapfunction-method"></a>ICorDebugILFrame2::RemapFunction, méthode
Remappe une fonction modifiée en spécifiant le nouvel offset MSIL (Microsoft Intermediate Language)  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `newILOffset`  
 dans Nouvel offset MSIL du frame de pile auquel le pointeur d’instruction doit être placé. Cette valeur doit être un point de séquence.  
  
 Il incombe à l’appelant de garantir la validité de cette valeur. Par exemple, l’offset MSIL n’est pas valide s’il est en dehors des limites de la fonction.  
  
## <a name="remarks"></a>Notes  
 Quand la fonction d’un frame a été modifiée, le débogueur peut appeler `RemapFunction` la méthode pour échanger la version la plus récente de la fonction du frame afin de pouvoir l’exécuter. L’exécution du code commence à l’offset MSIL donné.  
  
> [!NOTE]
> Appeler `RemapFunction`, comme appeler [ICorDebugILFrame:: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md), invalidera immédiatement toutes les interfaces de débogage liées à la génération d’une trace de la pile pour le thread. Ces interfaces incluent [ICorDebugChain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame et ICorDebugNativeFrame.  
  
 La `RemapFunction` méthode peut être appelée uniquement dans le contexte du frame actuel, et uniquement dans l’un des cas suivants:  
  
- Après réception d’un rappel [ICorDebugManagedCallback2:: FunctionRemapOpportunity,](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md) qui n’a pas encore été poursuivi.  
  
- Pendant l’arrêt de l’exécution du code en raison d’un événement [ICorDebugManagedCallback:: EditAndContinueRemap,](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md) pour ce frame.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug. idl, CorDebug. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

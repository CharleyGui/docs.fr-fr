---
title: ICorDebugStepper::SetInterceptMask, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetInterceptMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetInterceptMask
helpviewer_keywords:
- SetInterceptMask method [.NET Framework debugging]
- ICorDebugStepper::SetInterceptMask method [.NET Framework debugging]
ms.assetid: 6245e2ae-5cc2-43ff-8cc1-71953d12113a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37b644227a6085352bed682f0ddd7c3455b54895
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760702"
---
# <a name="icordebugsteppersetinterceptmask-method"></a>ICorDebugStepper::SetInterceptMask, méthode
Définit une valeur qui spécifie les types de code sont détaillé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `mask`  
 [in] Une combinaison de valeurs de l’énumération CorDebugIntercept qui spécifie les types de code.  
  
## <a name="remarks"></a>Notes  
 Si le bit pour un intercepteur est défini, l’exécution pas à pas se termine lorsque le type donné de code d’interception est rencontré. Si le bit est désactivé, le code d’interception sera ignoré.  
  
 Le `SetInterceptMask` méthode peut avoir des interactions imprévues avec [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (à partir du point de vue utilisateur). Par exemple, si visible uniquement (autrement dit, non interne) partie du code d’initialisation de classe ne possède pas les informations de mappage et que STOP_NO_MAPPING_INFO n’est pas définie (voir la [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (méthode) et le CorDebugUnmappedStop, énumération), l’ignorera l’initialisation de classe. Par défaut, seule la valeur INTERCEPT_NONE de le `CorDebugIntercept` énumération sera utilisée.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

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
ms.openlocfilehash: e88fa543eca39c14962f0dbbe8053829713401c8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137583"
---
# <a name="icordebugsteppersetinterceptmask-method"></a>ICorDebugStepper::SetInterceptMask, méthode
Définit une valeur qui spécifie les types de code qui sont en escalier.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `mask`  
 dans Combinaison de valeurs de l’énumération CorDebugIntercept, qui spécifie les types de code.  
  
## <a name="remarks"></a>Notes  
 Si le bit d’un intercepteur est défini, le pas à pas se termine lorsque le type donné de code d’interception est rencontré. Si le bit est effacé, le code d’interception est ignoré.  
  
 La méthode `SetInterceptMask` peut avoir des interactions imprévues avec [ICorDebugStepper :: SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (du point de vue de l’utilisateur). Par exemple, si la seule partie visible (autrement dit, non interne) du code d’initialisation de classe ne contient pas d’informations de mappage et que STOP_NO_MAPPING_INFO n’est pas défini (consultez la méthode [ICorDebugStepper :: SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) et CorDebugUnmappedStop, l’énumération), l’exécution pas à pas permet de parcourir l’initialisation de la classe. Par défaut, seule la valeur INTERCEPT_NONE de l’énumération `CorDebugIntercept` sera utilisée.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

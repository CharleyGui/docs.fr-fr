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
ms.openlocfilehash: aaba751a58e5b23b98b1d0629ea3cc9e1e7a83a9
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379005"
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
  
## <a name="remarks"></a>Remarks  
 Si le bit d’un intercepteur est défini, le pas à pas se termine lorsque le type donné de code d’interception est rencontré. Si le bit est effacé, le code d’interception est ignoré.  
  
 La `SetInterceptMask` méthode peut avoir des interactions imprévues avec [ICorDebugStepper :: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) (du point de vue de l’utilisateur). Par exemple, si la seule partie visible (autrement dit, non interne) du code d’initialisation de classe n’a pas d’informations de mappage et que STOP_NO_MAPPING_INFO n’est pas défini (consultez la méthode [ICorDebugStepper :: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) et l’énumération CorDebugUnmappedStop,), l’exécution pas à pas de la classe s’effectue pas à pas. Par défaut, seule la valeur INTERCEPT_NONE de l' `CorDebugIntercept` énumération sera utilisée.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

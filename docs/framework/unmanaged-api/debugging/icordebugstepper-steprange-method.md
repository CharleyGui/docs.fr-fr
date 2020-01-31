---
title: ICorDebugStepper::StepRange, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepRange
helpviewer_keywords:
- StepRange method [.NET Framework debugging]
- ICorDebugStepper::StepRange method [.NET Framework debugging]
ms.assetid: b9776112-6e6d-4708-892a-8873db02e16f
topic_type:
- apiref
ms.openlocfilehash: 21b8bf618e197372e301d5f56e7592c20710014d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791707"
---
# <a name="icordebugsteppersteprange-method"></a>ICorDebugStepper::StepRange, méthode
Fait en sorte que ces ICorDebugStepper effectuent un pas à pas détaillé dans son thread conteneur et le retournent lorsqu’il atteint le code au-delà de la dernière des plages spécifiées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `bStepIn`  
 dans Affectez la valeur `true` pour effectuer un pas à pas détaillé dans une fonction appelée dans le thread. Affectez la valeur `false` pour effectuer un pas à pas principal dans la fonction.  
  
 `ranges`  
 dans Tableau de structures COR_DEBUG_STEP_RANGE, chacune spécifiant une plage.  
  
 `cRangeCount`  
 [in] Taille du tableau `ranges`.  
  
## <a name="remarks"></a>Notes  
 La méthode `StepRange` fonctionne comme la méthode [ICorDebugStepper :: Step](icordebugstepper-step-method.md) , sauf qu’elle ne se termine pas tant que le code en dehors de la plage donnée n’est pas atteint.  
  
 Cela peut être plus efficace que l’exécution pas-à-pas d’une instruction à la fois. Les plages sont spécifiées sous la forme d’une liste de paires d’offsets à partir du début de la trame de l’exécution pas à pas.  
  
 Les plages sont relatives au code MSIL (Microsoft Intermediate Language) d’une méthode. Appelez [ICorDebugStepper :: SetRangeIL,](icordebugstepper-setrangeil-method.md) avec `false` pour rendre les plages relatives au code natif d’une méthode.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

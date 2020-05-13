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
ms.openlocfilehash: b040d9454a5a3a0d550bb645953c783357419f73
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379490"
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
  
## <a name="parameters"></a>Paramètres  
 `bStepIn`  
 dans Affectez `true` la valeur pour effectuer un pas à pas détaillé dans une fonction appelée dans le thread. Affectez `false` la valeur à pour effectuer un pas à pas principal dans la fonction.  
  
 `ranges`  
 dans Tableau de structures COR_DEBUG_STEP_RANGE, chacune spécifiant une plage.  
  
 `cRangeCount`  
 [in] Taille du tableau `ranges`.  
  
## <a name="remarks"></a>Remarks  
 La `StepRange` méthode fonctionne comme la méthode [ICorDebugStepper :: Step](icordebugstepper-step-method.md) , sauf qu’elle ne se termine pas tant que le code en dehors de la plage donnée n’est pas atteint.  
  
 Cela peut être plus efficace que l’exécution pas-à-pas d’une instruction à la fois. Les plages sont spécifiées sous la forme d’une liste de paires d’offsets à partir du début de la trame de l’exécution pas à pas.  
  
 Les plages sont relatives au code MSIL (Microsoft Intermediate Language) d’une méthode. Appelez [ICorDebugStepper :: SetRangeIL,](icordebugstepper-setrangeil-method.md) avec `false` pour rendre les plages relatives au code natif d’une méthode.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

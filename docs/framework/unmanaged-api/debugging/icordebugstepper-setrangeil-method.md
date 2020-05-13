---
title: ICorDebugStepper::SetRangeIL, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetRangeIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetRangeIL
helpviewer_keywords:
- SetRangeIL method [.NET Framework debugging]
- ICorDebugStepper::SetRangeIL method [.NET Framework debugging]
ms.assetid: a20c95f0-6da7-4b41-b27f-584211cebb92
topic_type:
- apiref
ms.openlocfilehash: 7fadffaab6eee5beed513f339ea300acef5a1c6b
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379002"
---
# <a name="icordebugsteppersetrangeil-method"></a>ICorDebugStepper::SetRangeIL, méthode
Définit une valeur qui spécifie si les appels à [ICorDebugStepper :: StepRange](icordebugstepper-steprange-method.md) passent des valeurs d’argument qui sont relatives au code natif ou relatives au code MSIL (Microsoft Intermediate Language) de la méthode en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `bIL`  
 dans Affectez `true` la valeur pour spécifier que les plages sont relatives au code MSIL. Affectez `false` la valeur pour spécifier que les plages sont relatives au code natif. La valeur par défaut est `true`.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

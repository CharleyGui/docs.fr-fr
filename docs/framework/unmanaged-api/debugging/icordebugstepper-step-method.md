---
title: ICorDebugStepper::Step, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Step
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Step
helpviewer_keywords:
- Step method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::Step method [.NET Framework debugging]
ms.assetid: 38c1940b-ada1-40ba-8295-4c0833744e1e
topic_type:
- apiref
ms.openlocfilehash: 234705e4495a1a582f3801ad1e645f923cd6f4b2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727690"
---
# <a name="icordebugstepperstep-method"></a>ICorDebugStepper::Step, méthode

Fait en sorte que ces ICorDebugStepper effectuent un pas à pas détaillé dans son thread conteneur et, éventuellement, continue à exécuter des fonctions pas à pas dans les fonctions appelées dans le thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `bStepIn`  
 dans Affectez `true` la valeur pour effectuer un pas à pas détaillé dans une fonction appelée dans le thread. Affectez `false` la valeur à pour effectuer un pas à pas principal dans la fonction.  
  
## <a name="remarks"></a>Remarques  

 L’étape se termine lorsque l’common language runtime exécute l’instruction managée suivante dans le frame de ce pas à pas. Si `Step` est appelé sur une exécution pas à pas, qui n’est pas en code managé, l’étape se termine lorsque l’instruction de code managé suivante est exécutée par le thread.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

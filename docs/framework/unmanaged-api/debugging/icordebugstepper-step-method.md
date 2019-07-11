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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d0f601c4b454b55edc5fa25eb2ee33d491009b9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760566"
---
# <a name="icordebugstepperstep-method"></a>ICorDebugStepper::Step, méthode
Provoque ICorDebugStepper à pas son thread conteneur et éventuellement, continuez le pas à pas via des fonctions appelées dans le thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `bStepIn`  
 [in] La valeur `true` à l’étape dans une fonction qui est appelée dans le thread. La valeur `false` pour ignorer la fonction.  
  
## <a name="remarks"></a>Notes  
 L’étape se termine lorsque le common language runtime exécute l’instruction managée suivante dans le frame de cette exécution pas à pas. Si `Step` est appelée sur une exécution pas à pas, ce qui n’est pas dans le code managé, l’étape se termine lorsque l’instruction de code managé suivante est exécutée par le thread.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

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
ms.openlocfilehash: 43f86e704e4a52a702b8f563e3c613806eb061b5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137532"
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
 dans Affectez la valeur `true` pour effectuer un pas à pas détaillé dans une fonction appelée dans le thread. Affectez la valeur `false` pour effectuer un pas à pas principal dans la fonction.  
  
## <a name="remarks"></a>Notes  
 L’étape se termine lorsque l’common language runtime exécute l’instruction managée suivante dans le frame de ce pas à pas. Si `Step` est appelé sur une exécution pas à pas, qui n’est pas en code managé, l’étape se termine lorsque l’instruction de code managé suivante est exécutée par le thread.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

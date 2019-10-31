---
title: ICorDebugChain::GetCallee, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCallee method
helpviewer_keywords:
- ICorDebugChain::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 19560c79-abdc-4bdf-a5fe-eb362a59edc0
topic_type:
- apiref
ms.openlocfilehash: 5d28af09faae84b0482d438ae33f593f250490c1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73196338"
---
# <a name="icordebugchaingetcallee-method"></a>ICorDebugChain::GetCallee, méthode
Obtient la chaîne qui a été appelée par cette chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ppChain`  
 à Pointeur vers l’adresse d’un objet ICorDebugChain qui représente la chaîne appelée. Si cette chaîne est en cours d’exécution (autrement dit, si cette chaîne n’attend pas le retour d’une chaîne appelée), `ppChain` a la valeur null.  
  
## <a name="remarks"></a>Notes  
 Cette chaîne attend que la chaîne appelée retourne avant de reprendre l’exécution. La chaîne appelée peut se trouver sur un autre thread dans le cas d’appels marshalés inter-threads.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

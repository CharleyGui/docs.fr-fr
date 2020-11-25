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
ms.openlocfilehash: a28da34cd3080826f346b8957aa6ba38258b924f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730121"
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
 à Pointeur vers l’adresse d’un objet ICorDebugChain qui représente la chaîne appelée. Si cette chaîne est en cours d’exécution (autrement dit, si cette chaîne n’attend pas une chaîne appelée à retourner), `ppChain` aura la valeur null.  
  
## <a name="remarks"></a>Remarques  

 Cette chaîne attend que la chaîne appelée retourne avant de reprendre l’exécution. La chaîne appelée peut se trouver sur un autre thread dans le cas d’appels marshalés inter-threads.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

---
title: ICorDebugChain::GetActiveFrame, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetActiveFrame
helpviewer_keywords:
- ICorDebugChain::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 36887017-670b-4f21-b406-8fab956f84a3
topic_type:
- apiref
ms.openlocfilehash: 03cb1556ee971124ed4c591f38d9f892fc7df7b0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192154"
---
# <a name="icordebugchaingetactiveframe-method"></a>ICorDebugChain::GetActiveFrame, méthode
Obtient le frame actif (c’est-à-dire le plus récent) de la chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ppFrame`  
 à Pointeur vers l’adresse d’un objet ICorDebugFrame qui représente le frame actif (autrement dit, le plus récent) de la chaîne.  
  
## <a name="remarks"></a>Notes  
 Si aucun frame de pile managé n’est disponible, `ppFrame` a la valeur null.  
  
 Si le frame actif n’est pas disponible, l’appel s’effectue correctement et `ppFrame` a la valeur null. Les frames actifs ne sont pas disponibles pour les chaînes lancées en raison de CHAIN_ENTER_UNMANAGED, et pour certaines chaînes lancées en raison de CHAIN_CLASS_INIT. Consultez l’énumération CorDebugChainReason,.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

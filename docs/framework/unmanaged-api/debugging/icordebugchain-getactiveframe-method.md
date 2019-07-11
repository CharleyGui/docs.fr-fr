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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c79f3b3b976b83eb99f8aa26d38a1fe316de471a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745000"
---
# <a name="icordebugchaingetactiveframe-method"></a>ICorDebugChain::GetActiveFrame, méthode
Obtient l’actif (autrement dit, plus récente) frame sur la chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ppFrame`  
 [out] Un pointeur vers l’adresse d’un objet ICorDebugFrame qui représente l’actif (autrement dit, plus récente) frame sur la chaîne.  
  
## <a name="remarks"></a>Notes  
 Si aucun frame de pile managée est disponible, `ppFrame` a la valeur null.  
  
 Si le frame actif n’est pas disponible, l’appel réussira et `ppFrame` sera null. Cadres active ne sera pas disponibles pour les chaînes lancées en raison de CHAIN_ENTER_UNMANAGED et pour certaines chaînes lancées en raison de CHAIN_CLASS_INIT. Consultez l’énumération CorDebugChainReason.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

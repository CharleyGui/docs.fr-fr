---
title: ICorDebugChain::GetReason, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- GetReason
helpviewer_keywords:
- GetReason method [.NET Framework debugging]
- ICorDebugChain::GetReason method [.NET Framework debugging]
ms.assetid: 9f9f62b9-113a-4a98-8f9b-b593cef27b03
topic_type:
- apiref
ms.openlocfilehash: 58e40995012d98c1af6a41eb12d898c6b9b1d47b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719669"
---
# <a name="icordebugchaingetreason-method"></a>ICorDebugChain::GetReason, méthode

Obtient la raison pour le Genesis de cette chaîne d’appel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetReason (  
    [out] CorDebugChainReason *pReason  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pReason`  
 à Pointeur vers une valeur (combinaison d’opérations de bits) de l’énumération CorDebugChainReason, qui indique la raison du Genesis de cette chaîne d’appel.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

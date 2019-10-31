---
title: ICorDebugChain::GetNext, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetNext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetNext
helpviewer_keywords:
- GetNext method [.NET Framework debugging]
- ICorDebugChain::GetNext method [.NET Framework debugging]
ms.assetid: 8d9744a5-e08b-4ab2-9855-5c22711cc1e6
topic_type:
- apiref
ms.openlocfilehash: 132734dfb6ba9d70836638ab67564fc215e9bc40
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192128"
---
# <a name="icordebugchaingetnext-method"></a>ICorDebugChain::GetNext, méthode
Obtient la chaîne suivante de frames pour le thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetNext (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ppChain`  
 à Pointeur vers l’adresse d’un objet ICorDebugChain qui représente la chaîne suivante de frames pour le thread. Si cette chaîne est la dernière chaîne, `ppChain` a la valeur null.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

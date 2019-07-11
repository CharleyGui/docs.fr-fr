---
title: ICorDebugChain::GetCaller, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCaller
helpviewer_keywords:
- ICorDebugChain::GetCaller method [.NET Framework debugging]
- GetCaller method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: d0b8ab4b-d7d2-4fa0-945f-3d2b87e7e991
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d11693473dc4ed4438bbcad7f95c1b20adc1062b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744971"
---
# <a name="icordebugchaingetcaller-method"></a>ICorDebugChain::GetCaller, méthode
Obtient la chaîne qui a appelé cette chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ppChain`  
 [out] Pointeur vers l’adresse d’un objet ICorDebugChain qui représente la chaîne d’appel.  
  
 Si cette chaîne a été appelée spontanément (comme c’est le cas si cette chaîne ou le débogueur initialisé la pile des appels), `ppChain` sera null.  
  
## <a name="remarks"></a>Notes  
 La chaîne d’appels peut être sur un thread différent, si l’appel a été marshalé sur des threads.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

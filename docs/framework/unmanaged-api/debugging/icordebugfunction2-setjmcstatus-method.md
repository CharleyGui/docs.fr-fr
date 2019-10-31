---
title: ICorDebugFunction2::SetJMCStatus, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::SetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 22c27b01-2869-4214-b840-5921f7c874fc
topic_type:
- apiref
ms.openlocfilehash: 758364b2d63343e464b727d5a1c1817533a6acea
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137794"
---
# <a name="icordebugfunction2setjmcstatus-method"></a>ICorDebugFunction2::SetJMCStatus, méthode
Marque la fonction représentée par ce ICorDebugFunction2 pour Uniquement mon code pas à pas.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `bIsJustMyCode`  
 dans Affectez la valeur `true` pour marquer la fonction en tant que code utilisateur ; Sinon, affectez la valeur `false`.  
  
## <a name="return-values"></a>Valeurs de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|La fonction a été marquée avec succès.|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|La fonction n’a pas pu être marquée comme code utilisateur, car elle ne peut pas être déboguée.|  
  
## <a name="remarks"></a>Notes  
 Une Uniquement mon code pas à pas permet d’ignorer le code non-utilisateur. Le code utilisateur doit être un sous-ensemble du code pouvant être débogué.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

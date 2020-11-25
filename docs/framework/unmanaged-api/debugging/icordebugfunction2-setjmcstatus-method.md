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
ms.openlocfilehash: 55f219b5b834f365b87440e69bfa7d2c4e519235
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696088"
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
 dans Affectez la valeur à pour `true` marquer la fonction en tant que code utilisateur ; sinon, affectez à la valeur `false` .  
  
## <a name="return-values"></a>Valeurs de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|La fonction a été marquée avec succès.|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|La fonction n’a pas pu être marquée comme code utilisateur, car elle ne peut pas être déboguée.|  
  
## <a name="remarks"></a>Remarques  

 Une Uniquement mon code pas à pas permet d’ignorer le code non-utilisateur. Le code utilisateur doit être un sous-ensemble du code pouvant être débogué.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

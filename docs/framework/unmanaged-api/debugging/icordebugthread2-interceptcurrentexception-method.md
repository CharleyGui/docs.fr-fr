---
title: ICorDebugThread2::InterceptCurrentException, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.InterceptCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::InterceptCurrentException
helpviewer_keywords:
- InterceptCurrentException method [.NET Framework debugging]
- ICorDebugThread2::InterceptCurrentException method [.NET Framework debugging]
ms.assetid: 536d2357-1b97-49e0-a10c-c860aed74e6e
topic_type:
- apiref
ms.openlocfilehash: c25a03ef5bbba18da31787c911f83a1348badd4b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791456"
---
# <a name="icordebugthread2interceptcurrentexception-method"></a>ICorDebugThread2::InterceptCurrentException, méthode
Permet à un débogueur d’intercepter l’exception actuelle sur ce thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `pFrame`  
 dans Pointeur vers un ICorDebugFrame qui représente le frame de pile actif.  
  
## <a name="remarks"></a>Notes  
 La méthode `InterceptCurrentException` peut être appelée entre un rappel d’exception ([ICorDebugManagedCallback :: exception](icordebugmanagedcallback-exception-method.md) ou [ICorDebugManagedCallback2 :: exception](icordebugmanagedcallback2-exception-method.md)) et l’appel associé à [ICorDebugController :: continue](icordebugcontroller-continue-method.md).  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

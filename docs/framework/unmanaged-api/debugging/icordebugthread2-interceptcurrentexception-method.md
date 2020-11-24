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
ms.openlocfilehash: 96e3a90bcb7700915bfd3618d7bae40c0ff64a75
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678595"
---
# <a name="icordebugthread2interceptcurrentexception-method"></a>ICorDebugThread2::InterceptCurrentException, méthode

Permet à un débogueur d’intercepter l’exception actuelle sur ce thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pFrame`  
 dans Pointeur vers un ICorDebugFrame qui représente le frame de pile actif.  
  
## <a name="remarks"></a>Remarques  

 La `InterceptCurrentException` méthode peut être appelée entre un rappel d’exception ([ICorDebugManagedCallback :: exception](icordebugmanagedcallback-exception-method.md) ou [ICorDebugManagedCallback2 :: exception](icordebugmanagedcallback2-exception-method.md)) et l’appel associé à [ICorDebugController :: continue](icordebugcontroller-continue-method.md).  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

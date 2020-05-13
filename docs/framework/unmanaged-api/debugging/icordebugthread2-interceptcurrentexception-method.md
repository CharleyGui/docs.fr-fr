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
ms.openlocfilehash: d87f07e6cadf8c9b5a4d8bb3063333c26e2c4ff1
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379032"
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
  
## <a name="remarks"></a>Remarks  
 La `InterceptCurrentException` méthode peut être appelée entre un rappel d’exception ([ICorDebugManagedCallback :: exception](icordebugmanagedcallback-exception-method.md) ou [ICorDebugManagedCallback2 :: exception](icordebugmanagedcallback2-exception-method.md)) et l’appel associé à [ICorDebugController :: continue](icordebugcontroller-continue-method.md).  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

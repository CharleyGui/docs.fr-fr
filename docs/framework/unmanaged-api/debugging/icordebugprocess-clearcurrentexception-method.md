---
title: ICorDebugProcess::ClearCurrentException, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ClearCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ClearCurrentException
helpviewer_keywords:
- ClearCurrentException method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::ClearCurrentException method [.NET Framework debugging]
ms.assetid: 9e02ee1a-e495-4578-bfb5-b946274bede7
topic_type:
- apiref
ms.openlocfilehash: b8d20de990ff4a27a82590342494a307c986457e
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207392"
---
# <a name="icordebugprocessclearcurrentexception-method"></a>ICorDebugProcess::ClearCurrentException, méthode
Efface l’exception non managée actuelle sur le thread donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
## <a name="parameters"></a>Paramètres  
 `threadID`  
 dans ID du thread sur lequel l’exception non managée actuelle sera effacée.  
  
## <a name="remarks"></a>Remarks  
 Appelez cette méthode avant d’appeler [ICorDebugController :: continue](icordebugcontroller-continue-method.md) lorsqu’un thread a signalé une exception non managée qui doit être ignorée par l’élément débogué. Cela effacera à la fois les événements in-Band (IB) et hors bande (OOB) en suspens sur le thread donné. Tous les points d’arrêt OOB et les exceptions à une seule étape sont automatiquement effacés.  
  
 Utilisez [ICorDebugThread2 :: InterceptCurrentException,](icordebugthread2-interceptcurrentexception-method.md) pour intercepter l’exception managée actuelle sur un thread.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

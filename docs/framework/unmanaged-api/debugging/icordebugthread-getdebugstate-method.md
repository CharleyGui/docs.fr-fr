---
title: ICorDebugThread::GetDebugState, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetDebugState
helpviewer_keywords:
- GetDebugState method [.NET Framework debugging]
- ICorDebugThread::GetDebugState method [.NET Framework debugging]
ms.assetid: 9be27b0c-1d99-4722-b0d4-40cf6753ce5c
topic_type:
- apiref
ms.openlocfilehash: 13125f60f596cb8a80d9c42c51a979f632de494b
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379756"
---
# <a name="icordebugthreadgetdebugstate-method"></a>ICorDebugThread::GetDebugState, méthode
Obtient l’état de débogage actuel de cet objet ICorDebugThread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pState`  
 à Pointeur vers une combinaison d’opérations de bits de valeurs d’énumération CorDebugThreadState qui décrit l’état de débogage actuel de ce thread.  
  
## <a name="remarks"></a>Remarks  
 Si le processus est actuellement arrêté, `pState` représente l’état de débogage qui existe pour ce thread si le processus devait être poursuivi, et non l’état actuel réel de ce thread.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

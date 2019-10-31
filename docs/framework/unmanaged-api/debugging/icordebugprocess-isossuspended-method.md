---
title: ICorDebugProcess::IsOSSuspended, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsOSSuspended
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsOSSuspended
helpviewer_keywords:
- IsOSSuspended method [.NET Framework debugging]
- ICorDebugProcess::IsOSSuspended method [.NET Framework debugging]
ms.assetid: 83406cb2-5797-4402-872d-89c9516aefec
topic_type:
- apiref
ms.openlocfilehash: 21da69d4bff0f17eb607dda45fb7dbafea8c59f7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128771"
---
# <a name="icordebugprocessisossuspended-method"></a>ICorDebugProcess::IsOSSuspended, méthode
Obtient une valeur qui indique si le thread spécifié a été suspendu suite à l’arrêt de ce processus par le débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a>Paramètres  
 `threadID`  
 dans ID du thread en question.  
  
 `pbSuspended`  
 à Pointeur vers une valeur booléenne qui est `true` si le thread spécifié a été interrompue ; sinon *`pbSuspended` est `false`.  
  
## <a name="remarks"></a>Notes  
 Lorsque le thread spécifié a été suspendu à la suite de l’arrêt de ce processus par le débogueur, le nombre de suspensions Win32 du thread spécifié est incrémenté d’une unité. L’interface utilisateur du débogueur peut prendre en compte ces informations si le nombre de suspensions du système d’exploitation du thread est affiché pour l’utilisateur.  
  
 La méthode `IsOSSuspended` est logique uniquement dans le contexte du débogage non managé. Pendant le débogage managé, les threads sont suspendus de manière coopérative plutôt que d’être suspendus par le système d’exploitation.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

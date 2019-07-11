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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 275f62c8211f71f067d310dd4b3af2ddb11e93d7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755459"
---
# <a name="icordebugprocessisossuspended-method"></a>ICorDebugProcess::IsOSSuspended, méthode
Obtient une valeur qui indique si le thread spécifié a été interrompu suite à l’arrêt de ce processus de débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a>Paramètres  
 `threadID`  
 [in] L’ID du thread en question.  
  
 `pbSuspended`  
 [out] Un pointeur vers une valeur booléenne qui est `true` si le thread spécifié a été suspendue ; sinon *`pbSuspended` est `false`.  
  
## <a name="remarks"></a>Notes  
 Quand le thread spécifié a été suspendu suite à l’arrêt de ce processus de débogueur, le compteur de suspension Win32 du thread spécifié est incrémenté d’un. L’interface utilisateur (IU) du débogueur souhaiterez peut-être prendre en compte ces informations si elle affiche le système d’exploitation (OS) compteur de suspension du thread à l’utilisateur.  
  
 Le `IsOSSuspended` méthode est pertinent uniquement dans le contexte de débogage non managé. Pendant le débogage managé, les threads sont coopération suspendu plutôt que du système d’exploitation suspendu.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

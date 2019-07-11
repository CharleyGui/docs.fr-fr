---
title: ICorDebugProcess::GetHelperThreadID, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHelperThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHelperThreadID
helpviewer_keywords:
- GetHelperThreadID method [.NET Framework debugging]
- ICorDebugProcess::GetHelperThreadID method [.NET Framework debugging]
ms.assetid: 84e1e605-37c1-49a5-8e12-35db85654622
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad62b267eb0c49ff8fbefeb45b523c21edc705fe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766039"
---
# <a name="icordebugprocessgethelperthreadid-method"></a>ICorDebugProcess::GetHelperThreadID, méthode
Obtient l’ID de thread de système d’exploitation (se) du thread d’assistance interne du débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pThreadID`  
 [out] Un pointeur vers le système d’exploitation ID de thread du thread d’assistance interne du débogueur.  
  
## <a name="remarks"></a>Notes  
 Pendant le débogage managé et, il incombe du débogueur pour vous assurer que le thread avec l’ID spécifié continue de s’exécuter s’il rencontre un point d’arrêt placé par le débogueur. Un débogueur peut souhaiter également masquer ce thread à partir de l’utilisateur. Si aucun thread d’assistance n’existe encore, dans le processus le `GetHelperThreadID` méthode retourne la valeur zéro dans *`pThreadID`.  
  
 Vous ne pouvez pas mettre en cache l’ID de thread du thread d’assistance, car il peut changer au fil du temps. Vous devez redemander l’ID de thread à chaque événement d’arrêt.  
  
 L’ID du thread d’assistance du débogueur est correct sur chaque non managé [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) événement, ce qui permet un débogueur de déterminer l’ID de son thread d’assistance et masquez-la par rapport à l’utilisateur. Un thread qui est identifié comme un thread d’assistance pendant une fonction non managée `ICorDebugManagedCallback::CreateThread` événement n’est jamais exécuté le code utilisateur managé.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl. CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

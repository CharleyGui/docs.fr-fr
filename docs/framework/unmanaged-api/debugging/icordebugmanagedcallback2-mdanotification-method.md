---
title: ICorDebugManagedCallback2::MDANotification, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.MDANotification
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::MDANotification
helpviewer_keywords:
- MDANotification method [.NET Framework debugging]
- ICorDebugManagedCallback2::MDANotification method [.NET Framework debugging]
ms.assetid: 93f79627-bd31-4f4f-b95d-46a032a52fe4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4011932af6f4b058906c19566e4c1abe96b409db
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762097"
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a>ICorDebugManagedCallback2::MDANotification, méthode
Fournit une notification que l’exécution de code a rencontré un assistant débogage managé (MDA) dans l’application est en cours de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pController`  
 [in] Pointeur vers une interface ICorDebugController qui expose le processus ou d’un domaine d’application dans lequel le MDA s’est produite.  
  
 Un débogueur ne doit pas faire d’hypothèses si le contrôleur est un processus ou un domaine d’application, bien qu’il puisse toujours interroger l’interface pour effectuer une détermination.  
  
 `pThread`  
 [in] Pointeur vers une interface ICorDebugThread qui expose le thread géré sur lequel l’événement de débogage s’est produite.  
  
 Si le MDA s’est produite sur une fonction non managée de thread, la valeur de `pThread` sera null.  
  
 Vous devez obtenir l’ID de thread de système d’exploitation (se) à partir de l’objet MDA lui-même.  
  
 `pMDA`  
 [in] Un pointeur vers un [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) interface qui expose les informations de l’Assistant Débogage MANAGÉ.  
  
## <a name="remarks"></a>Notes  
 Un MDA est un avertissement heuristique et ne nécessitent aucune action de débogueur explicite à l’exception d’appel [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) pour reprendre l’exécution de l’application est en cours de débogage.  
  
 Le common language runtime (CLR) peut déterminer quels MDA sont déclenchés et les données se trouvent dans n’importe quel MDA donné à tout moment. Par conséquent, les débogueurs ne doivent pas générer de fonctionnalités nécessitant des modèles MDA spécifiques.  
  
 Assistants Débogage managé peuvent être en file d’attente et déclenchés juste après que l’Assistant Débogage MANAGÉ est rencontré. Cela peut se produire si le runtime doit attendre jusqu'à ce qu’il atteigne un point sans risque pour déclencher le MDA, au lieu de déclencher lorsqu’il le rencontre. Cela signifie également que le runtime peut déclencher plusieurs Assistants Débogage managé dans un seul ensemble de rappels en file d’attente (semblables à une opération d’événement « joindre »).  
  
 Un débogueur doit libérer la référence à un `ICorDebugMDA` instance immédiatement après le retour à partir de la `MDANotification` rappel, pour permettre au CLR de recycler la mémoire consommée par un Assistant Débogage MANAGÉ. Libérer l’instance peut améliorer les performances si de nombreux Assistants Débogage managé sont déclenchent.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Diagnostic d’erreurs avec les Assistants Débogage managé](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [ICorDebugManagedCallback2, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)

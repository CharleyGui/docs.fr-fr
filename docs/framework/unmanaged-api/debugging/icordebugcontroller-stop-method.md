---
title: ICorDebugController::Stop, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugController.Stop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Stop
helpviewer_keywords:
- Stop method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Stop method [.NET Framework debugging]
ms.assetid: c34e79be-a7fb-479e-8dec-d126a4c330e5
topic_type:
- apiref
ms.openlocfilehash: bb7eee0997a6c8671693accf2c95e6e06e0a4f2e
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976575"
---
# <a name="icordebugcontrollerstop-method"></a>ICorDebugController::Stop, méthode
Exécute un arrêt coopératif sur tous les threads qui exécutent du code managé dans le processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `dwTimeoutIgnored`  
 Non utilisé.  
  
## <a name="remarks"></a>Notes   
 `Stop`exécute un arrêt coopératif sur tous les threads exécutant du code managé dans le processus. Pendant une session de débogage managée uniquement, les threads non managés peuvent continuer à s’exécuter (mais ils seront bloqués lors de la tentative d’appel de code managé). Pendant une session de débogage d’interopérabilité, les threads non managés sont également arrêtés. La `dwTimeoutIgnored` valeur est actuellement ignorée et traitée comme infinie (-1). Si l’arrêt coopératif échoue en raison d’un blocage, tous les threads sont suspendus et E_TIMEOUT est retourné.  
  
> [!NOTE]
> `Stop`est la seule méthode synchrone de l’API de débogage. Lorsque `Stop` retourne S_OK, le processus est arrêté. Aucun rappel n’est fourni pour notifier les écouteurs de l’arrêt. Le débogueur doit appeler [ICorDebugController :: continue](icordebugcontroller-continue-method.md) pour permettre au processus de reprendre.  
  
 Le débogueur gère un compteur d’arrêt. Lorsque le compteur atteint zéro, le contrôleur reprend. Chaque appel à `Stop` ou à chaque rappel distribué incrémente le compteur. Chaque appel à `ICorDebugController::Continue` décrémente le compteur.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

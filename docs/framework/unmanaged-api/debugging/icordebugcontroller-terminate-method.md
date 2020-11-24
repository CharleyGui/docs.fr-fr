---
title: ICorDebugController::Terminate, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugController.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Terminate
helpviewer_keywords:
- Terminate method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Terminate method [.NET Framework debugging]
ms.assetid: 4275af0c-b5a7-4e4c-97c9-7e41f36b2dd8
topic_type:
- apiref
ms.openlocfilehash: 460aeeca9d62ce91a11a24d774c8e681ed4f00ca
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679804"
---
# <a name="icordebugcontrollerterminate-method"></a>ICorDebugController::Terminate, méthode

Termine le processus avec le code de sortie spécifié.  
  
> [!NOTE]
> Cette méthode est un wrapper pour la `TerminateProcess` fonction Win32. Par conséquent, `Terminate` utilise le code de sortie de la même façon que la `TerminateProcess` fonction Win32.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `exitCode`  
 dans Valeur numérique qui est le code de sortie. Les valeurs numériques valides sont définies dans Winbase. h.  
  
## <a name="remarks"></a>Remarques  

 Si le processus est arrêté lorsque `Terminate` est appelé, le processus doit être poursuivi à l’aide de la méthode [ICorDebugController :: continue](icordebugcontroller-continue-method.md) afin que le débogueur reçoive la confirmation de l’arrêt par le biais du rappel [ICorDebugManagedCallback :: ExitProcess](icordebugmanagedcallback-exitprocess-method.md) ou [ICorDebugManagedCallback :: ExitAppDomain,](icordebugmanagedcallback-exitappdomain-method.md) .  
  
> [!NOTE]
> Cette méthode n’est pas implémentée par un domaine d’application. Autrement dit, il n’est pas implémenté au <xref:System.AppDomain> niveau.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

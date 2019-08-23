---
title: ICorDebugFrame, interface
ms.date: 03/30/2017
api_name:
- ICorDebugFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame
helpviewer_keywords:
- ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 0c48f764-3c64-4602-b2f4-4ffc60eb2c65
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4744ea67d0ce0d9ad2b13c45bdef65f884ef925
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937003"
---
# <a name="icordebugframe-interface"></a>ICorDebugFrame, interface

Représente un frame sur la pile en cours.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CreateStepper, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|Obtient un ICorDebugStepper pour exécuter des opérations pas à pas `ICorDebugFrame`relatives à ce.|  
|[GetCallee, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|Obtient un pointeur vers le `ICorDebugFrame` dans la chaîne actuelle appelée par ce frame, ou retourne la valeur null s’il s’agit du frame le plus profond dans la chaîne.|  
|[GetCaller, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|Obtient un pointeur vers le `ICorDebugFrame` dans la chaîne actuelle qui a appelé ce frame, ou retourne la valeur null s’il s’agit du frame le plus à l’extérieur dans la chaîne.|  
|[GetChain, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|Obtient un pointeur vers l’ICorDebugChain dont `ICorDebugFrame` il fait partie.|  
|[GetCode, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|Obtient un pointeur vers le ICorDebugCode associé à ce frame de pile.|  
|[GetFunction, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|Obtient un pointeur vers le ICorDebugFunction qui contient le code associé à ce frame de pile.|  
|[GetFunctionToken, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|Obtient le jeton de métadonnées pour la fonction qui contient le code associé à ce frame de pile.|  
|[GetStackRange, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|Obtient la plage d’adresses absolues du frame de pile représenté `ICorDebugFrame`par ce.|  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug. idl, CorDebug. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

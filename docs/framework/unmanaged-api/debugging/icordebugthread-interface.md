---
title: ICorDebugThread, interface
ms.date: 03/30/2017
api_name:
- ICorDebugThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread
helpviewer_keywords:
- ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3930fd9b-2bc3-4b72-80a0-b6eeb94d60c6
topic_type:
- apiref
ms.openlocfilehash: c7333f4210d0a2ec4ff71a0fac0ea00068fecc57
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133499"
---
# <a name="icordebugthread-interface"></a>ICorDebugThread, interface
Représente un thread de processus. La durée de vie d'une instance `ICorDebugThread` est la même que la durée de vie du thread qu'elle représente.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[ClearCurrentException, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|Cette méthode n’est pas implémentée. Ne pas l'utiliser.|  
|[CreateEval, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|Crée un objet ICorDebugEval qui fonctionne sur cette `ICorDebugThread`.|  
|[CreateStepper, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|Crée un objet ICorDebugStepper qui permet d’effectuer un pas à pas détaillé dans le frame actif dans cette `ICorDebugThread`.|  
|[EnumerateChains, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|Obtient un pointeur d’interface vers un énumérateur ICorDebugChainEnum qui contient toutes les chaînes de pile de cette `ICorDebugThread`.|  
|[GetActiveChain, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|Obtient un pointeur d’interface vers l’ICorDebugChain actif sur cette `ICorDebugThread`.|  
|[GetActiveFrame, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|Obtient un pointeur d’interface vers le ICorDebugFrame actif sur cette `ICorDebugThread`.|  
|[GetAppDomain, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|Obtient un pointeur d’interface vers le domaine d’application dans lequel ce `ICorDebugThread` est en cours d’exécution.|  
|[GetCurrentException, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|Obtient un pointeur d’interface vers un objet ICorDebugValue qui représente une exception actuellement levée par du code managé.|  
|[GetDebugState, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|Obtient une valeur CorDebugThreadState qui décrit l’état de débogage actuel de ce `ICorDebugThread`.|  
|[GetHandle, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|Obtient le handle actuel pour la partie active de cette `ICorDebugThread`.|  
|[GetID, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|Obtient l’identificateur de système d’exploitation actuel de la partie active de ce `ICorDebugThread`.|  
|[GetObject, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|Obtient un pointeur d’interface vers le thread common language runtime (CLR).|  
|[GetProcess, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|Obtient un pointeur d’interface vers le processus dont ce `ICorDebugThread` forme un composant.|  
|[GetRegisterSet, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|Obtient un pointeur d’interface vers le jeu de registres associé à ce `ICorDebugThread`.|  
|[GetUserState, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|Obtient une combinaison d’opérations de bits de valeurs CorDebugUserState, qui décrivent l’état actuel de cette `ICorDebugThread`.|  
|[SetDebugState, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|Définit une combinaison au niveau du bit des valeurs `CorDebugThreadState` qui décrivent l’état de débogage de ce `ICorDebugThread`.|  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

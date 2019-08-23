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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1517d686c50923f5599e33436e0ad6126e8be140
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923141"
---
# <a name="icordebugthread-interface"></a>ICorDebugThread, interface
Représente un thread de processus. La durée de vie d'une instance `ICorDebugThread` est la même que la durée de vie du thread qu'elle représente.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[ClearCurrentException, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|Cette méthode n’est pas implémentée. Ne pas l'utiliser.|  
|[CreateEval, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|Crée un objet ICorDebugEval qui fonctionne sur ce `ICorDebugThread`.|  
|[CreateStepper, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|Crée un objet ICorDebugStepper qui permet d’effectuer un pas à pas détaillé `ICorDebugThread`dans le frame actif dans ce.|  
|[EnumerateChains, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|Obtient un pointeur d’interface vers un énumérateur ICorDebugChainEnum qui contient toutes les chaînes de pile `ICorDebugThread`dans ce.|  
|[GetActiveChain, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|Obtient un pointeur d’interface vers l’ICorDebugChain actif sur `ICorDebugThread`ce.|  
|[GetActiveFrame, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|Obtient un pointeur d’interface vers le ICorDebugFrame actif sur `ICorDebugThread`ce.|  
|[GetAppDomain, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|Obtient un pointeur d’interface vers le domaine d’application dans `ICorDebugThread` lequel ce est actuellement en cours d’exécution.|  
|[GetCurrentException, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|Obtient un pointeur d’interface vers un objet ICorDebugValue qui représente une exception actuellement levée par du code managé.|  
|[GetDebugState, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|Obtient une valeur CorDebugThreadState qui décrit l’état de débogage actuel `ICorDebugThread`de ce.|  
|[GetHandle, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|Obtient le handle actuel pour la partie active de ce `ICorDebugThread`.|  
|[GetID, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|Obtient l’identificateur de système d’exploitation actuel de la partie active de `ICorDebugThread`ce.|  
|[GetObject, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|Obtient un pointeur d’interface vers le thread common language runtime (CLR).|  
|[GetProcess, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|Obtient un pointeur d’interface vers le processus dont `ICorDebugThread` se forme un composant.|  
|[GetRegisterSet, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|Obtient un pointeur d’interface vers le jeu de registres associé `ICorDebugThread`à ce.|  
|[GetUserState, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|Obtient une combinaison d’opérations de bits de valeurs CorDebugUserState, qui décrivent l' `ICorDebugThread`état actuel de ce.|  
|[SetDebugState, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|Définit une combinaison d’opérations `CorDebugThreadState` de bits de valeurs qui décrivent l’état de `ICorDebugThread`débogage de ce.|  
  
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

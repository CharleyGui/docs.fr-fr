---
title: ICorDebugChain, interface
ms.date: 03/30/2017
api_name:
- ICorDebugChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain
helpviewer_keywords:
- ICorDebugChain interface [.NET Framework debugging]
ms.assetid: f671f519-1cb3-4ae5-b9f1-abc5e783459f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 93ada40bd88e53cd06f5e8d8136b2d527d7741e6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969303"
---
# <a name="icordebugchain-interface"></a>ICorDebugChain, interface

Représente un segment d'une pile des appels physique ou logique.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnumerateFrames, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-enumerateframes-method.md)|Obtient un énumérateur qui contient tous les frames de pile managés dans la chaîne, en commençant par le frame le plus récent.|  
|[GetActiveFrame, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getactiveframe-method.md)|Obtient le frame actif (c’est-à-dire le plus récent) de la chaîne.|  
|[GetCallee, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcallee-method.md)|Obtient la chaîne qui a été appelée par cette chaîne.|  
|[GetCaller, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcaller-method.md)|Obtient la chaîne qui a appelé cette chaîne.|  
|[GetContext, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcontext-method.md)|Non implémenté.|  
|[GetNext, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getnext-method.md)|Obtient la chaîne suivante de frames pour le thread.|  
|[GetPrevious, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getprevious-method.md)|Obtient la chaîne précédente des frames pour le thread.|  
|[GetReason, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)|Obtient la raison pour le Genesis de cette chaîne d’appel.|  
|[GetRegisterSet, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getregisterset-method.md)|Obtient le Registre défini pour la partie active de cette chaîne.|  
|[GetStackRange, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getstackrange-method.md)|Obtient la plage d’adresses du segment de pile pour cette chaîne.|  
|[GetThread, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getthread-method.md)|Obtient le thread physique dont fait partie cette chaîne d’appel.|  
|[IsManaged, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-ismanaged-method.md)|Obtient une valeur qui indique si cette chaîne exécute du code managé.|  
  
## <a name="remarks"></a>Notes  
 Les frames de pile dans une chaîne occupent un espace de pile contigu et partagent le même thread et le même contexte. Une chaîne peut représenter des chaînes de code managées ou non managées. Une instance `ICorDebugChain` vide représente une chaîne de code non managé.  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug. idl, CorDebug. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

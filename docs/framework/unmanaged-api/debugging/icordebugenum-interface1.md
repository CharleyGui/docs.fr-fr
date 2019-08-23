---
title: ICorDebugEnum, interface
ms.date: 03/30/2017
api_name:
- ICorDebugEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum
helpviewer_keywords:
- ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 80be7efe-2c32-4b9f-8c52-40c6f6268219
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b25c47e101ad0fb8e8cbdbb2718a41c9be6c0c22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931986"
---
# <a name="icordebugenum-interface"></a>ICorDebugEnum, interface

Sert d’interface de base abstraite pour les énumérateurs utilisés par une application de débogage.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Clone, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-clone-method.md)|Crée une copie de cet `ICorDebugEnum` objet.|  
|[GetCount, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-getcount-method.md)|Obtient le nombre d’éléments dans l’énumération.|  
|[Reset, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-reset-method.md)|Déplace le curseur au début de l’énumération.|  
|[Skip, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-skip-method.md)|Déplace le curseur vers l’avant dans l’énumération d’après le nombre d’éléments spécifié.|  
  
## <a name="remarks"></a>Notes  
 Les énumérateurs suivants dérivent de `ICorDebugEnum`:  
  
- "ICorDebugAppDomainEnum"  
  
- "ICorDebugAssemblyEnum"  
  
- [ICorDebugBlockingObjectEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
  
- "ICorDebugBreakpointEnum"  
  
- "ICorDebugChainEnum"  
  
- "ICorDebugCodeEnum"  
  
- ICorDebugErrorInfoEnum  
  
- [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
  
- "ICorDebugFrameEnum"  
  
- [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
  
- [ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
  
- [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
  
- [ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
  
- "ICorDebugModuleEnum"  
  
- "ICorDebugObjectEnum"  
  
- "ICorDebugProcessEnum"  
  
- "ICorDebugStepperEnum"  
  
- "ICorDebugThreadEnum"  
  
- "ICorDebugTypeEnum"  
  
- "ICorDebugValueEnum"  
  
- [ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug. idl, CorDebug. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

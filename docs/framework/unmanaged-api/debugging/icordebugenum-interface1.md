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
ms.openlocfilehash: b208444de3b427329988f27b9d252b54143b7240
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698791"
---
# <a name="icordebugenum-interface"></a>ICorDebugEnum, interface

Sert d’interface de base abstraite pour les énumérateurs utilisés par une application de débogage.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Clone, méthode](icordebugenum-clone-method.md)|Crée une copie de cet objet `ICorDebugEnum`.|  
|[GetCount, méthode](icordebugenum-getcount-method.md)|Obtient le nombre d’éléments dans l’énumération.|  
|[Reset, méthode](icordebugenum-reset-method.md)|Déplace le curseur au début de l’énumération.|  
|[Skip, méthode](icordebugenum-skip-method.md)|Déplace le curseur vers l’avant dans l’énumération d’après le nombre d’éléments spécifié.|  
  
## <a name="remarks"></a>Remarques  

 Les énumérateurs suivants dérivent de `ICorDebugEnum` :  
  
- ICorDebugAppDomainEnum  
  
- ICorDebugAssemblyEnum  
  
- [ICorDebugBlockingObjectEnum](icordebugblockingobjectenum-interface.md)  
  
- ICorDebugBreakpointEnum  
  
- ICorDebugChainEnum  
  
- ICorDebugCodeEnum  
  
- ICorDebugErrorInfoEnum  
  
- [Icordebugexceptionobjectcallstackenum,](icordebugexceptionobjectcallstackenum-interface.md)  
  
- ICorDebugFrameEnum  
  
- [Icordebuggcreferenceenum,](icordebuggcreferenceenum-interface.md)  
  
- [Icordebugguidtotypeenum,](icordebugguidtotypeenum-interface.md)  
  
- [Icordebugheapenum,](icordebugheapenum-interface.md)  
  
- [Icordebugheapsegmentenum,](icordebugheapsegmentenum-interface.md)  
  
- ICorDebugModuleEnum  
  
- ICorDebugObjectEnum  
  
- ICorDebugProcessEnum  
  
- ICorDebugStepperEnum  
  
- ICorDebugThreadEnum  
  
- ICorDebugTypeEnum  
  
- ICorDebugValueEnum  
  
- [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)

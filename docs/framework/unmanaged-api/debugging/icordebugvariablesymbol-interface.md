---
title: ICorDebugVariableSymbol, interface
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3fb2538894184c19bc107ce52cbef3ac86a97345
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967979"
---
# <a name="icordebugvariablesymbol-interface"></a>ICorDebugVariableSymbol, interface
Récupère les informations sur les symboles de débogage pour une variable.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetName, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getname-method.md)|Obtient le nom d'une variable.|  
|[GetSize, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getsize-method.md)|Obtient la taille d'une variable en octets.|  
|[GetSlotIndex, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getslotindex-method.md)|Obtient l'index d'emplacement géré d'une variable locale.|  
|[GetValue, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getvalue-method.md)|Obtient la valeur d'une variable sous forme d'un tableau d'octets.|  
|[SetValue, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-setvalue-method.md)|Affecte la valeur d'un tableau d'octets à une variable.|  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
> Cette interface est uniquement disponible avec .NET Native. Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug. idl, CorDebug. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)

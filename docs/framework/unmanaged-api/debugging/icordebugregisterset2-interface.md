---
title: ICorDebugRegisterSet2, interface
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2
helpviewer_keywords:
- ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: d7fbccbf-3b6b-4db8-a96d-768e1cb6b1a6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95e8ad1ddce57252b7af3c7d72e8f8eb7bdb76b0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935089"
---
# <a name="icordebugregisterset2-interface"></a>ICorDebugRegisterSet2, interface
Étend les fonctionnalités de l’interface [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) pour les plateformes matérielles qui ont plus de 64 registres.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetRegisters, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregisters-method.md)|Obtient la valeur de chaque registre (sur l’ordinateur qui exécute actuellement le code) spécifié par le masque de bits.|  
|[GetRegistersAvailable, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregistersavailable-method.md)|Obtient un tableau d’octets qui fournit une bitmap des registres disponibles.|  
|[SetRegisters, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-setregisters-method.md)|Non implémenté dans la version 2,0 de .NET Framework.|  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug. idl, CorDebug. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [ICorDebugRegisterSet, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)

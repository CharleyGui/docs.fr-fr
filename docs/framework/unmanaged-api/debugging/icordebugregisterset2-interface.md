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
ms.openlocfilehash: f989f1c1f29c63af54ff125f4ad1aaa2bcee6757
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378203"
---
# <a name="icordebugregisterset2-interface"></a>ICorDebugRegisterSet2, interface
Étend les fonctionnalités de l’interface [ICorDebugRegisterSet](icordebugregisterset-interface.md) pour les plateformes matérielles qui ont plus de 64 registres.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetRegisters, méthode](icordebugregisterset2-getregisters-method.md)|Obtient la valeur de chaque registre (sur l’ordinateur qui exécute actuellement le code) spécifié par le masque de bits.|  
|[GetRegistersAvailable, méthode](icordebugregisterset2-getregistersavailable-method.md)|Obtient un tableau d’octets qui fournit une bitmap des registres disponibles.|  
|[SetRegisters, méthode](icordebugregisterset2-setregisters-method.md)|Non implémenté dans la version 2,0 de .NET Framework.|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [ICorDebugRegisterSet, interface](icordebugregisterset-interface.md)

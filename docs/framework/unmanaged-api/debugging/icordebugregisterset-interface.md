---
title: ICorDebugRegisterSet, interface
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet
helpviewer_keywords:
- ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: d3d9676d-0b87-4bc3-b679-7bbc7a186c88
topic_type:
- apiref
ms.openlocfilehash: f435db28d5c85d576f69e7612841fc46ae142332
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792079"
---
# <a name="icordebugregisterset-interface"></a>ICorDebugRegisterSet, interface
Représente l’ensemble des registres disponibles sur l’ordinateur qui exécute actuellement le code.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetRegisters, méthode](icordebugregisterset-getregisters-method.md)|Obtient la valeur de chaque registre (sur l’ordinateur qui exécute actuellement le code) spécifié par le masque de bits.|  
|[GetRegistersAvailable, méthode](icordebugregisterset-getregistersavailable-method.md)|Obtient un masque de bits indiquant quels registres de cette `ICorDebugRegisterSet` sont actuellement disponibles.|  
|[GetThreadContext, méthode](icordebugregisterset-getthreadcontext-method.md)|Obtient le contexte du thread actuel.|  
|[SetRegisters, méthode](icordebugregisterset-setregisters-method.md)|Non implémenté pour la version 2,0 de .NET Framework.|  
|[SetThreadContext, méthode](icordebugregisterset-setthreadcontext-method.md)|Non implémenté pour le .NET Framework 2,0.|  
  
## <a name="remarks"></a>Notes  
 L’interface `ICorDebugRegisterSet` prend en charge uniquement les registres 32 bits. Utilisez l’interface [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) sur les plateformes telles que IA-64 qui requièrent des registres supplémentaires.  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [ICorDebugRegisterSet2, interface](icordebugregisterset2-interface.md)

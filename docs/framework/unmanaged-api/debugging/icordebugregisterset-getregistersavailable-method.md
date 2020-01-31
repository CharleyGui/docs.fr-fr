---
title: ICorDebugRegisterSet::GetRegistersAvailable, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable
helpviewer_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable method [.NET Framework debugging]
- GetRegistersAvailable method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 4ba08ffa-55a2-4662-9d6d-4738f1db60c9
topic_type:
- apiref
ms.openlocfilehash: b137b956e06a2b2954918e4024860f9b234e7583
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792108"
---
# <a name="icordebugregistersetgetregistersavailable-method"></a>ICorDebugRegisterSet::GetRegistersAvailable, méthode
Obtient un masque de bits indiquant les registres actuellement disponibles dans ce [ICorDebugRegisterSet](icordebugregisterset-interface.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `pAvailable`  
 à Masque de bits qui indique les registres actuellement disponibles.  
  
## <a name="remarks"></a>Notes  
 Un registre peut ne pas être disponible si sa valeur ne peut pas être déterminée pour la situation donnée.  
  
 Le masque retourné contient un bit pour chaque registre (1 < < l’index du registre). La valeur de bit est 1 si le Registre est disponible, ou 0 s’il n’est pas disponible.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugRegisterSet, interface](icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2, interface](icordebugregisterset2-interface.md)

---
title: 'ICorDebugVirtualUnwinder:: Next, méthode'
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20a3d4bac42731bc94ecef7a0756392c8c0882fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967924"
---
# <a name="icordebugvirtualunwindernext-method"></a>ICorDebugVirtualUnwinder:: Next, méthode
Avance jusqu'au contexte de l'appelant.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="parameters"></a>Paramètres  
 Aucune.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK` en cas de réussite du déroulement ou `CORDBG_S_AT_END_OF_STACK` si le déroulement ne peut pas être effectué étant donné qu'il ne reste plus de frames.  
  
 Si un HRESULT indiquant un échec est retourné, les API ICorDebug retournent `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Notes  
 L'explorateur de pile doit vérifier sa progression vers l'avant. Ainsi, un appel à `Next` doit retourner un HRESULT indiquant un échec ou `CORDBG_S_AT_END_OF_STACK`. Si `S_OK` vous retournez indéfiniment, vous risquez de provoquer une boucle infinie.  
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug. idl, CorDebug. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugMemoryBuffer, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

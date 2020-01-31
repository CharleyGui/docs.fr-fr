---
title: Méthode ICorDebugVariableSymbol::GetSlotIndex
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
ms.openlocfilehash: 3510daffb55bdb22aa5f835bf27157e7c8428509
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790891"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a>Méthode ICorDebugVariableSymbol::GetSlotIndex
Obtient l'index d'emplacement géré d'une variable locale.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `pSlotIndex`  
 [out] Pointeur vers l'index d'emplacement de la variable locale.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK` si l'opération a réussi. `E_FAIL` si la variable est un argument de fonction.  
  
## <a name="remarks"></a>Notes  
 L'index emplacement managé d'une variable locale peut être utilisé pour récupérer des informations de métadonnées de la variable.  
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugVariableSymbol, interface](icordebugvariablesymbol-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)

---
title: Méthode ICorDebugVariableSymbol::GetSlotIndex
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
ms.openlocfilehash: fc42517cb95dfc14c472b5bb9111ebd70639cee7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725987"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a>Méthode ICorDebugVariableSymbol::GetSlotIndex

Obtient l'index d'emplacement géré d'une variable locale.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pSlotIndex`  
 [out] Pointeur vers l'index d'emplacement de la variable locale.  
  
## <a name="return-value"></a>Valeur renvoyée  

 `S_OK` si l'opération a réussi. `E_FAIL` si la variable est un argument de fonction.  
  
## <a name="remarks"></a>Remarques  

 L'index emplacement managé d'une variable locale peut être utilisé pour récupérer des informations de métadonnées de la variable.  
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugVariableSymbol, interface](icordebugvariablesymbol-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)

---
title: ICorDebugInstanceFieldSymbol::GetOffset, méthode
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
ms.openlocfilehash: f7c13d397b39698bdf1a22f14820680e1fd0a25f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782291"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a>ICorDebugInstanceFieldSymbol::GetOffset, méthode
Obtient l'offset en octets de ce champ d'instance dans sa classe parente.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `pcbOffset`  
 Pointeur vers le nombre d'octets correspondant à l'offset de ce champ d'instance dans sa classe parente.  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugInstanceFieldSymbol, interface](icordebuginstancefieldsymbol-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)

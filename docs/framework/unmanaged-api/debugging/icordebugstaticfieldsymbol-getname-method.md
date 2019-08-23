---
title: ICorDebugStaticFieldSymbol::GetName, méthode
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2187a205b41388d191ad4f06db6d6caa86971e13
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913417"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a>ICorDebugStaticFieldSymbol::GetName, méthode
Obtient le nom du champ static.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `cchName`  
 [in] Nombre de caractères dans la mémoire tampon `szName`.  
  
 `pcchName`  
 [out] Pointeur vers le nombre de caractères réellement écrits dans la mémoire tampon `szName`.  
  
 `szName`  
 [out] Tableau de caractères qui stocke le nom retourné.  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug. idl, CorDebug. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugStaticFieldSymbol, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

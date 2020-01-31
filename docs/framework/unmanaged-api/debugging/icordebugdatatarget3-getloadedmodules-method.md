---
title: Méthode ICorDebugDataTarget3::GetLoadedModules
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
ms.openlocfilehash: d4c22146422085daa4dc9d90ae5b3735a12500c2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793552"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a>Méthode ICorDebugDataTarget3::GetLoadedModules
Obtient la liste des modules qui ont été chargés jusqu'à présent.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `cRequestedModules`  
 [in] Nombre de modules pour lesquels des informations sont demandées.  
  
 `pcFetchedModules`  
 [out] Pointeur vers le nombre de modules à propos desquels des informations ont été retournées.  
  
 `pLoadedModules`  
 à Pointeur vers un tableau d’objets [ICorDebugLoadedModule](icordebugloadedmodule-interface.md) qui fournissent des informations sur les modules chargés.  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugDataTarget3, interface](icordebugdatatarget3-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)

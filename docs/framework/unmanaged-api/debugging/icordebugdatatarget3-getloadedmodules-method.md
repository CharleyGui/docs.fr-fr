---
title: ICorDebugDataTarget3::GetLoadedModules (méthode)
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
ms.openlocfilehash: c3565f4f9284bc121b0e2d3b0885cbea927acfdd
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976419"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a>ICorDebugDataTarget3::GetLoadedModules (méthode)
Obtient la liste des modules qui ont été chargés jusqu'à présent.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `cRequestedModules`  
 [in] Nombre de modules pour lesquels des informations sont demandées.  
  
 `pcFetchedModules`  
 [out] Pointeur vers le nombre de modules à propos desquels des informations ont été retournées.  
  
 `pLoadedModules`  
 à Pointeur vers un tableau d’objets [ICorDebugLoadedModule](icordebugloadedmodule-interface.md) qui fournissent des informations sur les modules chargés.  
  
## <a name="remarks"></a>Notes   
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugDataTarget3 (interface)](icordebugdatatarget3-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
